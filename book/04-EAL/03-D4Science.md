# FAIR-EASE@D4Science

[[D4Science]](https://www.d4science.org/) is a hybrid data
infrastructure, hosted by CNR Italy, designed to support scientific
collaboration and resource sharing across various domains, including
biology, ecology, environmental studies, social sciences. Established in
2014, it connects over 24,000 scientists from 50+ countries, integrates
data from 50+ providers, and provides access to over a billion records
in global repositories. Its key feature is the provision of Virtual
Research Environments (VREs) and Virtual Laboratory (VLab), web-based
platforms tailored to specific community needs. D4Science is notably
used by Blue Cloud 2026.

A Memorandum Of Understanding (MoU) was signed between Blue Cloud 2026
and FAIR-EASE in November 2024, to strengthen collaboration between the
two projects. This led to the creation of a FAIR-EASE VRE, including the
launch of a dedicated gateway
([[https://fair-ease.d4science.org/]](https://fair-ease.d4science.org/))
and the development of two VLABs for Coastal Water Dynamics and Marine
Omics Observation.


```{figure} 04_fe_vre_home.png
:height: 300px
:name: figure-04_fe_vre_home

FAIR-EASE VRE home page on D4Science
```

```{figure} 04_marine_omics_vlab.png
:height: 400px
:name: figure-04_marine_omics_vlab

Marine Omics Observation VLAB on D4Science
```

For the Marine Omics Observation VLAB, we collaborated with the
D4Science team to provide a Galaxy service that enables the chaining of
predefined tools. This instance is available at
[[https://galaxy-gcp.d4science.org/MarineOmicsObservations/]](https://galaxy-gcp.d4science.org/MarineOmicsObservations/).
Currently, only non-interactive tools can be executed due to a technical
issue that still needs to be resolved.

```{figure} 04_galaxy.png
:height: 300px
:name: figure-04_galaxy

Galaxy project service on D4Science
```

For Coastal Water Dynamics, we collaborated with D4Science team to
provide a webODV server providing access to satellite data as well as
reanalysis model output in the form of netCDF files:
[[https://fair-ease.d4science.org/group/coastalwaterdynamics/webodv]](https://fair-ease.d4science.org/group/coastalwaterdynamics/webodv).
These data complement the wide range of environmental data available on
the other webODV servers.

The IDDAS is also available as a VRE widget inside the FAIR-EASE VRE on
D4Science as illustrated in Figure below. The asset selector, like the
current web version of the IDDAS, allows for discovery and access to the
assets harvested from the data infrastructures. It is possible to push
the assets into the user's local workspace in their virtual lab to
conduct their analysis, or use for input to their models and services.
The asset selector includes a human readable as well as a machine
accessible interface with similar functionalities as the IDDAS.


```{figure} 04_iddas.png
:height: 300px
:name: figure-04_iddas

Access point of IDDAS from the FAIR-EASE EAL on D4Science
```