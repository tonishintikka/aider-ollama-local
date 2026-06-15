FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       ca-certificates \
       curl \
       fd-find \
       git \
       jq \
       python3 \
       python3-pip \
       python3-venv \
       ripgrep \
       unzip \
    && ln -sf /usr/bin/fdfind /usr/local/bin/fd \
    && rm -rf /var/lib/apt/lists/*

# Install aider into an isolated venv so it doesn't conflict with project deps
RUN python3 -m venv /opt/aider \
    && /opt/aider/bin/pip install --quiet aider-chat \
    && ln -s /opt/aider/bin/aider /usr/local/bin/aider

WORKDIR /workspaces
