ARG PHP_VERSION
FROM tugboatqa/php:${PHP_VERSION}-apache
ENV COMPOSER_DISCARD_CHANGES=true
ENV COMPOSER_NO_INTERACTION=true
ENV COMPOSER_ALLOW_SUPERUSER=true
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash - \
    && . ~/.bashrc \
    && nvm install --lts \
    && echo "#!/bin/bash" > /usr/local/bin/install-node-via-nvm.sh \
    && echo "set -ex" >> /usr/local/bin/install-node-via-nvm.sh \
    && echo ". ~/.bashrc" >> /usr/local/bin/install-node-via-nvm.sh \
    && echo "nvm install" >> /usr/local/bin/install-node-via-nvm.sh \
    && chmod +x /usr/local/bin/install-node-via-nvm.sh \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
    && apt-get update \
    && apt-get --quiet install -y --no-install-recommends \
      libzip-dev \
      parallel \
      python3-pip \
      redis-tools \
      software-properties-common \
    && python3 -m pip install --upgrade pip \
    && pip3 install --upgrade setuptools \
    && pip3 install wheel \
    && pip3 install ansible awscli pyyaml \
    && yes '' | pecl install -fo redis \
    && rm -rf /tmp/pear \
    && docker-php-ext-install opcache \
    && docker-php-ext-enable opcache \
    && docker-php-ext-enable redis \
    && docker-php-ext-install zip \
    && a2enmod headers rewrite \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
