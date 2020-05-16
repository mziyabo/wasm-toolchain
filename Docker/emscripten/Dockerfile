FROM debian:buster
ARG EMSCRIPTEN_VERSION=latest

# ------------------------------------------------------------------------------

RUN echo "## Install prerequisites"; \
    apt-get update; \
    apt-get install -y \
    python \
    cmake \
    make \
    default-jre \
    curl \
    xz-utils \
    unzip; \
    echo "## Install emscripten toolchain"; \
    curl -LSo emsdk.zip https://github.com/emscripten-core/emsdk/archive/master.zip; \
    unzip -jo ./emsdk.zip -d ./emsdk; \
    /emsdk/emsdk install ${EMSCRIPTEN_VERSION}; \
    /emsdk/emsdk activate ${EMSCRIPTEN_VERSION}; \
    mkdir /target;


ENV PATH "$PATH:/emsdk/node/12.9.1_64bit/bin:/emsdk/upstream/bin:/emsdk/upstream/emscripten:/emsdk/upstream;" 

# ------------------------------------------------------------------------------

LABEL maintainer="mziyabo" \
    org.label-schema.vcs-url="https://github.com/mziyabo/wasm-toolchain" \
    org.label-schema.docker.dockerfile="/docker/mziyabo/emscripten/Dockerfile"