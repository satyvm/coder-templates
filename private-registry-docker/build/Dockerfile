FROM registry.example.com/example:0.0.1

ARG USER=coder
RUN useradd --groups sudo --create-home --shell /bin/bash ${USER} \
    && echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
    && chmod 0440 /etc/sudoers.d/${USER}

USER ${USER}
WORKDIR /home/${USER}

ENV HOME=/home/${USER}
ENV PATH=$HOME/.local/bin:$PATH

CMD ["/bin/bash"] 