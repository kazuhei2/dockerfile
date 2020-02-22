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

# nvm environment variables
ENV NVM_DIR /root/.nvm
ENV NODE_VERSION 8.9.1

# Install nvm
RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.35.2/install.sh | bash

# Install Node and npm
RUN chmod 777 $NVM_DIR/nvm.sh
RUN source $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm use $NODE_VERSION

# Add node and npm to path so the commands are available
ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

# Install yarn
RUN npm install -g yarn

# Confirm installation
RUN node -v
RUN yarn -v
