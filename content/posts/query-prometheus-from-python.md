---
title: "How to query Prometheus from Python"
date: 2018-11-07T11:06:28-05:00
draft: false
description: "code snippet"
tags: [prometheus,python]
---

query_prometheus.py

```
from __future__ import print_function

import requests
import sys

if len(sys.argv) != 3:
    print('query_prometheus.py << prometheus server URL >> "<< query >>" ')
    print()
    print("""Example: query_prometheus.py http://localhost:9090 'irate(http_requests_total{code="200"}[1m])' """)
    print()
    sys.exit(1)

response = requests.get('{0}/api/v1/query'.format(sys.argv[1]),
        params={'query': sys.argv[2]})
results = response.json()['data']['result']
for r in results:
    print(r)

```
