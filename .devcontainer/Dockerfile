ARG ELIXIR_VERSION=1.16.3
ARG OTP_VERSION=26.2.5
ARG DEBIAN_VERSION=bullseye-20240612

FROM hexpm/elixir:${ELIXIR_VERSION}-erlang-${OTP_VERSION}-debian-${DEBIAN_VERSION}

ARG USERNAME=elixir
ARG USER_UID=1001
ARG USER_GID=$USER_UID

# Create non root user
RUN groupadd --gid $USER_GID $USERNAME \
  && useradd --uid $USER_UID --gid $USER_GID -s /bin/bash -m $USERNAME

RUN apt-get update -qq && \
  apt-get upgrade -y && \
  apt-get install -qq -y \
  autoconf \
  build-essential \
  curl \
  dirmngr \
  gawk \
  git \
  gpg \
  inotify-tools \
  libncurses5-dev \
  libpng-dev \
  libwebp-dev \
  libssh-dev \
  libssl-dev \
  nodejs \ 
  npm \
  unzip \
  webp \
  wget \
  zsh \
  jq

RUN npm install --global yarn

ENV LANG C.UTF-8

WORKDIR /workspace

USER elixir

# Oh my zsh
# https://ohmyz.sh
RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
RUN touch ~/.zshenv

RUN mix local.hex --force
RUN mix local.rebar --force

ENV ELIXIR_ERL_OPTIONS="-kernel shell_history enabled"