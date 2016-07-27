# RDF-store

How to run [Jena](https://jena.apache.org/) + [Fuseki2](https://jena.apache.org/documentation/fuseki2/).

## Requisites

* [Docker](https://www.docker.com/)

## Running

Setup admin password:

```sh
# Use a better password in real environments
export RDF_PASSWORD=pw
```

Create storage container:

```sh
docker run --name fuseki-data -v /fuseki busybox
```

Run Docker container:

```sh
docker run -d \
  --name fuseki \
  --publish 3030:3030 \
  --e ADMIN_PASSWORD=$RDF_PASSWORD \
  --volumes-from fuseki-data \
  stain/jena-fuseki
```
