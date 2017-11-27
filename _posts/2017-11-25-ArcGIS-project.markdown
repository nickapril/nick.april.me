---
layout: post
title:  "Energy Consumption with ArcGIS"
date:   2016-4-30 00:00:00
img: brandeis-main.jpg
description: ArcGIS is a geographical mapping program. I used this software to generate a map of the energy consumption of each building on the Brandeis campus and an estimate of the energy we could produce by covering certain locations with solar panels.
---

## About ArcGIS

ArcGIS is a system for the management, analysis, and display of geographic information. Geographic information is represented by a series of geographic datasets that model geography using simple, generic data structures. ArcGIS uses these techniques to gain greater insights into data.

## My Project: Energy Consumption

This map of Brandeis University shows each building relative to their energy consumption. The darker colors represent higher energy consumption. I created this map using Symbology techniques in ArcMap to connect the geodatabase of consumption statistics I created with the building objects on the map.

![alt text](../assets/img/extrusion.png?raw=true "Brandeis Energy Map")

This is the same map with an extrusion visualization using ArcScene. The extrusion visualization shows clear outliers between the buildings on campus.

The last part of this assignment was to generate an estimate for how much energy could be produced if all rooftops and parking lots were outfitted with solar panels. To calculate this, I estimated that realistically only 40% of a rooftop could physically be covered with solar panels. With ArcMap, I could calculate this using the area of each building and parking lot object on the map. The total came to 155,483.61(m2)

Data given to me from Mary Fischer, the sustainability manager at Brandeis, suggests that for every 1,065 (m2) solar canopy, 212,669 kWh of electricity could be produced. Using this measurement, I estimated that 12,419,358 kWh of electricity is the full solar energy potential of the Brandeis campus. 

![alt text](../assets/img/solar-current.png?raw=true "Brandeis Energy Map") 
![alt text](../assets/img/solar-projected.png?raw=true "Brandeis Energy Map")
