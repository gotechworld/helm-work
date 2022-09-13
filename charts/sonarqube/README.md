
# SonarQube 

SonarQube is an open source quality management platform that analyzes and measures code's technical quality. It enables developers to detect code issues, vulnerabilities, and bugs 
in early stages.

[Overview of SonarQube](http://www.sonarqube.org)


## Introduction

This chart bootstraps an [SonarQube](https://github.com/bitnami/bitnami-docker-sonarqube) cluster on a [Kubernetes](https://kubernetes.io) cluster using the [Helm](https://helm.sh) 
package manager.

Bitnami charts can be used with [Kubeapps](https://kubeapps.dev/) for deployment and management of Helm Charts in clusters.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.2.0+
- PV provisioner support in the underlying infrastructure
- ReadWriteMany volumes for deployment scaling

## Installing the Chart

To install the chart with the release name `sonarqube`:

```console
$ helm repo add bitnami https://charts.bitnami.com/bitnami

$ helm repo update

$ helm install sonarqube \
--create-namespace \
--namespace=sonarqube \
bitnami/sonarqube
```

The command deploys SonarQube on the Kubernetes cluster in the default configuration. The [Parameters](#parameters) section lists the parameters that can be configured during 
installation.

> **Tip**: List all releases using `helm list --all-namespaces`

## Access SonarQube

To access your SonarQube site from outside the cluster follow the steps below:

### 1. Get the SonarQube URL by running these commands:

  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        Watch the status with: '__kubectl get svc --namespace sonarqube -w sonarqube__'
```
   export SERVICE_IP=$(kubectl get svc --namespace sonarqube sonarqube --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
   echo "SonarQube URL: http://$SERVICE_IP/"
```
### 2. Open a browser and access SonarQube using the obtained URL.

### 3. Login with the following credentials below:
```
  echo Username: user
  echo Password: $(kubectl get secret --namespace sonarqube sonarqube -o jsonpath="{.data.sonarqube-password}" | base64 -d)
```

## Uninstalling the Chart

To uninstall/delete the `sonarqube` deployment:

```console
$ helm delete sonarqube -n sonarqube
```

The command removes all the Kubernetes components associated with the chart and deletes the release.




