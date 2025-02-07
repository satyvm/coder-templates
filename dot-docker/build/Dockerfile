FROM ubuntu

RUN apt-get update \
    && apt-get install -y \
    curl \
    git \
    golang \
    sudo \
    vim \
    wget \
    stow \
    tmux \
    neovim \
    zsh \
    && rm -rf /var/lib/apt/lists/*

ARG USER=coder
RUN useradd --groups sudo --no-create-home --shell /bin/bash ${USER} \
    && echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
    && chmod 0440 /etc/sudoers.d/${USER}

USER ${USER}
WORKDIR /home/${USER}

RUN curl -Lo install.sh https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh && \
    chmod +x install.sh && \
    RUNZSH=no CHSH=no /bin/zsh install.sh && \
    rm install.sh