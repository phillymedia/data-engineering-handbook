# GitHub

## Dependabot

In order to keep our applications secure and robust, it is important that we keep their dependencies up-to-date with the latest bugfixes and security updates. We leverage GitHub's [Dependabot](https://github.com/dependabot) tool to scan our repositories, detect available updates to our dependencies, and submit PRs to perform these updates. The associated config file can be found in our repositories at `.github/dependabot.yml`.

Notably, even with our CI/CD checks, merging these PRs manually incurs significant overhead, as merging a single Dependabot PR triggers a rebase of all other open Dependabot PRs. To address this, we also employ [Dependbot's GitHub Actions library](https://github.com/dependabot/fetch-metadata#enabling-auto-merge) to [automatically merge](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/automatically-merging-a-pull-request) any Dependabot PRs that perform a minor or patch upgrade. 

Due to the possibility of introducing backwards-incompatible changes, PRs that include version updates are deserving of special attention, and so these PRs will not be merged automatically. 

The associated config file can be found in our repositories at  `.github/workflows/dependabot_auto_merge.yml`

Note that a minor limitation of this approach is that the auto-merge functionality requires a [Github personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token), which makes it appear as if an individual merged the pull request when in fact it was performed automatically.