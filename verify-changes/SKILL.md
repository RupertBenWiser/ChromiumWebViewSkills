---
name: verify-changes
description: >
    This skill describes how to verify chromium changes don't have any obvious
    coding issues.
---

Whenever you are getting ready to verify a change, run `autoninja -C out/Default system_webview_apk`
in order to to see if the project builds correctly and if there are any linting issues.
