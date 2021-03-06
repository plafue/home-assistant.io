---
layout: page
title: "World Wide Lightning Location Network (WWLLN)"
description: "Instructions on how to integrate WWLLN within Home Assistant."
date: 2019-07-06 23:17
sidebar: true
comments: false
sharing: true
footer: true
logo: wwlln.jpg
ha_category: Geolocation
ha_release: 0.96
ha_iot_class: Cloud Polling
ha_config_flow: true
---

The `wwlln` integration displays lightning strike information from the
[World Wide Lightning Location Network (WWLLN)](http://wwlln.net).

Entities are generated, updated and removed automatically with each update 
from the feed. Each entity defines latitude and longitude and will be shown 
on the default map automatically, or on a map card by defining the source 
`wwlln`. The distance (in kilometers or miles, depending on your unit system)
is available as the state of each entity.

<p class='img'>
  <img src='{{site_root}}/images/screenshots/wwlln-feed-map.png' />
</p>

New data is returned every 5 minutes.

## Configuration

To retrieve data from the WWLLN, add the following to your `configuration.yaml`
file:

```yaml
wwlln:
```

{% configuration %}
latitude:
  description: The latitude you want to monitor; defaults to the value defined in `configuration.yaml`.
  required: false
  type: float
longitude:
  description: The longitude you want to monitor; defaults to the value defined in `configuration.yaml`.
  required: false
  type: float
radius:
  description: The radius around your location to monitor; defaults to 25 km or mi (depending on the unit system defined in your `configuration.yaml`).
  required: false
  type: integer
window:
  description: The amount of time before now for which strikes should be considered "active" and shown in the UI.
  required: false
  type: time
{% endconfiguration %}

## State Attributes

The following state attributes are available for each entity in addition to 
the standard ones:

| Attribute          | Description |
|--------------------|-------------|
| latitude           | Latitude of the lightning strike. |
| longitude          | Longitude of the lightning strike. |
| source             | `wwlln` to be used in conjunction with the `geo_location` automation trigger. |
| external_id        | The external ID used in the feed to identify the earthquake in the feed. |
| publication_date   | Date and time when this event occurred. |


## Full Configuration

```yaml
# Example configuration.yaml entry
wwlln:
    radius: 100
    latitude: 37.39
    longitude: -5.99
```
