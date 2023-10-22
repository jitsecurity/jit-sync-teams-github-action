# Create Teams GitHub Action

This GitHub Action creates teams in Jit using the [jit-customer-scripts](https://github.com/jitsecurity/jit-customer-scripts) repo.\
You need to provide the following inputs, which we recommend storing in GitHub Secrets:


## Inputs

* `JIT_CLIENT_ID`: The JIT Client ID.
* `JIT_CLIENT_SECRET`: The JIT Client Secret.
* `ORGANIZATION_NAME`: The name of the GitHub organization.
* `GITHUB_API_TOKEN`: The GitHub Personal Access Token.
* `TEAM_WILDCARD_TO_EXCLUDE`: A wildcard team name to exclude from the teams that are created.

## Outputs

None.

## Example
```
name: Sync Jit Teams
on:
  schedule:
    - cron: "0 3 * * *"
  workflow_dispatch:

jobs:
  sync-teams:
    runs-on: ubuntu-latest
    steps:
    - name: Check out code
      uses: actions/checkout@v3
    - name: Call action
      uses: jitsecurity/jit-sync-teams-github-action@v1.1.0
      with:
        JIT_CLIENT_ID: ${{ secrets.JIT_CLIENT_ID }}
        JIT_CLIENT_SECRET: ${{ secrets.JIT_CLIENT_SECRET }}
        ORGANIZATION_NAME: ${{ github.repository_owner }}
        GITHUB_API_TOKEN: ${{ secrets.MY_GITHUB_API_TOKEN }}
        TEAM_WILDCARD_TO_EXCLUDE: "*dev*, *test*"
```
