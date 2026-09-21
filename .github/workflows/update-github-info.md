---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:

network:
  allowed:
    - defaults
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[github-info] "
    labels: [documentation]
---

# Update GitHub Info

Maintain the GitHub Info content for Mona.

1. Read `notes/mona-notes.md` before making any changes.
2. Use the GitHub repository API tools to read repository guidance and reference files that inform this update. Do not use terminal, CLI, or sandboxed shell commands for repository guidance or reference-file reads.
3. Use the `web-fetch` tool to read both `https://github.blog/latest/` and `https://github.blog/changelog/`.
4. Identify recent GitHub Blog and Changelog items that are useful for developers learning GitHub. Prefer accurate, practical updates over filling space.
5. Update `site/content/github-info.md` with concise summaries and source links. Preserve the existing editorial angle and mention whether each item comes from the GitHub Blog or GitHub Changelog.
6. Review the final diff and request a draft pull request with the changes for Mona to review. Do not write directly to `main` and do not modify files outside the requested content file.
