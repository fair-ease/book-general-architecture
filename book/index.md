# Welcome to the FAIR-EASE book

[**EOSC FAIR-EASE**](https://fairease.eu/) project aims to provide researchers from all disciplines with simplified 
access to heterogeneous environmental and earth science data, computing resources, services and tools. This book 
documents the project's vision, challenges, technical solutions and demonstrators.

## General architecture
```{figure} fair-ease-general-architecture.png
```


## Data Acccess

The [**Interdisciplinary Data Discovery and Access Service**](01-data-discovery/01-introduction.md) (IDDAS)
focuses on providing a semantically enriched metadata catalogue based on
a customised DCAT application profile ([DCAT-FE](01-data-discovery/01-metadata-management/01-DCAT-FE.md)),
enabling seamless data discovery and access across domains and platforms, 
both for human and machine.

## Data Acccess

The [**FAIR-EASE**](https://fairease.eu/) project explored both server-side mechanisms, which aim to
improve performance, scalability and interoperability in heterogeneous
data infrastructures, and client-side usage, which focus on simplifying
data access for users, particularly those without in-depth technical
expertise, but also the robustness of applications over time.

By taking these two perspectives into account, the project ensures that
data can be accessed smoothly, efficiently and transparently, whether
through automated workflows or user-friendly interfaces tailored to real
scientific use cases.

For the server-side part we evaluated four technical solutions: 
- S3 / ARCO combination for serverless and cloud-ready subsetting
- STAC / OpenEO combination for unified data access and remote process on
datacubes
- Beacon for efficient data access and data harmonisation
capabilities, and Apache Iceberg for managing large-scale tabular data.

## Data 

To be completed

## Demonstrators

To be completed