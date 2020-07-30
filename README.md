# microservices-demo-knative

This repo contains Knative configuration manifests for running the [microservices-demo]
as a serverless appliction.

You should be able to deploy the application to any cluster with Kubernetes and Knative
installed. The configuration files to deploy the application are in the `manifests` directory.

For demo purposes, a script is provided to create a cluster on Google Cloud
and then deploy the application to a Knative environment using Cloud Run for Anthos.
The script is located in the `cluster/anthos` directory.

---
This is not an official Google project.

[microservices-demo]: https://github.com/GoogleCloudPlatform/microservices-demo