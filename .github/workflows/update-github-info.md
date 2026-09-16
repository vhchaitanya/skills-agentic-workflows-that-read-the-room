---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[github-info] "
---

# Update GitHub Info

Refresh the GitHub Info website content for Mona to review.

## Research

1. Read `notes/mona-notes.md` with the GitHub repository API tools. Follow its editorial guidance.
2. Read the current `site/content/github-info.md` with the GitHub repository API tools so the update preserves the existing structure and avoids repeating recent coverage.
3. Read any repository guidance or reference files needed for this task with the GitHub repository API tools. Do not use terminal, CLI, or sandboxed commands to read repository guidance or reference files.
4. Use `web-fetch` to read `https://github.blog/latest/`.
5. Use `web-fetch` to read `https://github.blog/changelog/`.
6. Use `web-fetch` to read `https://awesome-copilot.github.com/workflows/`.

## Update

Use the official GitHub Blog and GitHub Changelog sources to identify practical, current guidance that helps developers learn GitHub faster. Keep summaries short and practical, mention the source for every blog or changelog update, and preserve the existing Markdown style.

Use the `edit` tool to update `site/content/github-info.md` with only useful, source-backed changes. Review the resulting file for accuracy, clarity, and unnecessary duplication.

When the update is complete, use the `create-pull-request` safe output to open a draft pull request against the default branch for Mona to review. Include a concise title and body that summarize the changes and link to the official sources. Do not write directly to the default branch.