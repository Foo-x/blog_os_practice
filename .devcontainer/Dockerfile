# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.183.0/containers/rust/.devcontainer/base.Dockerfile

FROM mcr.microsoft.com/vscode/devcontainers/rust:0-1

# [Optional] Uncomment this section to install additional packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

RUN apt update && export DEBIAN_FRONTEND=noninteractive && apt install -y --no-install-recommends \
    bash-completion \
    hub \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

USER vscode

RUN curl -fsSL https://raw.githubusercontent.com/Foo-x/dotfiles/master/install.sh | bash \
    && mkdir -p ~/.local/share/bash-completion/completions \
    && rustup completions bash > ~/.local/share/bash-completion/completions/rustup \
    && rustup completions bash cargo > ~/.local/share/bash-completion/completions/cargo \
    && echo ". ~/.local/share/bash-completion/completions/rustup" >> ~/.bashrc \
    && echo ". ~/.local/share/bash-completion/completions/cargo" >> ~/.bashrc \
    && ln -sf /usr/bin/python3 ~/.local/bin/python
