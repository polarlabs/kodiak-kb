# Create a GitHub repo

This article describes how to create a GitHub repo.

## Prerequisites

Think about this before you start creating a repository.

- Name
- Description
- Public / Private: In general, we use public repos.
- License: We choose MIT license for all contributions to the community.

**Note:** Don't set the license when creating the repository. It's preferred to set the license by adding a license file to the repo root. 
See [Define a license](define-a-license.md) for more details.

## General Settings

To ensure that contributors are aware of and agree with [Developer Certificate of Origin](https://developercertificate.org/) 
enable *Require contributors to sign off on web-based commits*.

### Features

Based on a repo, GitHub supports various features. Consider which features your project benefits from. For public code repositories 
without much project management, the following features are in general reasonable.

- Issues
- Preserve this repository

### Pull Requests

Enable *Allow squash merging* as the only merge strategy. This keeps the repos commit history concise. Set the default of the 
merge commit message to *Default to pull request title*.

**Disable all other merge strategies.**

Set *Always suggest updating pull request branches* to notify pull requests about any commits on the base branch. 

In general, it makes sense to delete branches when the pull request has been merged. Set *Automatically delete head branches* to 
automate this step.

## Access Settings

By default, the access settings are configured correctly. Under *Moderation options > Reported content*, allow 
*All users* to report abusive or disruptive content.

## Code and Automation

**Note:** Some of these settings are only available when there is already code in the repo.

### Branches

Branch protection rules are only available when there is at least one branch in the repo.

At Kodiak, it's best practice to enforce signed commits. So, we create a rule with the following settings:

- Branch name pattern: *
- Require signed commits: checked
- Do not allow bypassing the above settings: checked

Another best practice is to raise pull requests which need approval instead of pushing directly to the 
*main* branch while maintaining a linear history. So, we create another rule. Again, we do not allow anyone 
to bypass these settings.

- Branch name pattern: main
- Require a pull request before merging: checked
  - Require approvals: checked
  - Dismiss stale pull request approvals when new commits are pushed: checked
- Require linear history: checked
- Do not allow bypassing the above settings: checked

## Code Security and Analysis

Allow your community to report any security concerns privately to maintainers and repository owners by enabling 
*Private vulnerability reporting*.

### Dependabot

With Dependabot, we keep our dependencies secure and up-to-date. Enable all the following features. Have a look at 
[Working with Dependabot](working-with-dependabot.md) for more details.

- Dependabot alerts
- Dependabot security updates
- Dependabot version updates (enabled by committing *.github/dependabot.yml* within the repo)

## Integrate with Codecov

WIP

# Links

[Developer Certificate of Origin](https://developercertificate.org/)
