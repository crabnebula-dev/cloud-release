# CrabNebula Cloud Release GitHub Action

This action wraps the CrabNebula Cloud CLI to be used as a GitHub Action.

The documentation for the CrabNebula Cloud can be found [here](https://docs.crabnebula.dev/). It includes information on [how to install the CLI](https://docs.crabnebula.dev/cloud/cli/) and how to use it as well as [example workflows](https://docs.crabnebula.dev/cloud/continuous-integration/) for this action.

## Example

```yml
name: Test Action

on:
  push:
    branches:
      - release

concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true

jobs:
  draft:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: create draft release
        uses: crabnebula-dev/cloud-release@v0.2.0
        id: draft
        with:
          command: release draft ${{ secrets.CN_APP_ID }} 0.1.0
          api-key: ${{ secrets.CN_API_KEY }}
```

## Licenses

MIT or MIT/Apache 2.0 where applicable.
