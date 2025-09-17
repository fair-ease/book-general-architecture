# TerriaMap

TerriaMap is an Australian Open Source web application for building
web-based map viewers, Atlases and Digital Twin Interfaces. The platform
was originally developed by CSIRO (Australia's national Science Agency).
It is similar in concept to the European
[EDITO](https://dive.edito.eu/) digital twin interface.
TerriaMap is now supported by a commercial Support company Terria Pty
ltd. ([terria.io](http://terria.io))

Terriamap was used in the "Terriamap Challenge" at the FAIREASE
Hackathon in Brest in March 2025. The hackathon challenge explored how
diverse environmental datasets (e.g. Argo, Omics data) and OGC and other
data services (from Examind, Thredds, ERDDAP, Beacon) could be
visualized and interacted with in the TerriaMap web application,
allowing for cross disciplinary integration of data services from the
FAIR-EASE use cases and infrastructure.

```{figure} 03_terriamap_2d_3d.png
:height: 300px
:name: figure-03_terriamap_2d_3d

Terriamap 2D and 3D display modes
```
Terriamap is based on the Terriajs javascript library, the source code
and user configurable files are published on Github in the [[TerriaMap
github repository]](https://github.com/TerriaJS/TerriaMap).
Documentation on the installation and configuration of Terriamap and the
various supported data services and data sources is available at
[https://docs.terria.io/guide/](https://docs.terria.io/guide/)

```{figure} 03_terriamap_omics_argo.png
:height: 300px
:name: figure-03_terriamap_omics_argo.png

Terriamap displaying OMICs metadata and ARGO profile data from ERDDAP
```
An instance of Terriamap configured with example datasets from the Brest
Hackathon is published on the the University Clermont Auvergne(UCA) at
[https://terriamap.eoscfe.mesocentre.uca.fr/](https://terriamap.eoscfe.mesocentre.uca.fr/)

```{figure} 03_terriamap_cmems.png
:height: 350px
:name: figure-03_terriamap_cmems

Terriamap displaying CMEMS Chlorophyll data from Examind and SO2 data from Thredds
```
The Terriamap example configurations compiled during the Hackathon are
available on
[https://github.com/fair-ease/terria-config](https://github.com/fair-ease/terria-config)