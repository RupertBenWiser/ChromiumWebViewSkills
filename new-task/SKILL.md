---
name: new-task
description: >
    Defines what to do whenever you start working on new changes.
    This should be done before you starting making any code changes.
---

Chromium has its own project aliases that come from depot.
Chromium relies on git but follows a trunk development flow.

Whenever you start making changes, first run `git new-branch <feature name>`
to separate your changes from any other changes.

If you need to stack changes, you can use `git new-branch --upstream-current <feature-name>`
on top of the current branch.

If you are working on a stacked change, but it is pointing to an out of date hash for its parent,
you will first need to rebase it to the new hash of the parent cl. Pull the parent branch, and then
rebase with `git rebase-update --no-fetch --tree <base-branch-of-stack>`.
