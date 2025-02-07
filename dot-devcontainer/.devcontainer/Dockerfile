FROM ubuntu

RUN apt-get update
RUN apt-get install vim sudo curl git stow tmux neovim -y

RUN useradd -m -s /bin/bash -G sudo coder
USER coder