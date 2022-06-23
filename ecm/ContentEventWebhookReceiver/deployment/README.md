# DBA Serverless and GitOps Samples
## Serverless Content Event Webhook Receiver Quarkus Project
### Deploying to OpenShift

#### Before you apply the manifests:
- Make sure you have the right images (jvm image and/or native image) either in your OpenShift project local registry or from your favorite registry (I use quay.io)
  - The pipelines sample in the [gitops](../../../gitops) section can build and deploy to OpenShift local registry or to any external registry
- Edit accordingly the container section in the two knative serving manifest files described below

#### Manifest files used for a quick OpenShit test/deploy
- ./openshift/01_webhook-kn-serving-jvm.yaml
  - used to deploy the jvm build version of the app
  - update the container section to point to your image
- ./openshift/02_webhook-kn-serving-native.yaml
  - used to deploy the native build version of the app
  - update the container section to point to your image
  - the traffic section split traffic between the 2 versions/revisions
- ./cs-server-configmap.yaml
  - config map, environment variables related to the CS Server, edit and update 
- ./webhook-event-secret.yaml
  - OpenShift secret, environment variables related to CS Event (HMAC and webhook registration ID), edit and update 

#### Deploy
```shell
oc apply ./openshift/01_webhook-kn-serving-jvm.yaml
```
Test and then deploy the second version/revision
```shell
oc apply ./openshift/01_webhook-kn-serving-native.yaml
```
You should have 2 versions of the app running with traffic splitted equally (50% each)
