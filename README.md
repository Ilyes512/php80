# php80

[![Build Images](https://github.com/Ilyes512/php80/actions/workflows/main.yml/badge.svg)](https://github.com/Ilyes512/php80/actions/workflows/main.yml)

A PHP 8.0 (FPM and Apache) based Docker base image.

## Pulling the images

```
docker pull ghcr.io/ilyes512/php80:runtime-latest
docker pull ghcr.io/ilyes512/php80:builder-latest
docker pull ghcr.io/ilyes512/php80:builder-nodejs-latest
docker pull ghcr.io/ilyes512/php80:vscode-latest

docker pull ghcr.io/ilyes512/php80/apache:runtime-latest
docker pull ghcr.io/ilyes512/php80/apache:builder-latest
docker pull ghcr.io/ilyes512/php80/apache:builder-nodejs-latest
docker pull ghcr.io/ilyes512/php80/apache:vscode-latest
```

The tag scheme: `{TARGET}-{VERSION}`

- **{TARGET}**: `runtime`, `builder`, `builder_nodejs` or `vscode`
- **{VERSION}**: `latest` or tag i.e. `1.0.0`

## Building the docker image(s)

There are multiple targets:

  - **runtime**: this is for *production*. It does not contain any development tools like Composer and Xdebug.
  - **builder**: this is for *development*. This is based on the runtime-target and it adds Composer, Xdebug etc.
  - **builder_nodejs**: this is for *development*. This is based on the builder-target and it adds NodeJS.
  - **vscode**: this is for *development* using
  [VS Code Remote](https://code.visualstudio.com/docs/remote/remote-overview). This is based on the
  `builder_nodejs`-target and adds some VS Code deps.

Building `runtime`-target:

```
docker build --tag ghcr.io/ilyes512/php80:runtime-latest --file fpm/Dockerfile --target runtime .
```

Building `builder`-target:

```
docker build --tag ghcr.io/ilyes512/php80:builder-latest --file fpm/Dockerfile --target builder .
```

Building `builder_nodejs`-target:

```
docker build --tag ghcr.io/ilyes512/php80:builder-nodejs-latest --file fpm/Dockerfile --target builder_nodejs .
```

Building `vscode`-target:

```
docker build --tag ghcr.io/ilyes512/php80:vscode-latest --file fpm/Dockerfile --target vscode .
```

## Task commands

Available [Task](https://taskfile.dev/#/) commands:

```
* build:              Build all PHP Docker image targets of both the FPM and Apache variants
* build:apache:       Build all PHP Docker image targets of the Apache variant
* build:fpm:          Build all PHP Docker image targets of the FPM variant
* lint:apache:        Apply a Dockerfile linter (https://github.com/hadolint/hadolint)
* lint:fpm:           Apply a Dockerfile linter (https://github.com/hadolint/hadolint)
* shell:apache:       Interactive shell
* shell:fpm:          Interactive shell
```
