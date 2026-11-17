---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
permissions:
  contents: read
  copilot-requests: write
strict: true
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
safe-outputs:
  create-pull-request:
    max: 1
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
    base-branch: main
    allowed-files:
      - site/content/github-info.md
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:

- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update `site/content/github-info.md` with concise, practical updates for readers. Verify details from the official sources, avoid duplicating existing content, and include source context and links for Blog or Changelog updates.

Open a pull request for Mona to review. Use a pull request title that mentions Mona or GitHub Info. Use `safe-outputs` with `create-pull-request`; do not write directly to `main` or merge the pull request. If there are no relevant, verifiable updates, leave the file unchanged and call `noop` with a brief reason.
