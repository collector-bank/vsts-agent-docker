FROM microsoft/vsts-agent:ubuntu-16.04

ENV DOCKER_CHANNEL stable
ENV DOCKER_VERSION 18.06.1-ce

RUN set -ex \
 && curl -fL "https://download.docker.com/linux/static/${DOCKER_CHANNEL}/`uname -m`/docker-${DOCKER_VERSION}.tgz" -o docker.tgz \
 && tar --extract --file docker.tgz --strip-components 1 --directory /usr/local/bin \
 && rm docker.tgz \
 && docker -v

ENV DOCKER_COMPOSE_VERSION 1.22.0

RUN set -x \
 && curl -fSL "https://github.com/docker/compose/releases/download/$DOCKER_COMPOSE_VERSION/docker-compose-`uname -s`-`uname -m`" -o /usr/local/bin/docker-compose \
 && chmod +x /usr/local/bin/docker-compose \
 && docker-compose -v

RUN apt-get update

RUN apt-get install unzip

# Install powershell
RUN cd /tmp \
  && curl -s https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb --output packages-microsoft-prod.deb \
  && dpkg -i packages-microsoft-prod.deb \
  && apt-get update \
  && apt-get install -y powershell
