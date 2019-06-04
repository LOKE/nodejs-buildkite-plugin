# NodeJS Buildkite plugin

Runs a command inside a node docker container

Includes a `package` command for creating package.tar.gz

## Usage

```yml
steps:
  - command: npm ci && npm test
    plugins:
      - LOKE/nodejs#v1.0.0:
          version: "10.16.0"
```

or to deploy something more specific

```yml
steps:
  - command: package
    plugins:
      - LOKE/nodejs#v1.0.0:
          version: "10.16.0"
          entrypoint: main.js
```

## Configuration

### `version` (optional)

The nodejs version to use, defaults to `lts`.

### `entrypoint` (optional)

The entrypoint for the packaged service, will be run with node

### `environment` (optional)

Extra environment variables to pass to the docker container, in an array. Items can be specified as either `KEY` or `KEY=value`. Each entry corresponds to a Docker CLI `--env` parameter. Values specified as variable names will be passed through from the outer environment.

Examples: `MY_SECRET_KEY`, `MY_SPECIAL_BUT_PUBLIC_VALUE=kittens`
