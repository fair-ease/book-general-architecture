# Galaxy project

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