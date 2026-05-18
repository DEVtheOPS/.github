# DEV'n the OPS before it was cool

## Reusable workflows

This repository hosts shared GitHub Actions workflows for the `DEVtheOPS` organization.

### Discord notifications

Use `.github/workflows/discord-notify.yml` from any repository in the org to post rich Discord webhook embeds for GitHub events.

Example consumer workflow:

```yaml
name: Discord Events

on:
  issues:
    types: [opened]
  pull_request:
    types: [opened]
  release:
    types: [published]

jobs:
  notify-discord:
    uses: DEVtheOPS/.github/.github/workflows/discord-notify.yml@main
    with:
      username: DEVtheOPS Bot
      title_prefix: "[DEVtheOPS]"
      include_body: true
    secrets:
      discord_webhook: ${{ secrets.DISCORD_WEBHOOK }}
```

Supported inputs:

- `username`
- `avatar_url`
- `title_prefix`
- `include_body`
- `color`

Required secret:

- `discord_webhook`
