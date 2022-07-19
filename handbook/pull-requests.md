## Pull Requests

Work on the data engineering team is most often delivered via a [pull request](communication.md#everything-starts-with-a-pull-request), or PR, allowing for discussions around a actionable proposed solution to a problem.

### Submitting Pull Requests

Unless [indicated otherwise](pull-requests.md#draft-pull-requests), when you submit a PR, you are acknowledging that the PR can be safely deployed to production at any time, by any individual with write access to the associated GitHub repository. 

You may also add a `DO NOT MERGE` [label](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/managing-labels) to the PR in instances where you want to defer the deployment of the PR. An example of such an instance would be when a deliverable piece of work requires multiple interdependent PRs to be merged and deployed in a particular order.

#### Linking PRs to JIRA

In order for JIRA to detect that a ticket has a linked PR, you must use one of the following [linkage methods](https://github.com/atlassian/github-for-jira/blob/main/README.md#see-github-development-information-in-jira):

* [Preferred] Give your development branch a name that begins with the JIRA issue key (e.g. `DI-123_add-columns`).
* Include the JIRA issue key in a commit message.
* Include the JIRA issue key in the title of the PR.

#### Soliciting Reviews and Approvals for Pull Requests

Given that the PR author is accountable for the PR's impact, and it is at the developer's discretion whether to request PRs reviews from stakeholder and other team members. Not all PRs will require reviews or explicit approvals, but we should be prudent when soliciting feedback to ensure that we are producing quality work that satisfies the requirements of our stakeholders.

#### Draft Pull Requests

In order to receive timely feedback on in-progress work, developers need not wait for their work to be 100% complete before submitting a pull request. In these instance, developers are encouraged to submit a [draft pull request](https://github.blog/2019-02-14-introducing-draft-pull-requests/) and solicit feedback on the draft PR.

### Merging Pull Requests

In the interest of agility and iteration, PRs should not remain open for extended period of time. If you have reviewed and approved a PR that does not require any further changes, you should also merge the PR (unless the PR is labeled `DO NOT MERGE`).

