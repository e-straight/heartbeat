# Heartbeat 💓

AI-powered project board updates for GitHub. When PRs merge, issues close, or comments are posted, Heartbeat writes a concise status summary to your GitHub Project.

Built with [gh-aw](https://github.com/github/gh-aw) — distributable agentic workflows for GitHub.

## Quick start 🚀

```sh
# Install the gh-aw extension
gh extension install e-straight/gh-aw

# Add the workflow to your repo
gh aw add-wizard e-straight/heartbeat/heartbeat

# Set your project board URL
gh aw secrets set GH_AW_TARGET_PROJECT \
  --value "https://github.com/users/YOUR_USER/projects/YOUR_PROJECT_NUMBER"

# Set a personal access token with project + read:org scopes
gh aw secrets set GH_AW_PROJECT_GITHUB_TOKEN --value "ghp_your_token_here"

# Commit and push
git add .github/workflows/
git commit -m "Add heartbeat workflow"
git push
```

## What it tracks 📡

- **PR merged** — summarizes the change, author, reviewers, and target branch
- **PR closed without merge** — notes it wasn't merged and why
- **Issue closed** — captures resolution, who closed it, and assignees
- **Issue edited** — reports what changed (title, body, labels)
- **Comments** — summarizes new comments on issues and PRs with a direct link

## Prerequisites 📋

- [GitHub CLI](https://cli.github.com) (`gh`) v2.0+
- The [`gh-aw`](https://github.com/github/gh-aw) extension
- A [GitHub Project](https://docs.github.com/en/issues/planning-and-tracking-with-projects) (v2)
- A [personal access token](https://github.com/settings/tokens/new?description=gh-aw-heartbeat&scopes=project,read:org) with `project` and `read:org` scopes

## License

MIT
