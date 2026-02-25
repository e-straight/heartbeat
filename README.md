# Heartbeat 💓

Never miss a beat. Automatically surface and summarize what's actually happening in your codebase, powered by GitHub Agentic Workflows.

**[Landing page](https://e-straight.github.io/heartbeat/)** · Built with [gh-aw](https://github.com/github/gh-aw): distributable agentic workflows for GitHub.

## Quick start 🚀

```sh
# Install the gh-aw extension
gh extension install github/gh-aw

# Add the workflow to your repo
gh aw add-wizard e-straight/heartbeat/heartbeat

# Set your project board URL (run from inside your repo)
repo=$(gh repo view --json nameWithOwner -q .nameWithOwner)
gh variable set GH_AW_TARGET_PROJECT \
  -b "https://github.com/users/YOUR_USER/projects/YOUR_PROJECT_NUMBER" \
  -R "$repo"

# Set a personal access token with project + read:org scopes
gh aw secrets set GH_AW_PROJECT_GITHUB_TOKEN --value "ghp_your_token_here"

# Commit and push
git add .github/workflows/
git commit -m "Add heartbeat workflow"
git push
```

## What it tracks 📡

- **PR merged**: summarizes the change, author, reviewers, and target branch
- **PR closed without merge**: notes it wasn't merged and why
- **PR opened**: notes when new work begins with author and branch info
- **PR ready for review**: signals when a draft PR is ready for feedback
- **Review requested**: tracks who's being asked to review
- **Review submitted**: captures approvals, change requests, and review comments
- **Inline review comment**: tracks line-level code review feedback with file path context
- **Issue closed**: captures resolution, who closed it, and assignees
- **Issue edited**: reports what changed (title, body, labels)
- **Comments**: summarizes new comments on issues and PRs with a direct link
- **Release published**: summarizes shipped releases with tag and changelog

## Prerequisites 📋

- [GitHub CLI](https://cli.github.com) (`gh`) v2.0+
- The [`gh-aw`](https://github.com/github/gh-aw) extension
- A [GitHub Project](https://docs.github.com/en/issues/planning-and-tracking-with-projects) (v2)
- A [personal access token](https://github.com/settings/tokens/new?description=gh-aw-heartbeat&scopes=project,read:org) with `project` and `read:org` scopes

## License

MIT
