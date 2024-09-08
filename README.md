# GAWG Quality Action

This GitHub Action is used to analyze the quality of the code using SonarCloud.

## Inputs

### `config-json`

**Required** JSON string containing workflow config parameters.

### `github-token`

**Required** GitHub token for authentication.

### `sonar-token`

**Required** SonarCloud token for authentication.

## Example Usage

```yaml
name: CI

on: [push]

jobs:
  quality:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Run GAWG Quality Action
      uses: alvarogarciapiz/gawg-quality@main
      with:
        config-json: '{"SONAR":"enabled","SONAR_ORGANIZATION":"your_organization","SONAR_PROJECTKEY":"your_project_key","SONAR_PROJECTBASEDIR":"./","SONAR_EXTRA_ARGS":""}'
        github-token: ${{ secrets.GITHUB_TOKEN }}
        sonar-token: ${{ secrets.SONAR_TOKEN }}
````
## What It Does
1. Checks if SonarCloud scan is enabled.
2. Validates the presence of required SonarCloud configuration parameters.
3. Runs the SonarCloud scan if all parameters are set and the scan is enabled.
