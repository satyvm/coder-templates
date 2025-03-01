FROM ubuntu:22.04

# Avoid prompts from apt
ENV DEBIAN_FRONTEND=noninteractive

# Update and install essential tools
RUN apt-get update && apt-get install -y \
    vim \
    sudo \
    curl \
    git \
    stow \
    tmux \
    neovim \
    wget \
    build-essential \
    ca-certificates \
    gnupg \
    lsb-release \
    locales \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Set up locale
RUN locale-gen en_US.UTF-8
ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8

# Create coder user with sudo privileges
RUN useradd -m -s /bin/bash -G sudo coder \
    && echo "coder ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/coder \
    && chmod 0440 /etc/sudoers.d/coder

# Set the working directory
WORKDIR /home/coder

# Switch to the coder user
USER coder

# Set up a welcome message
RUN echo 'echo "Welcome to your Coder devcontainer workspace with Terraform and Docker CLI!"' >> ~/.bashrc