[![Build Status](https://travis-ci.org/mivek/MetarParser.svg?branch=master)](https://travis-ci.org/mivek/MetarParser)
[![Maintainability](https://api.codeclimate.com/v1/badges/bfd4e09cccf432218d40/maintainability)](https://codeclimate.com/github/mivek/MetarParser/maintainability)
[![codecov](https://codecov.io/gh/mivek/MetarParser/branch/master/graph/badge.svg)](https://codecov.io/gh/mivek/MetarParser)
# MetarParser


This java lib provides a Metar decoder.

Use the MetarFacade class and its method decode to decode a metar.
Use the MetarFacade class and its method retrieveFromAirport to get the metar of an airport. This metod take the icao code as parameter.
The trends of the metar are not parsed.

## Model
![class diagram](model.jpg)
### Enumerations

The application contains numerous enumarations to represent datas.
  - CloudType: to represent the type of cloud.
  - CloudQuantity: to represent the amount of clouds.
  - Intensity: to represent the intensity of a meteorological phenomenon.
  - Descriptive: to represent the descriptive of a meteorological phenomenon.
  - Phenomenon: to represent a phenomenon.
  
### Classes

#### Airport
The airport class is composed of
  - Name
  - City
  - Country
  - IATA code
  - ICAO code
  - latitude
  - longitude
  - altitude
  - timezone

####  Cloud
In this application a cloud is composed of 
  - CloudQuantity
  - CloudType (optional)
  - altitude (optional)
  
#### Country
A country is represented by its name.

#### Runway information

The runway information is composed of 
  - The name of the runway
  - The minimal visibility on the runway
  - The maximal visibility on the runway (optional)
  - The trend of the visibility (optional)

#### Visibility

The visibility class is composed of
  - The main visibility
  - The minimal visibility (optional)
  - The direction of the minimal visibility (optional)

#### WeatherCondition
The weather condition is class to represent a meteorological phenomenon.
A weather condition is composed of 
  - an intensity (optional)
  - a descriptive (optional)
  - a list of phenomenon
  
#### Wind
The wind class is composed of 
  - the speed
  - the direction
  - the speed of the gust
  - the lowest variable wind
  - the highest variable wind
  - the unit of the wind's speed

## Examples
### Parse a metar
Instantiate the metarFacade and use its method parse.

```java
String code = "LFPG 131830Z 19005KT 170V250 9999 -SHRA FEW040TCU SCT086 16/08 Q1011";
MetarFacade facade = MetarFacade.getInstance();
Metar metar = facade.decode(code);
```

### Retrieve the metar of an airport
Instantiate the metarFacade.
Use the its method retrieveFromAirport with the ICAO code of the airport.

```java
String icao = "LFPG";
MetarFacade facade = MetarFacade.getInstance();
Metar metar = facade.retrieveFromAirport(icao);
```



