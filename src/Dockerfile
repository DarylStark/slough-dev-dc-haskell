# hadolint ignore=DL3007
FROM dast1986/slough-dev-dc-generic-base:1.0.0 AS base

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Configure Starship
ENV PROMPTNAME="HASKELL"

# Install build-essential for Rust compilation with native dependencies
# hadolint ignore=DL3008,DL3004
RUN sudo apt-get update && \
    sudo apt-get install -y ghc cabal-install haskell-stack && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/*

# Set the default command to bash
CMD ["bash"]