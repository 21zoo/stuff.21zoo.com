---
title: "Docker - Clean Up Unused Volumes"
date: 2018-10-30T21:32:02-04:00
draft: false
description: "docker maintenance"
---

From <a href="https://lebkowski.name/docker-volumes/" target="_blank">here</a> - a shell script to easily remove unused containers and volumes:<br>

```
#!/bin/bash

# remove exited containers:
docker ps --filter status=dead --filter status=exited -aq | xargs -r docker rm -v
    
# remove unused images:
docker images --no-trunc | grep '<none>' | awk '{ print $3 }' | xargs -r docker rmi

# remove unused volumes:
find '/var/lib/docker/volumes/' -mindepth 1 -maxdepth 1 -type d | grep -vFf <(
  docker ps -aq | xargs docker inspect | jq -r '.[] | .Mounts | .[] | .Name | select(.)'
) | xargs -r rm -fr
```
