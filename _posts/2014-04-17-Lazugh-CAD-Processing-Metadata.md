---
Date: 2014-04-17 20:00
Title: Processing the Lazugh CAD survey
Category: Oman, CAD, AutoCAD MAP, GIS, transform, enhance, Earthwatch, Lazugh, NFRCEC, Open Street Map
Tags: Oman, CAD, AutoCAD MAP, GIS, transform, enhance, Earthwatch, Lazugh, NFRCEC, Open Street Map
layout: post
---

# Metadata

This document is formatted using MarkDown

This work was done by Anthony Beck, [OrcID: 0000-0002-2991-811X](http://orcid.org/0000-0002-2991-811X).

This work was done for free because I want to see it in Open Street Map. 

You can download the files from [my anonymous ftp sites here: ftp://79.77.41.237/FTPBeck/Lazugh.zip](ftp://79.77.41.237/FTPBeck/Lazugh.zip).

# Things for others to do and be aware of

* Sort out the projection
* Check that these file reflect the original data (i.e. validate this stuff)
	* Specifically check to see if the number of trees output represent the number of trees in the oroginal
* There are, inevitable, weirdnesses in the data. If you see the csv file you will find co-ordinates that are not in Luzugh. Not sure if I can do anything about this - I think it's  an artifact of the way they did there CAD work.
* There are no attributes in the polygon shapefiles. I'm not that bothered. You may be
* The falaj system is currently as polylines (in Structure) you can export it as an individual thing. Do note that it does connect through to other landscape features (wells, cisterns, generators etc. ) - this connectivity has not been fully articulated (you are in a better position to do this than you were). BTW some of the falaj original survey is pretty poor).
* I'm happy to chat about this.

I will put this into Open Street Map once I've had initial feedback from you all. In OSM hopefully other people will sort out some of the problems/layering issues which means you will have a better base-map to work with :-)

# Processing the Lazugh CAD survey

* Done in AutoCAD MAP
* All saved in Lazugh/CAD
* Open file "Survey drawing".dwg
* Document layer types and details (stored in WhatTheLayersMean.xlsx)
* Cleaned out extraneous rubbish (hatch layers etc) saved the layer as Survey_drawing_ARB_clean.dwg 
* Created an autoCAD map query template linking to Survey_drawing_ARB_clean.dwg called LazughTemplate.dwg
* Pull out the groups as defined in the excell spreadsheet and process independently
* All further work saved in Lazugh/CAD/Derivatives

# Processing the 3d data

Completed = Yes

## Purpose

This data represents 3d point and breakline data suitable for producing a Digital Elevation Model within a GIS package.

## Outputs

* 3d_Lazugh.dwg
* 3d_points.csv
* 3d_breaklines.shp
* 3d points.shp

## Layers

* 3D breakline	Line
* b break line	Line
* SRF-FLT	Line
* SURVEY DATA	Point

## Processing

* Template saved as 3d_Lazugh.dwg
* A Map query was run as 'Report'on the layer 'SURVEY DATA' reporting X, Y, Z to the file 3d_points.csv
	* This was saved as Lazugh_Report_Template.dwg
* A Map query was run as 'draw' on the following layers
	* 3D breakline	Line
	* b break line	Line
	* SRF-FLT	Line
	* SURVEY DATA	Point
* A visual inspection showed that SRF-FLT contained most of the breakline data (layers '3d breakline' and 'b break line' were deleted)
* The data was exported into the subfolder ShapeFiles:
	* Line geometry as 3d_breaklines.shp
	* Point geometry as 3d points.shp
		
# Processing the Control data

Completed = Yes

## Purpose

The survey company established 3d control points in the study area. These will be useful for future survey work.

## Outputs

* Control_Lazugh.dwg
* Control_points.csv
* Control_points.shp

## Layers

* BENCH MARK 	Point

## Processing

* Using Lazugh_Report_Template.dwg
	* A Map query was run as 'Report' on the layer 'BENCH MARK' reporting X, Y, Z to the file Control_points.csv
* a copy of LazughTemplate.dwg was made and called Control_Lazugh.dwg
* A Map query was run as 'draw' on the following layers
	* BENCH MARK 	Point
* The data was exported into the subfolder ShapeFiles:
	* Point geometry as 3d points.shp
	
# Processing the Falaj data

Completed = No - it has been incorporated into the SURFACE output (you can extract it from the LINE shapefile). I'd have liked tis to be prettier.... ho hum.

## Purpose

The Falaj network in Lazugh.

## Outputs

* 


## Layers

* 3d falaj centre line	Line	Falaj
* 3d falaj line	Line	Falaj
* NEW FALAJ 3d CENTRE line	Line	Falaj
* NEW FALAJ 3d CENTRE line	Line	Falaj
* Wash box	Polygon	Falaj
* Water pole	Mixed	Falaj
* Water tank	Polygon	Falaj
* Well	Polygon	Falaj
* CW	Line	Falaj?

## Processing

* a copy of LazughTemplate.dwg was made and called Falaj_Lazugh.dwg
* A Map query was run as 'draw' on the following layers
	* 
* The data was exported into the subfolder ShapeFiles:
	* Point geometry as 

# Processing the Network data

Completed = Yes

## Purpose

Road and track network data in Lazurgh

## Outputs

* Network_Lazugh.dwg
* Network_Polygon.shp
* Network_Line.shp

## Layers

* Asphalt Road	Line
* TRACK ROAD	Line

## Processing

* A copy of LazughTemplate.dwg was made and called Network_Lazugh.dwg
* A Map query was run as 'draw' on the following layers
	* Asphalt Road	Line
	* TRACK ROAD	Line
* The polygon segments were closed
* Drawing cleanup was used to create topologically clean line segments
* Topology was created
* Closed polygons were created on the layer 'RoadPolygon'
* The data was exported into the subfolder ShapeFiles:
	* Polygon geometry as Network_Polygon.shp
	* Line geometry as Network_line.shp

# Processing the Street Furniture data

Completed = Yes

## Purpose

Street Furniture in Lazurgh

## Outputs

* StreetFurniture_Lazugh.dwg
* StreetFurniture_Points.shp
* StreetFurniture_Points.csv

## Layers

* BOLLARDS	point
* EP	Point
* FH	Point
* LP	Point
* PIPE	point
* POLE	point
* TP	Point
* UGC	Point
* VALVE02	Point
* Road Sign Board	point

## Processing

* A copy of LazughTemplate.dwg was made and called StreetFurniture_Lazugh.dwg
* A Map query was run as 'draw' on the following layers
	* BOLLARDS	point
	* EP	Point
	* FH	Point
	* LP	Point
	* PIPE	point
	* POLE	point
	* TP	Point
	* UGC	Point
	* VALVE02	Point
	* Road Sign Board	point
* The layers were renamed to something sensible
* The data was exported into the subfolder ShapeFiles (layers was exported as an attribute):
	* Point geometry as StreetFurniture_Point.shp
* The X,Y, Z and Layer value were then exported as a re[port into StreetFurniture_Points.csv

# Processing the Vegetation (including trees) data

Completed = Yes

## Purpose

Exporting al the the vegetation areas as recorded in Luzugh

## Outputs

* Vegetation_Lazugh.dwg
* Vegetation_Point.shp
* Vegetation_Point.csv

## Layers

* BUSH	Mixed
* DATES	Point
* DATES DRY	Point
* DATES MEDIUM	Point
* DATES SMALL	Point
* FLOWER	Point
* LEMON TREE DRY	Point
* TREE	Point
* TREE ALLEE	Point
* TREE ANAR	Point
* TREE BANANA	Point
* TREE COCONUT	Point
* TREE GUVA	Point
* TREE NEEM	Point
* TREE ORANGE	Point
* TREE PAPPAYA	Point
* TREE SMALL	Point

## Processing

* A Map query was run as 'report' on the following layers exporting (X, Y, Z and Layer) into Vegetation_point.csv
	* BUSH	Mixed
	* DATES	Point
	* DATES DRY	Point
	* DATES MEDIUM	Point
	* DATES SMALL	Point
	* FLOWER	Point
	* LEMON TREE DRY	Point
	* TREE	Point
	* TREE ALLEE	Point
	* TREE ANAR	Point
	* TREE BANANA	Point
	* TREE COCONUT	Point
	* TREE GUVA	Point
	* TREE NEEM	Point
	* TREE ORANGE	Point
	* TREE PAPPAYA	Point
	* TREE SMALL	Point
* This layer was edited in Open Office Calc. The following structural changes occured:
	* Z field removed
	* LAYER field renamed to ORIGINAL_LAYER
	* Fields PLANT_GROUP, SPECIES and CHARACTERISTICS added
* The following data was added (the first vale represents the value in OIRINGAL_LAYER)

ORIGINAL_LAYER|PLANT_GROUP|SPECIES|CHARACTERISTICS
----|----|----|----
BUSH|Bush|Unspecified|Unspecified
Dates|Tree|Date|Unspecified
DATES DRY|Tree|Date|Dry
DATES MEDIUM|Tree|Date|Medium
DATES SMALL|Tree|Date|Small
FLOWER|Flower|Unspecified|Unspecified
Lemon Tree dry|Tree|Lemon|Unspecified
TREE ALLEE|Tree|Allee|Unspecified
TREE ANAR|Tree|Anar|Unspecified
TREE COCONUT|Tree|Coconut|Unspecified
TREE GUVA|Tree|Guva|Unspecified
TREE LEMON|Tree|Lemon|Unspecified
TREE MANGO|Tree|Mango|Unspecified
TREE NEEM|Tree|Neem|Unspecified
TREE ORANGE|Tree|Orange|Unspecified
TREE UNSPECIFIED|Tree|Unspecified|Unspecified
TREE UNSPECIFIED SMALL|Tree|Unspecified|Small

* The csv data was imported into QGIS and then saved as a shapefile:
	* Point geometry as Vegetation_Point.shp

# Processing the Structure data

Completed = Yes

## Purpose

Exporting all the structure data recorded in Luzugh. The aim is to export this as polygons with real topology and lines for the non-polygon components. This may also include all the Falaj bits.

Essenitally this is a messy nightmare

## Outputs

* Structure_Lazugh.dwg
* Structure_Lazugh_Cleaned.dwg
* Structure_Line.shp
* Structure_Polygon.shp

## Layers

* All that I deem relevant

## Processing

* A Map query was run as 'draw' on the following layers
	* All that I deem relevant
* Line only layers were seperated (and their layers prefixed with line)
* A blanket drawing cleanup (overlaps, duplicates, intersections etc.) was used to remove initial cruft
* Hand editing and closing of polygons (FALAJ in particular)
* Gave up on the FALAJ as it was just too much
	* put falaj into the lines component
* All saved as Structure_Lazugh_Cleaned.dwg
* Created topology
	* Saved the version with a topology file
* All saved as Structure_Lazugh_Cleaned_withTopology.dwg
* Closed polyline topology layers exported as shapefile
	* Structure_Polygon.shp
* Polyline data exportde as shapefile with Layer as attribute 
	* Structure_Line.shp

