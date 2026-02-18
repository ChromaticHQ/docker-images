FROM tugboatqa/node:latest
RUN git clone https://github.com/tj/n.git \
    && cd n && make install && cd .. \
    && n lts \
    && yarn global add http-server \
    && wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | gpg --dearmor -o /usr/share/keyrings/google-chrome.gpg \
    && echo "deb [arch=amd64 signed-by=/usr/share/keyrings/google-chrome.gpg] http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google-chrome.list \
    && apt-get update \
    && apt-get --quiet install -y --no-install-recommends \
      libxss1 \
      libxtst6 \
      libx11-xcb1 \
      google-chrome-stable \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
