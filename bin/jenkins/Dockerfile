FROM jenkins/jenkins:lts
ENV JAVA_OPTS "-Djenkins.install.runSetupWizard=false ${JAVA_OPTS:-}"

# heavily influenced by these Dockerfiles:
# https://github.com/conchoid/docker-nodenv/blob/master/8.9.4-alpine3.6/Dockerfile\
# https://github.com/visibilityspots/dockerfile-jenkins-docker
# you should read through those first and understand them separately before editing this file

ENV TZ=Etc/UTC

USER root

# install deps
RUN set -x \
	&& ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
	&& apt-get update -y \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends apt-utils \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends apt-transport-https \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends ca-certificates \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends curl \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends gnupg2 \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends file \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends software-properties-common \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends build-essential \
	&& curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
	&& echo "does the fingerprint of next command matches 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88" \
	&& apt-key fingerprint 0EBFCD88 \
	&& add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" \
	&& apt-get update -y \
	&& DEBIAN_FRONTEND="noninteractive" apt-get install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends docker-ce \
	&& groupmod -g 900 docker \
	&& usermod -a -G docker jenkins \
	&& apt-get -q autoremove \
	&& apt-get -q clean -y \
        && rm -rf /var/lib/apt/lists/* \
	&& rm -f /var/cache/apt/*.bin

# install blueocean jenkins UI
RUN /usr/local/bin/install-plugins.sh blueocean jdk-tool configuration-as-code configuration-as-code-support

# use nodenv for node. its just better
ENV NODENV_ROOT /opt/nodenv
ENV PATH "$NODENV_ROOT/shims:$NODENV_ROOT/bin:$PATH"

RUN set -x \
  && nodenv_version="v1.2.0" \
  && git clone https://github.com/nodenv/nodenv.git ${NODENV_ROOT} \
  && cd ${NODENV_ROOT} && git checkout ${nodenv_version} \
  && src/configure \
  && make -C src \
  && node_build_version="v4.4.0" \
  && git clone https://github.com/nodenv/node-build.git ${NODENV_ROOT}/plugins/node-build \
  && cd ${NODENV_ROOT}/plugins/node-build && git checkout ${node_build_version} \
  && npm_migrate_version="0.1.0" \
  && git clone https://github.com/nodenv/nodenv-npm-migrate.git ${NODENV_ROOT}/plugins/nodenv-npm-migrate \
  && cd ${NODENV_ROOT}/plugins/nodenv-npm-migrate && git checkout ${npm_migrate_version} \
  && rm -rf ${NODENV_ROOT}/.git ${NODENV_ROOT}/plugins/node-build/.git ${NODENV_ROOT}/plugins/nodenv-npm-migrate/.git
RUN nodenv install 8.12.0
RUN nodenv global 8.12.0
