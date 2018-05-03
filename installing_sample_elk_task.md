---

copyright:
  years: 2017
lastupdated: "2017-06-07"

---

# Installing the Microservice Builder ELK Sample with Kubernetes

The following steps depend on whether you are working with Minikube or IBM Spectrum Conductor for Containers.

## Before you Begin
__Important__: To use the Sample ELK stack, make sure to deploy the Microservice Builder _fabric_ first. See the instructions for [Installing the Microservice Builder Fabric](https://microservicebuilder.ng.bluemix.net/docs/installing_fabric_task.html) to deploy the fabric. To learn more about the sample ELK stack for Microservices builder, see the information about the [ELK Sample](sample_elk_concept.md).

## Install the Microservice Builder ELK Sample locally on a Minikube environment

1. Download [Helm](https://github.com/kubernetes/helm).
2. Install Tiller using Helm
  ```
  helm init
  ```
3. Add the repository
  ```
  helm repo add mb-sample https://wasdev.github.io/sample.microservicebuilder.helm.elk/charts
  ```
4. Install Microservice Builder ELK Sample using Helm
  ```
  helm install mb-sample/sample-elk
  ```

## Install the Microservice Builder ELK Sample on to an IBM Spectrum Conductor for Containers Kubernetes cluster.

1. Log in to the IBM Spectrum Conductor for Containers dashboard.
2. Select **System** and then the **Repositories** tab.
3. Click **Add Repository**, enter _mb-sample_ as the repository name and  `https://wasdev.github.io/sample.microservicebuilder.helm.elk/charts` as the URL. Then, click **Add**.
4. Select **App Center**, click **Install** for mb-sample/sample-elk, and click **Install Package**.

---
Next, to configure your ELK Sample, see the [Using the ELK Sample](sample_elk_task.md) page.
