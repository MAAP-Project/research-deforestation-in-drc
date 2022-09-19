# Using Remote Sensing to Assess Deforestation in the Democratic Republic of Congo (DRC)

Example notebooks and methodology developed on the MAAP to understand deforestation in protected areas of the DRC.

## Research Goals

* Understand patterns of deforestation in the DRC, specifically in selected protected areas, using high-res Planet data.
* Where can higher spatial and temporal data, such as Planet data, help quickly identify areas of deforestation?

## Motivation:

There is risk of exploitation of forests in DRC from oil and gas, having extremely rich peatland areas
https://www.nytimes.com/2022/07/24/world/africa/congo-oil-gas-auction.html

## Methodology - High Level

### Done
* Establish the protected areas:
   * 1 protected area (PA) where the (global forest cover) GFC dataset showed an interesting “edge effect” deforestation signal
   * 1 PA that is rated lowest in efficiency of all the DRC PAs (using GEDI dataset)
* Establish where there is deforestation within those protected areas using Hans's Global Forest Change dataset.
* Inspect those areas for interesting deforestation signatures - interesting patterns or spotted areas

### Next

* Dig into those areas using the Planet data to understand deforestation better.
    * Quantify the deforestation using a metric such as NDVI loss of ~10% from 2020-2022
    * Tropical forests are always covered with clouds, so higher temporal resolution data helps in identifying deforestation, it allows us more scenes to choose from when selecting imagery (not limited to a couple images)

### Current status

Sam built a script to create virtual raster, stitches to make a mosaic of a given study area. A next step would be to use the script to pull NICFI data and study the data over areas marked as deforested.

## Methodology - Notebook

The methodology below outlines the steps taken in the notebook.

### Section 1: Data Prep

* Install packages, upload shapefiles, set folder paths, etc.
* Crop the GFC (global forest cover) tiles to the area of interest.
    * The GFC dataset is very large so it’s easier to crop it to the AOI before processing it further.
    * There is a checkpoint so that a smaller cropped GFC file is created (“gfc_masked”) that can be used if you want to close the notebook and return later or if your session times out
    * The GFC file is the “lossmask” version, which is a raster showing a value of 0 for “no loss” and a value of 1 for “loss”. Therefore when plotting this data keep in mind it does not show total biomass, rather just areas where there was some record of loss.

### Section 2: Crop the GFC tiles to Protected Areas (PAs)

* The first part of this section is only included because the PA file we had was not a multipolygon file, therefore you could not select one PA of interest and crop the GFC file using it.
    * The first part therefore splits up the PAs into a list, then you can index it to select a PA of interest.
    * Really there should be a new file with all the PAs saved as separate polygons with a field for their IDs according to “protected planet”, that way you can find one online and directly select it in the dataset
* Again there is a checkpoint at the end of the section so you can use that file later if you close the notebook

### Section 3: Test various PAs to see their GFC loss

* You can select a PA using second set of square brackets (currently says 65).
    * Change this number according to the index number from the list created in step 2.
* This shows a more granular view into the GFC loss within a specific PA.

### Section 4: Viewing the GFC lossmask data for the selected PAs

* Note: the cell with PA_3 has not been processed, so don’t use it until you’re sure the NICFI quads cover it
* The leaflet map was included just so the user could zoom and pan around the selected PAs
    * Since the GFC dataset has a spatial res of 30m, it isn’t the most helpful but can be used to see any landmarks or other POIs near the selected PAs


