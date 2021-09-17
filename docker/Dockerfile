FROM ubuntu:20.04 as builder
LABEL description="run calamari binary distribution in docker"
ARG TAG_NAME
ARG CALAMARI_PATH
ARG CALAMARI_BINARY="${CALAMARI_PATH}/calamari-pc"
ARG COMMIT_HASH
ARG KUSAMA_GENESIS="https://raw.githubusercontent.com/paritytech/polkadot/v0.9.9-1/node/service/res/kusama.json"

ENV DEBIAN_FRONTEND noninteractive

RUN echo $(ls -1 .)


COPY "$CALAMARI_BINARY" /calamari-bin/calamari-pc

ADD "$KUSAMA_GENESIS" /calamari-bin/kusama.json
WORKDIR /calamari-bin

RUN apt-get update && \
	apt install -y openssl libssl-dev

# shrink size
RUN rm -rf /usr/share/*


EXPOSE 30333 9933 9944 9615
VOLUME ["/calamari"]

ENV DEBIAN_FRONTEND teletype
