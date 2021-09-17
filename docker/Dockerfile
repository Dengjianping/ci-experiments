FROM ubuntu:20.04 as builder
LABEL description="run calamari binary distribution in docker"
ARG TAG_NAME
ARG CALAMARI_PATH
ARG COMMIT_HASH
ARG CALAMARI_GENESIS="https://raw.githubusercontent.com/Manta-Network/Manta/${COMMIT_HASH}/genesis/calamari-genesis.json"
ARG KUSAMA_GENESIS="https://raw.githubusercontent.com/paritytech/polkadot/v0.9.9-1/node/service/res/kusama.json"

ENV DEBIAN_FRONTEND noninteractive

WORKDIR /calamari-bin

COPY "$GITHUB_WORKSPACE/calamari-pc" /calamari-bin/calamari-pc

ADD "$CALAMARI_GENESIS" /calamari-bin/calamari-genesis.json
ADD "$KUSAMA_GENESIS" /calamari-bin/kusama.json

RUN apt-get update && \
	apt install -y openssl libssl-dev

# shrink size
RUN rm -rf /usr/share/*


EXPOSE 30333 9933 9944 9615
VOLUME ["/calamari"]

ENV DEBIAN_FRONTEND teletype
