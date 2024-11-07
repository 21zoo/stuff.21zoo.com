---
title: "How to Make a DNS Lookup in Golang"
date: 2019-09-06T12:12:58-04:00
draft: false
description: "code snippet"
tags: [go,golang,dns]
---


Save this snippet in a file and run with `go run .` or `go run . google.com`


```golang
package main

import (
	"fmt"
	"net"
	"os"
)

func main() {
	addr := "stuff.21zoo.com"
	if len(os.Args) > 1 {
		addr = os.Args[1]
	}
	ips, err := net.LookupIP(addr)
	if err != nil {
		fmt.Printf("net.LookupIP( %s ) err: %s", addr, err)
		return
	}
	for _, ip := range ips {
		fmt.Printf("%s has address %s\n", addr, ip.String())
	}
}
```

Sample output:

```shell
$ go run . stuff.21zoo.com
stuff.21zoo.com has address 104.31.85.183
stuff.21zoo.com has address 104.31.84.183
stuff.21zoo.com has address 2606:4700:30::681f:55b7
stuff.21zoo.com has address 2606:4700:30::681f:54b7
```