# Location Radar · Porto

An interactive map for one question: **is a house in this zone worth a look, and how good is the location?**

**Live:** https://angel-zero-star.github.io/escola-porto/

![Location Radar — map and zone card](screenshot.png)

---

## The problem

House hunting around Porto means comparing ~500 zones on things no listing site shows together: which public school your address is actually assigned to (and how good it is), whether there's a decent private school nearby, how far the ocean is, and how long it takes to reach a train or the city. Answering that for one zone takes an evening of research. For 491 zones it needs a tool.

## What it does

- **Map of 491 idealista zones**, coloured by two things in a fixed order: first the school situation, then distance to the ocean. Colour is an order, not a score — any zone with a strong school beats any zone with an average one.
- **School signal** — the zoned public school for the address (by cluster / *agrupamento*) and any private school within a set drive time, combined by a *lenient / strict* switch: lenient takes the better of the two, strict the worse.
- **Overlays** — hatching for zones far from a train station or from Porto, dotted edges for zones sitting right on a threshold, dots for zones split between two school clusters.
- **Sliders for every threshold** — school rank cut-offs, minutes to a private school, the ocean, a station and Porto. The map recolours instantly and the legend counts zones per colour.
- **Zone card** — four status lights, a plain-language explanation of the school situation, the underlying facts and sources, and a link to that zone's listings.
- **Table view** — every zone, sortable and filterable, with the long explanations collapsed to three lines.

## How it works

- **School rank uses the worse of two years.** Público's ranking moves a lot between editions (the median school shifts ~115 places), so a school only counts as strong if it cleared the bar in both.
- **Only the school you're actually zoned for counts.** Portuguese enrolment gives priority to your own cluster's school; a strong school next door in another cluster doesn't help, so it's shown in the card but doesn't colour the map.
- **Private schools have no rank cut-off** — almost all already sit near the top nationally — except the few ranked below the "grey" line.
- **Drive times** are precomputed car minutes without traffic, from each zone to its schools, the nearest Atlantic beach, the nearest suburban-rail or metro station, and a reference point in Porto.

## Data

- Zones: idealista; parish boundaries from the official CAOP.
- Schools: Público's 2025 school rankings (9th grade and secondary), school-cluster catchments from the Ministry of Education's data and school websites.
- Beaches, stations and roads: OpenStreetMap.

Everything is baked into the single HTML file; the map uses [Leaflet](https://leafletjs.com/).

## Built with

- One self-contained HTML file: plain JavaScript, Leaflet, light and dark mode.
- Designed and directed by me; data research and implementation done with Claude, with sources and a confidence level recorded for each school catchment.

## Notes

Catchment areas change and some zones span two school clusters — for a specific address, confirm with the school. Drive times exclude traffic.
