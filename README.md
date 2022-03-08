# kustomize-vs-helm
This repository show an example of use of Helm and Kustomize and follows the following objectives:
- Understand how works Kustomize
- Understand how works Helm
- Show the difference between both
- Use of both with an example using ArgoCD

## Kustomize
Kustomize lets you customize raw, template-free YAML files for multiple purposes, leaving the original YAML untouched and usable as is.

### Structure
The structure contains a ```base``` folder with the common descriptors and ```overlays``` folder with a folder for each environment.

> NOTE: An overlay is just another kustomization, referring to the base, and referring to patches to apply to that base.

Another important aspect is the ```kustomization.yaml``` file that contains some folders. This file indicates to Kustomize what files have to read and how, also some functions can be used to generate ConfigMap, prefixes, etc

```zsh
❯ tree
.
├── base
│   ├── hello-world.yaml
│   └── kustomization.yaml
└── overlays
    ├── dev
    │   ├── kustomization.yaml
    │   └── namespace.yaml
    └── pre
        ├── hello-world.yaml
        ├── kustomization.yaml
        └── namespace.yaml

4 directories, 7 files
```

### Usage
The use of Kustomize is simple. We'll use the example located inside the ```basic/kustomize``` folder.  

This example simulates two descriptors that change according to the environment.

The ```base``` folder contains the ```hello-world.yaml``` and each env contains a ```namespace.yaml``` file. 

```dev``` doesn't touch the ```hello-world.yaml``` file but add a new ```namespace.yaml``` file. If we execute:

```zsh
❯ kustomize build overlays/dev           
apiVersion: v1
kind: Namespace
metadata:
  name: dev
---
apiVersion: v1
kind: Test
metadata:
  name: hello-world
spec:
  message: hello
  replicas: 1
```

```pre``` also to do the same operations that ```dev```, modify inside the base file ```hello-world.yaml``` the key ```spec.message```:
```zsh
❯ kustomize build overlays/pre
apiVersion: v1
kind: Namespace
metadata:
  name: pre
---
apiVersion: v1
kind: Test
metadata:
  name: hello-world
spec:
  message: Hello world from pre!
  replicas: 1
```

## Helm

## Example

### ArgoCD

### Use case

### Conclusion

## References
