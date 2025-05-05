# Context7 MCP - Up-to-date Docs For Any AI Code Assistant

[![GitHub stars](https://img.shields.io/github/stars/upstash/context7?style=social)](https://github.com/upstash/context7/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/upstash/context7?style=social)](https://github.com/upstash/context7/network/members)
[![GitHub issues](https://img.shields.io/github/issues/upstash/context7)](https://github.com/upstash/context7/issues)
[![GitHub license](https://img.shields.io/github/license/upstash/context7)](https://github.com/upstash/context7/blob/main/LICENSE)

[GitHub Repository](https://github.com/upstash/context7) | [Documentation](https://github.com/upstash/context7/blob/main/README.md) | [Upstash](https://upstash.com)

- website: [context7.com](https://https://context7.com/)

Context7 MCP pulls up-to-date, version-specific documentation and code examples straight from the source — and places them directly into your prompt.

## 📚 Without Context7

LLMs rely on outdated or generic information about the libraries you use. You get:

- ❌ Code examples are outdated and based on year-old training data
- ❌ Hallucinated APIs don't even exist
- ❌ Generic answers for old package versions

## ✅ With Context7

Context7 MCP pulls up-to-date, version-specific documentation and code examples straight from the source — and places them directly into your prompt.

Add `use context7` to your question in your favorite AI code assistant:

```
How do I use the new Next.js `after` function? use context7
```

```
How do I invalidate a query in React Query? use context7
```

```
How do I protect a route with NextAuth? use context7
```

Context7 fetches up-to-date documentation and working code examples right into your LLM's context.

1️⃣ Ask your question naturally  
2️⃣ Tell the LLM to `use context7`  
3️⃣ Get working code answers

No tab-switching, no hallucinated APIs that don't exist, no outdated code generations.

## 🌐 Supported Languages and Frameworks

Context7 provides up-to-date documentation for hundreds of languages and frameworks. Here's a sampling of the supported languages and libraries:

### JavaScript/TypeScript/Node.js
- React, React Query, React Router, React Native
- Next.js, Remix, Gatsby
- Express.js, Fastify, NestJS
- Vue.js, Angular, Svelte
- Prisma, Sequelize, TypeORM
- Firebase, AWS SDK, Azure SDK
- Jest, Vitest, Playwright
- And hundreds more JavaScript libraries

### Python
- Django, Flask, FastAPI
- NumPy, Pandas, Matplotlib
- PyTorch, TensorFlow, Scikit-learn
- Requests, BeautifulSoup, Selenium
- AWS SDK, Google Cloud SDK
- SQLAlchemy, Pydantic
- TA-Lib, Temporal, OpenTelemetry
- And dozens more Python libraries

### Go (Golang)
- Standard library
- Gin, Echo, Fiber
- GORM, SQLx
- AWS SDK
- Google Cloud SDK
- And more Go packages

### Ruby
- Ruby on Rails
- ActiveRecord
- Stripe Ruby
- Vite Ruby
- And more Ruby gems

### PHP
- Laravel, Symfony
- Deployer
- Filament
- Pest, PHPUnit
- Twig
- Stripe PHP
- ReactPHP
- And more PHP libraries

### Java & Kotlin
- Spring Boot, Spring Framework
- Android SDK
- AWS SDK for Java
- Javalin
- And more Java/Kotlin libraries

### Rust
- Standard library
- AWS Lambda Rust Runtime
- AWS SDK for Rust
- Tokio, Actix, Axum
- wasm-bindgen
- Scylla Rust Driver
- And more Rust crates

### Swift
- Swift UI
- Swift Composable Architecture
- SnapshotTesting
- Swift Dependencies
- Swift Navigation
- Swift Testing
- And more Swift packages

### .NET (C#/F#)
- ASP.NET Core
- Entity Framework Core
- Roslyn
- Microsoft Orleans
- Akka.NET
- gRPC for .NET
- OpenTelemetry .NET
- And more .NET libraries

## 🚀 Getting Started

### Requirements

- Node.js >= v18.0.0 (tested with v20.19.0)
- Supported MCP Clients:
    - Cursor
    - VSCode
    - VSCode Insiders
    - Claude Desktop
    - Claude Code
    - Windsurf
    - Other MCP-compatible AI code assistants

### Installation Options

#### 1. Docker Installation (Recommended)

Clone the repository and build a Docker image:

```bash
git clone https://github.com/upstash/context7.git
cd context7
docker build -t context7-mcp .
```

Add to your MCP configuration (syntax varies by client):

```json
{
    "mcpServers": {
      "Context7": {
        "command": "docker",
        "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "context7-mcp"]
      }
    }
}
```

If you're also using Puppeteer:

```json
{
    "mcpServers": {
      "puppeteer": {
        "command": "docker",
        "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
      },
     "Context7": {
      "command": "docker",
        "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "context7-mcp"]
     }
    }
}
```

#### 2. NPX Installation

Using NPX (requires Node.js >= v18.0.0):

```json
{
    "mcpServers": {
      "Context7": {
        "command": "npx",
        "args": ["-y", "@upstash/context7-mcp@latest"]
      }
    }
}
```

If you're also using Puppeteer:

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
      }
    }
}
```

#### 3. Alternative Package Managers

Using Bun:

```bash
bun install -g @upstash/context7-mcp
```

Using Deno:

```bash
deno run -A npm:@upstash/context7-mcp
```

### Client-Specific Configurations

#### Cursor

Go to: `Settings` -> `Cursor Settings` -> `MCP` -> `Add new global MCP server`

Or manually add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

#### VSCode / VSCode Insiders

Add to your VSCode MCP config file:

```json
{
  "servers": {
    "Context7": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

#### Claude Desktop

Add to your Claude Desktop `claude_desktop_config.json` file:

```json
{
  "mcpServers": {
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

Or install via Smithery:

```bash
npx -y @smithery/cli install @upstash/context7-mcp --client claude
```

#### Claude Code

Run this command:

```bash
claude mcp add context7 -- npx -y @upstash/context7-mcp@latest
```

#### Windsurf

Add to your Windsurf MCP config file:

```json
{
  "mcpServers": {
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

## 🧰 Available Tools

- `resolve-library-id` : Resolves a general library name into a Context7-compatible library ID.
    - `libraryName` (optional): Search and rerank results

- `get-library-docs` : Fetches documentation for a library using a Context7-compatible library ID.
    - `context7CompatibleLibraryID` (required)
    - `topic` (optional): Focus the docs on a specific topic (e.g., "routing", "hooks")

## 📋 Example Usage

### JavaScript/TypeScript
```
How do I use useEffect in React? use context7
```

### Python
```
How to create a Django model with a many-to-many relationship? use context7
```

### Go (Golang)
```
What's the best way to implement worker pools in Go? use context7
```

### Ruby
```
How do I create a RESTful API in Ruby on Rails? use context7
```

### PHP
```
How to use Eloquent ORM in Laravel? use context7
```

### Java
```
How to create a Spring Boot REST controller? use context7
```

### Rust
```
How do I handle errors in Rust with Result and Option? use context7
```

### Swift
```
How to implement MVVM pattern in SwiftUI? use context7
```

### .NET/C#
```
How to use dependency injection in ASP.NET Core? use context7
```

## 🔄 Updating Context7

To update to the latest version when using NPX:

```bash
# NPX always pulls the latest version
# No additional steps required
```

When using Docker:

```bash
# Pull latest code
git pull origin main

# Rebuild the Docker image
docker build -t context7-mcp .
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request to the [Context7 repository](https://github.com/upstash/context7).

## 📝 License

MIT

---

Created and maintained by [Upstash](https://upstash.com)

[Context7 Repository](https://github.com/upstash/context7) | [Report Issues](https://github.com/upstash/context7/issues)