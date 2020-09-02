FROM tugboatqa/node:12
RUN curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
    && apt-get update \
    && apt-get --quiet install -y --no-install-recommends \
      yarn \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
