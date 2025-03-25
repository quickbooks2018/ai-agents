# Postgres MCP SERVER

### docker compose
```bash
---
services:
  postgres:
    image: postgres:15.8
    container_name: postgres-test
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: asim
      POSTGRES_USER: asim
      POSTGRES_DB: test
    ports:
      - "5432:5432"
    networks:
      - postgres
    volumes:
      - postgres_data:/var/lib/postgresql/data

  pgadmin:
    image: dpage/pgadmin4:latest
    container_name: pgadmin
    restart: unless-stopped
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@example.com
      PGADMIN_DEFAULT_PASSWORD: admin
    ports:
      - "8080:80"
    networks:
      - postgres
    depends_on:
      - postgres

networks:
  postgres:
    driver: bridge

volumes:
  postgres_data:
```

### MCP Configuration
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    },
  "postgres": {
    "command": "docker",
    "args": [
      "run",
      "-i",
      "--rm",
      "quickbooks2018/postgres:mcp",
      "postgresql://asim:asim@host.docker.internal:5432/postgres"]
  }
  }
}
```

### NodeJs Web App Prompt for Claude 3.7 Sonnet

```declarative
# Docker-Based Node.js Sample Webpage with PostgreSQL Connection

## Task Overview
Create a simple Node.js webpage running in Docker that connects to an existing PostgreSQL database server on MCP server. The application will be a single sample webpage that displays data from the database.

## Specific Requirements

### 1. Docker-Only Implementation
- **CRITICAL**: ALL development and execution MUST be done within Docker containers
- **NO packages or dependencies should be installed on the host machine**
- All builds, dependencies, and Node.js environment must be contained within Docker
- Only Docker and Docker Compose commands should be executed on the host machine

### 2. Sample Webpage
- Build a single-page web application using Express.js
- Implement a simple webpage that:
  - Displays some sample data from the PostgreSQL database
  - Has a clean, basic UI
  - Includes a health-check indicator showing database connection status
- Include appropriate error handling for database connection issues

### 3. Database Connection
- **IMPORTANT**: Connect to EXISTING PostgreSQL server using `host.docker.internal` as the hostname
- Database name: `my_online_store`
- The PostgreSQL server is already running on the MCP server
- Use the database credentials (username, password, port) as specified in the MCP configuration file
- DO NOT create a new database or include PostgreSQL in Docker Compose

### 4. Configuration
- Store database credentials (host, username, password, port, database name) in:
  - Environment variables defined in docker-compose.yml, or
  - A separate .env file
- **CRITICAL**: Use `host.docker.internal` as the hostname for the PostgreSQL connection
- Use the same credentials (username, password, etc.) that are mentioned in the MCP configuration file
- Document clearly where these settings should be configured

### 5. Docker Setup
- Create a Dockerfile for the Node.js application
- Create a docker-compose.yml file that ONLY manages the Node.js container
- Configure the Node.js container to connect to the external PostgreSQL server using `host.docker.internal`
- Ensure proper port mapping to access the webpage from the host browser
- Include all necessary build steps in the Dockerfile

### 6. Documentation
- Include a README.md with:
  - Clear setup instructions
  - How to start and stop the application
  - Environment variable configuration requirements

## Testing Success
The solution works when:
1. `docker-compose up -d` starts the webpage successfully without requiring any host-installed packages
2. The application connects to the existing PostgreSQL database using `host.docker.internal` and the MCP credentials
3. The webpage is accessible from a browser on the host machine and displays data from the database
4. The health-check endpoint or indicator shows a successful database connection
5. No additional PostgreSQL container is created or downloaded
6. No Node.js, npm, or other application dependencies are required on the host machine
```