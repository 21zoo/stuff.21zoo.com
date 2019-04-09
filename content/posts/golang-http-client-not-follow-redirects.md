---
title: "Golang HTTP Client - How to not follow redirects"
date: 2018-10-11T23:45:04-04:00
draft: false
description: "code snippet"
tags: [golang,go,http]
---

```
client: &http.Client{
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
        return http.ErrUseLastResponse
    },
}

resp, err := client.Do(req) ...

```
