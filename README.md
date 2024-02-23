# Publish mkdocs Action

This action builds and publishes documentation generated via [mkdocs][]. It
uses [mike][] for handling multiple versions and [repo-config][] to calculate
the version number to use.

It is very tied to the [repo-config][] configuration and the [mike][] tool.

Here is an example demonstrating how to use it in a workflow:

```yaml
jobs:
  build:
    name: Build
    runs-on: ubuntu-20.04

    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      - name: Publish documentation
        uses: frequenz-floss/gh-action-publish-mkdocs@v0.x.x
        with:
          python_version: "3.11"
```

## Inputs

* `python_version`: The Python version to use. Required.

   This is passed to the `actions/setup-python` action.

* `mkdocs_dependencies`: The dependencies needed to run mkdocs, mike and
  repo-config. Optional. Default: ".[dev-mkdocs]"

* `github_token`: The GitHub token to use to fetch tag and branches information
  for the repository using the GitHub API. Optional. Default: `${{ github.token
  }}`.

[mkdocs]: https://www.mkdocs.org/
[mike]: https://github.com/jimporter/mike
[repo-config]: https://frequenz-floss.github.io/frequenz-repo-config-python/
