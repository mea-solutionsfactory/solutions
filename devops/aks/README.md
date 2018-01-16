# Vote app using containers on Microsoft Azure

This template deploys a **Azure Container Service (AKS)** with Kubernetes. You will be deploying some containers on top of the cluster to create a Voting application.

`Tags: aks, containers, DevOps`

## Launch the Azure Cloud Shell

[![](https://shell.azure.com/images/launchcloudshell.png "Launch Azure Cloud Shell")](https://shell.azure.com)

Make sure to select the correct subscription if you have multiple subscriptions.

## Create the Resource Group

```
az group create -n votingRG -l eastus
```

## Create the Kubernetes cluster

```
az aks create -g votingRG -n aksCluster -l eastus --kubernetes-version 1.8.1 --generate-ssh-keys
```

On average, this takes about **10 minutes**.

## Retrieve the cluster credentials

```
az aks get-credentials -g votingRG -n aksCluster
```

## Deploy the application to Kubernetes

Use the [kubectl create](https://kubernetes.io/docs/user-guide/kubectl/v1.8/#create) command to run the application. This command parses the manifest file and create the defined Kubernetes objects.

```
kubectl create -f https://aka.ms/azure-voting-app-yaml
```

## Test the application

A [Kubernetes service](https://kubernetes.io/docs/concepts/services-networking/service/) is created which exposes the application to the internet. This process can take a few minutes. 

To monitor progress, use the [kubectl get service](https://review.docs.microsoft.com/azure/container-service/container-service-kubernetes-walkthrough?branch=pr-en-us-17681) command with the `--watch` argument.

```
kubectl get service azure-vote-front --watch
```

Initially, the **EXTERNAL-IP** for the ``azure-vote-front`` service appears as pending. Once the EXTERNAL-IP address has changed from ``pending`` to an IP address, use CTRL-C to stop the kubectl watch process.


```bash
NAME               CLUSTER-IP    EXTERNAL-IP   PORT(S)        AGE
azure-vote-front   10.0.42.158   <pending>     80:31873/TCP   1m
azure-vote-front   10.0.42.158   52.179.23.131 80:31873/TCP   2m
```

To see the application, browse to the external IP address.

## Resources

For further instructions, videos and quick-starts, make sure to check the [Azure Container Service (AKS)](https://azure.microsoft.com/en-us/services/container-service/) section on the Azure.com website
