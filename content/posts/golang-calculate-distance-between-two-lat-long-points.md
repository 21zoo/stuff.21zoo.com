---
title: "How to Calculate the Distance Between Two Lat,Long Points in Golang"
date: 2019-06-07T17:53:16-04:00
draft: false
description: "code snippet"
tags: [go,golang]
---

This will return the distance between two points in miles (based on the Haversine formula).
To get the distance in kilometers, multiply with `1.60934`.

```golang
func distance(lat1 float64, lng1 float64, lat2 float64, lng2 float64) float64 {
	radlat1 := float64(math.Pi * lat1 / 180)
	radlat2 := float64(math.Pi * lat2 / 180)

	theta := float64(lng1 - lng2)
	radtheta := float64(math.Pi * theta / 180)

	dist := math.Sin(radlat1)*math.Sin(radlat2) + math.Cos(radlat1)*math.Cos(radlat2)*math.Cos(radtheta)

	if dist > 1 {
		dist = 1
	}

	dist = math.Acos(dist)
	dist = dist * 180 / math.Pi
	dist = dist * 60 * 1.1515

	return dist
}
```
