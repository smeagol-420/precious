FROM jupyter/base-notebook

COPY . ${HOME}
USER root

# Install system packages: curl, build tools, and Node.js
RUN apt-get update && apt-get install -y \
    curl \
    build-essential \
    && curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install ijavascript globally
RUN npm install -g ijavascript && ijsinstall --install=global

RUN chown -R $NB_UID:$NB_GID /home/jovyan

USER $NB_UID

