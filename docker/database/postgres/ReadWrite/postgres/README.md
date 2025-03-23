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
git clone https://github.com/modelcontextprotocol/servers.git
cd servers
```

2. Create the necessary files:

- Copy the provided `index.ts` to `src/postgres/index.ts`
- Copy the provided `Dockerfile` to `src/postgres/Dockerfile`

3. Build the Docker image:

```bash
docker build -t mcp/postgres -f Dockerfile . --no-cachetr
```
