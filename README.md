# setup-fern-cli

A GitHub Action that installs the [Fern CLI](https://github.com/fern-api/fern) in your workflow.

## Requirements

Node.js and npm must be available before this action runs. Add [`actions/setup-node`](https://github.com/actions/setup-node) as a prior step if your runner doesn't include them by default.

## Usage

```yaml
- uses: actions/setup-node@v4
  with:
    node-version: "lts/*"

- uses: fern-api/setup-fern-cli@v1.0.0
```

### With a specific version

```yaml
- uses: fern-api/setup-fern-cli@v1.0.0
  with:
    version: "3.81.0"
```

## Inputs

| Input     | Description                              | Default  |
| --------- | ---------------------------------------- | -------- |
| `version` | Fern CLI version to install (`latest` or semver) | `latest` |

## Example workflow

```yaml
name: Generate SDKs

on:
  push:
    branches: [main]

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: "lts/*"

      - uses: fern-api/setup-fern-cli@v1.0.0

      - run: fern generate
```

## Releasing

Tag the commit and create a GitHub Release manually:

```sh
git tag v1.0.0
git push origin v1.0.0
gh release create v1.0.0 --generate-notes
```
