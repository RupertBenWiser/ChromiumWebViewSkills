---
name: inspect-webview
description: >
    This skill describes how to manually test a webview session and interact with the
    web contents when they are running.
    This can be used to verify changes or just see how behaviour works.
---

# Manual testing
Before verifying a change, confirm that you see a device connected with `adb devices`

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

