FROM debian:buster

# ------------------------------------------------------------------------------

RUN echo "## Install prerequisites"; \
    apt-get update; \
    apt-get install -y \
    curl \
    xz-utils; \
    echo "Installing wasmtime"; \
    curl https://wasmtime.dev/install.sh -sSf | bash; \
    mkdir /target; \
    echo "## Done";
    
ENV PATH "$PATH:/root/.wasmtime/bin/;" 

# ------------------------------------------------------------------------------

WORKDIR /target
ENTRYPOINT [ "/root/.wasmtime/bin/wasmtime" ]

# ------------------------------------------------------------------------------

LABEL maintainer="mziyabo" \
    org.label-schema.vcs-url="https://github.com/mziyabo/wasm-toolchain" \
    org.label-schema.docker.dockerfile="/docker/mziyabo/wasmtime/Dockerfile"
