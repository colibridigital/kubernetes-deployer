FROM alpine:3.10

LABEL maintainer="james.cross@colibridigital.io"

ARG KUBE_VERSION=1.16.2
ARG HELM_VERSION=3.1.0
ENV TERRAFORM_VERSION=0.12.20

ENV PATH ~/.local/bin:$PATH

RUN \
  apk update --no-cache && \
  apk add --no-cache bash python3 grep curl && \
  apk add --no-cache git && \
  apk add --no-cache jq && \
  python3 -m ensurepip && \
  ln -s /usr/bin/pip3 /usr/bin/pip && \
  ln -s /usr/bin/python3 /usr/bin/python && \
  rm -r /usr/lib/python*/ensurepip && \
  apk add --virtual=build gcc libffi-dev musl-dev openssl-dev python3-dev make && \
  pip --no-cache-dir install -U pip && \
  pip --no-cache-dir install azure-cli && \
  pip --no-cache-dir install awscli && \
  apk del --purge build \
    && mkdir -p /tmp/helm \
    && curl -LO https://storage.googleapis.com/kubernetes-release/release/v${KUBE_VERSION}/bin/linux/amd64/kubectl \
    && chmod +x ./kubectl \
    && mv ./kubectl /usr/bin/kubectl \
    && curl https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar.gz | tar -xzv -C /tmp/helm \
    && mv /tmp/helm/linux-amd64/helm /usr/bin/helm \
    && rm -rf /tmp/helm \
    && rm -rf /var/cache/apk/* \
    && rm -rf /root/.cache

RUN cd /usr/local/bin && \
    curl https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -o terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip