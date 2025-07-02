# Playwright MCP Server

- https://github.com/microsoft/playwright-mcp


### Installation Commands for MAC

```bash
npm install -g @playwright/mcp@latest
```

##### Json MAC
```json
    "playwright": {
      "command": "mcp-server-playwright"
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
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    },
    "browsermcp": {
      "command": "npx",
      "args": ["-y", "@browsermcp/mcp@latest"]
    },
    "playwright": {
      "command": "mcp-server-playwright"
    }
  }
}
```

- Json Linux (Ubuntu)
```json
  "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest"
      ]
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
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    },
    "browsermcp": {
      "command": "npx",
      "args": ["-y", "@browsermcp/mcp@latest"]
    },
    "azure": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "mcp/azure",
        "server",
        "start"
      ]
    },
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest"
      ]
    }
  }
}
```
