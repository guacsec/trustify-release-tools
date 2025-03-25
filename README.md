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

- [cherry-pick](./.github/workflows/cherry-pick.yaml) .- Allows backporting changes of a PR into another branch. Requires the `cherry-pick/branch_name` label to be set to the PR.