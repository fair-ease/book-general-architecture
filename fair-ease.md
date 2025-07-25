
# Introduction 

To address the diverse expectations of the pilots and meet the grant
agreement requirements, FAIR-EASE project followed an iterative
development approach (aka DevCycles) structured around three main
phases:

1.  Needs assessment and initial architecture sketch

2.  Evaluation of technical solutions

3.  Implementation in project mode

This approach enabled close collaboration across work packages and led
to the development of the following shared and integrated vision,
including Key Exploitable Results (KERs):

![](media/image42.png){width="6.692716535433071in" height="4.0in"}

[]{#_heading=h.zc12meb1s8s4 .anchor}*Figure 1 - FAIR-EASE's general
architecture*

This architecture is built around three key building blocks for
data-driven research: data discovery, data access, and data analysis.
These services are integrated within one or more e-infrastructures
called Earth Analytics Lab (EAL), which can be interconnected through
federating capabilities, following a system-of-systems approach. The
core objective of the EAL is to provide services that support
collaborative science and promote the adoption of FAIR principles across
all research products.

> ![](media/image22.png){width="3.560465879265092in"
> height="3.715751312335958in"}

[]{#_heading=h.w3b5ichmu3jd .anchor}*Figure 2 - EAL as an integrated
e-infrastructure for collaborative Earth System science*

A 3-day hackathon in March 2025 marked the culmination of this desire to
collaborate on shared challenges, involving a cross-domain analysis of
the Hunga Tonga volcanic eruption and the use of TerriaMap to visualize
heterogeneous datasets.

For clarity and ease of understanding, this deliverable will first
summarise the main elements related to the Data Discovery (lead by WP2)
and Data Access (lead by WP4) building blocks. It will then present the
analysis services, before providing an overview of the three EAL
implementations. These implementations are used by the FAIR-EASE
demonstrators (lead by WP5).

# Dive into data

One of the main challenges of FAIR-EASE is to simplify the process of
exploring and using data. This involves providing efficient and
user-focused services for data discovery, data access, and data
analysis, all tailored to the specific needs of the pilot use cases and
Earth System science.

![](media/image29.png){width="6.296870078740158in"
height="0.8542125984251968in"}

[]{#_heading=h.umxn4bgr8yr7 .anchor}*Figure 3 - From discovery to
analysis: a data diving journey*

## Data Discovery

The **Interdisciplinary Data Discovery and Access Service** (IDDAS)
focuses on providing a semantically enriched metadata catalogue based on
a customised DCAT application profile (DCAT-FE), enabling seamless data
discovery and access across domains and platforms, both for human
([[https://fair-ease-iddas.maris.nl]{.underline}](https://fair-ease-iddas.maris.nl/))
and machine
([[https://fair-ease-iddas.maris.nl/sparql]{.underline}](https://fair-ease-iddas.maris.nl/sparql)).

![](media/image27.png){width="6.692716535433071in"
height="3.763888888888889in"}

[]{#_heading=h.ofir2kfi56qq .anchor}*Figure 4 - IDDAS Architecture*

Full details of IDDAS are available in D2.5 - "FAIR-EASE Data Discovery
and Access Service - Final Release".

## Data access

The FAIR-EASE project explored both server-side mechanisms, which aim to
improve performance, scalability and interoperability in heterogeneous
data infrastructures, and client-side usage, which focus on simplifying
data access for users, particularly those without in-depth technical
expertise, but also the robustness of applications over time.

By taking these two perspectives into account, the project ensures that
data can be accessed smoothly, efficiently and transparently, whether
through automated workflows or user-friendly interfaces tailored to real
scientific use cases.

For the server-side part we evaluated four technical solutions: S3 /
ARCO combination for serverless and cloud-ready subsetting, STAC /
OpenEO combination for unified data access and remote process on
datacubes, Beacon for efficient data access and data harmonisation
capabilities, and Apache Iceberg for managing large-scale tabular data.

### Server side data access

#### S3, a cloud filesystem

S3 (Simple Storage Service) is a widely adopted cloud-based object
storage system that allows data to be stored and accessed as discrete
objects, each associated with both the actual data content and metadata.

![](media/image28.png){width="5.008858267716535in"
height="1.407843394575678in"}

[]{#_heading=h.6t96xzkh6pwo .anchor}*Figure 5 - Storage types
comparison*[^3]

Unlike traditional file systems, S3 operates over the HTTP protocol
along with API's, making it highly scalable and accessible across
distributed systems. It supports fine-grained access control, enabling
secure, policy-driven access to individual objects. UCA has provided a
1TB S3 endpoint to help users become acculturated to this technology.

Additionally, S3 API supports HTTP range requests[^4], allowing users or
applications to retrieve specific fragments of a file, using byte
ranges, without needing to download the entire file. This is an
essential feature for large-scale scientific datasets and cloud-native
workflows. This feature is notably used in particular by the Volcano
Space Observatory to optimize access to a specific satellite image from
a TIFF file supplied by Copernicus Data Space Ecosystem.

![](media/image33.png){width="3.6027351268591428in"
height="2.2886679790026245in"}

[]{#_heading=h.ycmdenv04vce .anchor}*Figure 6- HTTP range requests*

#### ARCO formats

**Analysis-Ready, Cloud-Optimised** (ARCO) formats, such as Zarr or
Apache Parquet, are designed to facilitate scalable and efficient access
to large data sets. These formats are said to be "analysis-ready", as
they organize data into manageable chunks indexed in embedded metadata,
making them ideal for intensive data processing (i.e. parallel or
distributed processing), such as big data or data science.

![](media/image26.png){width="5.589492563429571in"
height="3.0063867016622923in"}

[]{#_heading=h.1i9tn1ubwcw9 .anchor}*Figure 7 - Zarr structure*[^5]

They are said to be "cloud-optimised", as they are compatible with HTTP
range requests, i.e. the chunks and metadata are organized in such a way
that the chunks of interest can be accessed without downloading the
entire file. This design provides a serverless subsetting service and
greatly simplifies use. For example, a multidimensional dataset can be
loaded in a single line using tools such as
*xarray.open_dataset("s3://\.../file.zarr")*. The relevant chunks will
be downloaded only when a compute is performed.

Extensions to these formats exist to manage geospatial data (e.g.
GeoZarr, GeoParquet). It provides simplified integration with tools such
as QGIS desktop or GDAL, ensuring interoperability between desktop
applications and cloud-native platforms.

![](media/image32.png){width="6.739583333333333in"
height="4.239583333333333in"}

[]{#_heading=h.tm7ue41ef0j5 .anchor}*Figure 8 - Cloud-Optimised
Geospatial Formats*[^6]

FAIR-EASE promotes the use of these formats to speed up the analysis of
a subset of data, but also to improve the performance of standardised
services (e.g. OGC standards) implemented by data providers. See Lobelia
blog[^7] for more information.

#### STAC

The **Spatio-Temporal Assets Catalog**[^8] (STAC) is a standardised
model and API for geospatial data indexing and discovery. It provides a
lightweight yet powerful framework for organising and exposing data
inventories, whether native (e.g. NetCDF, Tiff) or ARCO (e.g. COG, Zarr,
Geoparquet).

STAC is structured hierarchically, and is based on the HATEOAS[^9]
principle, enabling navigation between these elements. Here are the main
concepts:

- Collection: represents a logical grouping of related data (for
  example, a sensor, a mission or a family of datasets)

- Item: describes a single observation or spatio-temporal scene, such as
  a satellite image or an in situ measurement campaign

- Asset: data or metadata files accessible via URLs

STAC offers rich search capabilities based on spatio-temporal criteria,
extended with additional filters using CQL2 (e.g. observed parameter).
This enables users and applications to discover relevant items and
directly retrieve the corresponding assets from distributed or cloud
infrastructures.

Originally developed for earth observation satellite images, FAIR-EASE
has extended its use to in situ data, taking care to provide rich
metadata, with as many links as possible to controlled vocabularies.

Here is the architecture proposed by FAIR-EASE:

![](media/image37.png){width="6.824268372703412in"
height="4.022391732283465in"}

[]{#_heading=h.8lyvumjjyts7 .anchor}*Figure 9 - STAC architecture*

An implementation has been provided by Ifremer to demonstrate the use of
STAC for in-situ data, including native ARGO datasets. This includes a
public **STAC API** available at
[[stac-pg-api.ifremer.fr]{.underline}](https://stac-pg-api.ifremer.fr/)
and a user-friendly **STAC Browser** at
[[stac-browser.ifremer.fr]{.underline}](https://stac-browser.ifremer.fr/?.language=fr),
which allows interactive exploration of the catalog and visualisation of
spatial footprints.

Here is a screenshot of an ARGO profile item from the STAC Browser:

![](media/image35.png){width="6.615625546806649in"
height="3.8994116360454942in"}

[]{#_heading=h.u9rtypwft8hi .anchor}*Figure 10 - STAC Browser example*

#### openEO

##### Overview

As part of the FAIR-EASE knowledge-building and sharing, a webinar
dedicated to openEO was organized by the Copernicus DataSpace Ecosystem
(CDSE) to introduce researchers and infrastructure providers to the
concepts, tools and practical applications of openEO.

OpenEO is a standardized web API designed to simplify access to and
processing of Earth Observation (EO) data across diverse cloud-based
backends. It provides an unified and language-agnostic interface that
enables users to define, execute, and monitor complex remote processing
workflows on datacubes. OpenEO provides a discovery interface (OpenEO
Discovery) that allows users to access data and metadata exposed via a
SpatioTemporal Asset Catalog (STAC) access point.

![](media/image31.png){width="4.993233814523185in"
height="1.8448895450568679in"}

[]{#_heading=h.ysmyn16ennak .anchor}*Figure 11 - Unify data access with
openEO*[^10]

With openEO, users can apply processing functions directly on the data
where it resides, chaining operations into workflows that are executed
server-side, without needing to download large datasets. This approach
is particularly well-suited for cloud-native and scalable processing,
and aligns with FAIR-EASE's goals of supporting interoperability between
Earth System domains.

![](media/image36.png){width="6.668124453193351in"
height="2.9279910323709535in"}

[]{#_heading=h.6uximkt5x7o .anchor}*Figure 12 - openEO workflow
mechanism*[^11]

The API is fully compatible with ARCO formats such as Zarr and COG, as
well as with STAC metadata, facilitating seamless integration with
modern EO data catalogs and storage solutions.

An online Web Editor is also available for users to interactively build,
test, and submit openEO workflows through a graphical interface,
lowering the barrier for non-expert users and fostering reproducibility.

![](media/image34.png){width="6.266447944006999in"
height="3.1265562117235346in"}

[]{#_heading=h.uyqz0tssp9xz .anchor}*Figure 13 - openEO Web Editor*[^12]

OpenEO is currently being standardized within OGC, and momentum is
growing towards the creation of a federation of openEO-compliant
backends, enabling interoperability between EO platforms on a European
and global scale.

##### Implementation on Examind Community

OpenEO has been implemented, during the FAIR-EASE project, within the
Examind Community platform, an open-source geospatial framework
developed and maintained by Geomatys. Examind Community is already
compatible with OGC services (e.g. WMS, WCS, WFS) and OGC API (e.g.
Common, Coverage, Processes). It can also manage geospatial native or
ARCO formats, from local or remote storage (e.g. HTTPs, S3).

![](media/image30.png){width="4.933023840769904in"
height="2.044608486439195in"}

[]{#_heading=h.7brmtkwg4mw5 .anchor}*Figure 14 - openEO on Examind
Community*

The OpenEO standard consists of two essential components: OpenEO
Discovery and OpenEO Processing, both of which have been implemented in
Examind Community.

The first one is an access point to a STAC catalog. It allows data and
metadata to be exposed via a user-accessible catalogue. This is
accessible in Examind via a WCS service (create a WCS service, associate
data with this service, and a STAC access point will be opened with this
data). For more detailed information about the STAC specification, you
can refer to the official documentation[^13].

The second component is the core of openEO, the processing part. It
enables users to access, modify, create and execute workflows by linking
unit processes. In Examind, this service is accessible via WPS (turn on
a wps service, and an openEO access point will be created). For more
detailed information about the OpenEO (processing part), you can refer
to the official documentation available openEO website[^14].

Here is an example with an Enhanced Vegetation Index (EVI) process via
Examind. All openEO processes / workflows in Examind will follow these
steps. In this example we are calculating an EVI on a forest area, but
any other process to be run on a data item will follow the same
procedure.

Examind offers different processes ('basic building blocks') for
creating workflows. These include operations from the openEO standard,
such as "load" and "save" to respectively load data into the graph and
save the result in a format (e.g. GeoTIFF or NetCDF). Examind also
offers a list of mathematical operations, on numbers or coverages (e.g.
multiplying the values of a coverage by a value), and other specific
processes.

To access the list of data and processes that can be used via openEO,
you can use the user interface (via a web editor client) or the STAC /
OpenEO Process API.

  ---------------------------------------------------------------------------------------------
  ![](media/image39.png){width="2.125in"   ![](media/image38.png){width="2.468834208223972in"
  height="0.9692979002624672in"}           height="0.989595363079615in"}
  ---------------------------------------- ----------------------------------------------------

  ---------------------------------------------------------------------------------------------

[]{#_heading=h.qyt6zaxpwtv8 .anchor}*Figure 15 - openEO processes on
Examind*

Once you have a list of the data you want to use and the processes you
want to use, you can create your first graph. In this graph, you will
chain processes to create the expected result. In the example of the EVI
calculation, we will transfer the formula: \`2.5 \* (NIR - RED) / (1 +
NIR + 6\*RED + 7.5\*BLUE)\`, using mathematical operations in openEO.

Once this first graph has been created, we will execute it. To do this,
we need to describe the parameters that the graph must use. For example,
the source data identifier, the type of file used for output, the
extent, etc..

The graph can be executed in one of two ways: synchronously or
asynchronously. Synchronously, the request will be launched and you will
receive the result in return. Asynchronously, a job will be created and
will have to be executed. You can then query the job to find out its
status and the result once it has finished.

Here is the json requests for the EVI graph, execution of the graph, and
the result :

![](media/image41.png){width="6.692716535433071in"
height="2.4027777777777777in"}

[]{#_heading=h.npboh27pp42p .anchor}*Figure 16 - openEO flow on Examind*

More information (Jupyter notebook + documentation) on Examind Community
OpenEO endpoint is available on
[*[https://github.com/fair-ease/Examind_Tutorials]{.underline}*](https://github.com/fair-ease/Examind_Tutorials).

There was no immediate practical use for the pilots, but the potential
for further developments are significant.

#### Beacon

**Beacon** is able to provide users with fast and easy access to
multidisciplinary data originating from large collections, on the fly
with high performance, and extract specific data based on the user's
request.

This software has been customised and deployed in the Blue-Cloud2026
project, FAIR-EASE, among other projects including national ones and is
designed to return one single harmonised file as output, regardless of
whether the input contains different data types. It allows everyone to
set-up their own Beacon 'instance' to enhance the access to their data
or use existing Beacon instances from well-known data infrastructures
such as Euro-Argo or the World Ocean Database for fast and easy access
to harmonized data subsets.

More technical details, example applications and general information on
Beacon can be found on the website
[[https://beacon.maris.nl/]{.underline}](https://beacon.maris.nl/) and
the documentation on Github[^15].

![](media/image44.png){width="1.454682852143482in"
height="2.1914709098862644in"}

[]{#_heading=h.rd96lgn31848 .anchor}*Figure 17 - Beacon architecture*

In order to use Beacon for providing access to harmonised subsets, a set
of in total 8 monolithic Beacon instances were set-up for relevant data
collections such as the WOD, Copernicus Marine Cora, Euro-Argo,
SeaDataNet, and more. The term 'monolithic' is used to indicate that the
Beacon instance concerns one data infrastructure. After initial
configuration at a MARIS server, all 8 instances have been deployed
operationally, with Argo also being available on the UCA Testbed. All
have been integrated with the D4Science federated AAI service, by which
access is arranged. All Beacon instances also have been provided with
its own dedicated Jupyter-notebook which sits on the Beacon API and
which makes it easier for the users to interact. The notebooks already
contain several queries and users can adapt their own notebooks.

The following figure shows access to the Argo data collection that is
hosted on the UCA Testbed. The user is able to retrieve on-the-fly
access to Argo data following their query criteria in less than 10
seconds. The data can be stored in different output formats and easily
converted to a dataframe as depicted here for further analysis.

![](media/image40.png){width="6.182276902887139in"
height="2.448047900262467in"}

[]{#_heading=h.bhf7h9s6i8co .anchor}*Figure 18 - Access to the Argo data
collection that is hosted on the UCA Testbed via a Jupyter Notebook for
on-the-fly access to Temperature and Salinity data*

The following figure shows an example application of Beacon for access
to the WOD. By sending a POST request to the Beacon endpoint, with a set
of columns and filters, the user retrieves on-the-fly in a few seconds
all data in one single file, fitting the filter criteria. This is then
available for further processing. Here a simple plot is shown for
temperature data from the WOD.

![](media/image43.png){width="6.692716535433071in"
height="6.902777777777778in"}

[]{#_heading=h.hkbdblde7xrt .anchor}*Figure 19 - Example application of
Beacon in a Jupyter Notebook for on-the-fly access to Temperature data
from the World Ocean Database.*

#### Apache Iceberg

**Apache Iceberg** is an open table format designed for managing
large-scale tabular data on cloud object storage, such as S3. It enables
efficient querying and data management by supporting features like
schema evolution, snapshot versioning, and time travel. Originally
developed to handle big data workloads, Iceberg is optimized for
performance and reliability in distributed environments. It separates
the table's metadata from the physical data files (often stored in
columnar formats like Parquet), allowing scalable SQL queries through
query engines like Trino or Spark. Its support for atomic operations and
concurrent reads/writes makes it a powerful foundation for building
modern data lakes and federated data platforms.

An Apache Iceberg instance was deployed on the UCA Infrastructure[^16],
using Ceph S3 storage, PySpark to initialise the Iceberg Lake house
files and then using Trino and the Trino JDBC driver to expose the Data
Lakehouse tables to a public ERDDAP instance. The dataset GLODAP
v2.2023[^17] was loaded into the Iceberg Lakehouse and published through
the ERDDAP instance.[^18]

An architecture diagram on how Apache Iceberg was deployed on the UCA
Infrastructure is displayed below. An example local docker setup has
also been created for users to experiment with on their own systems, it
is available on Github[^19] and uses Minio as a local S3 object store.
This can also be reconfigured to use cloud hosted S3 object stores.

![](media/image16.png){width="6.410340113735783in"
height="1.9703258967629047in"}

[]{#_heading=h.1gzs412new65 .anchor}*Figure 20 - Apache Iceberg Trino
and ERDDAP*

Geomatys is actively working to integrate Apache SIS, an open-source
geospatial framework they maintain and which is at the core of the
Examind Community platform, in order to handle geospatial \[meta\]data
associated with Iceberg tables. The goal is to eventually offer
standardized OGC-compliant services powered by an Apache Iceberg
backend, bridging big data infrastructures with geospatial
interoperability. Work to standardise geospatial components in iceberg
is also in progress, as is the development and design of a standard
schema (like geojson) for iceberg to manage geospatial data, temporal
data, 4D data, chunked data, etc. This work is still on-going.

### Client side data access

The diversity of protocols and standards, sometimes even for the same
dataset, can be a barrier for less technical users. There is a need to
access relevant data fragments (i.e. "what") without needing to know
"where" the data is stored or "how" it is accessed.

The original FAIR-EASE architectural document D4.1[^20] introduced a
client-side component responsible for the data-access. This concept got
elaborated in the deliverable D4.3[^21] through the **Uniform Data
Access Layer** (UDAL). Those documents describe the vision and practical
approach behind this technique to formally streamline all data access.

![](media/image17.png){width="6.307280183727034in"
height="2.1563648293963253in"}

[]{#_heading=h.2r7xtfjfs03q .anchor}*Figure 21 - UDAL principle*

By introducing formal data contracts, UDAL allows different components
of the data flow to interact without being tightly coupled, making it
easier to evolve or replace individual parts without disrupting the
whole system. This decoupling of interdependencies extends the lifespan
of each component, as they can be updated or maintained independently.
At the same time, the interface makes it possible to adopt new technical
solutions or innovations at a lower cost, by reducing the need for
extensive reengineering or custom integration.

A UDAL python interface[^22] and a python implementation example[^23]
have been published on Github. Two pilots have implemented the UDAL
principle, demonstrating its applicability in real-world contexts :

- Ocean BGC :
  [[https://github.com/fair-ease/py-udal-pokapok]{.underline}](https://github.com/fair-ease/py-udal-pokapok)

- Marine Omics Observation:
  [[https://github.com/fair-ease/py-udal-mgo]{.underline}](https://github.com/fair-ease/py-udal-mgo)

Most notably in this final phase of the project we would like to
highlight the introduction of the **Dataset Demand Registry** [^24] and
its associated "Query Editor":

![screenshot of the UDAL Query Editor](media/image14.png){width="6.0in"
height="6.791666666666667in"}

[]{#_heading=h.4149c2to9o12 .anchor}*Figure 22 - screenshot of the UDAL
Query Editor*

## Analytics services

FAIR-EASE promotes many data analysis services and platforms that help
users explore, process, and visualise data more easily. Whether for
interactive use, running predefined workflows, or viewing data on maps
and charts, these tools are designed to be accessible and adaptable to
different user needs.

Technical support was also provided to help pilots improve the TRL and
FAIRness of their tools, for example by publishing them in code
repositories, creating containers or integrating them into Galaxy
toolshed.

### Interactive notebooks

Interactive notebooks offer a flexible environment for combining code,
text, and visualisations, making them a widely used tool for exploratory
data analysis and reproducible research. Within FAIR-EASE, two platforms
are supported:

- JupyterLab, mainly used by data scientists, which is compatible with
  numerous languages (e.g. Python, R, Julia) and provide a lot of
  extensions ;

- Pluto.jl, dedicated for Julia programmers, which provides a reactive
  environment.

A special focus is placed on JupyterGIS, a new approach for
collaborative geospatial analysis within notebooks. It combines the
flexibility of Jupyter with tools tailored for GIS operations and
visualisation, enabling users to explore spatial data, apply processing
functions, and share results, all within a unified interface designed
for collaborative use.

![](media/image19.png){width="6.0400415573053365in"
height="3.0461001749781276in"}

[]{#_heading=h.ufywcjkgd1ju .anchor}*Figure 23 - JupyterGIS
example*[^25]

### Galaxy project

The **Galaxy Project** is an open, web-based platform designed to make
data-intensive research more accessible, reproducible, and
collaborative. Originally developed for bioinformatics, Galaxy has been
successfully extended by FAIR-EASE to support Earth System sciences and
geospatial data processing.

#### Why Galaxy matters for FAIR-EASE 

Galaxy is first and foremost a processing platform. Galaxy is built to
scale, capable of executing processes on heterogeneous infrastructures,
including HPC clusters and cloud systems. With Galaxy Pulsar, jobs can
be delegated to remote compute nodes, improving performance and
distribution.

At its core, Galaxy provides seamless access to a vast and diverse
ToolShed (i.e. Appstore) comprising nearly 10,000 tools, ranging from
format converters and statistical analysis tools to data visualization
applications and interactive environments like JupyterLab, as well as
desktop applications that run directly in the browser.

Galaxy supports a wide range of data access protocols (e.g. WebDAV, S3,
FTP, and iRODS), enabling users to easily work with curated reference
datasets or bring in their own data.

A key feature of Galaxy is its powerful workflow engine, which allows
users to create, share, and reuse complex data analysis pipelines.
Thanks to a comprehensive provenance tracking, Galaxy supports RO-Crate
metadata export, ensuring full traceability of both data and processes.

Security plays a central role in the platform, with SSO interfacing
(e.g. via OpenID Connect), and secret management to avoid having
passwords in plain text.

Galaxy is also designed to integrate with key research infrastructures,
offering direct connections to repositories such as Zenodo and
WorkflowHub. Its dynamic Galaxy training network promotes continuous
learning and skills development through collaborative tutorials,
workshops and training materials.

![](media/image23.png){width="6.064058398950131in"
height="2.3129910323709537in"}

[]{#_heading=h.r3bzvedfuy5o .anchor}*Figure 24 - Galaxy web UI*

#### Key Contributions of FAIR-EASE to Galaxy

Within FAIR-EASE, Galaxy was enhanced in several ways to better support
FAIR principles:

- RO-Crate adding tool information : Id, name, version, description,
  toolshed's url from tools used in an analysis are now added in
  RO-Crate archive ;

- RO-Crate Validation Tool: a validator was developed to check RO-Crate
  compliance with declared profiles. It supports validation from
  local/remote sources, has CLI and Python API access, and accepts
  custom SHACL profiles ;

- [[OGC API:Processes
  Integration]{.underline}](https://github.com/dmeaux/fair-ease-galaxy-ogcapi):
  Initial work began to expose Galaxy workflows as OGC-compliant
  computational services. It consists of a
  [[FastAPI]{.underline}](https://github.com/fastapi/fastapi) bridge
  server between [[Galaxy\'s]{.underline}](https://usegalaxy.org/) API
  and [[Open Geospatial Consortium
  APIs]{.underline}](https://ogc.org/publications) ;

- ODV Format Support: Galaxy can now recognize and handle Ocean Data
  View (ODV) files, including an interactive tool for visualization ;

- ZIP Explorer: lets users browse and selectively extract files from ZIP
  archives (local or remote), including RO-Crates, improving data
  ingestion and metadata recognition ;

- Improved Interactive Tools Panel: provides better access and status
  tracking for user sessions.

These developments significantly improved Galaxy's usability,
interoperability, and alignment with FAIR data management principles,
making it a core component of FAIR-EASE.

![](media/image21.png){width="5.552083333333333in"
height="3.1852088801399825in"}

[]{#_heading=h.yvlxl18amt7g .anchor}*Figure 25 - FAIR-EASE usage of
Galaxy*

### webODV

*webODV* is the online version of the popular Ocean Data View (ODV)
desktop software for analysis and visualization of marine and other
environmental data. ODV has over 130,000 registered users, and, based on
recent software download counts, is actively used by more than 13,000
researchers worldwide. Like ODV, *webODV* provides an interactive
graphical user interface and offers rich feature sets via context
specific menus. While desktop ODV requires all datasets to reside on the
end user machine, *webODV* works differently. All datasets as well as a
special version of the ODV software reside and run on dedicated *webODV*
servers. Users do not have to install any software or download the
sometimes-bulky datasets. Instead, users simply connect to datasets
using their web-browser. New browser tabs open for every opened dataset,
each tab providing an "ODV-like" interactive user interface. Previous
ODV users will find it very easy to work with *webODV*. Concise
getting-started documents help guide new users.

Large volumes of important environmental datasets for all parts of the
Earth System are accessible from *webODV* servers summarized at
[[https://webodv.awi.de/]{.underline}](https://explore.webodv.awi.de/).
This includes global TS- and BGC-Argo profile data, GLODAP carbon system
data, SOCAT surface fCO~2~ data, MEOP marine mammals data, and the World
Ocean Atlas (versions 2023 and 2018). In addition, we also provide
global collections of historical meteorological as well as river-runoff
data. The webODV deployments at D4Science
([[https://fair-ease.d4science.org/group/coastalwaterdynamics/webodv]{.underline}](https://fair-ease.d4science.org/group/coastalwaterdynamics/webodv))
and UCA
([[https://webodv.eoscfe.mesocentre.uca.fr/]{.underline}](https://webodv.eoscfe.mesocentre.uca.fr/))
focus on satellite data and model output made available via netCDF
files. Support for netCDF files in ODV and webODV was implemented during
the FAIR-EASE project.

The figure below shows a typical situation on the user's computer, where
several multi-disciplinary datasets residing on different webODV servers
are open in different browser panes. In addition, the user has several
local data collections open in separate instances of the ODV desktop
software running locally. Publication-ready figures can easily be
created from any of the open datasets.

![](media/image25.png){width="5.667011154855643in"
height="2.8439227909011375in"}

[]{#_heading=h.4dzmrt2gd4j8 .anchor}*Figure 26 - Screenshot of a data
analysis session with several multi-disciplinary datasets open in webODV
and ODV desktop*

As a new feature developed during the FAIR-EASE project, users can now
link the open multi-disciplinary datasets by exchanging graphics
elements as well as actual data between any two data windows in webODV
or ODV desktop.

![](media/image24.png){width="4.338990594925634in"
height="3.4725820209973755in"}

[]{#_heading=h.uqirkkz822l8 .anchor}*Figure 27 - Contours of surface
water Chorophyll-a concentrations determined by satellite sensors
overlain on color-shaded salinity at 10 m depth*

This is an example of exchanging graphics elements between datasets.
Here surface water Chorophyll-a concentrations determined by satellite
sensors are overlain on color-shaded salinity at 10 m depth. It is
clearly visible that high chlorophyll values in the northwestern
Adriatic and along the Italian coast coincide with low salinity caused
by runoff and transport of Po river water. This shows the importance of
river discharge for the biological productivity and eventually fish
stock size.

Exchange of actual data between windows allows the computation of new
quantities, such as difference or ratio. This can be applied to detect
spatial and temporal changes, for instance between reoccupations of
oceanographic sections. This will benefit research in our changing
environment.

### TerriaMap

TerriaMap is an Australian Open Source web application for building
web-based map viewers, Atlases and Digital Twin Interfaces. The platform
was originally developed by CSIRO (Australia's national Science Agency).
It is similar in concept to the European
[[EDITO]{.underline}](https://dive.edito.eu/) digital twin interface.
TerriaMap is now supported by a commercial Support company Terria Pty
ltd. ([[terria.io]{.underline}](http://terria.io))

Terriamap was used in the "Terriamap Challenge" at the FAIREASE
Hackathon in Brest in March 2025. The hackathon challenge explored how
diverse environmental datasets (e.g. Argo, Omics data) and OGC and other
data services (from Examind, Thredds, ERDDAP, Beacon) could be
visualized and interacted with in the TerriaMap web application,
allowing for cross disciplinary integration of data services from the
FAIR-EASE use cases and infrastructure.

![](media/image20.png){width="6.30239501312336in"
height="2.8959765966754154in"}

[]{#_heading=h.ht5nsi3yqbxy .anchor}*Figure 28 - Terriamap 2D and 3D
display modes*

Terriamap is based on the Terriajs javascript library, the source code
and user configurable files are published on Github in the [[TerriaMap
github repository]{.underline}](https://github.com/TerriaJS/TerriaMap).
Documentation on the installation and configuration of Terriamap and the
various supported data services and data sources is available at
[[https://docs.terria.io/guide/]{.underline}](https://docs.terria.io/guide/)

![](media/image18.png){width="5.279413823272091in"
height="2.4946686351706036in"}

[]{#_heading=h.j02u2532w8id .anchor}*Figure 29 - Terriamap displaying
OMICs metadata and ARGO profile data from ERDDAP*

An instance of Terriamap configured with example datasets from the Brest
Hackathon is published on the the University Clermont Auvergne(UCA) at
[[https://terriamap.eoscfe.mesocentre.uca.fr/]{.underline}](https://terriamap.eoscfe.mesocentre.uca.fr/)

![](media/image10.png){width="5.534900481189851in"
height="2.6188615485564304in"}

[]{#_heading=h.atfaaqf917ua .anchor}*Figure 30 - Terriamap displaying
CMEMS Chlorophyll data from Examind and SO2 data from Thredds*

The Terriamap example configurations compiled during the Hackathon are
available on
[[https://github.com/fair-ease/terria-config]{.underline}](https://github.com/fair-ease/terria-config)

# Earth Analytics Lab

## Overview

The Earth Analytics Lab is an integrated e-infrastructure that provides
value-added services to support research and foster collaborative
science. See D3.1[^26] for the full specifications.

![](media/image5.png){width="6.151020341207349in"
height="3.2710061242344706in"}

[]{#_heading=h.crzk83hi7436 .anchor}*Figure 31 - EAL functional view*

Based on a \"system of systems\" approach, FAIR-EASE allows for
interconnecting three EAL implementations through federated
capabilities, enabling users to seamlessly move from one EAL to another
and to access and use the available computing services and resources,
which may differ between EALs.

![](media/image45.png){width="6.501041119860018in"
height="1.3042530621172352in"}

[]{#_heading=h.y6j5d29pljj0 .anchor}*Figure 32 - EAL and system of
systems approach*

We will present these three EALs, including FAIR-EASE contributions,
followed by an analysis of their strengths as well as areas for
improvement.

## Implementations

### Galaxy Europe for Earth System subdomain

As part of FAIR-EASE, the Galaxy Europe Earth System subdomain
([[earth-system.usegalaxy.eu]{.underline}](https://earth-system.usegalaxy.eu))
was created to serve the needs of environmental scientists working with
marine, atmospheric, land, and biodiversity data.

![](media/image8.png){width="5.932202537182852in"
height="4.199691601049869in"}

[]{#_heading=h.nlljhx8v870k .anchor}*Figure 33 - Galaxy Europe - Earth
System subdomain welcome page*

It supports a wide range of scientific and operational needs, and
strengthens links with European data infrastructures such as Copernicus,
CMEMS and OBIS.

These tools help make environmental data more accessible and usable by:

- Connecting users to major data sources through simple, reproducible
  workflows ;

- Offering both batch processing and interactive exploration, all inside
  the Galaxy platform ;

- Supporting training, education and open science thanks to public code,
  Docker images and documentation ;

- Enabling long-term reusability and compatibility with EOSC and other
  European initiatives.

#### Tools integrated

These tools show how FAIR-EASE helps bridge the gap between data
providers and users, making complex data more usable for science,
policy, and operational services.

![](media/image9.png){width="5.611360454943132in"
height="3.323475503062117in"}

[]{#_heading=h.wkxqdce9m0m3 .anchor}*Figure 34 - ODV interactive tool in
Galaxy*

**Tools for Oceanographic Data**

+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Tool**                                                                                                                      | **Description**            | **Links**                                                                                                    |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Argo_getdata**                                                                                                              | Allows retrieval of Argo   | [[GitHub content]{.underline}](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | glider data (physical and  |                                                                                                              |
|                                                                                                                               | biogeochemical).           | [[GitHub Galaxy tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean)   |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy PR]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/81)                            |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **DIVA_full_analysis**                                                                                                        | Implemented as both batch  | [[GitHub content]{.underline}](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | and interactive tools,     |                                                                                                              |
|                                                                                                                               | this module enables        | [[GitHub Galaxy tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean)   |
|                                                                                                                               | advanced spatial           |                                                                                                              |
|                                                                                                                               | interpolation of marine    | [[Batch PR]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/118)                            |
|                                                                                                                               | data.                      |                                                                                                              |
|                                                                                                                               |                            | [[GxIT PR]{.underline}](https://github.com/usegalaxy-eu/galaxy/pull/160)                                     |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Copernicus Marine Data Store** (copernicusmarine)                                                                           | Batch tool to query and    | [[GitHub content]{.underline}](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | download datasets from     |                                                                                                              |
|                                                                                                                               | CMEMS.                     | [[GitHub Galaxy tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean)   |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/126)                           |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Ocean Data View**                                                                                                           | Used to plot               | [[GitHub Galaxy tool]{.underline}](https://github.com/bgruening/docker-odv)                                  |
|                                                                                                                               | geo-referenced ocean data  |                                                                                                              |
|                                                                                                                               | from NetCDF and other      | [[GxIT_PR]{.underline}](https://github.com/usegalaxy-eu/galaxy/pull/166)                                     |
|                                                                                                                               | formats.                   |                                                                                                              |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **ODV collection manager** (tool_odv)                                                                                         | Merges various datasets    | [[GitHub content]{.underline}](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | with a common vocabulary   |                                                                                                              |
|                                                                                                                               | and creates a single       | [[GitHub Galaxy                                                                                              |
|                                                                                                                               | generic ODV spreadsheet in | tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_data_view_manager) |
|                                                                                                                               | an automatic way           |                                                                                                              |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **ODV history manager** (tool_odv_history)                                                                                    | Report in the input file   | [[GitHub content]{.underline}](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | the ODV history including  |                                                                                                              |
|                                                                                                                               | the change of QC flag      | [[GitHub Galaxy                                                                                              |
|                                                                                                                               |                            | tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_data_view_manager) |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Canyon B**                                                                                                                  | Robust Estimation of Open  | [[GitHub content]{.underline}](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | Ocean CO2 Variables and    |                                                                                                              |
| (bgc_canyonb)                                                                                                                 | Nutrient Concentrations    | [[GitHub Galaxy                                                                                              |
|                                                                                                                               | From T, S, and O2 Data     | tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_neural_network)    |
|                                                                                                                               | Using Bayesian Neural      |                                                                                                              |
|                                                                                                                               | Network                    | [[Conda recipe]{.underline}](https://github.com/conda-forge/staged-recipes/pull/28638)                       |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/150)                           |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Sanntis**                                                                                                                   | The Sanntis tool identify  | [[GitHub content]{.underline}](https://github.com/Finn-Lab/SanntiS)                                          |
|                                                                                                                               | biosynthetic gene clusters |                                                                                                              |
| (sanntis_marine)                                                                                                              | (BGCs) in genomic &        | [[GitHub Galaxy                                                                                              |
|                                                                                                                               | metagenomic data           | tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/marine_omics)            |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/121)                           |
|                                                                                                                               |                            | [[Galaxy_PR_2]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/123)                         |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **QCV Harmonizer**                                                                                                            | Harmonizes oceanographic   | [[GitHub content]{.underline}](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
| ([[harmonize_insitu_to_netcdf]{.underline}](https://toolshed.g2.bx.psu.edu/repository/browse_repository?id=38ab3b3c936ea98a)) | biogeochemical data.       |                                                                                                              |
|                                                                                                                               |                            | [[GitHub Galaxy                                                                                              |
|                                                                                                                               |                            | tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/bgc_ocean)               |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]{.underline}](https://github.com/usegalaxy-eu/usegalaxy-eu-tools/pull/806)                       |
+===============================================================================================================================+============================+==============================================================================================================+

**Tools for Interactive Visualisation and Data Handling**

+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **Tool**              | **Description**            | **Links**                                                                                                          |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **QGIS**              | Full integration of QGIS   | [[GitHub Galaxy tool]{.underline}](https://github.com/usegalaxy-eu/docker-qgis)                                    |
|                       | as an interactive tool in  |                                                                                                                    |
|                       | Galaxy.                    | [[GxIT_PR]{.underline}](https://github.com/usegalaxy-eu/galaxy/pull/200)                                           |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **HoloViz Ecosystem** | A set of interactive       | [[GitHub Galaxy tool]{.underline}](https://github.com/usegalaxy-eu/docker-holoviz)                                 |
|                       | notebooks for data         |                                                                                                                    |
|                       | visualisation using Python | [[GxIT PR]{.underline}](https://github.com/usegalaxy-eu/galaxy/pull/207)                                           |
|                       | libraries as Panel, Bokeh, |                                                                                                                    |
|                       | Datashader, etc.           |                                                                                                                    |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **STAC Browser**      | Access and navigation      | [[GitHub content]{.underline}](https://github.com/radiantearth/stac-browser)                                       |
|                       | interface for STAC         |                                                                                                                    |
|                       | (SpatioTemporal Asset      | [[GxIT PR]{.underline}](https://github.com/usegalaxy-eu/galaxy/pull/220)                                           |
|                       | Catalogs).                 |                                                                                                                    |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **TerriaMap**         | Geospatial visualisation   | [[GitHub                                                                                                           |
|                       |                            | content]{.underline}](https://github.com/usegalaxy-eu/galaxy/tree/release_24.2_europe/tools/interactive/terriamap) |
|                       |                            |                                                                                                                    |
|                       |                            | [[GxIt]{.underline}](https://usegalaxy.eu/root?tool_id=interactive_tool_terriamap)                                 |
+=======================+============================+====================================================================================================================+

**Access to Global and Biodiversity Data**

+-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **Tool**              | **Description**            | **Links**                                                                                           |
+-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **OBIS occurences**   | A tool to search and       | [[GitHub content]{.underline}](https://github.com/Marie59/obisindicators)                           |
|                       | retrieve species           |                                                                                                     |
| (obis_data)           | occurrences from the OBIS  | [[GitHub Galaxy                                                                                     |
|                       | database.                  | tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/obisindicators) |
|                       |                            |                                                                                                     |
|                       |                            | [[Galaxy_PR]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/90)                   |
+-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **Copernicus Data     | Jupyter notebooks to       | [[GitHub content]{.underline}](https://github.com/eu-cdse/notebook-samples)                         |
| Space Ecosystem**     | explore Copernicus data    |                                                                                                     |
|                       | using SentinelHub and      | [[GxIT PR]{.underline}](https://github.com/usegalaxy-eu/galaxy/pull/210)                            |
|                       | OpenEO.                    |                                                                                                     |
+-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **Trends.Earth**      | Batch tool for computing   | [[GitHub content]{.underline}](https://github.com/Marie59/tools-ecology/tree/trends-earth)          |
|                       | land cover and degradation |                                                                                                     |
|                       | indicators, supporting     | [[GitHub Galaxy                                                                                     |
|                       | monitoring of SDG 15.3.1.  | tool]{.underline}](https://github.com/galaxyecology/tools-ecology/tree/master/tools/obisindicators) |
|                       |                            |                                                                                                     |
|                       |                            | [[Galaxy_PR]{.underline}](https://github.com/galaxyecology/tools-ecology/pull/117)                  |
+=======================+============================+=====================================================================================================+

#### Workflows developed and shared

Several Galaxy workflows have been developed and shared as part of
FAIR-EASE to support Earth system science. These include workflows to
process and analyse Argo float data, extract biogeochemical variables
like phosphate from large NetCDF datasets, and combine oceanographic
data with tools like ODV and the Pangeo ecosystem. All workflows are
openly available on WorkflowHub - [[FAIR-EASE Galaxy Project on
WorkflowHub]{.underline}](https://workflowhub.eu/projects/267/workflows?utm_source=chatgpt.com) -
and can be imported into Galaxy by clicking the "Run on Galaxy" button
on the WorkflowHub pages. They are designed for environmental scientists
working with oceanographic and Earth system data, and are compatible
with the [[Galaxy Europe For Earth System
instance](https://earth-system.usegalaxy.eu).]{.underline}

In addition, these workflows were demonstrated during major scientific
events such as EGU 2024, and training materials have been created to
help new users. Tutorials are available through the Galaxy Training
Network, showing how to run the workflows, understand the data, and use
FAIR practices like RO-Crate to describe and share results.

![](media/image7.png){width="5.802407042869642in"
height="3.843964348206474in"}

[]{#_heading=h.5670cqsigjgs .anchor}*Figure 35 - Water Coastal Dynamics
workflow*

  -----------------------------------------------------------------------------------------------------------------------------------------------------------
  **Workflow**       **Description**                    **Access**
  ------------------ ---------------------------------- -----------------------------------------------------------------------------------------------------
  **Marine Omics:    Detects biosynthetic gene clusters [[WorkflowHub]{.underline}](https://workflowhub.eu/workflows/1663?version=1&utm_source=chatgpt.com)
  Biosynthetic Gene  in marine omics data using tools   
  Clusters**         like Prodigal and SanntiS.         

  **Marine Omics     Converts OBIS biodiversity records [[WorkflowHub]{.underline}](https://workflowhub.eu/workflows/1698?version=1&utm_source=chatgpt.com)
  Visualisation      into indicators such as Shannon    
  (OBIS              and Simpson indices.               
  Indicators)**                                         

  **Process Argo     Processes Argo float data and      [[WorkflowHub]{.underline}](https://workflowhub.eu/workflows/1436?utm_source=chatgpt.com)
  Data with Pangeo & visualizes oceanographic variables 
  ODV**              using Pangeo and Ocean Data View   
                     (ODV).                             

  **Subset           Subsets NetCDF data for the        [[WorkflowHub]{.underline}](https://workflowhub.eu/workflows/1445?utm_source=chatgpt.com)
  Mediterranean Sea  Mediterranean Sea and extracts     
  & Extract          phosphate levels for analysis.     
  Phosphate**                                           

  **Full Analysis of End-to-end workflow to analyse and [[WorkflowHub]{.underline}](https://workflowhub.eu/workflows/1113)
  Argo Data**        visualise Argo profile datasets.   

  **Argo-Glider      Qualification, Calibration and     [[Galaxy Earth
  Nitrate QCV**      validation of Argo floats and      System]{.underline}](https://earth-system.usegalaxy.eu/published/workflow?id=44827462c065bae3)
                     Gliders ocean Biogeochemical Data  
                     Using Galaxy                       
  -----------------------------------------------------------------------------------------------------------------------------------------------------------

#### Galaxy Training Network (GTN)

Several high-quality, FAIR-aligned tutorials and learning pathways have
been developed and published on the Galaxy Training Network (GTN). These
resources are tagged with the \"earth-system\" label and cover a wide
range of topics including marine biodiversity, oceanographic data
processing, land monitoring, and FAIR metadata practices. Designed for
interdisciplinary Earth and environmental scientists, they support
hands-on learning with real datasets and workflows, and encourage reuse,
openness, and reproducibility. All materials are licensed under CC-BY
4.0.

![](media/image15.png){width="6.206229221347332in"
height="3.4838867016622923in"}

[]{#_heading=h.kdn5uj5nztzy .anchor}*Figure 36 - GTN example*

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Title**         **Type**   **Description**                   **Access**
  ----------------- ---------- --------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------
  **Getting your    Learning   Introduction to accessing and     [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/climate/tutorials/earth_system/tutorial.html)
  hands-on earth    Pathway    analyzing ocean, land,            
  data**                       atmosphere, biodiversity data in  
                               Galaxy.                           

  **OBIS Marine     Tutorial   Calculate biodiversity indices    [[Run
  Indicators**                 (Shannon, Simpson, ES50) from     Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/ecology/tutorials/obisindicators/tutorial.html?utm_source=chatgpt.com)
                               OBIS.                             

  **From NDVI with  Tutorial   Process NDVI satellite data for   [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/ecology/tutorials/ndvi/tutorial.html)
  OpenEO to time               land degradation analysis and     
  series with                  time-series visualization.        
  Holoviews**                                                    

  **Marine Omics:   Tutorial   Detect biosynthetic gene clusters [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/ecology/tutorials/marine_omics_bgc/tutorial.html)
  Identifying                  using Prodigal, InterProScan,     
  BGCs**                       SanntiS.                          

  **Ocean's         Tutorial   Subset Mediterranean ocean data   [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/climate/tutorials/oceans_var/tutorial.html)
  Variables Study**            and explore variables (e.g.,      
                               phosphate).                       

  **Ocean Data View Tutorial   Visualize NetCDF-based            [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/climate/tutorials/ocean_data_view/tutorial.html)
  (ODV)**                      oceanographic variables using     
                               ODV.                              

  **Sentinel 5P     Tutorial   Explore and analyze Sentinel-5P   [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/climate/tutorials/sentinel5_data/tutorial.html)
  Data                         atmosphere data interactively.    
  Visualisation**                                                

  **Analyse Argo    Tutorial   Process Argo float datasets with  [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/climate/tutorials/argo_pangeo/tutorial.html)
  Data**                       Pangeo tools and visualize using  
                               ODV                               

  **Make your tools Tutorial   Guide to managing tools in a      [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/community/tutorials/tools_subdomains/tutorial.html)
  available on your            Galaxy subdomain.                 
  subdomain**                                                    

  **Create a        Tutorial   Steps to create and administer a  [[Run Tutorial]{.underline}](https://training.galaxyproject.org/training-material/topics/community/tutorials/tools_subdomains/tutorial.html)
  subdomain for                Galaxy subdomain for your         
  your community**             community.                        
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#### Connecting IT resources

As part of FAIR-EASE, several actions were undertaken to integrate and
leverage PULSAR as a distributed execution backend within Galaxy
workflows. PULSAR endpoints were deployed on multiple infrastructures,
including at the University of Clermont Auvergne (UCA) and the Hellenic
Centre for Marine Research (HCMR) in Greece, enabling remote processing
from Galaxy. A proof-of-concept with the EGI Federated Cloud was also
carried out, demonstrating the ability to dynamically deploy PULSAR
nodes using the EGI Infrastructure Manager. These deployments supported
the execution of real-world workflows, validating the portability,
scalability, and interoperability of distributed processing in an EAL
platform.

![](media/image13.png){width="6.253650481189851in"
height="2.590508530183727in"}

[]{#_heading=h.tf6xqvihd4uk .anchor}*Figure 37 - French Galaxy Pulsar
endpoint at the UCA*

### FAIR-EASE@D4Science

[[D4Science]{.underline}](https://www.d4science.org/) is a hybrid data
infrastructure, hosted by CNR Italy, designed to support scientific
collaboration and resource sharing across various domains, including
biology, ecology, environmental studies, social sciences. Established in
2014, it connects over 24,000 scientists from 50+ countries, integrates
data from 50+ providers, and provides access to over a billion records
in global repositories. Its key feature is the provision of Virtual
Research Environments (VREs) and Virtual Laboratory (VLab), web-based
platforms tailored to specific community needs. D4Science is notably
used by Blue Cloud 2026.

A Memorandum Of Understanding (MoU) was signed between Blue Cloud 2026
and FAIR-EASE in November 2024, to strengthen collaboration between the
two projects. This led to the creation of a FAIR-EASE VRE, including the
launch of a dedicated gateway
([[https://fair-ease.d4science.org/]{.underline}](https://fair-ease.d4science.org/))
and the development of two VLABs for Coastal Water Dynamics and Marine
Omics Observation.

![](media/image12.png){width="5.139067147856518in"
height="2.458254593175853in"}

[]{#_heading=h.qk3hsvm0itgm .anchor}*Figure 38 - FAIR-EASE VRE home page
on D4Science*

![](media/image11.png){width="5.396681977252843in"
height="4.267834645669291in"}

[]{#_heading=h.bop6vx8z2cqp .anchor}*Figure 39 - Marine Omics
Observation VLAB on D4Science*

For the Marine Omics Observation VLAB, we collaborated with the
D4Science team to provide a Galaxy service that enables the chaining of
predefined tools. This instance is available at
[[https://galaxy-gcp.d4science.org/MarineOmicsObservations/]{.underline}](https://galaxy-gcp.d4science.org/MarineOmicsObservations/).
Currently, only non-interactive tools can be executed due to a technical
issue that still needs to be resolved.

![](media/image3.png){width="6.692716535433071in"
height="2.388888888888889in"}

[]{#_heading=h.ajmpeaatej25 .anchor}*Figure 40 - Galaxy project service
on D4Science*

For Coastal Water Dynamics, we collaborated with D4Science team to
provide a webODV server providing access to satellite data as well as
reanalysis model output in the form of netCDF files:
[[https://fair-ease.d4science.org/group/coastalwaterdynamics/webodv]{.underline}](https://fair-ease.d4science.org/group/coastalwaterdynamics/webodv).
These data complement the wide range of environmental data available on
the other webODV servers.

The IDDAS is also available as a VRE widget inside the FAIR-EASE VRE on
D4Science as illustrated in Figure below. The asset selector, like the
current web version of the IDDAS, allows for discovery and access to the
assets harvested from the data infrastructures. It is possible to push
the assets into the user's local workspace in their virtual lab to
conduct their analysis, or use for input to their models and services.
The asset selector includes a human readable as well as a machine
accessible interface with similar functionalities as the IDDAS.

![](media/image2.png){width="6.405485564304462in"
height="2.8999956255468065in"}

[]{#_heading=h.71paqiezlw87 .anchor}*Figure 41 - Access point of IDDAS
from the FAIR-EASE EAL on D4Science*

### FAIR-EASE@UCA

Since mid-2024, we have been working on the implementation of an EAL at
Université de Clermont-Auvergne (UCA), building upon its existing
hardware infrastructure. This infrastructure also hosts the FAIR-EASE
data lake, as described in *Deliverable D4.5 - Deployment of the data
lake: operational version*.

The EAL FAIR-EASE@UCA remains in an incubation phase but is
progressively taking shape through key developments. Notably, it has
been interfaced with the EGI Check-in SSO service to support federated
authentication and has integrated an S3 object storage
([[s3://s3.mesocentre.uca.fr]{.underline}](http://s3.mesocentre.uca.fr))
with Ceph deployed by UCA. Applications are being deployed via
OpenStack, providing a flexible and scalable environment for future
services. These foundational components will support the upcoming
deployment of analytical tools and workflows aligned with FAIR-EASE
objectives.

![](media/image6.png){width="6.535603674540682in"
height="2.7886679790026245in"}

[]{#_heading=h.uwtsmvpukv5p .anchor}*Figure 42 - Accessing JupyterLab on
UCA via EGI CheckIn*

Here are the services deployed:

+------------+----------------+----------------------------------------------------------------------------------------------------------------------+
| **Building | **Service**    | **URL**                                                                                                              |
| block**    |                |                                                                                                                      |
+------------+----------------+----------------------------------------------------------------------------------------------------------------------+
| **Data     | Examind        | [[https://examind.eoscfe.mesocentre.uca.fr/examind/]{.underline}](https://examind.eoscfe.mesocentre.uca.fr/examind/) |
| Access**   | Community      |                                                                                                                      |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | Thredds        | [[https://thredds.eoscfe.mesocentre.uca.fr/]{.underline}](https://thredds.eoscfe.mesocentre.uca.fr/)                 |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | ERDDAP         | [[https://erddap.eoscfe.mesocentre.uca.fr]{.underline}](https://erddap.eoscfe.mesocentre.uca.fr)                     |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | Beacon         | [[https://beacon-argo.eoscfe.mesocentre.uca.fr/]{.underline}](https://beacon-argo.eoscfe.mesocentre.uca.fr/)         |
+------------+----------------+----------------------------------------------------------------------------------------------------------------------+
| **Data     | WebODV         | [[https://webodv.eoscfe.mesocentre.uca.fr/]{.underline}](https://webodv.eoscfe.mesocentre.uca.fr/)                   |
| Analysis** |                |                                                                                                                      |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | TerriaMap      | [[https://terriamap.eoscfe.mesocentre.uca.fr/]{.underline}](https://terriamap.eoscfe.mesocentre.uca.fr/)             |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | JupyterHub/Lab | [[https://jupyterhub.eoscfe.mesocentre.uca.fr/]{.underline}](https://jupyterhub.eoscfe.mesocentre.uca.fr/)           |
+============+================+======================================================================================================================+

### Strengths and areas for improvement

+-------------------------+-------------------------+-------------------------+
| **EAL Implementation**  | **Strengths**           | **Areas for             |
|                         |                         | improvement**           |
+-------------------------+-------------------------+-------------------------+
| **Galaxy for Earth      | \- Galaxy as PaaS       | \- Implement user group |
| System**                |                         | management features     |
|                         | \- Galaxy Pulsar        |                         |
| (TRL = 9)               | integration             | \- Enhance integration  |
|                         |                         | for discovering and     |
|                         | \- Galaxy Training      | accessing geospatial    |
|                         | Materials               | reference datasets      |
|                         |                         |                         |
|                         | \- CI/CD with GitHub    |                         |
|                         |                         |                         |
|                         | \- Community-based      |                         |
|                         | contributions           |                         |
+-------------------------+-------------------------+-------------------------+
| **FAIR-EASE@D4Science** | \- Integration of       | \- S3 API direct access |
|                         | various services        | for better tool/service |
| (TRL = 9)               | (discovery, access,     | integration and support |
|                         | analysis)               | for HTTP Range          |
|                         |                         |                         |
|                         | \- Catalogue and        | \- Streamline           |
|                         | publication mechanisms  | deployment of new       |
|                         |                         | services by external    |
|                         | \- Group management     | teams                   |
|                         | (VLAB, VRE, landing     |                         |
|                         | pages)                  |                         |
|                         |                         |                         |
|                         | \- Collaboration tools  |                         |
+-------------------------+-------------------------+-------------------------+
| **FAIR-EASE@UCA**       | \- S3 storage           | \- Design a landing     |
|                         | (reference data,        | page for better user    |
| (TRL = 6)               | userspace)              | entry points            |
|                         |                         |                         |
|                         | \- Deployment of new    | \- Implement group and  |
|                         | services                | collaboration           |
|                         |                         | management features     |
|                         | \- Integration of       |                         |
|                         | access and analysis     | \- Develop a dedicated  |
|                         | workflows               | service catalogue in    |
|                         |                         | connection with the     |
|                         | \- Links to other EALs  | EOSC node federation    |
|                         | (e.g., Galaxy Europe    |                         |
|                         | via Pulsar)             | \- Deploy a vault       |
+=========================+=========================+=========================+

# Conclusion

Over the course of the project, FAIR-EASE has achieved a series of
notable results that have contributed to both technological progress and
community engagement across multiple scientific domains.

FAIR-EASE has exploited existing solutions and successfully adapted them
to new domains and contexts, demonstrating the versatility and
robustness of tools such as Galaxy and webODV for data analysis
services. These technologies, initially designed for specific
communities, have been enhanced to meet broader scientific needs,
promoting interoperability between fields. At the same time, FAIR-EASE
has fostered innovation by introducing new concepts and tackling
technical challenges. The development and implementation of principles
such as UDAL and EAL reflect this commitment to innovation.
Collaboration has been the cornerstone of this success. FAIR-EASE
fostered close interaction between internal partners while building
bridges with external initiatives.

FAIR-EASE has also played a key role in disseminating good practice,
particularly in improving the fairness of data, software and processes.
In response to the growing demand for sustainable computing, FAIR-EASE
has also advocated for remote data processing to minimize unnecessary
data transfers. By supporting standards and technologies such as OGC
API:Processes, S3/ARCO formats, OpenEO, and Galaxy Pulsar, the project
has paved the way for more efficient and scalable processing approaches.
By integrating these principles into tools and workflows, the project
has helped to improve the overall quality and sustainability of research
products.

The project has provided integrated e-infrastructures (EAL) that support
large-scale collaborative science, enabling users to move from one to
another EAL through a system of systems approach, using common federated
capabilities. Platforms such as Galaxy for Earth System Science,
FAIR-EASE@D4Science and the FAIR-EASE@UCA have provided pilots with
robust environments for experimentation, sharing and validation.

Finally, FAIR-EASE has produced a significant number of KERs[^27], each
contributing tangible value to the scientific and technical communities.
These results are not only deliverables but also stepping stones for
further innovation, adoption, and impact beyond the lifetime of the
project.

[^1]: [[https://doi.org/10.5281/zenodo.10069773]{.underline}](https://doi.org/10.5281/zenodo.10069773)

[^2]: [[https://doi.org/10.5281/zenodo.14711074]{.underline}](https://doi.org/10.5281/zenodo.14711074)

[^3]: Source:
    [[https://www.codesmith.io/]{.underline}](https://www.codesmith.io/)

[^4]: [[https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Range_requests]{.underline}](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Range_requests)

[^5]: Source:
    [[https://earthmover.io/]{.underline}](https://earthmover.io/)

[^6]: Source:
    [[https://guide.cloudnativegeo.org/]{.underline}](https://guide.cloudnativegeo.org/)

[^7]: [[https://blog.lobelia.earth/arco-the-smartest-way-to-access-big-geospatial-data-eaf689eff3c9]{.underline}](https://blog.lobelia.earth/arco-the-smartest-way-to-access-big-geospatial-data-eaf689eff3c9)

[^8]: [[https://stacspec.org/en/]{.underline}](https://stacspec.org/en/)

[^9]: [[https://en.wikipedia.org/wiki/HATEOAS]{.underline}](https://en.wikipedia.org/wiki/HATEOAS)

[^10]: S*ource: [[https://openeo.org]{.underline}](https://openeo.org)*

[^11]: S*ource:
    [[https://dataspace.copernicus.eu/]{.underline}](https://dataspace.copernicus.eu/)*

[^12]: *Source:
    [[https://dataspace.copernicus.eu/]{.underline}](https://dataspace.copernicus.eu/)*

[^13]: [*[https://stacspec.org/en/about/stac-spec/]{.underline}*](https://stacspec.org/en/about/stac-spec/)

[^14]: [*[https://openeo.org/documentation/1.0/developers/api/reference.html#section/Processes]{.underline}*](https://openeo.org/documentation/1.0/developers/api/reference.html#section/Processes)

[^15]: [[https://maris-development.github.io/beacon/]{.underline}](https://maris-development.github.io/beacon/)

[^16]: [[https://erddap.eoscfe.mesocentre.uca.fr/]{.underline}](https://erddap.eoscfe.mesocentre.uca.fr/)

[^17]: [[https://glodap.info/index.php/merged-and-adjusted-data-product-v2-2023/]{.underline}](https://glodap.info/index.php/merged-and-adjusted-data-product-v2-2023/)

[^18]: [[https://erddap.eoscfe.mesocentre.uca.fr/erddap/tabledap/glodap_v2_2023_iceberg2.graph]{.underline}](https://erddap.eoscfe.mesocentre.uca.fr/erddap/tabledap/glodap_v2_2023_iceberg2.graph)

[^19]: [[https://github.com/fair-ease/erddap-trino-iceberg]{.underline}](https://github.com/fair-ease/erddap-trino-iceberg)

[^20]: Marc Portier (2023) FAIR-EASE_D4.1_Landscaping exercise_The
    -meta-data, software and cloud needs for the data lake. Zenodo. doi:
    10.5281/zenodo.7965398.

[^21]: PORTIER, M. (2024) FAIR-EASE - D4.3 Status and expectations of
    the FAIR-EASE data lake. Zenodo. doi: 10.5281/zenodo.13933551.

[^22]: [<https://github.com/fair-ease/py-udal-interface>]{.underline}

[^23]: [<https://github.com/fair-ease/py-udal-fe-impl>]{.underline}

[^24]: [[https://lab.fairease.eu/dataset-demand-register/registry/]{.underline}](https://lab.fairease.eu/dataset-demand-register/registry/)

[^25]: *Source:
    [[https://jupytergis.readthedocs.io/en/latest/]{.underline}](https://jupytergis.readthedocs.io/en/latest/)*

[^26]: [[https://doi.org/10.5281/zenodo.10069773]{.underline}](https://doi.org/10.5281/zenodo.10069773)

[^27]: [[https://fairease.eu/kers]{.underline}](https://fairease.eu/kers)
