# Heartbeat 💓

Never miss a beat. Automatically surface and summarize what's actually happening in your codebase, powered by GitHub Agentic Workflows.

**[Landing page](https://e-straight.github.io/heartbeat/)** · Built with [gh-aw](https://github.com/github/gh-aw): distributable agentic workflows for GitHub.

## Quick start 🚀

```sh
# Install the gh-aw extension
gh extension install github/gh-aw

# Add the workflows to your repo
gh aw add-wizard e-straight/heartbeat/reporting e-straight/heartbeat/daily-summary

# Set your project board URL (run from inside your repo)
repo=$(gh repo view --json nameWithOwner -q .nameWithOwner)
gh variable set GH_AW_TARGET_PROJECT \
  -b "https://github.com/users/YOUR_USER/projects/YOUR_PROJECT_NUMBER" \
  -R "$repo"

# Set a personal access token with project + read:org scopes
gh aw secrets set GH_AW_PROJECT_GITHUB_TOKEN --value "ghp_your_token_here"

# Commit and push
git add .github/workflows/
git commit -m "Add reporting workflow"
git push
```

## Workflows

### Reporting

Event-driven status updates. Every meaningful repository event — PR merges, reviews, issue changes, comments, releases — triggers an AI-generated status update on your GitHub Project board.

### Daily Summary

A nightly digest of all status updates from the past 24 hours, grouped by category (PRs, Issues, Releases). Runs on a cron schedule at midnight Pacific (08:00 UTC) and posts a scannable summary to your project board.

## Prerequisites 📋

- [GitHub CLI](https://cli.github.com) (`gh`) v2.0+
- The [`gh-aw`](https://github.com/github/gh-aw) extension
- A [GitHub Project](https://docs.github.com/en/issues/planning-and-tracking-with-projects) (v2)
- A [personal access token](https://github.com/settings/tokens/new?description=gh-aw-reporting&scopes=project,read:org) with `project` and `read:org` scopes

## License

MIT
