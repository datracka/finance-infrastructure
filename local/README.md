# Local

Steps to provision architecture in K8S locally

## Add a service

- run `kubectl apply -f service.yml` in local folder

To check the service `kubectl get service api-service`

## Add an ingress (in case it is not already there)

### Using Helm

Helm is a package manager for kubernetes

`helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx`
`helm repo update`
`helm install nginx-ingress ingress-nginx/ingress-nginx`

check `helm list` afterwards

### Using kubectl

using a manifest from kubernetes

`kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml`

Afterwards,

You can check the pods provisioned in your namespace with `kubectl get pods --all-namespaces`.

## Create the ingress

`kubectl apply -f ingress.yml`

## update the etc/host to point

127.0.0.1   finance-api.local

## What is all about

Ingress is acting as kind of reverse proxy.

it handles /api requests directly to the backend (java app) where are processed.
