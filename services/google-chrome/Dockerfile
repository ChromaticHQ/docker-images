FROM tugboatqa/httpd:2.4
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
    && curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
    && apt-get update \
    && apt-get --quiet install -y --no-install-recommends \
      libxss1 \
      google-chrome-stable \
      yarn \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
