# DesktopCommanderMCP

- https://github.com/aaddrick/claude-desktop-debian

- https://github.com/wonderwhy-er/DesktopCommanderMCP

- DesktopCommanderMCP

```json
{
  "mcpServers": {
    "desktop-commander": {
      "command": "npx",
      "args": [
        "-y",
        "@wonderwhy-er/desktop-commander"
      ]
    }
  }
}
```

```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    },
    "desktop-commander": {
      "command": "npx",
      "args": [
        "-y",
        "@wonderwhy-er/desktop-commander"
      ]
    },
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    },
    "browsermcp": {
      "command": "npx",
      "args": ["-y", "@browsermcp/mcp@latest"]
    },
    "playwright": {
      "command": "mcp-server-playwright"
    },
    "azure-mcp-server": {
      "command": "npx",
      "args": [
        "-y",
        "@azure/mcp@latest",
        "server",
        "start"
      ]
    },
    "terraform": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "hashicorp/terraform-mcp-server"
      ]
    }
  }
}
```
