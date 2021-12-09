# Chromatic Docker Images

Custom docker images, published to
[DockerHub](https://hub.docker.com/u/chromatichq/).

These images are rebuilt weekly on Thursday nights so if any issues are
introduced from upstream changes we have the opportunity to resolve them before
the weekend.

## A note on `php-apache-node`

The `php-apache-node` image installs [n](https://github.com/tj/n) and installs
[Node LTS](https://nodejs.org/en/about/releases/) by default. Any projects
using this image may invoke `n auto` to install whatever version of Node.js is
specified in the project’s `.nvmrc`. Other filenames are also supported; see
[Specifying Node.js Versions](https://github.com/tj/n#specifying-nodejs-versions)
for further details.

The image also pre-installs Yarn, so any `yarn *` commands also work out of the
box.
