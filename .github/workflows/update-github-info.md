---
name: update-github-info
on: daily
permissions:
  contents: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    max: 1
---

# Update GitHub Info

Refresh Mona's GitHub Info content using current official sources.

1. Read `notes/mona-notes.md` before drafting anything.
2. Use the GitHub repository API tools to read repository guidance and reference files, including `site/content/github-info.md`. Do not use terminal, the GitHub CLI, or sandboxed shell commands for repository reads.
3. Use web-fetch to read https://github.blog/latest/.
4. Use web-fetch to read https://github.blog/changelog/.
5. Select useful, current items for developers and update `site/content/github-info.md` with short, practical summaries. Attribute every item to its GitHub Blog or GitHub Changelog source and include the original source URL.
6. Keep the existing editorial angle and Markdown structure unless a small structural change is needed for the new content.
7. Review the resulting diff for accuracy, relevance, and concise writing.
8. Use the `create_pull_request` safe-output tool to open one pull request containing the changes, with a clear title and summary for Mona to review. Never write directly to `main`.

If the official pages contain no useful new information, leave the content unchanged and still use the `create_pull_request` safe output only if there are meaningful changes to propose.
