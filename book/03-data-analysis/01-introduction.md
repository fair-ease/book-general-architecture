# Data Analysis

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


```{figure} 03_01_udal_principle.png
:height: 300px
:name: 03_01_udal_principle

UDAL principle
```

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
  [[https://github.com/fair-ease/py-udal-pokapok]](https://github.com/fair-ease/py-udal-pokapok)

- Marine Omics Observation:
  [[https://github.com/fair-ease/py-udal-mgo]](https://github.com/fair-ease/py-udal-mgo)

Most notably in this final phase of the project we would like to
highlight the introduction of the **Dataset Demand Registry** [^24] and
its associated "Query Editor":

```{figure} 03_01_udal_query_editor.png
:height: 400px
:name: 03_01_udal_query_editor

screenshot of the UDAL Query Editor
```
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


[^20]: Marc Portier (2023) FAIR-EASE_D4.1_Landscaping exercise_The-meta-data, software and cloud needs for the data lake. Zenodo. doi: 10.5281/zenodo.7965398.
[^21]: PORTIER, M. (2024) FAIR-EASE - D4.3 Status and expectations of the FAIR-EASE data lake. Zenodo. doi: 10.5281/zenodo.13933551.
[^22]: [<https://github.com/fair-ease/py-udal-interface>]
[^23]: [<https://github.com/fair-ease/py-udal-fe-impl>]
[^24]: [[https://lab.fairease.eu/dataset-demand-register/registry/](https://lab.fairease.eu/dataset-demand-register/registry/)