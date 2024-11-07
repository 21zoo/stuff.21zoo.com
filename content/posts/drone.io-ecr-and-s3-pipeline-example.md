---
title: "Use drone.io to publish a Docker image to ECR and copy files to S3"
date: 2023-09-05T01:01:01-00:00
draft: false
tags: [drone,aws,ecr,s3]
---
Here's an example on how to use the drone.io CI/CD system to build a new Docker image, push it to ECR and copy some files to S3 as part of the build process.


```yaml
kind: pipeline
type: docker
name: default

steps:
  # Your build steps go here. For example:
  - name: build
    image: alpine
    commands:
      - make build

  # Upload some files to S3
  - name: upload files to s3
    image: plugins/s3
    settings:
      bucket: my-s3-bucket
      region: us-east-1
      source: /test/bundle_file/my_file.js
      target: /my_file.js
      access_key:
        from_secret: aws_access_key_id
      secret_key:
        from_secret: aws_secret_access_key 
             
  # Push Docker image to ECR
  - name: publish to ecr
    image: plugins/ecr
    settings:
      repo: your-aws-account-id.dkr.ecr.us-west-2.amazonaws.com/your-repo
      region: us-west-2
      tags:
        - latest
        - "1.0.0"
      create_repository: true
      access_key:
        from_secret: aws_access_key_id
      secret_key:
        from_secret: aws_secret_access_key

```
