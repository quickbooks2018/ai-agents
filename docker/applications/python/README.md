# Docker-Based Python Flask Sample Webpage with PostgreSQL Connection

## Task Overview
A simple Python Flask webpage running in Docker that connects to an existing PostgreSQL database server on MCP server. The application is a single sample webpage that displays data from the database.

## Specific Requirements

### 1. Docker-Only Implementation
- **CRITICAL**: ALL development and execution MUST be done within Docker containers
- **NO packages or dependencies should be installed on the host machine**
- All builds, dependencies, and Python environment must be contained within Docker
- Only Docker and Docker Compose commands should be executed on the host machine

### 2. Project Structure
- **IMPORTANT**: All files must be placed ONLY in a directory named "application"
- The complete project structure including Dockerfile, docker-compose.yml, and all source code must be contained within "application" directory

### 3. Sample Webpage
- Built with a single-page web application using Flask
- Implements a simple webpage that:
    - Displays some sample data from the PostgreSQL database
    - Has a clean, basic UI
    - Includes a health-check indicator showing database connection status
- Includes appropriate error handling for database connection issues

### 4. Database Connection
- **IMPORTANT**: Connects to EXISTING PostgreSQL server using `host.docker.internal` as the hostname
- Database name: `my_online_store`
- The PostgreSQL server is already running on the MCP server
- Uses the database credentials (username: asim, password: asim, port: 5432) as specified in the MCP configuration file
- DOES NOT create a new database or include PostgreSQL in Docker Compose

### 5. Configuration
- Stores database credentials (host, username, password, port, database name) in:
    - Environment variables defined in docker-compose.yml, and
    - A separate .env file
- **CRITICAL**: Uses `host.docker.internal` as the hostname for the PostgreSQL connection
- Uses the same credentials (username, password, etc.) that are mentioned in the MCP configuration file

### 6. Docker Setup
- Contains a Dockerfile for the Python Flask application
- Contains a docker-compose.yml file that ONLY manages the Flask container
- Configures the Flask container to connect to the external PostgreSQL server using `host.docker.internal`
- Ensures proper port mapping to access the webpage from the host browser
- Includes all necessary build steps in the Dockerfile

## Project Structure

```
application/
```

## Setup Instructions

1. Ensure Docker and Docker Compose are installed on your system

2. Navigate to the application directory:
   ```
   cd application
   ```

3. Start the application with Docker Compose:
   ```
   docker-compose up -d
   ```

4. Access the web application in your browser:
   ```
   http://localhost:5000
   ```

5. To check the API health endpoint:
   ```
   http://localhost:5000/health
   ```

## Database Configuration

The application connects to the existing PostgreSQL database with the following configuration:

- Host: `host.docker.internal` (connects to the host machine from Docker)
- Database: `my_online_store`
- Username: `asim`
- Password: `asim`
- Port: `5432`

These settings can be configured in:
- The `.env` file
- The environment variables in `docker-compose.yml`

## Testing Success
The solution works when:
1. `docker compose up -d` started from within the "application" directory starts the webpage successfully
2. The application connects to the existing PostgreSQL database using `host.docker.internal` and the MCP credentials
3. The webpage is accessible from a browser on the host machine and displays data from the database
4. The health-check indicator shows a successful database connection
5. No additional PostgreSQL container is created or downloaded
6. No Python, pip, or other application dependencies are required on the host machine
7. All project files are contained exclusively within the "application" directory

## Stopping the Application

To stop the application:
```
docker compose down
```

- Note: Use docker compose cli updated command `docker compose` instead of `docker-compose` for Docker CLI version 20.10.0 and higher.