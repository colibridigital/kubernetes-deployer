[![CircleCI](https://circleci.com/gh/colibridigital/kubernetes-deployer.svg?style=svg)](https://circleci.com/gh/colibridigital/kubernetes-deployer)

# Kubernetes Deployer
Git Repo for a super userful Kubernetes deployment image based on Alpine or Ubuntu.  Contains a bunch of handy dependencies, making it an ideal image to use when deploying applications onto Kubernetes from any CI system.

## Libs Included
- Kubectl
- Helm
- Terraform
- Terragrunt
- AWS CLI
- Azure CLI
- Python3
- Pip3

## Tags
Supports two versions of Helm and both Ubuntu and Alpine as bases:
- For Helm 2.16.1 with alpine: use the tag `helm2-alpine`
- For Helm 3.1.0 with alpine: use the tag `helm3-alpine`
- For Helm 2.16.1 with ubuntu: use the tag `helm2-ubuntu`
- For Helm 3.1.0 with ubuntu: use the tag `helm3-ubuntu`

