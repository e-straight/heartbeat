# Heartbeat — Agent Instructions

## Testing Workflows

All workflows live in `workflows/` and are compiled with `gh aw compile`. Before merging any PR that modifies workflows:

1. Ensure the workflow has a `workflow_dispatch:` trigger (required for `gh aw trial`)
2. Recompile: `gh aw compile --dir workflows`
3. Copy lock files: `cp workflows/*.lock.yml .github/workflows/`
4. Validate: `gh aw compile --dir workflows --strict --no-emit --validate --verbose` (must pass with 0 errors)
5. Run trials against representative events:

   ```bash
   # Test with a specific issue or PR as context
   gh aw trial ./workflows/<workflow>.md \
     -s e-straight/heartbeat \
     --trigger-context <issue-or-pr-url> \
     --verbose --yes

   # Test daily summary (no trigger context needed)
   gh aw trial ./workflows/daily-summary.md \
     -s e-straight/heartbeat \
     --verbose --yes
   ```

6. Review trial output in `trials/*.json` — verify status is "completed" and safe outputs contain well-formed status updates
7. If trials fail due to missing variables in the temp repo, use `--host-repo .` instead of `-s`
