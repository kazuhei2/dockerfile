FROM ubuntu:18.04
RUN mkdir /work
WORKDIR /work
SHELL ["/bin/bash", "-c"]

RUN apt-get update
RUN apt-get install -y build-essential git vim curl

RUN apt-get install -y jq tree

# nvm environment variables
ENV NVM_DIR /root/.nvm
ENV NODE_VERSION 12.16.1

# Install nvm
RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.35.3/install.sh | bash

# Install Node and npm
RUN chmod 777 $NVM_DIR/nvm.sh
RUN source $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm use $NODE_VERSION

# Add node and npm to path so the commands are available
ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

# Confirm installation
RUN node -v

# Install @vue/cli
RUN npm install -g yarn
RUN yarn global add @vue/cli

# Vim configuration
RUN git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
RUN sh ~/.vim_runtime/install_awesome_vimrc.sh
#RUN vim +PluginInstall +qall

