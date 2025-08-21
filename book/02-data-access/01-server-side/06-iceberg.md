# Apache Iceberg

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


```{figure} 02_01_iceberg.png
:height: 300px
:name: figure-02_01_iceberg

Apache Iceberg Trino and ERDDAP
```

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


[^16]: [[https://erddap.eoscfe.mesocentre.uca.fr/]](https://erddap.eoscfe.mesocentre.uca.fr/)

[^17]: [[https://glodap.info/index.php/merged-and-adjusted-data-product-v2-2023/]](https://glodap.info/index.php/merged-and-adjusted-data-product-v2-2023/)

[^18]: [[https://erddap.eoscfe.mesocentre.uca.fr/erddap/tabledap/glodap_v2_2023_iceberg2.graph]](https://erddap.eoscfe.mesocentre.uca.fr/erddap/tabledap/glodap_v2_2023_iceberg2.graph)

[^19]: [[https://github.com/fair-ease/erddap-trino-iceberg]](https://github.com/fair-ease/erddap-trino-iceberg)
