# hadolint ignore=DL3007
FROM dast1986/slough-dev-dc-generic-base:1.0.0 AS base

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Configure Starship
ENV PROMPTNAME="HASKELL"

# hadolint ignore=DL3008,DL3004
RUN sudo apt update && \
    sudo apt -y full-upgrade && \
    sudo apt -y install \
        build-essential \
        curl \
        libgmp-dev \
        libncurses-dev \
        libtinfo-dev \
        xz-utils \
        git && \
    sudo apt -y clean && \
    sudo apt -y autoremove && \
    sudo rm -rf /var/lib/apt/lists/*

ENV BOOTSTRAP_HASKELL_NONINTERACTIVE=1 \
    BOOTSTRAP_HASKELL_GHC_VERSION=latest \
    BOOTSTRAP_HASKELL_CABAL_VERSION=latest \
    BOOTSTRAP_HASKELL_HLS_VERSION=latest \
    GHCUP_USE_XDG_DIRS=1 \
    GHCUP_INSTALL_BASE_PREFIX=/home/developer

# Install Haskell and Stack
RUN curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | bash -s -- -y --set-path no && \
    /home/developer/.local/bin/ghcup install ghc latest && \
    /home/developer/.local/bin/ghcup install cabal latest && \
    /home/developer/.local/bin/ghcup install hls latest && \
    /home/developer/.local/bin/ghcup set ghc latest && \
    /home/developer/.local/bin/ghcup set cabal latest && \
    /home/developer/.local/bin/ghcup set hls latest

ENV PATH="/home/developer/.ghcup/bin:${PATH}"

# Set the default command to bash
CMD ["bash"]