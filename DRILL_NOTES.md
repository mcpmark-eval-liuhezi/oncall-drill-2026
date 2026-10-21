# On-Call Drill Notes

This repository is a rehearsal for the runaway-job procedure before an on-call shift.

## What this drill covers

- Cutting a feature branch and committing a deliberately long-running workflow (`.github/workflows/stuck-job.yml`) that sleeps for 1800 seconds (30 minutes).
- Opening a pull request, merging it as a squash, and verifying the files landed in the merge commit.
- Watching the resulting workflow run reach a queued / in-progress state, then canceling every run of it that has not finished, as practice for killing a runaway CI job.

## Expected behavior

- The `stuck-job` workflow triggers on push (including the squash merge to the default branch) and on manual dispatch (`workflow_dispatch`).
- The single job simply runs `sleep 1800`, so it stays in progress long enough to be observed and canceled.
