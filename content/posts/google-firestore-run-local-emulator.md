---
title: "How to Run the Google Firestore Emulator"
date: 2019-06-03T12:55:58-04:00
draft: false
description: "Useful for local development"
tags: [firestore,google,gcp]
---

You can run the Firestore emulator by running:

`gcloud beta emulators firestore start`

and then set the `FIRESTORE_EMULATOR_HOST` environment variable as per the console output (e.g. run `export FIRESTORE_EMULATOR_HOST=::1:8505`).

This requires the <a href="https://cloud.google.com/sdk/install">Google Cloud SDK</a> and a Java 8+ JRE installed and on your system PATH.

