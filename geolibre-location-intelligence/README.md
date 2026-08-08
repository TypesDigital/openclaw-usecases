# GeoLibre Location Intelligence for OpenClaw

A TypesDigital use case built around the open-source **GeoLibre** GIS project: turn natural-language business questions into map-based analysis that an OpenClaw agent can invoke.

## Source project

- Upstream: https://github.com/opengeos/GeoLibre
- This use case is an integration/reference implementation, not a replacement for GeoLibre.
- Preserve GeoLibre's upstream MIT license and attribution when incorporating or redistributing its code/assets.

## Why this fits TypesDigital

Geo-spatial analysis can make digital marketing and startup decisions more concrete:

- identify prospect-dense territories
- compare campaign coverage by area
- cluster leads geographically
- prioritize field-sales zones
- evaluate candidate branch/site locations
- generate map-backed reports for clients

## OpenClaw workflow

OpenClaw receives a request such as:

> Find the three Lagos territories with the highest concentration of demo leads and summarize the opportunity.

The GIS service should:

1. geocode or load the relevant locations
2. query spatial data
3. rank candidate areas
4. return structured metrics and GeoJSON/map references
5. optionally produce a shareable project/report URL

## Suggested integration contract

`POST /api/geospatial/analyze`

Request fields:

- `task`: natural-language geospatial task
- `dataset`: dataset identifier
- `bbox`: optional bounding box
- `filters`: optional structured filters

Response fields:

- `summary`
- `metrics`
- `features` (GeoJSON-compatible)
- `map_url` or project reference
- `confidence`

`GET /api/health`

Returns service health and integration version.

## Demo scope

The companion app should use clearly labeled synthetic Lagos/Nigeria business-territory data. It should demonstrate territory planning, lead-density mapping, clustering, distance analysis, and map-based reporting without implying that demo records are real customer data.

## Build direction

Use GeoLibre concepts where they provide leverage—MapLibre rendering, DuckDB Spatial-style analytical workflows, GeoJSON/GeoParquet, SQL-driven exploration, and natural-language GIS interaction—while keeping the TypesDigital product surface focused on marketing, sales, and startup decisions.
