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

# Beacon

**Beacon** is able to provide users with fast and easy access to
multidisciplinary data originating from large collections, on the fly
with high performance, and extract specific data based on the user's
request.

This software has been customised and deployed in the Blue-Cloud2026
project, FAIR-EASE, among other projects including national ones and is
designed to return one single harmonised file as output, regardless of
whether the input contains different data types. It allows everyone to
set-up their own Beacon 'instance' to enhance the access to their data
or use existing Beacon instances from well-known data infrastructures
such as Euro-Argo or the World Ocean Database for fast and easy access
to harmonized data subsets.

More technical details, example applications and general information on
Beacon can be found on the [website](https://beacon.maris.nl/), [documentation](https://maris-development.github.io/beacon/) and on [Github](https://github.com/maris-development/beacon).

In order to use Beacon for providing access to harmonised subsets, a set
of in total 8 monolithic Beacon instances were set-up for relevant data
collections such as the WOD, Copernicus Marine Cora, Euro-Argo,
SeaDataNet, and more. The term 'monolithic' is used to indicate that the
Beacon instance concerns one data infrastructure. After initial
configuration at a MARIS server, all 8 instances have been deployed
operationally, with Argo also being available on the UCA Testbed. All
have been integrated with the D4Science federated AAI service, by which
access is arranged. All Beacon instances also have been provided with
its own dedicated Jupyter-notebook which sits on the Beacon API and
which makes it easier for the users to interact. The notebooks already
contain several queries and users can adapt their own notebooks.

The following figure shows access to the Argo data collection that is
hosted on the UCA Testbed. The user is able to retrieve on-the-fly
access to Argo data following their query criteria in less than 10
seconds. The data can be stored in different output formats and easily
converted to a dataframe as depicted here for further analysis.

```{figure} beaconargo.png

Access to Argo collection via Beacon
```
The following figure shows an example application of Beacon for access
to the WOD. By sending a POST request to the Beacon endpoint, with a set
of columns and filters, the user retrieves on-the-fly in a few seconds
all data in one single file, fitting the filter criteria. This is then
available for further processing. Here a simple plot is shown for
temperature data from the WOD.

```{figure} wod.png

Access to World Ocean Database collection via Beacon
```
