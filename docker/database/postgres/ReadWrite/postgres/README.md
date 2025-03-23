# PostgreSQL MCP Server with Write Capabilities

This is a Model Context Protocol (MCP) server implementation for PostgreSQL that supports both read and write operations.

## Features

- List database tables as resources
- Read database schema information
- Write data to database tables
- Execute SQL queries (read-only)
- Execute SQL commands (with write capabilities)

## Prerequisites

- Docker
- 
## Getting Started

1. Clone this repository:

```bash
git clone https://github.com/quickbooks2018/ai-agents.git
cd docker/database/postgres/ReadWrite/postgres
```

3. Build the Docker image:

```bash
docker build -t mcp/postgres -f Dockerfile . --no-cachetr
```

4. Pull ReadWrite MCP Server image:

```bash
docker pull quickbooks2018/postgres:mcp

# optional
docker tag quickbooks2018/postgres:mcp mcp/postgres
```

5. Add Server in Cursor/Windsurf/ClaudeDesktop:

- tag: "mcp/postgres"
```json
{
  "mcpServers": {
    "postgres": {
      "command": "docker",
      "args": [
        "run", 
        "-i", 
        "--rm", 
        "mcp/postgres",
        "postgresql://asim:asim@host.docker.internal:5432/bank_db"]
    }
  }
}
```

- tag : "quickbooks2018/postgres:mcp"
```json
{
  "mcpServers": {
    "postgres": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "quickbooks2018/postgres:mcp",
        "postgresql://asim:asim@host.docker.internal:5432/bank_db"]
    }
  }
}
```
