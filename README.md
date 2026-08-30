# wildfire-evac-kg

Road network for wildfire evacuation modelling — Paradise, California.

Source: **OpenStreetMap** via the Overpass API, licensed **ODbL 1.0**.
© OpenStreetMap contributors. See [`DATASET_CARD.md`](DATASET_CARD.md).

## What is here

```
data/paradise_ca.json     raw Overpass response, 1.6 MB
                          12,610 nodes + 1,177 ways = 13,787 elements
```

## Published dataset

A graph form of this extract is published at
**[huggingface.co/datasets/VaidhyaMegha/wildfire-evac-kg](https://huggingface.co/datasets/VaidhyaMegha/wildfire-evac-kg)**
— 13,787 nodes and 26,831 edges as node/edge CSVs, with `paradise_ca.json` shipped alongside
unmodified.

```python
from datasets import load_dataset
junctions = load_dataset("VaidhyaMegha/wildfire-evac-kg", "junction")
```

> The graph form is **derived for that publication**, not by this repository — see below.
> OSM nodes become junctions, ways become roads, consecutive node references along a way
> become connections. The raw extract travels with it so the derivation can be checked.
> **ODbL share-alike applies**: the published dataset is ODbL, and so must any database
> derived from it be.

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
