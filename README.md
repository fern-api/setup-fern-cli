<p align="center">
  <a href="https://buildwithfern.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/dugofqzck/image/upload/v1687829491/fern/intro-fern-dark_zirnuq.png" />
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/dugofqzck/image/upload/v1687829489/fern/intro-fern-light_nkwbf7.png" />
      <img alt="Fern" src="https://res.cloudinary.com/dugofqzck/image/upload/v1687829489/fern/intro-fern-light_nkwbf7.png" width="300" />
    </picture>
  </a>
</p>

<p align="center">
  <a href="https://github.com/fern-api/setup-fern-cli/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-Apache%202.0-blue" alt="Apache 2.0 license" />
  </a>
  <a href="https://github.com/marketplace/actions/setup-fern-cli">
    <img src="https://img.shields.io/badge/GitHub%20Marketplace-Setup%20Fern%20CLI-green" alt="GitHub Marketplace" />
  </a>
  <a href="https://discord.com/invite/JkkXumPzcG">
    <img src="https://img.shields.io/badge/discord-join-7289DA?logo=discord&logoColor=white&labelColor=7289DA" alt="Join Discord" />
  </a>
</p>

<p align="center">
  A GitHub Action that installs the <a href="https://github.com/fern-api/fern">Fern CLI</a> in your workflow — so you can generate SDKs and docs on every push.
</p>

---

## Requirements

Node.js and npm must be available before this action runs. Add [`actions/setup-node`](https://github.com/actions/setup-node) as a prior step if your runner doesn't include them by default.

## Usage

Use the major version tag (e.g. `@v1`) to automatically receive the latest updates:

```yaml
- uses: actions/setup-node@v4
  with:
    node-version: "lts/*"

- uses: fern-api/setup-fern-cli@v1
```

### With a specific version

```yaml
- uses: fern-api/setup-fern-cli@v1
  with:
    version: "3.81.0"
```

## Inputs

| Input     | Description                                      | Default  |
| --------- | ------------------------------------------------ | -------- |
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

      - uses: fern-api/setup-fern-cli@v1

      - run: fern generate
```

## Releasing

Tag the commit and publish a GitHub Release:

```sh
git tag v1.0.1
git push origin v1.0.1
gh release create v1.0.1 --generate-notes
```

The [release workflow](.github/workflows/release.yml) automatically moves the major version tag (e.g. `v1`) to the new release so users pinned to `@v1` get the update immediately.

---

<p align="center">
  Built with 🌿 by <a href="https://buildwithfern.com">Fern</a>
</p>
