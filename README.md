# Major Version Tag GitHub Action

This repository provides a reusable GitHub Action for updating a repo's major version tag (:saluting_face:). For example, when triggered for a new tag `v1.2.3`, this will create or update the `v1` tag to point to `v1.2.3`. The primary intended use case is GitHub Action repo's, to align with the [versioning recommendations](https://github.com/actions/toolkit/blob/master/docs/action-versioning.md#recommendations).

## Usage

To use the action, add it to a workflow in your repository:

```yml
name: Major version tag

on:
  workflow_dispatch:
  push:
    tags: ["v[0-9]+.*"]

jobs:
  major-version-tag:
    name: Major version tag
    permissions:
      contents: write
    runs-on: ubuntu-24.04
    steps:
      - name: Checkout repository
        uses: actions/checkout@v5

      - name: Create or update major version tag
        uses: minvws/action-major-version-tag@v1
```

Please note that this actions requires the `contents: write` permission.

In this basic example, the workflow is executed automatically whenever a `v[0-9]+.*` tag is pushed. And thanks to the `workflow_dispatch` trigger it can also be executed manually from the repository's Actions tab.

### Configuration

This action has no inputs.

## Contribution

If you plan to make non-trivial changes, we recommend to open an issue beforehand where we can discuss your planned changes.
This increases the chance that we might be able to use your contribution (or it avoids doing work if there are reasons why we wouldn't be able to use it).

Git commits must be signed. Please check the [Signing commits documentation on GitHub](https://docs.github.com/en/github/authenticating-to-github/signing-commits).

## License

This repository is released under the EUPL 1.2 license. [See LICENSE.txt](./LICENSE.txt) for details.

## Part of iCore

This package is part of the iCore project.
