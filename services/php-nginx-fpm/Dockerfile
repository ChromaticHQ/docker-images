ARG PHP_VERSION
FROM tugboatqa/php-nginx:${PHP_VERSION}-fpm
ENV COMPOSER_DISCARD_CHANGES=true
ENV COMPOSER_NO_INTERACTION=true
ENV COMPOSER_ALLOW_SUPERUSER=true
RUN git clone https://github.com/tj/n.git \
    && cd n && make install && cd .. \
    && n lts \
    && npm install --global yarn \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
    && apt-get update \
    && apt-get --quiet install -y --no-install-recommends \
      libzip-dev \
      redis-tools \
      software-properties-common \
    && yes '' | pecl install -fo redis \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable redis \
    && docker-php-ext-install zip \
    && a2enmod headers rewrite \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && git config --global --unset user.name  \
    && git config --global --unset user.email
