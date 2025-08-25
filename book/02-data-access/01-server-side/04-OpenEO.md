# openEO

##### Overview

As part of the FAIR-EASE knowledge-building and sharing, a webinar
dedicated to openEO was organized by the Copernicus DataSpace Ecosystem
(CDSE) to introduce researchers and infrastructure providers to the
concepts, tools and practical applications of openEO.

OpenEO is a standardized web API designed to simplify access to and
processing of Earth Observation (EO) data across diverse cloud-based
backends. It provides a unified and language-agnostic interface that
enables users to define, execute, and monitor complex remote processing
workflows on datacubes. OpenEO provides a discovery interface (OpenEO
Discovery) that allows users to access data and metadata exposed via a
SpatioTemporal Asset Catalog (STAC) access point.

```{figure} 02_01_openeo.png
:height: 300px
:name: figure-02_01_openeo

Unify data access with openEO *[^1]*
```

With openEO, users can apply processing functions directly on the data
where it resides, chaining operations into workflows that are executed
server-side, without needing to download large datasets. This approach
is particularly well-suited for cloud-native and scalable processing,
and aligns with FAIR-EASE's goals of supporting interoperability between
Earth System domains.

```{figure} 02_01_openeo_wflow.png
:height: 300px
:name: figure-02_01_openeo_wflow

openEO workflow mechanism *[^2]*
```

The API is fully compatible with ARCO formats such as Zarr and COG, as
well as with STAC metadata, facilitating seamless integration with
modern EO data catalogs and storage solutions.

An online Web Editor is also available for users to interactively build,
test, and submit openEO workflows through a graphical interface,
lowering the barrier for non-expert users and fostering reproducibility.

```{figure} 02_01_openeo_web_editor.png
:height: 300px
:name: figure-02_01_openeo_web_editor

openEO Web Editor *[^3]*
```

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

- Examind Community website : https://www.examind.com/en/examind-community/

```{figure} 02_01_openeo_examind_community.png
:height: 300px
:name: figure-02_01_openeo_examind_community

openEO on Examind Community
```

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
such as `load` and `save` to respectively load data into the graph and
save the result in a format (e.g. GeoTIFF or NetCDF). Examind also
offers a list of mathematical operations, on numbers or coverages (e.g.
multiplying the values of a coverage by a value), and other specific
processes.

To access the list of data and processes that can be used via openEO,
you can use the user interface (via a web editor client) or the STAC /
OpenEO Process API.

```{figure} 02_01_openeo_processes.png
:name: figure-02_01_openeo_processes

openEO processes on Examind
```

Once you have a list of the data you want to use and the processes you
want to use, you can create your first graph. In this graph, you will
chain processes to create the expected result. In the example of the EVI
calculation, we will transfer the formula: `2.5 * (NIR - RED) / (1 +
NIR + 6 * RED + 7.5 * BLUE)`, using mathematical operations in openEO.

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

```{figure} 02_01_openeo_flow_examind.png
:height: 300px
:name: figure-02_01_openeo_flow_examind

openEO flow on Examind
```

**More information (Jupyter notebook + documentation) on Examind Community
OpenEO endpoint is available on
[https://github.com/fair-ease/Examind_Tutorials](https://github.com/fair-ease/Examind_Tutorials).**

There was no immediate practical use for the pilots, but the potential
for further developments are significant.

##### Another example with Copernicus

To give another example of openEO processing, we can use the Copernicus 
platform. You can find all Sentinel data directly here, as well as processes 
that are already available. Below is an example of a workflow for 
calculating an NDVI from Sentinel data.

```{figure} 02_01_openeo_copernicus.png
:name: figure-02_01_openeo_copernicus

openEO flow on Copernicus (NDVI calculation)
```

[^1]: S*ource: [https://openeo.org](https://openeo.org)*
[^2]: S*ource: [https://dataspace.copernicus.eu/](https://dataspace.copernicus.eu/)*
[^3]: S*ource: [https://editor.openeo.org/](https://editor.openeo.org/)*