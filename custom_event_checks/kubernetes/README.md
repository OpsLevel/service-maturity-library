# Kubernetes Custom Event Check

## Overview

These checks are based around validating aspects about your kubernetes manifests.  We provide a easy way to ship your manifests to a custom event check endpoint via our [kubectl opslevel](https://github.com/OpsLevel/kubectl-opslevel) integration.

We have also written a [blog post](https://www.opslevel.com/blog/validating-kubernetes-best-practices/) on how some of these checks were created.

## Setup

Import any custom event check from this library into your OpsLevel Service Maturity rubric with the steps below:

1. From the [new integraiton menu in OpsLevel](https://app.opslevel.com/integrations/new), create a new Custom Event integration, which creates a new, unique endpoint
1. Setup the [kubectl opslevel collect]() with the new Custom Event integration so your kubernetes payloads are collected perodically
1. Import any check using the CLI: `opslevel create check -f ./custom_event_check/kubernetes/$filename.yaml` and you will be prompted to fill out any missing fields from the yaml

## Sending payloads to OpsLevel

For kubernetes we have built a command in our [kubectl opslevel](https://github.com/OpsLevel/kubectl-opslevel) CLI which acts as a kubernetes controller and sends payloads of your kubernetes resource to an OpsLevel Custom Event integration.  If you have not setup our [kubernetes integration](https://www.opslevel.com/docs/integrations/kubernetes/) we recommend you do that first to familiarize yourself with the configuration file.

If you have the tool install locally you can test it out if you have access to your kubernetes cluster.

```sh
kubectl opslevel collect -i "https://app.opslevel.com/integrations/custom_event/eeb1f18e-7205-41a5-97fe-60a0657f062d" -f ./opslevel-k8s.yaml
```

We have also setup a [helm-chart](https://github.com/OpsLevel/helm-charts) to make deployment of it in your cluster easy.  Just enable it setting

```yaml
collector:
  enabled: true
  integrations:
  - https://app.opslevel.com/integrations/custom_event/eeb1f18e-7205-41a5-97fe-60a0657f062d
```
