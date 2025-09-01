# Release Tools

This project contains, or should contain, all of the configuration and automation to maintain, build, and release Trustification projects.

Check out the [config.yaml](./pkg/config/config.yaml) to see:

1. The repositories we are managing
1. The Labels we are configuring in repositories
1. The milestones we are configuring in repositories

This allows us to have a single source of truth to make sure that, as we create
enhancments, issues, and pull requests, they can be tracked properly.

You can find our reusable GitHub Workflows in [./.github/workflows](./.github/workflows).

## Reusable Actions

### [backport](./.github/workflows/backport.yaml)

Allows backporting changes of a PR into another branch. Requires the `backport/branch_name` label to be set to the PR.

To use it, Opt-in adding this action to your repository:

```yaml
name: PR Closed

on:
  pull_request_target:
    branches:
      - main
    types:
      - closed

jobs:
  backport_job:
    permissions:
      pull-requests: write
      contents: write
    if: github.event.pull_request.merged == true
    secrets: inherit
    uses: guacsec/release-tools/.github/workflows/backport.yaml@main
```