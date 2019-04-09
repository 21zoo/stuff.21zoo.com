---
title: "Prometheus & Kubernetes - Configure to Scrape Pods"
date: 2019-08-12T10:45:00-04:00
draft: false
description: "How to scrape pods, not services"
tags: [prometheus,kubernetes]
---

In your prometheus.yml file, make sur you use `pod` for the role 
when setting up the `kubernetes_sd_configs`.

```
- job_name: 'kubernetes-pods'

  kubernetes_sd_configs:
  - role: pod

  relabel_configs:
  # only scrape when annotation prometheus.io/scrape: 'true' is set
  - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_scrape]
    action: keep
    regex: true
  - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_path]
    action: replace
    target_label: __metrics_path__
    regex: (.+)
  - source_labels: [__address__, __meta_kubernetes_pod_annotation_prometheus_io_port]
    action: replace
    regex: (.+):(?:\d+);(\d+)
    replacement: ${1}:${2}
    target_label: __address__
  - action: labelmap
    regex: __meta_kubernetes_pod_label_(.+)
  - source_labels: [__meta_kubernetes_namespace]
    action: replace
    target_label: kubernetes_namespace
  - source_labels: [__meta_kubernetes_pod_name]
    action: replace
    target_label: kubernetes_pod_name
 ```

and add the proper annotations to your `Deployment` config:

```
kind: Deployment

...

spec:
  template:
    metadata:
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "<< PORT OF YOUR CONTAINER >>"
```

[Source](https://github.com/prometheus/prometheus/blob/70ce3df23ce02a37de0596fcda01b90faa7d06d5/documentation/examples/prometheus-kubernetes.yml#L241-L281)
