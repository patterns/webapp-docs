# Mapping Data \(geoJSON\)

## isgood.ai Maps

Maps use [Leaflet.js](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github) and support all the geometry types outlined in [the geoJSON spec](http://www.geojson.org/geojson-spec.html) \(Point, LineString, Polygon, MultiPoint, MultiLineString, MultiPolygon, and GeometryCollection\). TopoJSON files should be type "Topology" and adhere to the [topoJSON spec](https://github.com/mbostock/topojson/wiki/Specification).

[Leaflet.js](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github) will be used as a base for all geo-based visualisations, including in dashboards.  The underlying data is via [OpenStreetMap](http://www.openstreetmap.org/), and OSM is also used for location and GIS lookups and such, where it is used throughout the webapp and platform.

## Specifications

We follow the [same guidelines as github for the basics of how we work with geo,](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github) as we are default JSON for all data in our app, ad therefor geoJSON and OSM for how we work with this.  Please review the [Github Guidelines](https://docs.github.com/en/github/managing-files-in-a-repository/mapping-geojson-files-on-github), as it will help you work with this.

**Please note that our default DB store everywhere is Postgres, and therefore the DB fields storing geo data must be the right Postgres field formats for working with GIS data.**

Note that the data-format is to be STANDARDISED and normalised throughout the WebApp and the platform, so this needs to be enforced in the platform DBs, inbound and connected data DBs, as well as in the webapp DBs ... to ensure all data is comparable with all data, within our platform and with the right DB-field types.

## Ref: Geo Data-type Definitions

{% hint style="info" %}
Postgres ref:  [https://www.postgresql.org/docs/current/datatype.html](https://www.postgresql.org/docs/current/datatype.html)
{% endhint %}

```text
11,POINT(lat, lon),Geolocation (lat,lon),Address,true, (SRID: 4326)
12,double,Geolocation (Longitude),Address,true,   (convert internally to a point)
13,double,Geolocation (Latitude),Address,true,    (convert internally to a point)
14,single,Geolocation (Altitude),Address,true,    (mysql doesnt handle x,y,z points sadly)
```

```text

latitude double COMMENT 'Number representing Latitude of a point',
longitude double COMMENT 'Number representing Longitude of a Point',
geo_point point not null COMMENT 'gis point field that represents lat/lon',
geo_zone varchar(100) COMMENT 'a defined area, as opposed to exact location, how do we process or extrapolate this for analysis?',
geo_zone_point point not null COMMENT 'a GIS point representation of geo_zone for use in GIS Spatial functions',
geo_polygon polygon not null COMMENT 'GIS Polygon Describing a specific Area',
geo_line linestring not null COMMENT 'everything the other side of something (like road, etc)',
geo_radius int COMMENT 'distance from defined geo_zone always in meters',
geo_range varchar(10) COMMENT 'textural representation of distance form the geo_zone eg: close, near, far, or whatever',
address varchar(50) COMMENT 'Contains the value of Unit No., Street Name.',
suburb varchar(30) COMMENT 'Holds the value of suburb or city,',
state varchar(5) COMMENT 'Holds the value state.',
country varchar(3) COMMENT 'Holds the value of country. ISO Code',
postcode varchar(8) COMMENT 'Holds the value of postcode.',
```

{% hint style="danger" %}
_A **BIG Gotcha**, for some unknown reason, MySQL user POINT\(lat, lon\) whereas the rest of the world uses POINT \( lon, lat\) ... YOU HAVE BEEN WARNED !_
{% endhint %}

