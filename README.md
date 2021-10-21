# Chromatic Docker Images

Custom docker images, published to
[DockerHub](https://hub.docker.com/u/chromatichq/).

These images are rebuilt weekly on Thursday nights so if any issues are
introduced from upstream changes we have the opportunity to resolve them before
the weekend.

## A note on `php-apache-nvm`

The `php-apache-nvm` image installs nvm and creates a script to easily install
your project’s required version of Node.js. Running the following from a
project that uses this Docker image will install the version of Node specified
in your project’s `.nvmrc` file and then install Yarn:

```sh
/usr/local/bin/install-node-yarn-via-nvm
```

It should be noted that any Node-based commands (`node`, `nvm`, `npm`, `yarn`,
etc.) are only available if nvm is loaded in the context in which your commands
are run. The easiest way to ensure this is the case is to run your commands
with Bash in login mode. This can be done in a variety of ways, but the most
useful ways are as follows (using a few Yarn commands as examples):

1. For single-liners, you can just run your command like so:
    ```sh
    bash -lc "yarn build"
    ```
1. If you need to write several commands, you can create a shell script file
   with the appropriate shebang at the top of the file:
   ```sh
   #!/bin/bash -l

   yarn lint
   yarn build
   ```
