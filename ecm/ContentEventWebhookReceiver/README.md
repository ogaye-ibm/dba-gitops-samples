# DBA Serverless and GitOps Samples
## Serverless Content Event Webhook Receiver Quarkus Project

### Introduction
- This is a Quarkus, Serverless/Knative *modernization* of the ECM J2EE sample [https://github.com/ibm-ecm/ibm-content-platform-engine-samples](https://github.com/ibm-ecm/ibm-content-platform-engine-samples)
  - The sample project contains code for creating a sample application that can be used as a Content Event Webhook Receiver. The application can be used as the base or inspiration for creating a custom Content Event Webhook Receiver application.
  - Before using the Webhook Receiver sample application, you will need to prepare an object store on the Content Platform Engine server. For more information about Content Event Webhooks and how to set up the Content Platform Engine object store please refer to the legacy project ReaMe at [https://github.com/ibm-ecm/ibm-content-platform-engine-samples](https://github.com/ibm-ecm/ibm-content-platform-engine-samples)
- OpenShift deployment
  - The folder [deployment](deployment) contain sample manifests for a test deployment to OpenShit. However, for a Production grade deployment, the CICD samples (Tekton, ArgoCD) provide under [../../gitops](../../gitops) are more appropriate

### Running the code
#### Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```shell script
./gradlew quarkusDev
```

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

#### Packaging and running the application

The application can be packaged using:
```shell script
./gradlew build
```
It produces the `quarkus-run.jar` file in the `build/quarkus-app/` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `build/quarkus-app/lib/` directory.

The application is now runnable using `java -jar build/quarkus-app/quarkus-run.jar`.

If you want to build an _über-jar_, execute the following command:
```shell script
./gradlew build -Dquarkus.package.type=uber-jar
```

The application, packaged as an _über-jar_, is now runnable using `java -jar build/*-runner.jar`.

#### Creating a native executable

You can create a native executable using: 
```shell script
./gradlew build -Dquarkus.package.type=native
```

Or, if you don't have GraalVM installed (see here for [how to](../../quarkus)), you can run the native executable build in a container using: 
```shell script
./gradlew build -Dquarkus.package.type=native -Dquarkus.native.container-build=true
```
**Note:** when building native image with the *quarkus.native.container-build=true* option, you might encounter Docker and 
resources issues. If so, go to your Docker Preferences and increase the Memory setting from the default 2GB. For 
example, I build Native Image with Memory set to 8GB and using the following command
```shell
./gradlew build -Dquarkus.package.type=native -Dquarkus.native.container-build=true -Dquarkus.native.native-image-xmx=8G -x test 
```

**Note:** Building and pushing manually:
```shell
docker build -f src/main/docker/Dockerfile.native-micro -t webhook-native:0.0.1 .
docker tag webhook-native:0.0.1 quay.io/omar.gaye-ibm/webhook-native:0.0.1
docker push quay.io/omar.gaye-ibm/webhook-native:0.0.1
```

To execute a native executable from command line:
```shell
./build/webhook-1.0.0-SNAPSHOT-runner
```

If you want to learn more about building native executables, please consult https://quarkus.io/guides/gradle-tooling.

#### Related Guides
- If you want to learn more about Quarkus, please visit its website: 
- [https://quarkus.io](https://quarkus.io)
- [https://quarkus.io/guides](https://quarkus.io/guides): 







