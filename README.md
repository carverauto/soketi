# soketi setup

https://cloud.google.com/artifact-registry/docs/helm/quickstart

## Create helm package
```shell
 helm package soketi
 helm push soketi-0.15.3.tgz oci://us-central1-docker.pkg.dev/chaseapp-8459b/soketi
```

## Add gcloud artifacts

```shell
 gcloud artifacts docker images list us-central1-docker.pkg.dev/chaseapp-8459b/soketi
```

## Create cluster
```shell
 gcloud container clusters create --zone us-central1-a chart-cluster
```
## Get credentials for helm to use next
```shell
 gcloud container clusters get-credentials --zone us-central1-a chart-cluster
```

## Install the helm chart
```shell
 helm install soketi-chart oci://us-central1-docker.pkg.dev/chaseapp-8459b/soketi/soketi --version 0.15.3
```

## Setup networking

```shell
kubectl expose deployment soketi-chart --port=8765 --target-port=9376 \
        --name=soketi-service --type=LoadBalancer
```
