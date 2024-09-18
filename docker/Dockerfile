ARG BASE_IMAGE

FROM ${BASE_IMAGE}

# install some basic tools - can be removed once https://github.com/actions/runner/pull/3056 is included in a release
RUN sudo apt update
RUN sudo apt install -y --no-install-recommends unzip curl git

# install other tools
# note: once base image upgrades to Ubuntu 24.04, node can potentially be installed without nodesource step
#       currently the node version included in the Ubuntu sources is too old, so this is required
RUN sudo add-apt-repository ppa:rmescandon/yq
RUN curl -sL https://deb.nodesource.com/setup_20.x -o nodesource_setup.sh
RUN sudo bash nodesource_setup.sh
RUN sudo rm nodesource_setup.sh
RUN sudo apt install -y --no-install-recommends yq nodejs
