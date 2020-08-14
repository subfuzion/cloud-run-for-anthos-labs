# Setting up

## Install command line tools

> Tip: If you are using Cloud Shell in the Google Cloud console, you can skip steps 1 and 2.

1. [Install the Cloud SDK], which includes the `gcloud` command-line tool. Ensure you follow all the steps to **select or create a project** and **confirm that billing is enabled** for your project.
2. Install `kubectl`.  You can use gcloud (shown below) or go to the [Kubernetes docs].

```
gcloud components install kubectl 
```

## Set up environment variables

1. If you skipped steps 1 and 2 above, then make sure now to [select or create a project] now and [confirm billing is enabled] for it.
2. Set `PROJECT_ID`, `ZONE, and CLUSTER` environment variables, as shown below (change any values as desired; you can select any zone from [here]):

```
PROJECT_ID=myproject
gcloud config set project $PROJECT_ID

ZONE=us-central1-c
gcloud config set compute/zone $ZONE

CLUSTER=cluster-1
```

## Enable Google Cloud APIs for your project

1. Enable the following APIs needed for Cloud Run for Anthos:

```
gcloud services enable container.googleapis.com containerregistry.googleapis.com cloudbuild.googleapis.com
```

## Create a GKE cluster

1. Create a cluster enabled for Cloud Run with enough worker nodes to run and scale the microservices demo app:

```
gcloud beta container clusters create $CLUSTER \
  --release-channel regular \
  --zone $ZONE --num-nodes 3 --machine-type n2-standard-4 \
  --enable-autoscaling --min-nodes 3 --max-nodes 6 \
  --enable-ip-alias \
  --addons CloudRun,HttpLoadBalancing --enable-stackdriver-kubernetes
```

The last line of the command specifically adds everything needed for Cloud Run for Anthos, including logging.

> Tip: You can also use the shell script at `cluster/cluster.sh` to create a cluster.

## Clone the configuration repository

The application source code and sample Kubernetes and Istion manifests on GitHub ([GoogleCloudPlatform/microservices-demo]). It is typically deployed using the manifests under the `kubernetes-manifests` and `istio-manifests` directories, respectively, to demonstrate a microservices application with a service mesh on Kubernetes.

However, for this tutorial, you will use the manifests located at [subfuzion/cloud-run-for-anthos-labs] instead. We will cover the differences between the Kubernetes and the Knative manifests in the next section.

Clone the repo to your system so you will be able to review, apply and update the Knative manifests to deploy the app for this tutorial.

```
git clone https://github.com/subfuzion/cloud-run-for-anthos-labs.git 
```

Then, change directory to this lab:

```
cd cloud-run-for-anthos-labs/labs/101-deploy-a-microservices-app/
```

[confirm billing is enabled]: https://cloud.google.com/billing/docs/how-to/modify-project
[GoogleCloudPlatform/microservices-demo]: https://github.com/GoogleCloudPlatform/microservices-demo
[here]: https://cloud.google.com/compute/docs/regions-zones#available
[select or create a project]: https://cloud.google.com/resource-manager/docs/creating-managing-projects#console
[Install the Cloud SDK]: https://cloud.google.com/sdk/install
[Kubernetes docs]: https://kubernetes.io/docs/tasks/tools/install-kubectl/
[subfuzion/cloud-run-for-anthos-labs]: https://github.com/subfuzion/cloud-run-for-anthos-labs

---
[[toc]](README.md) [[back]](01-introduction.md) [[next]](03-knative-configuration.md)
