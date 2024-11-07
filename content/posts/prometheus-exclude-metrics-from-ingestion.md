---
title: "How to exclude metrics from ingestion into your Prometheus server"
date: 2024-09-21T11:22:33-04:00
draft: false
tags: [prometheus,metrics]
---

If you're scraping a target and there are certain metrics you 
don't want to ingest (for instance because they are too high cardinality and take up too much space)
then you can add the following to your target config:


```yaml

  - job_name: something_exporter
    static_configs:
      - targets:
        - localhost.com:9119
    metric_relabel_configs:
      # dropping all go garbage collection metrics - not needed
    - source_labels: [ __name__ ]
      regex: 'go_gc_.*'
      action: drop

```

`regex: 'go_gc_.*'` will match all metrics starting with `go_gc_` and prevent them from getting ingested.
