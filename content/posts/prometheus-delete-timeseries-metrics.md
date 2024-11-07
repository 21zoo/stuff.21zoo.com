---
title: "How to delete a timeseries / metrics from Prometheus"
date: 2024-01-21T11:22:33-00:00
draft: false
tags: [prometheus,metrics]
---

First, you need to enable the admin API via the command line:

```
--web.enable-admin-api
```

Now you can delete a metric by calling the respective endpoint, for example by using curl.


```

curl -v -X POST -g 'http://localhost:9090/api/v1/admin/tsdb/delete_series?match[]=node_cpu_seconds_total'
```

This will delete all timeseries called `node_cpu_seconds_total`.

The actual data still exists on disk and is cleaned up in future compactions or 
can be explicitly cleaned up by calling the `clean_tombstones` endpoint:

```
curl -X POST http://localhost:9090/api/v1/admin/tsdb/clean_tombstones
```


See the [official Prometheus docs](https://prometheus.io/docs/prometheus/latest/querying/api/) for more useful admin API endpoints.
