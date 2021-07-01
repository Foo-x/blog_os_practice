# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.183.0/containers/rust/.devcontainer/base.Dockerfile

FROM mcr.microsoft.com/vscode/devcontainers/rust:0-1

# [Optional] Uncomment this section to install additional packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

RUN apt update && export DEBIAN_FRONTEND=noninteractive && apt install -y --no-install-recommends \
    bash-completion \
    && apt install -y \
    qemu \
    qemu-system-x86 \
    && curl -L https://github.com/cli/cli/releases/download/v1.11.0/gh_1.11.0_linux_amd64.deb -o /tmp/gh.deb \
    && apt install -y --no-install-recommends /tmp/gh.deb \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

USER vscode

RUN curl -fsSL https://raw.githubusercontent.com/Foo-x/dotfiles/master/install.sh | bash \
    && mkdir -p ~/.config \
    && mkdir -p ~/.local/bin \
    && ln -sf /usr/bin/python3 ~/.local/bin/python

RUN rustup override set nightly \
    && rustup component add rust-src \
    && cargo install bootimage \
    && rustup component add llvm-tools-preview \
    && rustup component add rustfmt --toolchain nightly-x86_64-unknown-linux-gnu
