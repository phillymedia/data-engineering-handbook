## Pull Requests

Work on the data engineering team is most often delivered via a [pull request](communication.md#everything-starts-with-a-pull-request), or PR, allowing for discussions around a actionable proposed solution to a problem.

### Submitting Pull Requests

Unless [indicated otherwise](pull-requests.md#draft-pull-requests), when you submit a PR, you are acknowledging that the PR may be deployed to production at any time, provided that it passes the [merge requirements](pull-requests.md#merging-pull-requests).

You may add a `DO NOT MERGE` [label](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/managing-labels) to the PR in instances where you want to defer the deployment of the PR. An example of such an instance would be when a deliverable piece of work requires multiple interdependent PRs to be merged and deployed in a particular order.

#### Linking PRs to JIRA

In order for JIRA to detect that a ticket has a linked PR, you must use one of the following [linkage methods](https://github.com/atlassian/github-for-jira/blob/main/README.md#see-github-development-information-in-jira):

* [Preferred] Give your development branch a name that begins with the JIRA issue key (e.g. `DI-123_add-columns`).
* Include the JIRA issue key in a commit message.
* Include the JIRA issue key in the title of the PR.

#### Soliciting Reviews and Approvals for Pull Requests

At least one approving peer review is required in order for a PR to be merged. When submitting a PR, add the Data Engineering team (`phillymedia/data-engineering`), the Analytics team (`phillymedia/analytics`), or both teams as a reviewers. When choosing PR reviewers, consider the expertise of each team and the sort of feedback you are trying to solicit. If you are seeking a particular person's subject matter expertise, then you may add them individually as a reviewer. Note that some repositories have a [`CODEOWNERS`](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners) file which will automatically assign a reviewer depending on the files changed in the PR.

#### Draft Pull Requests

In order to receive timely feedback on in-progress work, developers need not wait for their work to be 100% complete before submitting a pull request. In these instance, developers are encouraged to submit a [draft pull request](https://github.blog/2019-02-14-introducing-draft-pull-requests/) and solicit feedback on the draft PR.

### Merging Pull Requests

For all GitHub repositories owned by the Data Engineering team, merging PRs to the main branch will be blocked until the following conditions are met:
1. The PR passes an automated CI/CD status check
2. The PR receives at least one approval

For each of these repositories, authors can elect to automatically merge the PR when conditions 1. and 2. above are met by clicking "Squash and merge via auto-merge" when submitting a pull request. In the interest of agility and iteration, PRs should not remain open for extended period of time. As such, it’s **strongly recommended** that PR authors enable auto-merge upon submitting the PR. 

