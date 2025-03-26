# IDA Pro MCP

Simple [MCP Server](https://modelcontextprotocol.io/introduction) to allow vibe reversing in IDA Pro.

## IDA Pro Installation

1. Copy `mcp-plugin.py` in your plugins folder (`%appdata%\Hex-Rays\IDA Pro\plugins` on Windows)
2. Open an IDB and click `Edit -> Plugins -> MCP` to start the server

## MCP Server Installation (Cline/Claude)

To install the MCP server in Cline, follow these steps:

1. Install [uv](https://github.com/astral-sh/uv) globally:
   - Windows: `pip install uv`
   - Linux/Mac: `curl -LsSf https://astral.sh/uv/install.sh | sh`
2. Clone this repository, for this example `C:\MCP\ida-pro-mcp`.
3. Navigate to the Cline _MCP Servers_ configuration (see screenshot).
4. Click on the _Installed_ tab.
5. Click on _Configure MCP Servers_, which will open `cline_mcp_settings.json`.
6. Add the `ida-pro-mcp` server:

```json
{
  "mcpServers": {
    "github.com/mrexodia/ida-pro-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "c:\\MCP\\ida-pro-mcp",
        "run",
        "server.py"
      ],
      "timeout": 600
    }
  }
}

```

## Development

```sh
uv run fastmcp dev server.py
```

This will open a web interface at http://localhost:5173 and allow you to interact with the MCP tools for testing.

## Available tools

```
<use_mcp_tool>
<server_name>github.com/mrexodia/ida-pro-mcp</server_name>
<tool_name>get_current_function</tool_name>
<arguments></arguments>
</use_mcp_tool>
```