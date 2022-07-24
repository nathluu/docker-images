FROM debian:bullseye-slim

ARG UID=1000
ARG GID=1000

ENV HOME /home/mogo

RUN groupadd -g ${GID} mongo || groupmod -n mongo `getent group ${GID} | cut -d: -f1` \
    && useradd --shell /bin/bash -u ${UID} -g ${GID} -m mongo \
    && apt-get update \
    && apt-get upgrade -y openssl \
    && apt-get install -y jq vim dnsutils curl \
    && apt-get autoremove -y

WORKDIR $HOME

RUN curl -L https://fastdl.mongodb.org/tools/db/mongodb-database-tools-debian11-x86_64-100.5.4.deb -o /tmp/mongodb-database-tools-debian11-x86_64-100.5.4.deb \
    && apt-get install /tmp/mongodb-database-tools-*-100.5.4.deb \
    && rm -rf /tmp/mongodb-database-tools-debian11-x86_64-100.5.4.deb

USER mongo

CMD ["/bin/bash"]
