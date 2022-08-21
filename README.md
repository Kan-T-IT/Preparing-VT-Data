# Preparing Vector Tile Data



The process to produce Vector Tiles is based on the conversion with the tippecanoe library from geojson to mbtiles where it is subsequently uploaded to the server to be served from the web.

In this case we use a docker already available in Docker hub 

[morlov/tippecanoe](https://hub.docker.com/r/morlov/tippecanoe) 


The following structure is created

* **geojson**: where are the geojson of the data in EPSG:4326.
* **tiles**: where the mbtiles will be generated.

```
mkdir geojson
mkdir tiles
```


docker run --entrypoint tippecanoe -v $PWD:/tippecanoe morlov/tippecanoe:latest -o tippecanoe/tiles/predio.mbtiles  -l default -Z10 -z22 -pk --drop-fraction-as-needed tippecanoe/geojson/4326_predio.geojson


-rwxr-xr-x 1 root root 5.1G Jun 28 17:30 4326_construccion.geojson




docker run --entrypoint tippecanoe -v $PWD:/tippecanoe morlov/tippecanoe:latest -o tippecanoe/tiles/construccion.mbtiles  -l default -Z10 -z22 -pk --drop-fraction-as-needed tippecanoe/geojson/4326_construccion.geojson
