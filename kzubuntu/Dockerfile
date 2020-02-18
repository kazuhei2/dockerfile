FROM ubuntu:latest
RUN mkdir /work
WORKDIR /work

RUN apt-get update
RUN apt-get install -y build-essential git vim curl jq clang-format

# Git configuration
RUN git config --global user.name "Kazuhei Hamada"
RUN git config --global user.email kazuhei.git@gmail.com
RUN git config --global core.editor vim
RUN git config --global core.autocrlf input
RUN echo '*.swp' > ~/.gitignore_global

SHELL ["/bin/bash", "-c"]

# Rust installation
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y
RUN source $HOME/.cargo/env
RUN export PATH="$HOME/.cargo/bin:$PATH"
