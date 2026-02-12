# hadolint ignore=DL3007
FROM dast1986/slough-dev-dc-generic-base:1.0.0 AS base

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Configure Starship
ENV PROMPTNAME="HASKELL"

# hadolint ignore=DL3008,DL3004
RUN sudo apt-get update && \
RUN sudo apt-get full-upgrade -y && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/*

# Install Haskell and Stack
RUN curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | bash -s -- -y \
    && ~/.ghcup/bin/ghcup install ghc \
    && ~/.ghcup/bin/ghcup install hls \
    && ~/.ghcup/bin/ghcup set ghc \
    && ~/.ghcup/bin/ghcup set hls \
    && ~/.ghcup/bin/ghcup install cabal \
    && ~/.ghcup/bin/ghcup set cabal

# Set the default command to bash
CMD ["bash"]