---
license: odbl-1.0
pretty_name: wildfire-evac-kg
tags:
  - knowledge-graph
  - samyama
  - property-graph
  - geospatial
  - openstreetmap
  - emergency-management
language:
  - en
---

# Dataset Card for `wildfire-evac-kg`

**Road network for wildfire evacuation modelling — Paradise, California**

> Part of the **Samyama** ecosystem. This card describes the dataset; the repository
> holds the extract and the loader specifics.

## Provenance and licence

| | |
|---|---|
| **Source** | [OpenStreetMap](https://www.openstreetmap.org) via the Overpass API (`Overpass API 0.7.62.11`) |
| **Licence** | **ODbL 1.0** — [Open Database License](https://opendatacommons.org/licenses/odbl/1-0/) |
| **Attribution** | © OpenStreetMap contributors |
| **Extracted** | 2026-05-11T16:29:15Z (`osm3s.timestamp_osm_base`) |
| **Area** | Paradise, Butte County, California, USA |

The licence is not inferred. The extract carries it in its own metadata:

```json
"osm3s": {
  "timestamp_osm_base": "2026-05-11T16:29:15Z",
  "copyright": "The data included in this document is from www.openstreetmap.org.
                The data is made available under ODbL."
}
```

### What ODbL requires of you

ODbL is share-alike. If you distribute this data or a derived database, you must
attribute OpenStreetMap and offer the derived database under ODbL. Producing
*results* from it — a map, an analysis, an evacuation model — does not require you
to license those results under ODbL, but does require attribution.

## Contents

`data/paradise_ca.json` — a raw Overpass response, 1.6 MB.

| | count |
|---|---:|
| nodes | 12,610 |
| ways | 1,177 |
| **total elements** | **13,787** |

Predominant tags: `highway` (1,251), `name` (1,064), and TIGER lineage fields
(`tiger:county`, `tiger:cfcc`, `tiger:reviewed`) reflecting the US Census road
data OSM imported for this area.

## Why Paradise

The 2018 Camp Fire destroyed the town of Paradise and killed 85 people. Evacuation
was constrained by a road network with few outbound routes for its population,
which makes it a well-studied and unusually clear case for modelling egress
capacity, bottlenecks and route redundancy.

The dataset carries **no incident data** — no fire perimeter, no casualty record,
no personal data of any kind. It is the road network alone.

## Status

**This is a raw extract, not yet a knowledge graph.** There is no loader, no
schema and no snapshot in this repository at present. The engine ships
`examples/wildfire_evac_demo.rs`, and the product specification cites
wildfire-evac among the workloads motivating geospatial support — both currently
rest on this extract rather than on a built graph.

Turning it into one needs a loader producing nodes for intersections and edges for
road segments, with the geospatial attributes the demo assumes.

## Limitations

- **One town, one snapshot.** Nothing here generalises to other fires or regions.
- **OSM completeness varies.** TIGER-derived US road data is known for
  inconsistent classification and occasional geometry artefacts.
- **Extracted 2026-05**, seven years after the 2018 fire — the network reflects
  the town as rebuilt, not as it stood during the evacuation. Any historical
  analysis has to account for that, and this dataset cannot support it alone.
