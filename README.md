# action_dart_dependency_updater

Updates the dependencies of a Dart / Flutter repo automatically and optionally 

## Inputs

Name           | Default    | Description
---------------|------------|-------------
`branch`       | `main`     | Branch to check for the dependencies
`channel`      | `stable`   | Dart / Flutter channel to use for the build
`paths`        | `.`      | (Optional) Comma delimited list of paths
`merge`        | `true`     | (Optional) Set to `true` to automatically merge the PR when status checks pass, set to `false` otherwise
`pull_request` | `true`     | (Optional) Set to `true` to automatically create a pull request when paths change, set to `false` otherwise
`repository`   | n/a        | The `owner/repo` GitHub repository combination
`token`        | n/a        | Access token for GH.  Typically: `${{ secrets.GITHUB_TOKEN }}`


## Example usage

```yaml
name: Update Dart / Flutter dependencies

on:
  schedule:
    - cron: "0 0 * * 0"

jobs:
  dependencies:
    runs-on: ubuntu-latest

    steps:
      - name: Dependencies
        uses: peiffer-innovations/action-dart-dependency-updater@v1.0.5
        with:
          merge: true
          pull_request: true
          repository: ${{ github.action_repository }}
          token: ${{ secrets.GITHUB_TOKEN }}
```

