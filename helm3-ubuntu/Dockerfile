FROM ubuntu:16.04

LABEL maintainer="andreas.adamides@colibridigital.io"

ARG KUBE_VERSION=1.16.2
ARG HELM_VERSION=3.2.4
ARG TERRAFORM_VERSION=1.0.9
ARG TERRAGRUNT_VERSION=0.23.10

RUN apt-get update \
    && apt install software-properties-common -y \
    && apt-get install git -y \
    && apt-get install curl -y \
    && apt-get install -y unzip \
    && apt-get install jq -y \
    && curl -sL https://aka.ms/InstallAzureCLIDeb | bash \
    && rm -rf /var/cache/apk/* \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /tmp/helm \
    && curl -LO https://storage.googleapis.com/kubernetes-release/release/v${KUBE_VERSION}/bin/linux/amd64/kubectl \
    && chmod +x ./kubectl \
    && mv ./kubectl /usr/bin/kubectl \
    && curl https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar.gz | tar -xzv -C /tmp/helm \
    && mv /tmp/helm/linux-amd64/helm /usr/bin/helm \
    && curl -LO https://github.com/gruntwork-io/terragrunt/releases/download/v${TERRAGRUNT_VERSION}/terragrunt_linux_amd64 \
    && chmod +x terragrunt_linux_amd64 \
    && mv terragrunt_linux_amd64 /usr/bin/terragrunt \
    && rm -rf /tmp/helm \
    && rm -rf /var/cache/apk/* \
    && rm -rf /root/.cache \
    && rm -rf /var/lib/apt/lists/*

RUN cd /usr/local/bin && \
    curl https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -o terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip