FROM ubuntu:14.04

RUN apt-get update && apt-get install -y --no-install-recommends \
            vim tmux nkf \
            ca-certificates curl wget \
            bzr git mercurial openssh-client subversion \

            autoconf build-essential imagemagick libbz2-dev libcurl4-openssl-dev \
            libevent-dev libffi-dev libglib2.0-dev libjpeg-dev liblzma-dev \
            libmagickcore-dev libmagickwand-dev libncurses-dev libreadline-dev \
            libmysqlclient-dev libpq-dev libsqlite3-dev \
            libssl-dev libxml2-dev libxslt-dev libyaml-dev zlib1g-dev \

    && rm -rf /var/lib/apt/lists/*

RUN locale-gen en_US.UTF-8 && update-locale LANG=en_US.UTF-8

ENV LC_ALL en_US.UTF-8

CMD ["/bin/bash"]


