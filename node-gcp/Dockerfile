FROM node:9-alpine

ENV CLOUD_SDK_VERSION 162.0.0

ENV PATH /google-cloud-sdk/bin:$PATH

RUN apk --no-cache add curl python py-crcmod bash libc6-compat openssh-client git docker
RUN curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz
RUN \
    tar xzf google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
    rm google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
    ln -s /lib /lib64 && \
    gcloud config set core/disable_usage_reporting true && \
    gcloud config set component_manager/disable_update_check true && \
    gcloud config set metrics/environment github_docker_image
RUN gcloud components update kubectl

ADD bin/_deploy /bin/
