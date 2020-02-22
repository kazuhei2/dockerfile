FROM ubuntu:latest
RUN mkdir /work
WORKDIR /work
SHELL ["/bin/bash", "-c"]

RUN apt-get update
RUN apt-get install -y build-essential git vim curl

# Rust installation
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y
RUN source $HOME/.cargo/env
RUN export PATH="$HOME/.cargo/bin:$PATH"

RUN apt-get install -y jq clang-format tree

# Git configuration
RUN git config --global user.name "Kazuhei Hamada"
RUN git config --global user.email kazuhei.git@gmail.com
RUN git config --global core.editor vim
RUN git config --global core.autocrlf input
RUN echo '*.swp' > ~/.gitignore_global

# Vim configuration
RUN git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
RUN sh ~/.vim_runtime/install_awesome_vimrc.sh
RUN vim +PluginInstall +qall

# Web frontend development
RUN apt-get install -y npm yarn
