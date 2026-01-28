FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# Install clipboard utilities for OSC 52 integration
RUN apt-get update && apt-get install -y \
    wl-clipboard \
    xclip \
    && rm -rf /var/lib/apt/lists/*

# Swap to vscode user for remaining user-specific config
USER vscode

# make sure mise is activated in both zsh and bash. 
# Might be overridden by a user's dotfiles.
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(mise activate zsh)"' >> /home/vscode/.zshrc
