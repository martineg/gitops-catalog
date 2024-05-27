# Quay Bridge Operator

Installs the Quay Bridge Operator.

Do not use the `base` directory directly, as you will need to patch the `channel` based on the version of the operator you want to use.

The current *overlays* available are for the following channels:
* [stable-3.11](overlays/stable-3.11)

## Usage

If you have cloned the `gitops-catalog` repository, you can install  based on the overlay of your choice by running from the root (`gitops-catalog`) directory.

```
oc apply -k quay-bridge-operator/operator/overlays/<channel>
```

Or, without cloning:

```
oc apply -k https://github.com/redhat-cop/gitops-catalog/quay-bridge-operator/operator/overlays/<channel>
```

As part of a different overlay in your own GitOps repo:

```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
  - https://github.com/redhat-cop/gitops-catalog/quay-bridge-operator/operator/overlays/<channel>?ref=main
```