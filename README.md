# SMOP


## General information

SMOP stands for Smart MObility Planner.

The route planning engine is OTP.


## Architecture

SMOP is composed of multiple services:

* Maps : [nextmoov-smop-maps](https://github.com/nextmoov/nextmoov-smop-maps)
* Autocomplete addresses : [nextmoov-smop-autocomplete-addr](https://github.com/nextmoov/nextmoov-smop-autocomplete-addr)
* Autocomplete transit : [nextmoov-smop-autocomplete-transit](https://github.com/nextmoov/nextmoov-smop-autocomplete-transit)
* OTP : [nextmoov-smop-otp](https://github.com/nextmoov/nextmoov-smop-otp)

## Data sources

### Maps

The map data proposed are here : [Geofabriek - Download Belgium](http://download.geofabrik.de/europe/belgium.html)

### GTFS Data

The consolidated GTFS file may be provided by [iRail - GTFS](https://gtfs.irail.be/)
