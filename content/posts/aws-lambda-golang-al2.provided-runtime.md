---
title: "Migrate AWS Lambda Golang Functions to the \"al2.provided\" Runtime"
date: 2023-08-23T18:50:04-04:00
draft: false
tags: [aws,lambda,golang,go,al2.provided]
---
AWS is deprecating the go1.x runtime on Lambda and it's time to udpate your Golang lambda functions.
Functions need to migrate to the `al2.provided` runtime and it's pretty straight-forward.<br/>
In the AWS console select `al2.provided` as the new runtime and when you compile your Golang handler 
you need to create an executable named `bootstrap`.


<b>Here's a sample Golang lambda program:</b>

```golang
package main

import (
  "context"
  "fmt"

  "github.com/aws/aws-lambda-go/lambda"
)

type MyEvent struct {
  Name string `json:"name"`
}

func HandleRequest(ctx context.Context, event MyEvent) (string, error) {
  return fmt.Sprintf("Hello from Lambda, %s!", event.Name), nil
}

func main() {
  lambda.Start(HandleRequest)
}

```

Build it (this is for Graviton - if you (have to) use Intel then use `GOARCH=amd64`):
```shell
GOARCH=arm64 GOOS=linux go build -o bootstrap .
```

Zip up the executable (and anything related that is needed):

```shell
zip myFunction.zip bootstrap
```

And now you can use that zip to deploy your function.