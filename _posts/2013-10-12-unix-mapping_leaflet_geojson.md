---
layout: post
title: Maping on websites
tags: gis mapping geojson html
---
 
## Converting files

### Shapefiles

When converting files, I used a utility called ogr2ogr which worked great at taking a shp file and converting it into GeoJSON. Here is what I rant to turn `ne_10m_admin_0_countries.sh` into a GeoJSON called `all_countries.js`

		ogr2ogr -f "GeoJSON" all_countries.js ne_10m_admin_0_countries.shp
		
### Open Street Map files

OSM releases data from a [number of websites](http://wiki.openstreetmap.org/wiki/Planet.osm), I found the [cloudmade](http://downloads.cloudmade.com/) site to be good for a list of countries that the files isn't huge. You have to convert the file differently than the `shp` file above,

		ogr2ogr -f GeoJSON india.js india.administrative.osm multipolygons

That last argument is important, you need that otherwise you get an error, there are other options, including

* points
* lines
* multilinestrings
* multipoints
* other_relations

Make sure to look at [stackexchange](http://gis.stackexchange.com/questions/22788/how-do-you-convert-osm-xml-to-geojson) for the source.
 
## Some resources

* [A source of shapefiles](http://www.naturalearthdata.com/downloads/)
* [One way to embed data from above](https://plus.google.com/+PaulSaxman/posts/adrenkxxT79)
* [A GeoJSON of the world on github](https://github.com/johan/world.geo.json)

## Docs

* [Leaflet GeoJSON docs](http://leafletjs.com/examples/geojson.html)
* [Stack Exchange - How to load GeoJSON as an eternal file](http://gis.stackexchange.com/questions/68489/how-to-load-external-geojson-file-into-leaflet-map) - helpful for using external file
