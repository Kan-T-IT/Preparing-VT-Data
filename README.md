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



Upload / download of GEOjson, for example:

```
cd geojson

wget https://cdn.buenosaires.gob.ar/datosabiertos/datasets/secretaria-de-desarrollo-urbano/tejido-urbano/tejido.geojson

cd ..
```


Execute process trasnform of GEOjson to MBtiles

```
docker run --entrypoint tippecanoe -v $PWD:/tippecanoe morlov/tippecanoe:latest -o tippecanoe/tiles/<name of mbtiles>.mbtiles  -l default -Z10 -z22 -pk --drop-fraction-as-needed tippecanoe/geojson/<name of geojson>.geojson
```

For example:

```
docker run --entrypoint tippecanoe -v $PWD:/tippecanoe morlov/tippecanoe:latest -o tippecanoe/tiles/tejido_gcba.mbtiles  -l default -Z10 -z22 -pk --drop-fraction-as-needed tippecanoe/geojson/tejido.geojson
```

A Finish process to copy in folder of Tile Server. 


