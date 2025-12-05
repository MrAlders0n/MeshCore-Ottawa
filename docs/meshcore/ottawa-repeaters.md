# Overview

This page lists all deployed and reserved repeater IDs in Ottawa, along with their current configurations.
If you notice anything that should be updated, contact MrAlders0n on Discord or MeshCore, or reach out to any of the Knowledge Curators on the Discord server.

## Available Repeater IDs

The following MeshCore node identifiers are currently **unused** and available for future Ottawa repeaters:  
```{{ unused_ids | join(',') }}```
*({{ unused_ids | length }} remaining IDs)*

## Deployed Repeater IDs

| Identifier | Repeater Name   | Antenna   | Location / Height   | MeshCore Contact URL |
|-----------:|-----------------|-----------|---------------------|----------------------|
{% for r in repeaters -%}
| {{ r.id }} | {{ r.name }} | {{ r.antenna }} | {{ r.location }} | {%- if r.contact %} [Contact]({{ r.contact }}) {%- else %} TBD {%- endif %} |
{% endfor %}

*If you spot an error in this repeater list or would like to add your own, please contact MrAlders0n on the Greater Ottawa Mesh Enthusiasts Discord.*
