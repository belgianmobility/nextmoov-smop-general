# SMOP


## General information

SMOP stands for Smart MObility Planner.

The route planning engine is OTP.


## Architecture

![Software Architecture](./doc/SoftwareArchitecture.png)

SMOP is composed of multiple services:

* Maps : [nextmoov-smop-maps](https://github.com/nextmoov/nextmoov-smop-maps)
* Autocomplete addresses : [nextmoov-smop-autocomplete-addr](https://github.com/nextmoov/nextmoov-smop-autocomplete-addr)
* Autocomplete transit : [nextmoov-smop-autocomplete-transit](https://github.com/nextmoov/nextmoov-smop-autocomplete-transit)
* OTP : [nextmoov-smop-otp](https://github.com/nextmoov/nextmoov-smop-otp)

You can get all the modules by usuing : `git submodule update --init`.

## Starting things

You can use each module independently, just pick what you need in the `docker-compose.yml` file.

### With OTP (aka With Route Planning)

To have a system operational with OTP, you need to:

* To provide a OSM PBF file (See [Data sources](#data-sources)) in the directory `data` alongside the docker-compose.yml file.

* To provide static GTFS zip files (See [Data sources](#data-sources)) in the directory `data` alongside the docker-compose.yml file.

* The provided static GTFS files needs to be named `xxx-gtfs.zip` (where xxx is only composed of lower case letters).

* Build OTP (it takes 15 minutes... on my machine) : `docker-compose run otp-builder ./build`

Example of last line of the build, when it succeeds :
```
13:49:26.629 INFO (GraphBuilder.java:153) Graph building took 15.1 minutes.
```

Then see [Without OTP](#without-otp-aka-without-route-planning).

### Without OTP (aka Without Route Planning)

To start the system, you need to : 

* Start everything : `docker-compose up`

## Using the services

All services will be accessible trough the reverce-proxy [Traefik 2](https://traefik.io/) on http://localhost:8080.

Only the OTP web interface is located at http://localhost:8081. 

See each services for more information about their API.

## Data sources

### Maps

The map data proposed are here : [Geofabriek - Download Belgium](http://download.geofabrik.de/europe/belgium.html)

### GTFS static

The consolidated GTFS file may be provided by [iRail - GTFS](https://gtfs.irail.be/)

### GTFS RT

To have access to the GTFS RT feeds from the public transport operators (PTOs) you need to subscribe to their services :

* [DeLijn](https://data.delijn.be/docs/services/)
* [SNCB / NMBS](https://www.belgiantrain.be/en/3rd-party-services/mobility-service-providers/public-data)
* [STIB / MIVB](https://opendata.stib-mivb.be/)
* TEC is currently working on feed accessible to everyone

### Villo

JCDecaux provides an open API to get bikes availability, you can subscribe [here](https://developer.jcdecaux.com/#/opendata/vls?page=getstarted) to create an account.
