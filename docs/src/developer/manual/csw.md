# CSW

## Overview

Catalogue Service for the Web ([CSW](https://www.ogc.org/standard/cat/)) is a catalogue service support the ability to 
publish and search collections of descriptive information (metadata) for data, services, and related information objects. 
Metadata in catalogues represent resource characteristics that can be queried and presented for evaluation and further 
processing by both humans and software. Catalogue services are required to support the discovery and binding to registered 
information resources within an information community.


In SAEOSS portal, we implemented [pycsw](https://pycsw.org) to allow the publishing and discovery of geospatial metadata 
via numerous APIs. 



## pycsw configuration

There are many ways to install pycsw, but in SAEOSS we install it via docker. After building the project, there is a 
container called `saeoss-pycsw-1`

After running the `docker-compose`, the CSW page is visible at [http://localhost:5001/](http://localhost:5001/)

![csw-page](img/csw-page.png)


### Generate pycsw DB view

To be able to access the portal's datasets via various OGC standards and on CSW web page, a materialized view 
must be created into the database and integrated into pycsw. 

```bash
docker exec -ti saeoss_ckan-web_1 poetry run ckan saeoss pycsw create-materialized-view
```


### Refresh pycsw materialized view



```bash
docker exec -t saeoss-ckan-web-1 poetry run ckan saeoss pycsw refresh-materialized-view
```
