ARG PHP_VERSION
FROM tugboatqa/php:${PHP_VERSION}-apache
ENV COMPOSER_DISCARD_CHANGES=true
ENV COMPOSER_NO_INTERACTION=true
ENV COMPOSER_ALLOW_SUPERUSER=true
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
    && curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
    && apt-get update \
    && apt-get --quiet install -y --no-install-recommends \
      libzip-dev \
      nodejs \
      parallel \
      python3-pip \
      redis-tools \
      software-properties-common \
      yarn \
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
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && a2enmod headers rewrite \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && git config --global --unset user.name  \
    && git config --global --unset user.email
