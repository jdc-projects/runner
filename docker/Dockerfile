ARG BASE_IMAGE=ghcr.io/actions/actions-runner:2.320.0

FROM ${BASE_IMAGE}

# install node
# note: once base image upgrades to Ubuntu 24.04, node can potentially be installed without nodesource step
#       currently the node version included in the Ubuntu sources is too old, so this is required
ARG NODE_VERSION=20
RUN curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x -o nodesource_setup.sh
RUN sudo bash nodesource_setup.sh
RUN rm nodesource_setup.sh
RUN sudo apt install -y --no-install-recommends nodejs

# install yq
# note: the PPA in the docs is very out of date, so we don't use it
ARG YQ_VERSION=v4.44.3
ARG YQ_BINARY=linux_amd64
RUN curl -Lo yq_${YQ_BINARY}.tar.gz https://github.com/mikefarah/yq/releases/download/${YQ_VERSION}/yq_${YQ_BINARY}.tar.gz
RUN tar -xzf yq_${YQ_BINARY}.tar.gz
RUN sudo mv ./yq_${YQ_BINARY} /usr/bin/yq
RUN rm yq*

# shouldn't be needed, but tidy up with apt, just in case
RUN sudo apt autoremove -y
RUN sudo apt autoclean -y
