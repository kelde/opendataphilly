opendataphilly
==============

About the Open Data Philly Visualization Contest
================================================

OpenDataPhilly is a portal that provides access to free datasets related to the Philadelphia region. It contains datasets on Philadelphia’s education system, police department, maps of the Philadelphia region, property values, and more.

Azavea is a company in Philadelphia that creates GIS-based decision-support software. Azavea has a socially-conscious focus and its mission is to empower and improve communities through its work. To further this mission, Azavea has re-designed OpenDataPhilly. To celebrate their unveiling of the new design, Azavea has called on developers and data enthusiasts around the world to submit data visualizations to their Open Data Philly Visualization Contest.

About our submission
====================

For this competition, we produced a data visualization that allows users to visualize energy consumption in the city of Philadelphia. The visualization consists of a map and scatterplot, which display the energy consumption patterns of large commercial buildings in the Philadelphia region. The map allows users to view each building’s natural gas consumption, electricity consumption, energy use intensity (EUI), energy star score, and greenhouse gas emissions using visualizations developed in D3.js and the Google Maps API. The visualization can be used to detect poor and outstanding performers against energy benchmarks, or it can be used to understand energy consumption patterns in the City of Philadelphia.

What data sources does the visualization use?
=============================================

The visualization uses the following two sources of data, which are available for public use through OpenDataPhilly.com:

Buildings
http://www.opendataphilly.org/opendata/resource/6/buildings/.
This dataset, produced by the GIS Services Group of the City of Philadelphia, encodes the shapes of buildings and building footprints.

Building Energy Benchmarking
http://www.opendataphilly.org/opendata/resource/258/building-energy-benchmarking/
Compiled by the City of Philadelphia Mayor’s Office of Sustainability, the energy benchmarking data is self-reported data on energy consumption metrics pertaining to large commercial properties in Philadelphia.

How did we do it?
=================

We produced our submission by first programmatically encoding all of the addresses in the energy benchmarking dataset to longitude and latitude points using the Google Maps geocoding service. Once we had these points, we encoded the energy data as a GeoJSON file containing a collection of points with the energy data stored in each point’s properties. We then converted OpenDataPhilly’s “buildings” shapefile into GeoJSON and linked this file with the collection of points by looking up each point in the buildings GeoJSON using a “point in polygon” approach. This allowed us to associate the energy benchmarking data with the polygons encoded in the buildings GeoJSON file. Once we produced our final GeoJSON file, we were able to use the Google Maps Javascript API and D3.js to draw the resulting polygons, heatmap, and scatterplot, each of which made use of the energy data in coloring, sizing, and charting. All of the preliminary data processing work was performed in Node.js and Python, while the final web-based visualization was produced primarily using D3.js and the Google Maps Javascript API.

How can I view the visualization first-hand?
============================================

You can view the visualization here: http://www.kennethelder.com/energy-benchmarking/

Please be aware that the visualization will likely not function properly on older browser versions and it has not been tested on Internet Explorer.

What technology and tools does the project make use of?
=======================================================

To show our appreciation for those developing open source tools and technology, we’ve included brief descriptions and links to some of the tools we used below:

GDAL: A translator library for working with vector and raster geospatial data formats, which we used for its ogr2ogr command-line utility
Geojson-Merge: A Node.js package / utility developed by Mapbox, which provides a command-line interface for merging multiple GeoJSON files together
GeoJSON-JS-Utils: A Javascript module that provides some useful functions for manipulating and working with GeoJSON, which we used primarily for its “point in polygon” implementation
D3.js: A powerful data visualization library for generating data visualizations using Javascript, which we used to produce the scatterplot, render the polygons on the Google Maps overlay, and color the polygons by EUI
D3-tip: A great tooltip implementation for D3.js written by Justin Palmer (if you haven’t seen his amazing data visualizations of Portland, Oregon, then check them out!)
JQuery: The Javascript library that we all know and love…
ColorBrewer: A color scheme by Cynthia Brewer that can be used to color shapes by their values (our project used the CSS implementation)