# osm2geojson

Parse OSM and Overpass JSON with python.
**This library is under development!**

### Usage

Install this package with pip:

```sh
$ pip install osm2geojson
```

If you want to convert OSM xml or Overpass json/xml to Geojson you can import this lib and use one of 4 methods:

- `json2shapes(dict json_from_overpass)` - to convert Overpass json to \*Shape-objects
- `xml2shapes(str xml_from_osm)` - to convert OSM xml or Overpass xml to \*Shape-objects
- `json2geojson(dict json_from_overpass)` - to convert Overpass json to Geojson
- `xml2geojson(str xml_from_osm)` - to convert OSM xml or Overpass xml to Geojson

**\*Shape-object - for convinience created simple dict to save Shapely object (geometry) and OSM-properties. Structure of this object:**

```py
shape_obj = {
    'shape': Point | LineString | Polygon ...,
    'properties': {
        'type': 'relation' | 'node' ...,
        'tags': { ... },
        ...
    }
}
```

### Examples

Convert OSM-xml to Geojson:

```py
import codecs
import osm2geojson

with codecs.open('file.osm', 'r', encoding='utf-8') as data:
    xml = data.read()

geojson = osm2geojson.xml2geojson(xml)
# >> { "type": "FeatureCollection", "features": [ ... ] }
```

Convert OSM-json to Shape-objects:

```py
import codecs
import osm2geojson

with codecs.open('file.json', 'r', encoding='utf-8') as data:
    json = data.read()

geojson = osm2geojson.json2shapes(json)
# >> [ { "shape": <Shapely-object>, "properties": {...} }, ... ]
```

### Development

Clone project with submodules

```sh
$ git clone --recurse-submodules https://github.com/aspectumapp/osm2geojson.git
```

Setup package

```sh
$ python setup.py develop
```

Run tests

```sh
$ python -m unittest discover
```

Update osm-polygon-features to last version (if you want last version)

```sh
$ ./update-osm-polygon-features.sh
```
