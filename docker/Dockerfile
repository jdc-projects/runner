ARG BASE_IMAGE=ghcr.io/actions/actions-runner:2.319.1

FROM ${BASE_IMAGE}

# install some basic tools - can be removed once https://github.com/actions/runner/pull/3056 is included in a release
RUN sudo apt update
RUN sudo apt install -y --no-install-recommends unzip curl git

# install node
# note: once base image upgrades to Ubuntu 24.04, node can potentially be installed without nodesource step
#       currently the node version included in the Ubuntu sources is too old, so this is required
ARG NODE_VERSION=20
RUN curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x -o nodesource_setup.sh
RUN sudo bash nodesource_setup.sh
RUN sudo rm nodesource_setup.sh
RUN sudo apt install -y --no-install-recommends nodejs

# install yq
# note: the PPA in the docs is very out of date, so we don't use it
ARG YQ_VERSION=v4.44.3
ARG YQ_BINARY=linux_amd64
RUN sudo curl -Lo yq_${YQ_BINARY}.tar.gz https://github.com/mikefarah/yq/releases/download/${YQ_VERSION}/yq_${YQ_BINARY}.tar.gz
RUN sudo tar -xzf yq_${YQ_BINARY}.tar.gz
RUN sudo mv ./yq_${YQ_BINARY} /usr/bin/yq
