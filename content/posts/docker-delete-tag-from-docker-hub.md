---
title: "Delete a Tag from Docker Hub"
date: 2019-03-20T09:56:43-04:00
draft: false
description: "docker maintenance"
tags: [docker]
---

First, authenticate with Docker Hub:
```sh
export USERNAME="<< your Docker Hub username >>"
export PASSWORD="<< your Docker Hub password >>"

TOKEN=`curl -s -H "Content-Type: application/json" -X POST \
-d '{"username": "'$USERNAME'", "password": "'$PASSWORD'"}' \
https://hub.docker.com/v2/users/login/ | jq -r .token`
```

Now delete the image tag: \
```sh
export ORG="oliver006"
export IMAGE="drone-gcf"
export TAG="tst"

curl 'https://hub.docker.com/v2/repositories/${ORG}/${IMAGE}/tags/${TAG}/' \
-X DELETE \
-H "Authorization: JWT ${TOKEN}"
```
