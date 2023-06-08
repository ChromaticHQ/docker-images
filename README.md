# Chromatic Docker Images

Custom docker images, published to [DockerHub](https://hub.docker.com/u/chromatichq/).

These images are rebuilt weekly on Thursday nights so if any issues are introduced from upstream changes we have the opportunity to resolve them before the weekend.

## A note on how Node is installed

The `node` and `php-apache-node` images use [n](https://github.com/tj/n) to install [Node LTS](https://nodejs.org/en/about/releases/) by default. Any projects using these images may invoke `n auto` to install whatever version of Node.js is specified in the project’s `.node-version`. Other filenames are also supported; see [Specifying Node.js Versions](https://github.com/tj/n#specifying-nodejs-versions) for further details.

The image also pre-installs Yarn so that any `yarn *` commands also work out of the box and `http-server` to easily serve static files when necessary.
