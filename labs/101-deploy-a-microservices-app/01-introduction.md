# Introduction

[Cloud Run for Anthos] is an integration with [Anthos], Google Cloud’s app modernization platform, that let's you leverage Kubernetes and serverless together.

The serverless experience is powered by [Knative], an open source project that supports serverless workloads running on Kubernetes. Kubernetes support is provided by Google Kubernetes Engine (GKE), bringing custom machines types, VPC networking, and integration with any Kubernetes‐based workloads together, as needed by your enterprise solutions.

In this lab, you will deploy a sample [microservices application] using Cloud Run for Anthos. This is a sophisticated enterprise microservices demo that is typically deployed as a Kubernetes application, but this tutorial will cover the changes that need to be made to deploy most of the app leveraging Knative support.

## What you'll learn

* How to create a Kubernetes cluster with Cloud Run support
* How to identify the services that must be deployed as standard Kubernetes services and those that can be deployed as Knative services
* How to create Knative service configuration (and understand the differences from Kubernetes configuration)
* How to deploy and monitor the status of both the Kubernetes and Knative services in the demo app
* How to modify the autoscaling and request concurrency attributes of the Knative services

## What you'll need

* You will need to be able to install and use a number of command line tools using Bash in a terminal. The next section provides links to the tools you'll need, but doesn't show you how to install them.
* You will also need `git` [installed](https://github.com/git-guides/install-git) and know [how to clone a repo](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository).
* You will need a project with billing enabled that lets you create a GKE cluster and enable Google Cloud APIs.

[Anthos]: https://cloud.google.com/anthos
[Cloud Run for Anthos]:  https://cloud.google.com/anthos/run
[Knative]: https://knative.dev/
[microservices application]: https://github.com/GoogleCloudPlatform/microservices-demo

---
[[toc]](README.md) [[next]](02-setting-up.md)
