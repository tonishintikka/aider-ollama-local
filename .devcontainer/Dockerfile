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

# Install aider with all optional deps pre-baked so it never prompts at runtime
RUN python3 -m venv /opt/aider \
    && /opt/aider/bin/pip install --quiet 'aider-chat[browser]' \
    && ln -s /opt/aider/bin/aider /usr/local/bin/aider \
    && chmod -R a+rX /opt/aider

WORKDIR /workspaces
