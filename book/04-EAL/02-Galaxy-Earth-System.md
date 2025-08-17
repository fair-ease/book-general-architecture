
# Galaxy Europe for Earth System subdomain

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
