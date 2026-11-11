---
name: update-github-info
description: Draft updates for Mona's GitHub Info website from official GitHub sources.
on:
  schedule:
    - cron: "17 9 * * *"
  workflow_dispatch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
    base-branch: main
    allowed-files:
      - site/content/github-info.md
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
engine:
  id: copilot
  copilot-sdk: true
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making any changes. Review
`site/content/github-info.md` and keep updates concise, practical, and consistent
with its existing themes.


Use web-fetch to review these sources:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` only. Include clear source context for
information from the GitHub Blog or GitHub Changelog. Do not invent updates or
make changes when there is nothing useful to add.

When you make a meaningful update, open a draft pull request for Mona to review.
Use a title that mentions Mona or GitHub Info, and describe the changes and their
official sources. Do not write directly to `main`; use the configured
`safe-outputs` `create-pull-request` operation.
