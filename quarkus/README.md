# DBA Serverless and GitOps Samples

### Quarkus, Getting Started

Quote (https://quarkus.io): Quarkus is a Kubernetes Native Java stack tailored for OpenJDK HotSpot and GraalVM, crafted from the best of breed Java libraries and standards

### Getting started
- Quarkus Install and getting started: [https://quarkus.io/get-started/](https://quarkus.io/get-started/)
- On Mac, Homebrew can be used to install Quarkus CLI:
```shell
brew install quarkus
```  
- Getting started, create app with maven, gradle, quarkus CLIs: [https://quarkus.io/guides/getting-started](https://quarkus.io/guides/getting-started)

### Native images
- [Introduction](https://www.graalvm.org/22.1/docs/introduction/): Native image is an innovative technology that compiles Java code into a standalone native executable or a native shared library. The Java bytecode that is processed during the build of a native executable includes all application classes, dependencies, third party dependent libraries, and any JDK classes that are required. A generated self-contained native executable is specific to each individual operating systems and machine architecture that does not require a JVM.
- GraalVM download and install instructions
  - https://github.com/graalvm/graalvm-ce-builds/releases/tag/vm-22.1.0
  - https://www.graalvm.org/22.1/docs/getting-started/macos/
  - If you are using macOS Catalina and later you may need to remove the quarantine attribute from the bits before you can use them. To do this, run the following:
```shell
sudo xattr -r -d com.apple.quarantine path/to/graalvm/folder/
```
- Build native image with Quarkus
    - https://quarkus.io/guides/building-native-image
- GraalVM
- https://www.graalvm.org/
  
**More Quarkus References ans samples:**
1. https://github.com/quarkusio
2. https://github.com/quarkusio/quarkus-quickstarts