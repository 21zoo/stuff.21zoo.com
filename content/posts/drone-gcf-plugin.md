---
title: "drone-gcf - a Google Cloud Function plugin for drone.io"
date: 2019-02-28T15:17:09-05:00
draft: false
description: "automation"
tags: [drone, automation, gcf]
---

[Google Cloud Funtions](https://cloud.google.com/functions/) allow you to execute small pieces of 
code, written in NodeJS, Python or Golang and whenever a certain event is triggered.
The events can be e.g. a HTTP request, a message published to PubSub, a file uploaded to GCS and so on.

The [drone.io](https://drone.io) CI/CD server is a simple yet powerful and extendable Continuous Delivery platform
that supports a plugin architecture where plugins a re supplied as docker images.


[https://github.com/oliver006/drone-gcf](drone-gcf) is a plugin that supports managing Cloud Functions as part of a 
drone CI/CD pipeline.
For instance, it allows you to first run a set of tests and, if successful, publish a new version of your code
as a Cloud Function.

See the drone pipeline below for an example of a Golang pipeline that runs tests when new code is pushed and
publishes the function when code is merged into master:

```

kind: pipeline
name: default

steps:
  - name: test
    image: golang
    commands:
      - "go test -v"
    when:
      event:
        - push


  - name: deploy-cloud-functions
    image: oliver006/drone-gcf
    settings:
      action: deploy
      project: myproject
      token:
        from_secret: token
      runtime: go111
      functions:
        - TransferFileToGCS:
          - trigger: http
            memory: 2048MB
        - ProcessEmails:
          - trigger: http
            memory: 512MB
            runtime: python37
            source: ./python/src/functions/

    when:
      event: push
      branch: master

```
