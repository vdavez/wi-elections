# WI Election Explorer

First up, we grab all of the GeoJSON data from the [WI Legislature data site](https://data-ltsb.opendata.arcgis.com/datasets/2012-2020-wi-election-data-with-2017-wards/data) and convert it to a [Geobuf format](https://github.com/mapbox/geobuf).
```
npm install geobuf

curl https://opendata.arcgis.com/datasets/99cddbb661bd42d3b9e37fd6ef6251a5_0.geojson > wi-elections-2012-2020.geojson
curl https://opendata.arcgis.com/datasets/336c768bad3041de89a80011015e0a3e_0.geojson > wi-elections-2002-2010.geojson
curl https://opendata.arcgis.com/datasets/44c7cd59ac4b4390abdfd28815f8b1ad_0.geojson > wi-elections-1990-2000.geojson

./node_modules/.bin/geojson-merge -s wi-elections-1990-2000.geojson wi-elections-2002-2010.geojson wi-elections-2012-2020.geojson > wi-elections-1990-2020.geojson


./node_modules/.bin/json2geobuf wi-elections-1990-2020.geojson > wi-elections-1990-2020.pbf
```

Now we have all of the election data in a 38MB file. Not bad!
