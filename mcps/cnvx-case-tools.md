---
title: "CNVX Case Tools MCP"
description: "Local Unicode lowercase, uppercase and inverse-case conversion over stdio, without a remote API or account."
tags:
  - text
  - productivity
  - python
  - local
author: "CNVX"
featured: false
install_command: "git clone https://github.com/cnvxstudio/case-tools-mcp.git"
connection_type: "stdio"
paid_api: false
---

# CNVX Case Tools MCP

A small MCP server for repeatable plain-text case conversion. It changes letter case in the local Python process without rewriting the wording or calling a conversion service.

Source: [cnvxstudio/case-tools-mcp](https://github.com/cnvxstudio/case-tools-mcp). MIT licensed; Python 3.10 or newer is required.

## Install

```sh
git clone https://github.com/cnvxstudio/case-tools-mcp.git
cd case-tools-mcp
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
```

On Windows, use the corresponding `.venv\Scripts\python.exe` path.

## Configure an MCP host

Use absolute paths to the Python interpreter and server on your computer:

```json
{
  "mcpServers": {
    "cnvx-case-tools": {
      "command": "/absolute/path/to/case-tools-mcp/.venv/bin/python",
      "args": ["/absolute/path/to/case-tools-mcp/server.py"]
    }
  }
}
```

The transport is stdio. There is no hosted HTTP endpoint, API key, account or paid API requirement.

## Available tool

`convert_case(text, mode)` returns an object containing `text` and `mode`.

| Mode | Input | Result |
| --- | --- | --- |
| `lowercase` | `A Quick Guide` | `a quick guide` |
| `uppercase` | `A Quick Guide` | `A QUICK GUIDE` |
| `inverse` | `A Quick Guide` | `a qUICK gUIDE` |

Example arguments:

```json
{"text": "Release Notes\n\nAPI v2", "mode": "lowercase"}
```

Result:

```json
{"text": "release notes\n\napi v2", "mode": "lowercase"}
```

Spaces, blank lines, numbers and punctuation are preserved. The maximum input is 20,000 Unicode code points and 100 lines; empty input is valid. Invalid modes and oversized inputs return MCP tool errors.

Unicode behavior follows Python `str.lower`, `str.upper` and `str.swapcase`. Some letters expand, such as `ß` becoming `SS` in uppercase, so inverse case is not guaranteed to reverse every Unicode input.

## Check the installation

```sh
.venv/bin/python verify.py
```

The verification script starts the real stdio server, initializes an MCP client, lists the tool and exercises the three modes, multiline Unicode input and error cases.

## Scope and data handling

The server implements these three basic operations; it does not implement editorial title-case styles. Conversion makes no network requests and does not write input text to files. Your MCP host can separately transmit or log tool arguments according to its settings.

Maintained by CNVX, the team behind [Title Case Converter](https://titlecaseconverter.app/), the companion browser interface for case-formatting work.
