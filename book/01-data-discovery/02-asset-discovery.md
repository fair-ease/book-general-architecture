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
---

# Asset Discovery

## Search UI
The search UI of the IDDAS is available [here](https://fair-ease-iddas.maris.nl/search) and is built on top of the SPARQL endpoint. The SPARQL is the only database behind the UI, which makes it so that all human searches can be translated to a machine to machine query that can be used directly on the SPARQL endpoint. The SPARQL API is accessible [here](https://fair-ease-iddas.maris.nl/sparql) and currently contains the assets provided via the DAB brokering framework and the Blue-Cloud API. In order to set-up the SPARQL endpoint the following approach is taken:
1. The Blue-Cloud records are published in RDF (DCAT-FE) and harvested and collected in one big triple file. 
2. The DAB records are published as RDF (DCAT-FE) and harvested with a SPARQL endpoint. 
3. The Blue-Cloud and DAB records are combined and loaded into one big triple database (Apache DTB). 
4. The database is published via a SPARQL [endpoint](https://fair-ease-iddas.maris.nl/sparql). 

The search UI is designed to be user-friendly, making it easy for users to search and access data using a set of common filters. And because it is built on a RDF database, the current set of filters can easily be expanded too. The search results that are displayed depend on the metadata completeness of the provided data sources. The more complete the metadata of a source, the higher the chance that the result will be displayed. The free text search allows users to find relevant data based on the title, description, and keywords available through the DCAT-FE. Users can narrow down their search results by specifying a time period, using a start date and end date. It is possible to filter data based on a geographic area, by selecting a bounding box with minimum and maximum values for longitude and latitude and by drawing a bounding box on the map.


```{figure} fair-ease-iddas.png

IDDAS search UI
```

## SPARQL API
Instead of using the search UI, users can also use the SPARQL API, which users can query using [Yasgui](https://docs.triply.cc/yasgui-api/) on the [IDDAS SPARQL page](https://fair-ease-iddas.maris.nl/sparql). The direct link to the SPARQL service can also be used, which is available [here](https://fair-ease-iddas.maris.nl/sparql/query). The SPARQL API supports GeoSPARQL for geospatial search. In the SPARQL API, users can construct the SPARQL query themselves, or copy the SPARQL from the search UI and adapt it to their needs. The Figure below shows the input field for the SPARQL query. The user can click on the triangle to execute the query and retrieve the results. 

```{figure} sparql.png

SPARQL API input field
```

The results are given in a table see Figure below with information on the title, media type, link to RDF representation, description, bounding box and catalogue. The results can also be downloaded to CSV.

```{figure} tableIDDASsparql.png

Results from a SPARQL query
```

