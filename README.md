# Using Remote Sensing to Assess Deforestation in the Democratic Republic of Congo (DRC)

Example notebooks and methodology developed on the MAAP to understand deforestation in protected areas of the DRC.

## Research Goals

* Understand patterns of deforestation in the DRC, specifically in selected protected areas, using high-res Planet
* Where can higher spatial and temporal data, such as Planet data, help quickly identify areas of deforestation?

## Motivation:

A lot of motivation to exploit forests in DRC, extremely rich peatland areas
https://www.nytimes.com/2022/07/24/world/africa/congo-oil-gas-auction.html

## Methodology

### Done
* Establish the protected areas:
   * 1 PA where the GFC dataset showed an interesting “edge effect” deforestation signal
   * 1 PA that is rated lowest in efficiency of all the DRC PAs (using GEDI dataset)
* Establish where there is deforestation within those protected areas using Hans's Global Forest Change dataset.
* Inspect those areas for interesting deforestation signatures - interesting patterns or spotted areas

### Next

* Dig into those areas using the Planet data to understand deforestation better.
    * Quantify the deforestation using a metric such as NDVI loss of ~10% from 2020-2022
    * Tropical forests are always covered with clouds, so higher temporal resolution data helps in identifying deforestation, it allows us more scenes to choose from when selecting imagery (not limited to a couple images)


### Current status

Sam built a script to create virtual raster, stitches to make a mosaic of a given study area. A next step would be to use the script to pull NICFI data and study the data over areas marked as deforested.


