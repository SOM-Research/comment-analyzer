# Analyze Comments GitHub Action

This GitHub Action analyzes comments in issues, pull requests, and discussions, and performs actions in the repository based on the analysis.

## Features

- Analyzes comments in issues, pull requests, and discussions.
- Automatically handles comments by posting responses or deleting inappropriate comments.
- Integrates with an external analysis server to determine the nature of the comment.

## Inputs

- `github_token` **(required)**: GitHub token for authentication.
- `server_url` **(required)**: URL of the analysis server.

## Usage

To use this action in your workflow, include it as a step in your GitHub Actions workflow file. Below is an example configuration:

```yaml
name: Check Comments

on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]
  discussion_comment:
    types: [created]

jobs:
  check-comment:
    runs-on: ubuntu-latest
    steps:
      - name: Analyze Comments
        uses: SOM-Research/comment-analyzer@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          server_url: '{server_url}'
```

## How It Works
- **Checkout Repository**: The action checks out the repository to get the latest code and context.
- **Save Comment Details**: The action saves the details of the comment to a JSON file.
- **Send for Analysis**: The comment details are sent to an external server for analysis.
- **Determine Action**: Based on the analysis, the action determines if the comment should be deleted or responded to.
- **Perform Action**: If required, the action will delete the comment or post a positive response.

## Example Scenario
- **Positive Comment**: The action will post a predefined positive response.
- **Inappropriate Comment**: The action will delete the comment based on the analysis results.

## Permissions
This action requires the following permissions:

- `contents: write`
- `issues: write`
- `pull-requests: write`
- `discussions: write`
- `actions: read`

Ensure these permissions are set in your workflow.

## License
This work is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.

The CC BY-SA license allows users to distribute, remix, adapt, and build upon the material in any medium or format, so long as attribution is given to the creator. The license allows for commercial use. If you remix, adapt, or build upon the material, you must license the modified material under identical terms.

[Creative Commons License](https://creativecommons.org/licenses/by-sa/4.0/)

## Author
Created by CobosDS. For any issues or contributions, please open an issue or submit a pull request on the [GitHub repository](https://github.com/SOM-Research/comment-analyzer).
