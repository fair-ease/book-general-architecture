---
authors:
  - name: Tjerk Krijger
    orcid: 0000-0002-1722-0523
    affiliations:
      - id: maris
        institution: Maris
        ror: 03wr7bx86
  - name: Peter Thijsse
    orcid: 0000-0002-1722-0523
    affiliations:
      - id: maris
        institution: Maris
        ror: 03wr7bx86
  - name: Alexandra Kokkinaki
    orcid: 0000-0001-8042-6391
    affiliations:
      - id: bodc
        institution: British Oceanographic Data Centre
        ror: 03102fn17
  - name: Gwenaëlle Moncoiffé
    orcid: 0000-0001-6559-4178
    affiliations:
      - id: bodc
        institution: British Oceanographic Data Centre
        ror: 03102fn17
  - name: Enrico Boldrini
    orcid: 0000-0003-2075-4742
    affiliations:
      - id: CNR
        institution: National Research Council
        ror: 04zaypm56
---

# DCAT-FE
To optimize dataset discovery and access for users on the web and in the FAIR-EASE Virtual Research Environment (or Earth Analytical Lab), both syntactic and semantic brokerage were required. Since the data providers were not part of the FAIR-EASE project, changes could not be requested in how they expose data and metadata, enhance FAIRness levels, or incorporate additional semantics. Instead, the transformation had to be implemented within the FAIR-EASE IDDAS, utilising the geoDAB broker, Blue-Cloud API and the Semantic Analyser to achieve both syntactic and semantic harmonization while simultaneously improving the FAIRness of the datasets.

To deliver this level of harmonisation the following strategy was adopted:
- A harmonised metadata profile for all datasets was created (DCAT-FE) following the W3C DCAT vocabulary. This target profile (in principle generally applicable) provides the option to enable machine to machine discovery of datasets, independent of datasets being published in a metadata catalogue (harmonised syntactically by the DAB) or via sub-setting services like ERDDAP, BEACON or other. 
- The geoDAB broker harvests metadata from the diverse data sources and harmonises them according to the ISO 19115 XML profile based on the following common metadata elements: identifier, title, keyword, bounding box, temporal extent, parameter, instrument, platform, organisation, date-stamp, revision date, and resource identifier. The metadata are automatically converted to DCAT-FE, immediately raising their FAIR interoperability score.
- In the context of FE, with access to the Blue-Cloud API, a machine-to-machine connection to the data records from the Blue Data Infrastructures (BDI) is available. For each BDI record, the metadata from level 1 and level 2 are combined into one larger metadata file, in order to provide all available metadata. The combined metadata file for each record is thereafter mapped towards DCAT-FE.
- The semantic analyser (SA) assists in detecting terms and controlled vocabularies used within the data sources. In particular, the SA identifies terms listed as free text keywords and provides matches against possible semantic artefacts (terms originating from controlled vocabularies and ontologies). Those matches are then used to replace free text keywords with unique URIs and proper references of semantic artefacts, resulting in raising the semantic profile of a dataset thus its interoperability score.

Full details of IDDAS are available in the final report [D2.5 - FAIR-EASE Data Discovery and Access Service - Final Release](<https://doi.org/10.5281/zenodo.15836888>).

DCAT-FE is available on the FE GitHub [DCAT-FE Profile](<https://github.com/fair-ease/asset-standards/blob/main/DCAT-AP/dataset-example.ttl>). 