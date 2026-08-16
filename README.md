# wildfire-evac-kg

Road network for wildfire evacuation modelling — Paradise, California.

Source: **OpenStreetMap** via the Overpass API, licensed **ODbL 1.0**.
© OpenStreetMap contributors. See [`DATASET_CARD.md`](DATASET_CARD.md).

## What is here

```
data/paradise_ca.json     raw Overpass response, 1.6 MB
                          12,610 nodes + 1,177 ways = 13,787 elements
```

## Status: extract only

This repository holds the **source extract**, not a built graph. There is no
loader, schema or `.sgsnap` snapshot yet.

That matters because two things already reference it: the engine's
`examples/wildfire_evac_demo.rs`, and the product specification, which cites
wildfire-evac among the workloads motivating geospatial support. Both rest on
this extract.

## Re-fetching the data

The extract is an Overpass API response for the Paradise, CA area. Re-fetching
gives a newer snapshot of the same area — useful, but it will not reproduce this
file byte-for-byte, because OSM changes continuously. The timestamp of this
extract is recorded in the data itself and in the dataset card.

## Licence

The **data** is OpenStreetMap's, under [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/).
ODbL is share-alike: redistributing this data or a derived database requires
attribution to OpenStreetMap and ODbL licensing of the derivative.

Any loader or tooling added to this repository is licensed separately; the data
licence is not affected by it.
