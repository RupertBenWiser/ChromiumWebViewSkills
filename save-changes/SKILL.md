---
name: save-changes
description: >
    This is what you should do whenever you are ready to save
    any changes for review.
---

When you are getting ready to save changes, first add all changes where
necessary to git staging and then run `git cl format`.

Chromium relies on internal git alias commands that you can use.
Chromium uses git so you can first prepare a commit using `git commit`
like most git projects should.

If a bug ID has been provided, please include in the git message with
the following line at the end of the commit: `Bug: <ID>`

