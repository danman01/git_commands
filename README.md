## Intro

These are custom git commands that I've made and found useful. Read how to make one [here](https://dev.to/shobhit/git-refresh-4hn)

## Commands

### git mergeto

from the current working branch (feature, bugfix, etc), you can run `git mergeto <destination>` and specify the destination branch (dev, for example)

    - checks out destination branch
    - refreshes with origin
    - merges using --ff-only so as not to create a merge commit ( otherwise this script will fail )
    - pushes destination branch to origin
    - When finished, the script will prompt for current working branch deletion at the end of the process
    - if not deleted, checks back out to current working branch

#### options

--rebase

you can optionally rebase your working branch onto the destination branch before the merge. This will then allow a fast-forward merge. You will be prompted (y/N) to force push the rebased branch to the remote.


## PR and Release helpers

The following make use of a config file

The config file can be defined per-repo and / or in your home dir. It reads per-repo first, home dir as fallback same as .gitconfig local/global. The helper does the following:

  1. Load ~/.pr-config (global defaults)
  2. Source <repo-root>/.pr-config on top (overrides only what's specified)

  So a repo only needs to define what differs. If all your NCD repos share the same reviewers, put that in ~/.pr-config. A
  repo with a different main branch just overrides MAIN_BRANCH.

  ---

These commands have confirmation, especially important as git commands can actually release code.

Confirmation screen for git do-release:

  Repo:      ncd/shopping-cart-app
  Merging:   pre-release → main
  Approval:  NOT APPROVED

  Warning: PR not approved. Recommended to get approval before continuing.
  Continue without approval? (y/N): y

  Repo:      ncd/shopping-cart-app
  Merging:   pre-release → main
  Reviewers: Jim-John, dev-number-1-at-company
  Approval:  NOT APPROVED
  Commits:
    a1b2c3d fix: cart total calculation
    d4e5f6a feat: add promo code support

  Proceed with release merge? (y/N):

  If approved, the NOT APPROVED line becomes APPROVED and no warning prompt.


## git pre-pre-release

PR created for pre-release branch to run GH actions in prod-like environment

dev -> pre-release (if pre-release exists)

## git pre-release

PR created for final QA and signoff: 
pre-release -> main

## git do-release

actually does the merge using git mergeto (fast forward only)

## git pr

PR creation helper that sets up your feature branch to merge into dev ( or main if it doesn't exist...shame shame shame )

## git list-custom-commands 

to see all commands
