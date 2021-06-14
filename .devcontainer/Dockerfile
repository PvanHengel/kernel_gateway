# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.177.0/containers/python-3/.devcontainer/base.Dockerfile

# [Choice] Python version: 3, 3.9, 3.8, 3.7, 3.6
ARG VARIANT="3.9"
FROM mcr.microsoft.com/vscode/devcontainers/python:0-${VARIANT}


ADD https://bitbucket.invesco.adaptavist.com/projects/EMTECH/repos/ivz-shared-pipelines/raw/docker/jupyterworker/IVZRoot.crt?at=refs%2Fheads%2Fmaster /usr/local/share/ca-certificates/IVZRoot.crt 
ADD https://bitbucket.invesco.adaptavist.com/projects/EMTECH/repos/ivz-shared-pipelines/raw/docker/sipBaseJava/ivzdev.cert?at=refs%2Fheads%2Fmaster /usr/local/share/ca-certificates/IVZDevRoot.crt
ADD https://bitbucket.invesco.adaptavist.com/projects/EMTECH/repos/ivz-shared-pipelines/raw/docker/sipBaseJava/ivz.cert?at=refs%2Fheads%2Fmaster /usr/local/share/ca-certificates/IVZ.crt

RUN chmod 644 /usr/local/share/ca-certificates/IVZRoot.crt && chmod 644 /usr/local/share/ca-certificates/IVZDevRoot.crt && chmod 644 /usr/local/share/ca-certificates/IVZ.crt && update-ca-certificates

ENV SSL_CERT_FILE /etc/ssl/certs/ca-certificates.crt
ENV SSL_CERT_DIR  /etc/ssl/certs/
ENV NODE_EXTRA_CA_CERTS /etc/ssl/certs/ca-certificates.crt


# [Option] Install Node.js
ARG INSTALL_NODE="true"
ARG NODE_VERSION="lts/*"
RUN if [ "${INSTALL_NODE}" = "true" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] If your pip requirements rarely change, uncomment this section to add them to the image.
# COPY requirements.txt /tmp/pip-tmp/
# RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
#    && rm -rf /tmp/pip-tmp

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1