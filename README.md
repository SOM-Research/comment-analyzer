# Analyze Comments GitHub Action

This GitHub Action analyzes comments in issues, pull requests, and discussions, and performs actions in the repository based on the analysis.

--- 

## Features

- Analyzes comments in issues, pull requests, and discussions.
- Automatically handles comments by posting responses or deleting inappropriate comments.
- Integrates with an external analysis server to determine the nature of the comment.
- Sends email notifications based on the analysis results.

---

## Inputs

- `github_token` **(required)**: GitHub token for authentication.
- `server_url` **(required)**: URL of the analysis server.
- `sendinblue_api_key` **(required)**: Sendinblue API key for sending email notifications.
- `email_from` **(required)**: Sender email address for notifications.
- `email_to` **(required)**: Recipient email address for notifications.
- `bot_user` **(required)**: GitHub username of the bot.
- `bot_token` **(required)**: GitHub token of the bot for performing comment actions.
- `comment_json` **(required)**: Path to the comment JSON file.
- `flags` **(required)**: Flags from the analysis.

---

## Example Comment JSON

```json
{
  "type": "comment",
  "data": {
    "comment_id": "2258055095",
    "user": "username",
    "user_id": "user_id",
    "user_avatar_url": "https://avatars.githubusercontent.com/u/user_id?v=4",
    "user_html_url": "https://github.com/username",
    "user_type": "User",
    "event_type": "issue",
    "event_number": "4",
    "event_title": "Sample issue title",
    "event_body": "Describe the issue or problem you detected",
    "comment_body": "Sample comment body",
    "created_at": "2024-07-30T10:49:28Z",
    "updated_at": "2024-07-30T10:49:28Z",
    "event_url": "https://github.com/username/repo/issues/4",
    "comment_url": "https://github.com/username/repo/issues/4#issuecomment-2258055095",
    "repository_name": "username/repo",
    "repository_full_name": "",
    "repository_html_url": ""
  }
}
```
---

### How It Works
1. **Checkout Repository**: The action checks out the repository to get the latest code and context.
2. **Save Comment Details**: The action saves the details of the comment to a JSON file.
3. **Send for Analysis**: The comment details are sent to an external server for analysis.
4. **Determine Action**: Based on the analysis, the action determines if the comment should be deleted or responded to.
5. **Perform Action**: If required, the BigBOSS-SOM bot will delete the comment or post a positive response.
6. **Send Email Notification**: Sends an email notification with the analysis results.

---

## Example Scenario
- **Positive Comment**: The action will post a predefined positive response.
- **Inappropriate Comment**: The action will delete the comment based on the analysis results.

---
## Permissions
This action requires the following permissions:

- `contents: write`
- `issues: write`
- `pull-requests: write`
- `discussions: write`
- `actions: read`

Ensure these permissions are set in your workflow.

---

## License
This work is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.

The CC BY-SA license allows users to distribute, remix, adapt, and build upon the material in any medium or format, so long as attribution is given to the creator. The license allows for commercial use. If you remix, adapt, or build upon the material, you must license the modified material under identical terms.

[Creative Commons License](https://creativecommons.org/licenses/by-sa/4.0/)

