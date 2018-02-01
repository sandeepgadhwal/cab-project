Instructions

install postgresql
install postgis
import shapefile
  shp2pgsql -I -s 4326 bangalore.shp public.bangalore | psql -U sandyjones -d city

import geojson by ogr2ogr
  ogr2ogr -f "PostgreSQL" PG:"dbname=city user=sandyjones" "bbmp.geojson"

enable postgis extension
  CREATE EXTENSION POSTGIS;

run a dummy spatial query
  SELECT ST_AsText(ST_Centroid(geom)) FROM Bangalore;
