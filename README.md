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

## Helm

## Example

### ArgoCD

### Use case

### Conclusion

## References
