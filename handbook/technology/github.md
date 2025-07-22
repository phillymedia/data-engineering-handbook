# GitHub

## Dependabot

In order to keep our applications secure and robust, it is important that we keep their dependencies up-to-date with the latest bugfixes and security updates. We leverage GitHub's [Dependabot](https://github.com/dependabot) tool to scan our repositories, detect available updates to our dependencies, and submit PRs to perform these updates. The associated config file can be found in our repositories at `.github/dependabot.yml`.

Notably, even with our CI/CD checks, merging these PRs manually incurs significant overhead, as merging a single Dependabot PR triggers a rebase of all other open Dependabot PRs. To address this, we also employ [Dependbot's GitHub Actions library](https://github.com/dependabot/fetch-metadata#enabling-auto-merge) to [automatically merge](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/automatically-merging-a-pull-request) any Dependabot PRs that perform a minor or patch upgrade. 

Due to the possibility of introducing backwards-incompatible changes, PRs that include version updates are deserving of special attention, and so these PRs will not be merged automatically. 

The associated config file can be found in our repositories at  `.github/workflows/dependabot_auto_merge.yml`

Note that a minor limitation of this approach is that the auto-merge functionality requires a [Github personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token), which makes it appear as if an individual merged the pull request when in fact it was performed automatically.

## Token Refreshes

Several of our repositories use services that require enhanced GitHub permissions. We provision this access via [GitHub personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens). For security purposes, we generally configure these tokens to expire after 90 days. When the tokens are set to expire, we mint new tokens and substitute them into the appropriate [repository secret](https://docs.github.com/en/actions/how-tos/writing-workflows/choosing-what-your-workflow-does/using-secrets-in-github-actions#creating-secrets-for-a-repository).  The following list outlines which repository services need GitHub tokens, the name of the secret where the token is stored, and the type of token required (either classic or fine-grained):

* [inquirer-dbt](https://github.com/phillymedia/inquirer-dbt)
  * [Actions](https://github.com/phillymedia/inquirer-dbt/settings/secrets/actions)
    * `ADMIN_PAT` (fine-grained token)
    * `DEPENDABOT_GITHUB_TOKEN` (classic token)
  * [Codespaces](https://github.com/phillymedia/inquirer-dbt/settings/secrets/codespaces)
    * `DBT_GIT_TOKEN` https://github.com/phillymedia/inquirer-dbt/pull/1172
  * [Dependabot](https://github.com/phillymedia/inquirer-dbt/settings/secrets/dependabot)
    * `ADMIN_PAT` (fine-grained token)
  * [inq-warehouse-dags](https://github.com/phillymedia/inq-warehouse-dags)
    * [Actions](https://github.com/phillymedia/inq-warehouse-dags/settings/secrets/actions)
      * `DEPENDABOT_GITHUB_TOKEN` (classic token)
  * [inq-data-resources](https://github.com/phillymedia/inq-data-resources)
    * [Actions](https://github.com/phillymedia/inq-data-resources/settings/secrets/actions)
      * `DEPENDABOT_GITHUB_TOKEN` (classic token)

### Token permissions
In order to function properly, the tokens stored in the secrets listed above need the following permissions:

* `ADMIN_PAT`
  * Access to the [phillymedia/inquirer-dbt](https://github.com/phillymedia/inquirer-dbt) repository
  * **Read** access to metadata and secrets 
  * **Read** and **Write** access to actions, code, commit statuses, pull requests, and workflows
* `DEPENDABOT_GITHUB_TOKEN`
  * repo (Full control of private repositories)