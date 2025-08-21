# openEO

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

```{figure} 02_01_openeo.png
:height: 300px
:name: figure-02_01_openeo

Unify data access with openEO *[^10]*
```
[^10]

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

[^10]: S*ource: [[https://openeo.org]](https://openeo.org)*
[^11]: S*ource: [[https://dataspace.copernicus.eu/]{.underline}](https://dataspace.copernicus.eu/)*