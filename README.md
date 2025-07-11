# PHP - Composer install

- This pipeline is designed to install the dependencies of a PHP project that uses Composer. 
It will install the dependencies and cache them for future runs.
- The pipeline is designed to be as generic as possible, so they can be easily reused in any project.
- This repository is a part of the generic GitHub Actions pipeline collection that can be used in any project.

## Usage

Here is a basic example of how you can integrate it in your project.

<details>
  <summary>Example workflow</summary>

This workflow is executed automatically on push to the main branch, on a pull request and can also be executed manually from the actions tab `workflow_dispatch`.

In the code below you need to replace `<php_version>` with the PHP version you want to use. For example `8.3` (default) or `8.4`.

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

      # Using the action
      - name: Install dependencies
        uses: minvws/action-php-composer-install/.github/actions/composer-install@main
        with:
          COMPOSER_AUTH_TOKEN: ${{ secrets.REPO_READ_ONLY_TOKEN }}
          php_version: <php_version>
```

</details>

### Configuration

The action has inputs. The inputs are:

- php_version: Semver version of the PHP version you want to use. For example `8.2` or `8.3`.

## Contributing

If you want to contribute a new pipeline, please check the reusable workflow guidelines in the
[GitHub documentation](https://docs.github.com/en/actions/using-workflows/reusing-workflows#creating-a-reusable-workflow).
