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
