# See (https://mcr.microsoft.com/en-us/artifact/mar/devcontainers/base/about)
# See (https://github.com/devcontainers/images/tree/main/src/base-ubuntu)
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Labels
LABEL "org.opencontainers.image.title"="Btlab's devcontainer"
LABEL "org.opencontainers.image.description"="A devcontainer for Btlab"
LABEL "org.opencontainers.image.source"="https://github.com/h0tbird/btlab/tree/main/.devcontainer/Dockerfile"

# Environment variables
ENV LOCALE=en_US.UTF-8 LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8
ENV PATH=/workspaces/btlab/bin:${PATH}

# Install base packages
RUN apt update && \
    apt install -y --no-install-recommends \
    curl jq python3-pip

# Set zsh as default shell
RUN chsh -s /usr/bin/zsh root && \
    chsh -s /usr/bin/zsh vscode && \
    echo 'export GPG_TTY=$(tty)' >> /etc/zsh/zshenv && \
    sed -i '/^ZSH_THEME/c\ZSH_THEME="robbyrussell"' /root/.zshrc && \
    sed -i '/^ZSH_THEME/c\ZSH_THEME="robbyrussell"' /home/vscode/.zshrc

# Install Rust
WORKDIR /home/vscode
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="/home/vscode/.cargo/bin:${PATH}"
