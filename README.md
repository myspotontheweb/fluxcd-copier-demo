# fluxcd-copier-demo

Demo repository created from fluxcd-copier-template

# How this repo was populated

This project uses [copier](https://copier.readthedocs.io/) to generate a project layout designed to launch and manage 
an [AWS EKS cluster](https://eksctl.io/) using [FluxCD](https://fluxcd.io/).

The project template is located here

* [myspotontheweb/fluxcd-copier-template](https://github.com/myspotontheweb/fluxcd-copier-template)

## Install software

```bash
# eksctl
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl

# flux
brew install fluxcd/tap/flux

# copier
brew install pipx
pipx install copier
```

## Generate content

```bash
#
# Generate project files
#
copier copy gh:myspotontheweb/fluxcd-copier-template . --exclude LICENSE --exclude README.md

#
# Save files to git
#
git add .
git commit -am "Save generated files"
git push
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
