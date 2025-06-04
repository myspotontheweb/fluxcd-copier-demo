# fluxcd-copier-demo

Demo repository created from fluxcd-copier-template

# How this repo was populated

This project uses [copier](https://copier.readthedocs.io/) to generate a project layout designed to launch and manage 
an [AWS EKS cluster](https://eksctl.io/) using [FluxCD](https://fluxcd.io/).

The project template is located here

* [myspotontheweb/fluxcd-copier-template](https://github.com/myspotontheweb/fluxcd-copier-template)

## Install software

```bash
#
# Dependencies
#
brew install python3
brew intsall pipx

#
# Install copier
#
pipx install copier
```

## Generate content

```bash
copier copy gh:myspotontheweb/fluxcd-copier-template . --exclude LICENSE --exclude README.md
```

## Create a cluster

```
export AWS_PROFILE=development
export GITHUB_TOKEN=$(gh auth token)

eksctl create cluster -f bootstrap/eks/cluster-dev1.yaml
```

## Update content

```bash
copier update --defaults --exclude LICENSE --exclude README.md
```
