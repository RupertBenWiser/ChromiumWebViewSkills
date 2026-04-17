---
name: verify-changes
description: >
    This skill describes how to verify chromium changes don't have any obvious
    coding issues.
---

# Manual testing
Whenever you are getting ready to verify a change, run `autoninja -C out/Default system_webview_apk`
in order to to see if the project builds correctly and if there are any linting issues.

You can then build the webview system shell app to run an app that will actually use the webview with
`autoninja -C out/Default system_webview_shell_apk`

You can then install the WebView instance with:
`./out/Default/bin/system_webview_apk install` and then `./out/Default/bin/system_webview_apk set-webview-provider`

Next install the webview shell app with `./out/Default/bin/system_webview_shell_apk install`

Finally you can launch the shell app with `./out/Default/bin/system_webview_shell_apk launch "<url to test>"`
"https://www.google.com" is a safe default.

Use the connected chrome devtools mcp server to interact with the page for your testing.

