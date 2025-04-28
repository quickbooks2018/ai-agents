# Browser MCP
- https://docs.browsermcp.io/setup-server#cursor
- https://github.com/BrowserMCP/mcp?tab=readme-ov-file
- [Browser](https://www.youtube.com/watch?v=eD5SUj5qqgI)

- Install Browser Extension
- https://browsermcp.io/

- MCP Browser Json
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    },
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    },
    "BrowserToolsMcp": {
      "command": "npx",
      "args": ["-y", "@agentdeskai/browser-tools-mcp"]
    },
    "browsermcp": {
      "command": "npx",
      "args": ["-y", "@browsermcp/mcp@latest"]
    }
  }
}
```

- Bowser MCP
```json
   "browsermcp": {
      "command": "npx",
      "args": ["-y", "@browsermcp/mcp@latest"]
    }
```

### MCP Server Browser Tools

- Github Repository: [mcp-server-browser-tools](https://github.com/AgentDeskAI/mcp-server-browser-tools)
- [Browser Tools](https://www.youtube.com/watch?v=g08kmknV5Sg)

```bash
git clone https://github.com/AgentDeskAI/browser-tools-mcp.git
```
- MCP Brower Tools Json
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    },
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    },
    "BrowserToolsMcp": {
      "command": "npx",
      "args": ["-y", "@agentdeskai/browser-tools-mcp"]
    }
  }
}
```

- browser-tools-json
```json
"BrowserToolsMcp": {
   "command": "npx",
   "args": ["-y", "@agentdeskai/browser-tools-mcp"]
}
```
