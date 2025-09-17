
# Galaxy Europe for Earth System subdomain

As part of FAIR-EASE, the Galaxy Europe Earth System subdomain
([[earth-system.usegalaxy.eu]](https://earth-system.usegalaxy.eu))
was created to serve the needs of environmental scientists working with
marine, atmospheric, land, and biodiversity data.

```{figure} 04_02_eal_galaxy.png
:height: 400px
:name: 04_02_eal_galaxy

Earth System subdomain welcome page
```

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

```{figure} 04_02_eal_odv.png
:height: 330px
:name: 04_02_eal_odv

ODV interactive tool in Galaxy
```

**Tools for Oceanographic Data**

<!-- +-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Tool**                                                                                                                      | **Description**            | **Links**                                                                                                    |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Argo_getdata**                                                                                                              | Allows retrieval of Argo   | [[GitHub content]](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | glider data (physical and  |                                                                                                              |
|                                                                                                                               | biogeochemical).           | [[GitHub Galaxy tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean)   |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy PR]](https://github.com/galaxyecology/tools-ecology/pull/81)                            |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **DIVA_full_analysis**                                                                                                        | Implemented as both batch  | [[GitHub content]](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | and interactive tools,     |                                                                                                              |
|                                                                                                                               | this module enables        | [[GitHub Galaxy tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean)   |
|                                                                                                                               | advanced spatial           |                                                                                                              |
|                                                                                                                               | interpolation of marine    | [[Batch PR]](https://github.com/galaxyecology/tools-ecology/pull/118)                            |
|                                                                                                                               | data.                      |                                                                                                              |
|                                                                                                                               |                            | [[GxIT PR]](https://github.com/usegalaxy-eu/galaxy/pull/160)                                     |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Copernicus Marine Data Store** (copernicusmarine)                                                                           | Batch tool to query and    | [[GitHub content]](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | download datasets from     |                                                                                                              |
|                                                                                                                               | CMEMS.                     | [[GitHub Galaxy tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean)   |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]](https://github.com/galaxyecology/tools-ecology/pull/126)                           |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Ocean Data View**                                                                                                           | Used to plot               | [[GitHub Galaxy tool]](https://github.com/bgruening/docker-odv)                                  |
|                                                                                                                               | geo-referenced ocean data  |                                                                                                              |
|                                                                                                                               | from NetCDF and other      | [[GxIT_PR]](https://github.com/usegalaxy-eu/galaxy/pull/166)                                     |
|                                                                                                                               | formats.                   |                                                                                                              |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **ODV collection manager** (tool_odv)                                                                                         | Merges various datasets    | [[GitHub content]](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | with a common vocabulary   |                                                                                                              |
|                                                                                                                               | and creates a single       | [[GitHub Galaxy                                                                                              |
|                                                                                                                               | generic ODV spreadsheet in | tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_data_view_manager) |
|                                                                                                                               | an automatic way           |                                                                                                              |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **ODV history manager** (tool_odv_history)                                                                                    | Report in the input file   | [[GitHub content]](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | the ODV history including  |                                                                                                              |
|                                                                                                                               | the change of QC flag      | [[GitHub Galaxy                                                                                              |
|                                                                                                                               |                            | tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_data_view_manager) |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Canyon B**                                                                                                                  | Robust Estimation of Open  | [[GitHub content]](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
|                                                                                                                               | Ocean CO2 Variables and    |                                                                                                              |
| (bgc_canyonb)                                                                                                                 | Nutrient Concentrations    | [[GitHub Galaxy                                                                                              |
|                                                                                                                               | From T, S, and O2 Data     | tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_neural_network)    |
|                                                                                                                               | Using Bayesian Neural      |                                                                                                              |
|                                                                                                                               | Network                    | [[Conda recipe]](https://github.com/conda-forge/staged-recipes/pull/28638)                       |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]](https://github.com/galaxyecology/tools-ecology/pull/150)                           |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Sanntis**                                                                                                                   | The Sanntis tool identify  | [[GitHub content]](https://github.com/Finn-Lab/SanntiS)                                          |
|                                                                                                                               | biosynthetic gene clusters |                                                                                                              |
| (sanntis_marine)                                                                                                              | (BGCs) in genomic &        | [[GitHub Galaxy                                                                                              |
|                                                                                                                               | metagenomic data           | tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/marine_omics)            |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]](https://github.com/galaxyecology/tools-ecology/pull/121)                           |
|                                                                                                                               |                            | [[Galaxy_PR_2]](https://github.com/galaxyecology/tools-ecology/pull/123)                         |
+-------------------------------------------------------------------------------------------------------------------------------+----------------------------+--------------------------------------------------------------------------------------------------------------+
| **QCV Harmonizer**                                                                                                            | Harmonizes oceanographic   | [[GitHub content]](https://github.com/Marie59/FE-ft-ESG/tree/main/ocean)                         |
| ([[harmonize_insitu_to_netcdf]](https://toolshed.g2.bx.psu.edu/repository/browse_repository?id=38ab3b3c936ea98a)) | biogeochemical data.       |                                                                                                              |
|                                                                                                                               |                            | [[GitHub Galaxy                                                                                              |
|                                                                                                                               |                            | tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/bgc_ocean)               |
|                                                                                                                               |                            |                                                                                                              |
|                                                                                                                               |                            | [[Galaxy_PR]](https://github.com/usegalaxy-eu/usegalaxy-eu-tools/pull/806)                       |
+===============================================================================================================================+============================+==============================================================================================================+ -->

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 40%" />
<col style="width: 26%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><strong>Tool</strong></th>
<th style="text-align: left;"><strong>Description</strong></th>
<th style="text-align: left;"><strong>Links</strong></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Argo_getdata</strong></th>
<th style="text-align: left;">Allows retrieval of Argo glider data
(physical and biogeochemical).</th>
<th><p><a
href="https://github.com/Marie59/FE-ft-ESG/tree/main/ocean"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/pull/81"><u>Galaxy
PR</u></a></p></th>
</tr>
<tr>
<th><strong>DIVA_full_analysis</strong></th>
<th style="text-align: left;">Implemented as both batch and interactive
tools, this module enables advanced spatial interpolation of marine
data.</th>
<th><p><a
href="https://github.com/Marie59/FE-ft-ESG/tree/main/ocean"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/pull/118"><u>Batch
PR</u></a></p>
<p><a href="https://github.com/usegalaxy-eu/galaxy/pull/160"><u>GxIT
PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Copernicus Marine Data
Store</strong> (copernicusmarine)</th>
<th style="text-align: left;">Batch tool to query and download datasets
from CMEMS.</th>
<th><p><a
href="https://github.com/Marie59/FE-ft-ESG/tree/main/ocean"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/pull/126"><u>Galaxy_PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Ocean Data View</strong></th>
<th style="text-align: left;">Used to plot geo-referenced ocean data
from NetCDF and other formats.</th>
<th style="text-align: left;"><p><a
href="https://github.com/bgruening/docker-odv"><u>GitHub Galaxy
tool</u></a></p>
<p><a
href="https://github.com/usegalaxy-eu/galaxy/pull/166"><u>GxIT_PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>ODV collection manager</strong>
(tool_odv)</th>
<th style="text-align: left;">Merges various datasets with a common
vocabulary and creates a single generic ODV spreadsheet in an automatic
way</th>
<th style="text-align: left;"><p><a
href="https://github.com/Marie59/FE-ft-ESG/tree/main/ocean"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_data_view_manager"><u>GitHub
Galaxy tool</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>ODV history manager</strong>
(tool_odv_history)</th>
<th style="text-align: left;">Report in the input file the ODV history
including the change of QC flag</th>
<th style="text-align: left;"><p><a
href="https://github.com/Marie59/FE-ft-ESG/tree/main/ocean"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_data_view_manager"><u>GitHub
Galaxy tool</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><p><strong>Canyon B</strong></p>
<p>(bgc_canyonb)</p></th>
<th style="text-align: left;">Robust Estimation of Open Ocean CO2
Variables and Nutrient Concentrations From T, S, and O2 Data Using
Bayesian Neural Network</th>
<th style="text-align: left;"><p><a
href="https://github.com/Marie59/FE-ft-ESG/tree/main/ocean"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/ocean_neural_network"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/conda-forge/staged-recipes/pull/28638"><u>Conda
recipe</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/pull/150"><u>Galaxy_PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><p><strong>Sanntis</strong></p>
<p>(sanntis_marine)</p></th>
<th style="text-align: left;">The Sanntis tool identify biosynthetic
gene clusters (BGCs) in genomic &amp; metagenomic data</th>
<th style="text-align: left;"><p><a
href="https://github.com/Finn-Lab/SanntiS"><u>GitHub content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/marine_omics"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/pull/121"><u>Galaxy_PR</u></a>
<a
href="https://github.com/galaxyecology/tools-ecology/pull/123"><u>Galaxy_PR_2</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>QCV Harmonizer</strong> (<a
href="https://toolshed.g2.bx.psu.edu/repository/browse_repository?id=38ab3b3c936ea98a"><u>harmonize_insitu_to_netcdf</u></a>)</th>
<th style="text-align: left;">Harmonizes oceanographic biogeochemical
data.</th>
<th style="text-align: left;"><p><a
href="https://github.com/Marie59/FE-ft-ESG/tree/main/ocean"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/bgc_ocean"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/usegalaxy-eu/usegalaxy-eu-tools/pull/806"><u>Galaxy_PR</u></a></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Tools for Interactive Visualisation and Data Handling**

<!-- +-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **Tool**              | **Description**            | **Links**                                                                                                          |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **QGIS**              | Full integration of QGIS   | [[GitHub Galaxy tool]](https://github.com/usegalaxy-eu/docker-qgis)                                    |
|                       | as an interactive tool in  |                                                                                                                    |
|                       | Galaxy.                    | [[GxIT_PR]](https://github.com/usegalaxy-eu/galaxy/pull/200)                                           |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **HoloViz Ecosystem** | A set of interactive       | [[GitHub Galaxy tool]](https://github.com/usegalaxy-eu/docker-holoviz)                                 |
|                       | notebooks for data         |                                                                                                                    |
|                       | visualisation using Python | [[GxIT PR]](https://github.com/usegalaxy-eu/galaxy/pull/207)                                           |
|                       | libraries as Panel, Bokeh, |                                                                                                                    |
|                       | Datashader, etc.           |                                                                                                                    |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **STAC Browser**      | Access and navigation      | [[GitHub content]](https://github.com/radiantearth/stac-browser)                                       |
|                       | interface for STAC         |                                                                                                                    |
|                       | (SpatioTemporal Asset      | [[GxIT PR]](https://github.com/usegalaxy-eu/galaxy/pull/220)                                           |
|                       | Catalogs).                 |                                                                                                                    |
+-----------------------+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| **TerriaMap**         | Geospatial visualisation   | [[GitHub                                                                                                           |
|                       |                            | content]](https://github.com/usegalaxy-eu/galaxy/tree/release_24.2_europe/tools/interactive/terriamap) |
|                       |                            |                                                                                                                    |
|                       |                            | [[GxIt]](https://usegalaxy.eu/root?tool_id=interactive_tool_terriamap)                                 |
+=======================+============================+====================================================================================================================+ -->

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 40%" />
<col style="width: 26%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><strong>Tool</strong></th>
<th style="text-align: left;"><strong>Description</strong></th>
<th style="text-align: left;"><strong>Links</strong></th>
</tr>
<tr>
<th style="text-align: left;"><strong>QGIS</strong></th>
<th style="text-align: left;">Full integration of QGIS as an interactive
tool in Galaxy.</th>
<th style="text-align: left;"><p><a
href="https://github.com/usegalaxy-eu/docker-qgis"><u>GitHub Galaxy
tool</u></a></p>
<p><a
href="https://github.com/usegalaxy-eu/galaxy/pull/200"><u>GxIT_PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>HoloViz Ecosystem</strong></th>
<th style="text-align: left;">A set of interactive notebooks for data
visualisation using Python libraries as Panel, Bokeh, Datashader,
etc.</th>
<th style="text-align: left;"><p><a
href="https://github.com/usegalaxy-eu/docker-holoviz"><u>GitHub Galaxy
tool</u></a></p>
<p><a href="https://github.com/usegalaxy-eu/galaxy/pull/207"><u>GxIT
PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>STAC Browser</strong></th>
<th style="text-align: left;">Access and navigation interface for STAC
(SpatioTemporal Asset Catalogs).</th>
<th style="text-align: left;"><p><a
href="https://github.com/radiantearth/stac-browser"><u>GitHub
content</u></a></p>
<p><a href="https://github.com/usegalaxy-eu/galaxy/pull/220"><u>GxIT
PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>TerriaMap</strong></th>
<th style="text-align: left;">Geospatial visualisation</th>
<th style="text-align: left;"><p><a
href="https://github.com/usegalaxy-eu/galaxy/tree/release_24.2_europe/tools/interactive/terriamap"><u>GitHub
content</u></a></p>
<p><a
href="https://usegalaxy.eu/root?tool_id=interactive_tool_terriamap"><u>GxIt</u></a></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Access to Global and Biodiversity Data**

<!-- +-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **Tool**              | **Description**            | **Links**                                                                                           |
+-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **OBIS occurences**   | A tool to search and       | [[GitHub content]](https://github.com/Marie59/obisindicators)                           |
|                       | retrieve species           |                                                                                                     |
| (obis_data)           | occurrences from the OBIS  | [[GitHub Galaxy                                                                                     |
|                       | database.                  | tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/obisindicators) |
|                       |                            |                                                                                                     |
|                       |                            | [[Galaxy_PR]](https://github.com/galaxyecology/tools-ecology/pull/90)                   |
+-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **Copernicus Data     | Jupyter notebooks to       | [[GitHub content]](https://github.com/eu-cdse/notebook-samples)                         |
| Space Ecosystem**     | explore Copernicus data    |                                                                                                     |
|                       | using SentinelHub and      | [[GxIT PR]](https://github.com/usegalaxy-eu/galaxy/pull/210)                            |
|                       | OpenEO.                    |                                                                                                     |
+-----------------------+----------------------------+-----------------------------------------------------------------------------------------------------+
| **Trends.Earth**      | Batch tool for computing   | [[GitHub content]](https://github.com/Marie59/tools-ecology/tree/trends-earth)          |
|                       | land cover and degradation |                                                                                                     |
|                       | indicators, supporting     | [[GitHub Galaxy                                                                                     |
|                       | monitoring of SDG 15.3.1.  | tool]](https://github.com/galaxyecology/tools-ecology/tree/master/tools/obisindicators) |
|                       |                            |                                                                                                     |
|                       |                            | [[Galaxy_PR]](https://github.com/galaxyecology/tools-ecology/pull/117)                  |
+=======================+============================+=====================================================================================================+ -->

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 40%" />
<col style="width: 26%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><strong>Tool</strong></th>
<th style="text-align: left;"><strong>Description</strong></th>
<th style="text-align: left;"><strong>Links</strong></th>
</tr>
<tr>
<th style="text-align: left;">OBIS occurences (obis_data)</th>
<th style="text-align: left;">A tool to search and retrieve species
occurrences from the OBIS database.</th>
<th style="text-align: left;"><p><a
href="https://github.com/Marie59/obisindicators"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/obisindicators"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/pull/90"><u>Galaxy_PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;">Copernicus Data Space Ecosystem</th>
<th style="text-align: left;">Jupyter notebooks to explore Copernicus
data using SentinelHub and OpenEO.</th>
<th style="text-align: left;"><p><a
href="https://github.com/eu-cdse/notebook-samples"><u>GitHub
content</u></a></p>
<p><a href="https://github.com/usegalaxy-eu/galaxy/pull/210"><u>GxIT
PR</u></a></p></th>
</tr>
<tr>
<th style="text-align: left;">Trends.Earth</th>
<th style="text-align: left;">Batch tool for computing land cover and
degradation indicators, supporting monitoring of SDG 15.3.1.</th>
<th style="text-align: left;"><p><a
href="https://github.com/Marie59/tools-ecology/tree/trends-earth"><u>GitHub
content</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/tree/master/tools/obisindicators"><u>GitHub
Galaxy tool</u></a></p>
<p><a
href="https://github.com/galaxyecology/tools-ecology/pull/117"><u>Galaxy_PR</u></a></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

#### Workflows developed and shared

Several Galaxy workflows have been developed and shared as part of
FAIR-EASE to support Earth system science. These include workflows to
process and analyse Argo float data, extract biogeochemical variables
like phosphate from large NetCDF datasets, and combine oceanographic
data with tools like ODV and the Pangeo ecosystem. All workflows are
openly available on WorkflowHub - [[FAIR-EASE Galaxy Project on
WorkflowHub]](https://workflowhub.eu/projects/267/workflows?utm_source=chatgpt.com) -
and can be imported into Galaxy by clicking the "Run on Galaxy" button
on the WorkflowHub pages. They are designed for environmental scientists
working with oceanographic and Earth system data, and are compatible
with the [[Galaxy Europe For Earth System
instance](https://earth-system.usegalaxy.eu).]

In addition, these workflows were demonstrated during major scientific
events such as EGU 2024, and training materials have been created to
help new users. Tutorials are available through the Galaxy Training
Network, showing how to run the workflows, understand the data, and use
FAIR practices like RO-Crate to describe and share results.

```{figure} 04_02_water_workflow.png
:height: 400px
:name: 04_02_water_workflow

Water Coastal Dynamics workflow
```

<!--  -----------------------------------------------------------------------------------------------------------------------------------------------------------
  **Workflow**       **Description**                    **Access**
  ------------------ ---------------------------------- -----------------------------------------------------------------------------------------------------
  **Marine Omics:    Detects biosynthetic gene clusters [[WorkflowHub]](https://workflowhub.eu/workflows/1663?version=1&utm_source=chatgpt.com)
  Biosynthetic Gene  in marine omics data using tools   
  Clusters**         like Prodigal and SanntiS.         

  **Marine Omics     Converts OBIS biodiversity records [[WorkflowHub]](https://workflowhub.eu/workflows/1698?version=1&utm_source=chatgpt.com)
  Visualisation      into indicators such as Shannon    
  (OBIS              and Simpson indices.               
  Indicators)**                                         

  **Process Argo     Processes Argo float data and      [[WorkflowHub]](https://workflowhub.eu/workflows/1436?utm_source=chatgpt.com)
  Data with Pangeo & visualizes oceanographic variables 
  ODV**              using Pangeo and Ocean Data View   
                     (ODV).                             

  **Subset           Subsets NetCDF data for the        [[WorkflowHub]](https://workflowhub.eu/workflows/1445?utm_source=chatgpt.com)
  Mediterranean Sea  Mediterranean Sea and extracts     
  & Extract          phosphate levels for analysis.     
  Phosphate**                                           

  **Full Analysis of End-to-end workflow to analyse and [[WorkflowHub]](https://workflowhub.eu/workflows/1113)
  Argo Data**        visualise Argo profile datasets.   

  **Argo-Glider      Qualification, Calibration and     [[Galaxy Earth
  Nitrate QCV**      validation of Argo floats and      System]](https://earth-system.usegalaxy.eu/published/workflow?id=44827462c065bae3)
                     Gliders ocean Biogeochemical Data  
                     Using Galaxy                       
  ----------------------------------------------------------------------------------------------------------------------------------------------------------- -->


<table>
<colgroup>
<col style="width: 26%" />
<col style="width: 48%" />
<col style="width: 24%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><strong>Workflow</strong></th>
<th style="text-align: left;"><strong>Description</strong></th>
<th style="text-align: left;"><strong>Access</strong></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Marine Omics: Biosynthetic Gene
Clusters</strong></th>
<th style="text-align: left;">Detects biosynthetic gene clusters in
marine omics data using tools like Prodigal and SanntiS.</th>
<th style="text-align: left;"><a
href="https://workflowhub.eu/workflows/1663?version=1&amp;utm_source=chatgpt.com"><u>WorkflowHub</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Marine Omics Visualisation (OBIS
Indicators)</strong></th>
<th style="text-align: left;">Converts OBIS biodiversity records into
indicators such as Shannon and Simpson indices.</th>
<th style="text-align: left;"><a
href="https://workflowhub.eu/workflows/1698?version=1&amp;utm_source=chatgpt.com"><u>WorkflowHub</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Process Argo Data with Pangeo
&amp; ODV</strong></th>
<th style="text-align: left;">Processes Argo float data and visualizes
oceanographic variables using Pangeo and Ocean Data View (ODV).</th>
<th style="text-align: left;"><a
href="https://workflowhub.eu/workflows/1436?utm_source=chatgpt.com"><u>WorkflowHub</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Subset Mediterranean Sea &amp;
Extract Phosphate</strong></th>
<th style="text-align: left;">Subsets NetCDF data for the Mediterranean
Sea and extracts phosphate levels for analysis.</th>
<th style="text-align: left;"><a
href="https://workflowhub.eu/workflows/1445?utm_source=chatgpt.com"><u>WorkflowHub</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Full Analysis of Argo
Data</strong></th>
<th style="text-align: left;">End-to-end workflow to analyse and
visualise Argo profile datasets.</th>
<th style="text-align: left;"><a
href="https://workflowhub.eu/workflows/1113"><u>WorkflowHub</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Argo-Glider Nitrate
QCV</strong></th>
<th style="text-align: left;">Qualification, Calibration and validation
of Argo floats and Gliders ocean Biogeochemical Data Using Galaxy</th>
<th><a
href="https://earth-system.usegalaxy.eu/published/workflow?id=44827462c065bae3"><u>Galaxy
Earth System</u></a></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

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

```{figure} 04_02_gtn.png
:height: 400px
:name: 04_02_gtn

GTN example
```


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 12%" />
<col style="width: 46%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><strong>Title</strong></th>
<th style="text-align: left;"><strong>Type</strong></th>
<th style="text-align: left;"><strong>Description</strong></th>
<th style="text-align: left;"><strong>Access</strong></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Getting your hands-on earth
data</strong></th>
<th style="text-align: left;">Learning Pathway</th>
<th style="text-align: left;">Introduction to accessing and analyzing
ocean, land, atmosphere, biodiversity data in Galaxy.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/climate/tutorials/earth_system/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>OBIS Marine
Indicators</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Calculate biodiversity indices (Shannon,
Simpson, ES50) from OBIS.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/ecology/tutorials/obisindicators/tutorial.html?utm_source=chatgpt.com"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>From NDVI with OpenEO to time
series with Holoviews</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Process NDVI satellite data for land
degradation analysis and time-series visualization.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/ecology/tutorials/ndvi/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Marine Omics: Identifying
BGCs</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Detect biosynthetic gene clusters using
Prodigal, InterProScan, SanntiS.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/ecology/tutorials/marine_omics_bgc/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Ocean’s Variables
Study</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Subset Mediterranean ocean data and
explore variables (e.g., phosphate).</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/climate/tutorials/oceans_var/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Ocean Data View
(ODV)</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Visualize NetCDF-based oceanographic
variables using ODV.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/climate/tutorials/ocean_data_view/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Sentinel 5P Data
Visualisation</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Explore and analyze Sentinel-5P atmosphere
data interactively.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/climate/tutorials/sentinel5_data/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Analyse Argo Data</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Process Argo float datasets with Pangeo
tools and visualize using ODV</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/climate/tutorials/argo/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Make your tools available on your
subdomain</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Guide to managing tools in a Galaxy
subdomain.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/community/tutorials/tools_subdomains/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Create a subdomain for your
community</strong></th>
<th style="text-align: left;">Tutorial</th>
<th style="text-align: left;">Steps to create and administer a Galaxy
subdomain for your community.</th>
<th style="text-align: left;"><a
href="https://training.galaxyproject.org/training-material/topics/community/tutorials/tools_subdomains/tutorial.html"><u>Run
Tutorial</u></a></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<!--
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Title**         **Type**   **Description**                   **Access**
  ----------------- ---------- --------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------
  **Getting your    Learning   Introduction to accessing and     [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/climate/tutorials/earth_system/tutorial.html)
  hands-on earth    Pathway    analyzing ocean, land,            
  data**                       atmosphere, biodiversity data in  
                               Galaxy.                           

  **OBIS Marine     Tutorial   Calculate biodiversity indices    [[Run
  Indicators**                 (Shannon, Simpson, ES50) from     Tutorial]](https://training.galaxyproject.org/training-material/topics/ecology/tutorials/obisindicators/tutorial.html?utm_source=chatgpt.com)
                               OBIS.                             

  **From NDVI with  Tutorial   Process NDVI satellite data for   [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/ecology/tutorials/ndvi/tutorial.html)
  OpenEO to time               land degradation analysis and     
  series with                  time-series visualization.        
  Holoviews**                                                    

  **Marine Omics:   Tutorial   Detect biosynthetic gene clusters [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/ecology/tutorials/marine_omics_bgc/tutorial.html)
  Identifying                  using Prodigal, InterProScan,     
  BGCs**                       SanntiS.                          

  **Ocean's         Tutorial   Subset Mediterranean ocean data   [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/climate/tutorials/oceans_var/tutorial.html)
  Variables Study**            and explore variables (e.g.,      
                               phosphate).                       

  **Ocean Data View Tutorial   Visualize NetCDF-based            [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/climate/tutorials/ocean_data_view/tutorial.html)
  (ODV)**                      oceanographic variables using     
                               ODV.                              

  **Sentinel 5P     Tutorial   Explore and analyze Sentinel-5P   [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/climate/tutorials/sentinel5_data/tutorial.html)
  Data                         atmosphere data interactively.    
  Visualisation**                                                

  **Analyse Argo    Tutorial   Process Argo float datasets with  [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/climate/tutorials/argo_pangeo/tutorial.html)
  Data**                       Pangeo tools and visualize using  
                               ODV                               

  **Make your tools Tutorial   Guide to managing tools in a      [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/community/tutorials/tools_subdomains/tutorial.html)
  available on your            Galaxy subdomain.                 
  subdomain**                                                    

  **Create a        Tutorial   Steps to create and administer a  [[Run Tutorial]](https://training.galaxyproject.org/training-material/topics/community/tutorials/tools_subdomains/tutorial.html)
  subdomain for                Galaxy subdomain for your         
  your community**             community.                        
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -->

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

```{figure} 04_02_pulsar.png
:height: 350px
:name: 04_02_pulsar

French Galaxy Pulsar endpoint at the UCA
```
