# DBA Serverless and GitOps Samples
### GitOps Samples - Flux Samples  


## Introduction
- [Installation](../../_install-setup/README.md)
- Originally developed by Weaveworks and now incubated under CNCF
- Provides GitOps for both apps and infrastructure
- Just like ArgoCD, Flux is a tool that matches your live environments with the desired states defined and stored in your Git repository. 
- Mostly CLI-first approach, UI being just a supplementary add-on, not as mature as its ArgoCD couterpart
- [Argo CD vs Flux CD](https://rajputvaibhav.medium.com/argo-cd-vs-flux-cd-right-gitops-tool-for-your-kubernetes-cluster-c71cff489d26)
- [Argo CD vs Flux CD 2](https://thenewstack.io/gitops-on-kubernetes-deciding-between-argo-cd-and-flux/)
- Works with any Kubernetes platforms
- Designed with security in mind
- [Flux Home](https://fluxcd.io)

## Getting started
Once Flux CLI [installed](../../_install-setup/README.md), check:
[The Flux Getting started](https://fluxcd.io/docs/get-started/) page
```shell
flux check --pre
```
Return looks like:
```yaml
► checking prerequisites
✔ Kubernetes 1.21.11+6b3cbdd >=1.20.6-0
✔ prerequisites checks passed
```

- Install for GitHub or GitHub enterprise, example:
  Export GIt and token first:
```shell
export GITHUB_TOKEN=<TOKEN_HERE>
export GITHUB_USER=<A_USER_HERE>
```
```shell
flux bootstrap github \   
 --owner=$GITHUB_USER \   
 --repository=clusters-infra \   
 --path=clusters/dev-cluster \  
 --branch=main \   
 --personal 
```
The **bootstrap** command above does the following:
   - Creates a git repository clusters-infra on your GitHub account
   - Adds Flux component manifests to the repository
   - Deploys Flux Components to your Kubernetes Cluster
   - **Configures Flux components to track the path /clusters/dev-cluster/ in the repository**

Then clone the git repository Flux created:
```shell
git clone git@github.com:$GITHUB_USER/clusters-infra.git
cd clusters-infra
```
- Install for generic git server
```shell
flux bootstrap git \
  --url=ssh://git@<host>/<org>/<repository> \
  --branch=<my-branch> \
  --path=clusters/my-cluster
```

**Read this [Page](https://fluxcd.io/docs/get-started/) for more details on how to achieve the following objective**
  1. Bootstrap Flux on a Kubernetes Cluster
  2. Deploy a sample application using Flux
  3. Customize application configuration through Kustomize patches



## References and Guides
1. [Flux Home](https://fluxcd.io/docs/get-started/)
2. [Argo CD vs Flux CD](https://rajputvaibhav.medium.com/argo-cd-vs-flux-cd-right-gitops-tool-for-your-kubernetes-cluster-c71cff489d26)
