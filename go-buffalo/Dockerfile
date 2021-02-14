# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.158.0/containers/go/.devcontainer/base.Dockerfile

# [Choice] Go version: 1, 1.15, 1.14
ARG VARIANT="1"
FROM mcr.microsoft.com/vscode/devcontainers/go:0-${VARIANT}

ENV GOPROXY=https://proxy.golang.org
ENV GO111MODULE=on

# [Option] Install Node.js
ARG INSTALL_NODE="true"
ARG NODE_VERSION="lts/*"
RUN if [ "${INSTALL_NODE}" = "true" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends build-essential sqlite3 libsqlite3-dev postgresql libpq-dev vim

# Installing yarn
RUN npm install -g --no-progress yarn \
    && yarn config set yarn-offline-mirror /npm-packages-offline-cache \
    && yarn config set yarn-offline-mirror-pruning true

# Install golangci
RUN curl -sfL https://install.goreleaser.com/github.com/golangci/golangci-lint.sh | sh -s -- -b $(go env GOPATH)/bin v1.24.0

# Installing buffalo binary
#RUN curl -sf https://gobinaries.com/gobuffalo/buffalo/buffalo@v0.16.21 | sh 

# Installing buffalo
RUN wget https://github.com/gobuffalo/buffalo/releases/download/v0.16.21/buffalo_0.16.21_Linux_x86_64.tar.gz
RUN tar -xvzf buffalo_0.16.21_Linux_x86_64.tar.gz
RUN sudo mv buffalo /usr/local/bin/buffalo
RUN rm buffalo_0.16.21_Linux_x86_64.tar.gz README.md LICENSE.txt

# Intalling buffalo-pop
RUN go get github.com/gobuffalo/buffalo-pop/v2


# [Optional] Uncomment the next line to use go get to install anything else you need
RUN go get github.com/gobuffalo/buffalo-pop/v2

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1

# Show buffalo version
RUN buffalo version


