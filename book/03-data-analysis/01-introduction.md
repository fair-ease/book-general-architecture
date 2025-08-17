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