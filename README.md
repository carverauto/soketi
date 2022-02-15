# soketi setup

https://cloud.google.com/artifact-registry/docs/helm/quickstart

## Create helm package
```
 helm package soketi
 helm push soketi-0.15.3.tgz oci://us-central1-docker.pkg.dev/chaseapp-8459b/soketi
```

## Add gcloud artifacts

```
 gcloud artifacts docker images list us-central1-docker.pkg.dev/chaseapp-8459b/soketi
```

## Create cluster
```
 gcloud container clusters create --zone us-central1-a chart-cluster
```
## Get credentials for helm to use next
```
 gcloud container clusters get-credentials --zone us-central1-a chart-cluster
```

## Install the helm chart
```
 helm install soketi-chart oci://us-central1-docker.pkg.dev/chaseapp-8459b/soketi/soketi --version 0.15.3
```
# soketi
