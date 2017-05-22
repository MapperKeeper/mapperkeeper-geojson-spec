# mapperkeeper-geojson-spec

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in
this document are to be interpreted as described in RFC 2119.

## 1. Purpose

This specification attempts to create a standard for styling
geospatial data, setting popup contents, and listing images and YouTube videos for a feature
that can be easily uploaded to [MapperKeeper](http://www.mapperkeepeer.com).

## 2. Format

`mapperkeeper-geojson` is a set of agreed-upon 'special values' in
the pre-existing [GeoJSON](http://geojson.org/) data standard that
define styles and popup contents. As such, files implementing
`mapperkeeper-geojson` are by definition valid GeoJSON files and
valid [JSON](http://json.org/) format.

```javascript
{
    "type": "FeatureCollection",
    "features": [{ "type": "Feature",
        "geometry": {
            "type": "Point",
            "coordinates": [0, 0]
        },
        "properties": {
            // OPTIONAL: default ""
            // A title that shows up in the popup header.
            // Links can be quickly accessed when writing
            // in the content panel by typing the @ symbol then
            // selecting a feature by its title.
            "title": "A title",

            // OPTIONAL: default ""
            // A description that shows up in the popup under the
            // header.  A description should explain the feature.
            "description": "A description",

            // OPTIONAL: default "medium"
            // specify the size of the marker. sizes
            // can be different pixel sizes in different
            // implementations
            // Value must be one of
            // "small"
            // "medium"
            // "large"
            "marker-size": "medium",

            // OPTIONAL: default "circle"
            // a symbol to position in the center of this icon
            // if not provided or "", no symbol is overlaid
            // and only the marker is shown
            // Allowed values include
            // - Icon ID from the Maki project at http://mapbox.com/maki/
            // - An integer 0 through 9
            // - A lowercase charecter "a" through "z"
            "marker-symbol": "circle",

            // OPTIONAL: default "#653294"
            // the color or the marker is by default
            // a color to which the graphic is tinted
            //
            // marker-color must be a valid hex color
            // it can be in short form:
            //   marker-color: "#ace"
            // or long form
            //   marker-color: "#aaccee"
            // But other color formats or named colors
            // are not supported
            "marker-color": "#653294",

            // OPTIONAL: default "#653294"
            // the color of a line as part of a polygon, polyline, or
            // multigeometry
            //
            // value must follow COLOR RULES
            "stroke": "#653294",

            // OPTIONAL: default 1.0
            // the opacity of the line component of a polygon, polyline, or
            // multigeometry
            //
            // value must be a floating point number greater than or equal to
            // zero and less or equal to than one
            "stroke-opacity": 1.0,

            // OPTIONAL: default 3
            // the width of the line component of a polygon, polyline, or
            // multigeometry
            //
            // value must be a floating point number greater than or equal to 0
            "stroke-width": 3,

            // OPTIONAL: default "555555"
            // the color of the interior of a polygon
            //
            // value must follow COLOR RULES
            "fill": "#555555",

            // OPTIONAL: default 0.6
            // the opacity of the interior of a polygon. Implementations
            // may choose to set this to 0 for line features.
            //
            // value must be a floating point number greater than or equal to
            // zero and less or equal to than one
            "fill-opacity": 0.6,

            // OPTIONAL: default []
            // Array of media objects to display in the
            // popup for a feature.  Currently, only images
            // are supported.
            "gallery": [{
              // REQUIRED: default ''
              // type of media item
              // Allowed values include
              // -image
              // -youtube
              "type": "image",
              // REQUIRED: default ''
              // url to the image or youtube resource
              "url": "http://tinyurl.com/jdcr2hp",
              // REQUIRED default ''
              // title of the image and ALL ATTRIBUTION
              // REQUIRED to give credit if image is not
              // your own
              "title": "Portland, OR (Credit Zack Spear)"
            }]
        }
    }]
}
```
