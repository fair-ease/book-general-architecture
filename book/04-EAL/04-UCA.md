# FAIR-EASE@UCA

Since mid-2024, we have been working on the implementation of an EAL at
Université de Clermont-Auvergne (UCA), building upon its existing
hardware infrastructure. This infrastructure also hosts the FAIR-EASE
data lake, as described in *Deliverable D4.5 - Deployment of the data
lake: operational version*.

The EAL FAIR-EASE@UCA remains in an incubation phase but is
progressively taking shape through key developments. Notably, it has
been interfaced with the EGI Check-in SSO service to support federated
authentication and has integrated an S3 object storage
([s3://s3.mesocentre.uca.fr](http://s3.mesocentre.uca.fr))
with Ceph deployed by UCA. Applications are being deployed via
OpenStack, providing a flexible and scalable environment for future
services. These foundational components will support the upcoming
deployment of analytical tools and workflows aligned with FAIR-EASE
objectives.

```{figure} 04_uca_egi.png
:height: 300px
:name: figure-04_uca_egi.png

Accessing JupyterLab on UCA via EGI CheckIn
```

Here are the services deployed:


<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 22%" />
<col style="width: 59%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><strong>Building block</strong></th>
<th style="text-align: left;"><strong>Service</strong></th>
<th style="text-align: left;"><strong>URL</strong></th>
</tr>
<tr>
<th rowspan="4" style="text-align: left;"><strong>Data
Access</strong></th>
<th style="text-align: left;">Examind Community</th>
<th style="text-align: left;"><a
href="https://examind.eoscfe.mesocentre.uca.fr/examind/"><u>https://examind.eoscfe.mesocentre.uca.fr/examind/</u></a></th>
</tr>
<tr>
<th style="text-align: left;">Thredds</th>
<th style="text-align: left;"><a
href="https://thredds.eoscfe.mesocentre.uca.fr/"><u>https://thredds.eoscfe.mesocentre.uca.fr/</u></a></th>
</tr>
<tr>
<th style="text-align: left;">ERDDAP</th>
<th style="text-align: left;"><a
href="https://erddap.eoscfe.mesocentre.uca.fr"><u>https://erddap.eoscfe.mesocentre.uca.fr</u></a></th>
</tr>
<tr>
<th style="text-align: left;">Beacon</th>
<th style="text-align: left;"><a
href="https://beacon-argo.eoscfe.mesocentre.uca.fr/"><u>https://beacon-argo.eoscfe.mesocentre.uca.fr/</u></a></th>
</tr>
<tr>
<th rowspan="3" style="text-align: left;"><strong>Data
Analysis</strong></th>
<th style="text-align: left;">WebODV</th>
<th style="text-align: left;"><a
href="https://webodv.eoscfe.mesocentre.uca.fr/"><u>https://webodv.eoscfe.mesocentre.uca.fr/</u></a></th>
</tr>
<tr>
<th style="text-align: left;">TerriaMap</th>
<th style="text-align: left;"><a
href="https://terriamap.eoscfe.mesocentre.uca.fr/"><u>https://terriamap.eoscfe.mesocentre.uca.fr/</u></a></th>
</tr>
<tr>
<th style="text-align: left;">JupyterHub/Lab</th>
<th style="text-align: left;"><a
href="https://jupyterhub.eoscfe.mesocentre.uca.fr/"><u>https://jupyterhub.eoscfe.mesocentre.uca.fr/</u></a></th>
</tr>
</thead>
<tbody>
</tbody>
</table>


<!-- +------------+----------------+----------------------------------------------------------------------------------------------------------------------+
| **Building | **Service**    | **URL**                                                                                                              |
| block**    |                |                                                                                                                      |
+------------+----------------+----------------------------------------------------------------------------------------------------------------------+
| **Data     | Examind        | [[https://examind.eoscfe.mesocentre.uca.fr/examind/]{.underline}](https://examind.eoscfe.mesocentre.uca.fr/examind/) |
| Access**   | Community      |                                                                                                                      |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | Thredds        | [[https://thredds.eoscfe.mesocentre.uca.fr/]{.underline}](https://thredds.eoscfe.mesocentre.uca.fr/)                 |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | ERDDAP         | [[https://erddap.eoscfe.mesocentre.uca.fr]{.underline}](https://erddap.eoscfe.mesocentre.uca.fr)                     |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | Beacon         | [[https://beacon-argo.eoscfe.mesocentre.uca.fr/]{.underline}](https://beacon-argo.eoscfe.mesocentre.uca.fr/)         |
+------------+----------------+----------------------------------------------------------------------------------------------------------------------+
| **Data     | WebODV         | [[https://webodv.eoscfe.mesocentre.uca.fr/]{.underline}](https://webodv.eoscfe.mesocentre.uca.fr/)                   |
| Analysis** |                |                                                                                                                      |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | TerriaMap      | [[https://terriamap.eoscfe.mesocentre.uca.fr/]{.underline}](https://terriamap.eoscfe.mesocentre.uca.fr/)             |
|            +----------------+----------------------------------------------------------------------------------------------------------------------+
|            | JupyterHub/Lab | [[https://jupyterhub.eoscfe.mesocentre.uca.fr/]{.underline}](https://jupyterhub.eoscfe.mesocentre.uca.fr/)           |
+============+================+======================================================================================================================+ -->



### Strengths and areas for improvement


<table>
<colgroup>
<col style="width: 26%" />
<col style="width: 36%" />
<col style="width: 37%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><strong>EAL Implementation</strong></th>
<th style="text-align: left;"><strong>Strengths</strong></th>
<th style="text-align: left;"><strong>Areas for
improvement</strong></th>
</tr>
<tr>
<th style="text-align: left;"><strong>Galaxy for Earth
System</strong></th>
<th style="text-align: left;"><p>- Galaxy as PaaS</p>
<p>- Galaxy Pulsar integration</p>
<p>- Galaxy Training Materials</p>
<p>- CI/CD with GitHub</p>
<p>- Community-based contributions</p></th>
<th style="text-align: left;"><p>- Implement user group management
features</p>
<p>- Enhance integration for discovering and accessing geospatial
reference datasets</p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>D4Science</strong></th>
<th style="text-align: left;"><p>- Integration of various services
(discovery, access, analysis)</p>
<p>- Catalogue and publication mechanisms</p>
<p>- Group management (VLAB, VRE, landing pages)</p>
<p>- Collaboration tools</p></th>
<th style="text-align: left;"><p>- S3 API direct access for better
tool/service integration and support for HTTP Range</p>
<p>- Streamline deployment of new services by external teams</p></th>
</tr>
<tr>
<th style="text-align: left;"><strong>FAIR-EASE@UCA</strong></th>
<th style="text-align: left;"><p>- S3 storage (reference data,
userspace)</p>
<p>- Deployment of new services</p>
<p>- Integration of access and analysis workflows</p>
<p>- Links to other EALs (e.g., Galaxy Europe via Pulsar)</p></th>
<th style="text-align: left;"><p>- Design a landing page for better user
entry points</p>
<p>- Implement group and collaboration management features</p>
<p>- Develop a dedicated service catalogue in connection with the EOSC
node federation</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

+-------------------------+-------------------------+-------------------------+
| **EAL Implementation**  | **Strengths**           | **Areas for             |
|                         |                         | improvement**           |
+-------------------------+-------------------------+-------------------------+
| **Galaxy for Earth      | \- Galaxy as PaaS       | \- Implement user group |
| System**                |                         | management features     |
|                         | \- Galaxy Pulsar        |                         |
| (TRL = 9)               | integration             | \- Enhance integration  |
|                         |                         | for discovering and     |
|                         | \- Galaxy Training      | accessing geospatial    |
|                         | Materials               | reference datasets      |
|                         |                         |                         |
|                         | \- CI/CD with GitHub    |                         |
|                         |                         |                         |
|                         | \- Community-based      |                         |
|                         | contributions           |                         |
+-------------------------+-------------------------+-------------------------+
| **FAIR-EASE@D4Science** | \- Integration of       | \- S3 API direct access |
|                         | various services        | for better tool/service |
| (TRL = 9)               | (discovery, access,     | integration and support |
|                         | analysis)               | for HTTP Range          |
|                         |                         |                         |
|                         | \- Catalogue and        | \- Streamline           |
|                         | publication mechanisms  | deployment of new       |
|                         |                         | services by external    |
|                         | \- Group management     | teams                   |
|                         | (VLAB, VRE, landing     |                         |
|                         | pages)                  |                         |
|                         |                         |                         |
|                         | \- Collaboration tools  |                         |
+-------------------------+-------------------------+-------------------------+
| **FAIR-EASE@UCA**       | \- S3 storage           | \- Design a landing     |
|                         | (reference data,        | page for better user    |
| (TRL = 6)               | userspace)              | entry points            |
|                         |                         |                         |
|                         | \- Deployment of new    | \- Implement group and  |
|                         | services                | collaboration           |
|                         |                         | management features     |
|                         | \- Integration of       |                         |
|                         | access and analysis     | \- Develop a dedicated  |
|                         | workflows               | service catalogue in    |
|                         |                         | connection with the     |
|                         | \- Links to other EALs  | EOSC node federation    |
|                         | (e.g., Galaxy Europe    |                         |
|                         | via Pulsar)             | \- Deploy a vault       |
+=========================+=========================+=========================+


# Conclusion

Over the course of the project, FAIR-EASE has achieved a series of
notable results that have contributed to both technological progress and
community engagement across multiple scientific domains.

FAIR-EASE has exploited existing solutions and successfully adapted them
to new domains and contexts, demonstrating the versatility and
robustness of tools such as Galaxy and webODV for data analysis
services. These technologies, initially designed for specific
communities, have been enhanced to meet broader scientific needs,
promoting interoperability between fields. At the same time, FAIR-EASE
has fostered innovation by introducing new concepts and tackling
technical challenges. The development and implementation of principles
such as UDAL and EAL reflect this commitment to innovation.
Collaboration has been the cornerstone of this success. FAIR-EASE
fostered close interaction between internal partners while building
bridges with external initiatives.

FAIR-EASE has also played a key role in disseminating good practice,
particularly in improving the fairness of data, software and processes.
In response to the growing demand for sustainable computing, FAIR-EASE
has also advocated for remote data processing to minimize unnecessary
data transfers. By supporting standards and technologies such as OGC
API:Processes, S3/ARCO formats, OpenEO, and Galaxy Pulsar, the project
has paved the way for more efficient and scalable processing approaches.
By integrating these principles into tools and workflows, the project
has helped to improve the overall quality and sustainability of research
products.

The project has provided integrated e-infrastructures (EAL) that support
large-scale collaborative science, enabling users to move from one to
another EAL through a system of systems approach, using common federated
capabilities. Platforms such as Galaxy for Earth System Science,
FAIR-EASE@D4Science and the FAIR-EASE@UCA have provided pilots with
robust environments for experimentation, sharing and validation.

Finally, FAIR-EASE has produced a significant number of KERs[^27], each
contributing tangible value to the scientific and technical communities.
These results are not only deliverables but also stepping stones for
further innovation, adoption, and impact beyond the lifetime of the
project.

[^1]: [[https://doi.org/10.5281/zenodo.10069773]{.underline}](https://doi.org/10.5281/zenodo.10069773)

[^2]: [[https://doi.org/10.5281/zenodo.14711074]{.underline}](https://doi.org/10.5281/zenodo.14711074)

[^3]: Source:
    [[https://www.codesmith.io/]{.underline}](https://www.codesmith.io/)

[^4]: [[https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Range_requests]{.underline}](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Range_requests)

[^5]: Source:
    [[https://earthmover.io/]{.underline}](https://earthmover.io/)

[^6]: Source:
    [[https://guide.cloudnativegeo.org/]{.underline}](https://guide.cloudnativegeo.org/)

[^7]: [[https://blog.lobelia.earth/arco-the-smartest-way-to-access-big-geospatial-data-eaf689eff3c9]{.underline}](https://blog.lobelia.earth/arco-the-smartest-way-to-access-big-geospatial-data-eaf689eff3c9)

[^8]: [[https://stacspec.org/en/]{.underline}](https://stacspec.org/en/)

[^9]: [[https://en.wikipedia.org/wiki/HATEOAS]{.underline}](https://en.wikipedia.org/wiki/HATEOAS)

[^10]: S*ource: [[https://openeo.org]{.underline}](https://openeo.org)*

[^11]: S*ource:
    [[https://dataspace.copernicus.eu/]{.underline}](https://dataspace.copernicus.eu/)*

[^12]: *Source:
    [[https://dataspace.copernicus.eu/]{.underline}](https://dataspace.copernicus.eu/)*

[^13]: [*[https://stacspec.org/en/about/stac-spec/]{.underline}*](https://stacspec.org/en/about/stac-spec/)

[^14]: [*[https://openeo.org/documentation/1.0/developers/api/reference.html#section/Processes]{.underline}*](https://openeo.org/documentation/1.0/developers/api/reference.html#section/Processes)

[^15]: [[https://maris-development.github.io/beacon/]{.underline}](https://maris-development.github.io/beacon/)

[^16]: [[https://erddap.eoscfe.mesocentre.uca.fr/]{.underline}](https://erddap.eoscfe.mesocentre.uca.fr/)

[^17]: [[https://glodap.info/index.php/merged-and-adjusted-data-product-v2-2023/]{.underline}](https://glodap.info/index.php/merged-and-adjusted-data-product-v2-2023/)

[^18]: [[https://erddap.eoscfe.mesocentre.uca.fr/erddap/tabledap/glodap_v2_2023_iceberg2.graph]{.underline}](https://erddap.eoscfe.mesocentre.uca.fr/erddap/tabledap/glodap_v2_2023_iceberg2.graph)

[^19]: [[https://github.com/fair-ease/erddap-trino-iceberg]{.underline}](https://github.com/fair-ease/erddap-trino-iceberg)

[^20]: Marc Portier (2023) FAIR-EASE_D4.1_Landscaping exercise_The
    -meta-data, software and cloud needs for the data lake. Zenodo. doi:
    10.5281/zenodo.7965398.

[^21]: PORTIER, M. (2024) FAIR-EASE - D4.3 Status and expectations of
    the FAIR-EASE data lake. Zenodo. doi: 10.5281/zenodo.13933551.

[^22]: [<https://github.com/fair-ease/py-udal-interface>]

[^23]: [<https://github.com/fair-ease/py-udal-fe-impl>]

[^24]: [[https://lab.fairease.eu/dataset-demand-register/registry/]](https://lab.fairease.eu/dataset-demand-register/registry/)

[^25]: *Source:
    [[https://jupytergis.readthedocs.io/en/latest/]](https://jupytergis.readthedocs.io/en/latest/)*

[^26]: [[https://doi.org/10.5281/zenodo.10069773]](https://doi.org/10.5281/zenodo.10069773)

[^27]: [[https://fairease.eu/kers]](https://fairease.eu/kers)
