# Create Teams GitHub Action

This action creates teams in JIT Security.

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
uses: jitsecurity/jit-create-teams-github-actions@v1
with:
JIT_CLIENT_ID: ${{ secrets.JIT_CLIENT_ID }}
JIT_CLIENT_SECRET: ${{ secrets.JIT_CLIENT_SECRET }}
ORGANIZATION_NAME: ${{ github.organization }}
GITHUB_API_TOKEN: secrets.GITHUBA​PIT​OKENTEAMW​ILDCARDT​OE​XCLUDE:"∗dev∗,∗test∗"ThiswillcreateteamsintheGitHuborganizationnamed‘{{ github.organization }}, excluding any teams that match the wildcard patterndev, test`.
Running in Python 3.9

To run this action in Python 3.9, you need to modify the runs section of the action as follows:

runs:
  using: "python3.9"

You also need to install the setup-python action, which will set up a Python environment with the specified version.

steps:
  - name: Setup Python
    id: setup-python
    uses: actions/setup-python@v2
     with:
       python-version: 3.9
```