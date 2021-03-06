FROM jetbrains/teamcity-minimal-agent:latest

ENV DEBIAN_FRONTEND noninteractive
ENV DEBCONF_NONINTERACTIVE_SEEN true

# Install Python stuff
RUN apt-get update && apt-get install -y \
    build-essential \
    checkinstall \
    libreadline-gplv2-dev \
    libncursesw5-dev \
    libssl-dev \
    libsqlite3-dev \
    tk-dev \
    libgdbm-dev \
    libc6-dev \
    libbz2-dev \
    wget \
    locales

# Set the locale
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

# Install 3.6.6
RUN cd /usr/src && wget https://www.python.org/ftp/python/3.6.6/Python-3.6.6.tgz && tar xzf Python-3.6.6.tgz
RUN cd /usr/src/Python-3.6.6 && ./configure && make altinstall

RUN apt-get update && apt-get install -y \
    git \
    # python stuff
    python3-pip \
    software-properties-common \
    # pg
    libpq-dev \
    # images
    libjpeg-dev \
    zlib1g-dev \
    libpng-dev \
    # docker client
    docker.io \
    # AWS CLI
    awscli

# docker compose
RUN curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
RUN chmod +x /usr/local/bin/docker-compose

# nodejs
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - && apt-get -y install nodejs npm
# gulp
RUN npm install -g gulp-cli
