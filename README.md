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



