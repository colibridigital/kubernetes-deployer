FROM ubuntu:16.04

LABEL maintainer="andreas.adamides@colibridigital.io"

ARG KUBE_VERSION=1.16.2
ARG HELM_VERSION=2.16.1
ENV TERRAFORM_VERSION 0.12.19

RUN apt-get update \
    && apt install software-properties-common -y \
    && apt-get install git -y \
    && apt-get install curl -y \
    && apt-get install -y unzip \
    && curl -sL https://aka.ms/InstallAzureCLIDeb | bash 

RUN mkdir -p /tmp/helm \
    && curl -LO https://storage.googleapis.com/kubernetes-release/release/v${KUBE_VERSION}/bin/linux/amd64/kubectl \
    && chmod +x ./kubectl \
    && mv ./kubectl /usr/bin/kubectl \
    && curl https://storage.googleapis.com/kubernetes-helm/helm-v${HELM_VERSION}-linux-amd64.tar.gz | tar -xzv -C /tmp/helm \
    && mv /tmp/helm/linux-amd64/helm /usr/bin/helm \
    && rm -rf /tmp/helm \
    && rm -rf /var/cache/apk/* \
    && rm -rf /root/.cache

RUN cd /usr/local/bin && \
    curl https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -o terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip