# workflow-sandbox

Sandbox environment for learning how to use github actions

## The Reality

Actions executed from a workflow will not trigger other workflows.

## The Issue

If there's an auto-code formatting workflow that commits code, then
other workflows won't be triggered by that code commit, which is
problematic on a branch that requires checks to run.

## Workarounds

Github is already aware of this issue and confirm that this is expected
behavior. Basically every action during a workflow, behind the scenes,
uses a token called `GITHUB_TOKEN`. Actions taken by workflows using this
token will not trigger other workflows to run.

Here are possible workarounds for this issue:

1. Disable branch protection rules / required checks
2. ~~Add functionality to run the workflows manually~~ **(DOES NOT WORK)**
3. Use a Personal Access Token (PAT) **(RECOMMENDED BY GITHUB)**
4. Create a Github App with the necessary permissions
