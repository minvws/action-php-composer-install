# PHP - Composer install GitHub Action

This repository provides a reusable GitHub Action for installing the dependencies of a PHP project that uses Composer. It will install the dependencies and cache them for future runs.

## Usage

To use the action, add it to a workflow in your repository:

```yml
name: Build PHP project

on:
  workflow_dispatch:
  pull_request:
  push:
    branches:
      - main

jobs:
  build-php:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Install dependencies
        uses: minvws/action-php-composer-install@v1
        with:
          COMPOSER_AUTH_TOKEN: ${{ secrets.REPO_READ_ONLY_TOKEN }}
          php_version: <php_version>
```

Replace `<php_version>` with the PHP version you want to use. For example `"8.3"`.

In this basic example, the workflow is executed automatically on push to the `main` branch and on any pull request. And thanks to the `workflow_dispatch` trigger it can also be executed manually from the repository's Actions tab.

### Configuration

The action has the following inputs:

- `php_version` (**required**): which PHP version to use. For example `"8.4"`, `"8.x"` or `latest`.
- `COMPOSER_AUTH_TOKEN` (**required**): the GitHub authentication token. Supports both Classic and Fine-grained tokens.

## Contributing

If you want to contribute a new pipeline, please check the reusable workflow guidelines in the
[GitHub documentation](https://docs.github.com/en/actions/using-workflows/reusing-workflows#creating-a-reusable-workflow).

## License

This repository is released under the EUPL 1.2 license. See [LICENSE](./LICENSE) for details.

## Part of iCore

This package is part of the iCore project.
