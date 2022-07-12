---
title: "Run CloudSQL proxy with docker-compose"
date: 2022-07-11T18:50:04-04:00
draft: false
description: ''
tags: [gcp,cloudsql,sql,proxy]
---
Using CloudSQL proxy allows you to access your CloudSQL isntance without exposing its port to the big bad internet.
First, create a service account in your project and place the `service-account-key-file.json` key file in the current directory.  


<b>`docker-compose.yml`</b>

```
services:
  cloudsql-proxy:
    image: gcr.io/cloudsql-docker/gce-proxy:1.30.1
    volumes:
      - ./service-account-key-file.json:/config
    ports:
      - 127.0.0.1:5432:5432
    command: "/cloud_sql_proxy -instances=<< DB CONNECTION STRING >>=tcp:0.0.0.0:5432 -credential_file=/config"
```

`DB CONNECTION STRING` looks something like `your-project:us-central1:db-instance-name`.  


To bring up the CloudSQL proxy in daemon (background) mode run:

```
docker-compose up -d
```

Now you an connect to `localhost:5432` and the proxy will forward the connection to your CloudSQL instance.
