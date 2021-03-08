# Mapping Data \(geoJSON\)

## isgood.ai Maps

Maps use [Leaflet.js](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github) and support all the geometry types outlined in [the geoJSON spec](http://www.geojson.org/geojson-spec.html) \(Point, LineString, Polygon, MultiPoint, MultiLineString, MultiPolygon, and GeometryCollection\). TopoJSON files should be type "Topology" and adhere to the [topoJSON spec](https://github.com/mbostock/topojson/wiki/Specification).

[Leaflet.js](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github) will be used as a base for all geo-based visualisations, including in dashboards.  The underlying data is via [OpenStreetMap](http://www.openstreetmap.org/), and OSM is also used for location and GIS lookups and such, where it is used throughout the webapp and platform.

## Specifications

We follow the [same guidelines as github for the basics of how we work with geo,](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github) as we are default JSON for all data in our app, ad therefor geoJSON and OSM for how we work with this.  Please review the [Github Guidelines](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github), as it will help you work with this.

Please note that our default DB store everywhere is Postgres, and therefore the DB fields storing geo data must be the right Postgres field formats for working with GIS data.

Note that the data-format is to be STANDARDISED and normalised throughout the WebApp and the platform, so this needs to be enforced in the platform DBs, inbound and connected data DBs, as well as in the webapp DBs ... to ensure all data is comparable with all data, within our platform and with the right DB-field types.

