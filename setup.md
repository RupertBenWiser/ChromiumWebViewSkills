# WebView Remote Debugging Setup

This guide describes how to set up remote debugging for Android WebView and connect to it using the Model Context Protocol (MCP) server without launching a local Chrome instance.

## Prerequisites

Ensure you have an Android device or emulator connected and visible via `adb devices`.

## Build and Install

1.  Build the WebView and Shell APKs:
    ```bash
    autoninja -C out/Default system_webview_apk
    autoninja -C out/Default system_webview_shell_apk
    ```

2.  Install WebView and set it as the provider:
    ```bash
    ./out/Default/bin/system_webview_apk install
    ./out/Default/bin/system_webview_apk set-webview-provider
    ```

3.  Install the WebView Shell:
    ```bash
    ./out/Default/bin/system_webview_shell_apk install
    ```

## Launch and Port Forward

1.  Launch the WebView Shell with a target URL:
    ```bash
    ./out/Default/bin/system_webview_shell_apk launch "https://www.google.com"
    ```

2.  Find the PID of the WebView Shell:
    ```bash
    adb shell pidof org.chromium.webview_shell
    ```

3.  Forward the debugging port (replace `<PID>` with the actual PID):
    ```bash
    adb forward tcp:9222 localabstract:webview_devtools_remote_<PID>
    ```

## MCP Configuration

To prevent the `chrome-devtools-mcp` server from launching a new Chrome instance and instead force it to connect to your forwarded WebView port, update your MCP configuration file (e.g., `mcp_config.json`) to include the `--browserUrl` argument.

Example configuration:
```json
{
  "mcpServers": {
    "chrome-devtools-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "chrome-devtools-mcp@latest",
        "--browserUrl",
        "http://127.0.0.1:9222"
      ]
    }
  }
}
```
