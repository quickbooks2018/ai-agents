# AI Agents in Container
- https://hub.docker.com/u/mcp

# kasm Desktop
```bash
docker run \
  --name browser-use \
  --shm-size=4096m \
  -w /mnt \
  -p 8080:6901 \
  -e VNC_PW=password \
  -id kasmweb/ubuntu-noble-desktop:1.16.1
  
user: kasm_user
password: password
 ```

### browser-use
- https://github.com/browser-use/browser-use.git

# Install latest version of python
```bash
docker exec -u root -it browser-use bash
visudo
kasm-user ALL=(ALL) NOPASSWD: ALL
passwd kasm-user
passwd root
exit

docker exec -it browser-use bash
sudo apt update -y
sudo apt install -y python3-venv git xvfb python3-full
```

### web-ui
- https://github.com/browser-use/web-ui.git
```bash
# Start in Desktop directory
cd /home/kasm-user/Desktop

# Remove any existing web-ui directory if it exists
sudo rm -rf web-ui

# Clone the repository
git clone https://github.com/browser-use/web-ui.git
cd web-ui

# Create and set up virtual environment in your home directory instead
python3 -m venv ~/web-ui-venv
source ~/web-ui-venv/bin/activate

# Install UV
curl -LsSf https://github.com/astral-sh/uv/releases/latest/download/uv-installer.sh | sh
source $HOME/.local/bin/env

# Verify environment
whoami
uv --version
python3 --version

# Install requirements using the virtual environment in home directory
uv pip install -r requirements.txt

# Install Playwright dependencies
playwright install-deps 
playwright install

# Setup environment file
cp .env.example .env

# Run the application with Xvfb
xvfb-run -a --server-args="-screen 0 1280x1024x24" python webui.py --ip 0.0.0.0 --port 7788

# Access the application at:
# http://localhost:7788


# Remove existing venv
deactivate
cd /home/kasm-user/Desktop
sudo rm -rf web-ui
```

### Install OLLAMA
```bash
curl -fsSL https://ollama.com/install.sh | sh

ollama serve &

http://localhost:11434

ollama pull deepseek-r1:8b

ollama pull deepseek-r1:8b  # I used this for docker

ollama run deepseek-r1:8b

ollama list

ollama stop deepseek-r1:8b

ollama rm deepseek-r1:8b
```

### MAC OS

- Install latest version of python
```bash
brew install python3

git clone https://github.com/browser-use/web-ui.git

# Install UV Package https://docs.astral.sh/uv/getting-started/installation/

cd web-ui

python3 -m venv .venv

source .venv/bin/activate

curl -LsSf https://github.com/astral-sh/uv/releases/latest/download/uv-installer.sh | sh

source $HOME/.local/bin/env

uv --version

python3 --version

uv pip install -r requirements.txt

playwright install-deps 

playwright install

cp .env.example .env

python webui.py --ip 127.0.0.1 --port 7788

http://localhost:7788
```

### Install OLLAMA on MAC OS
```bash
https://ollama.com/download/mac

ollama pull deepseek-r1:8b  # I used this for Mac OS

ollama run deepseek-r1:8b
```

### Vscode Insiders
- https://code.visualstudio.com/insiders/

### Google AI Studio (API Key)
- https://aistudio.google.com/apikey

### MCP ServerS
- https://github.com/modelcontextprotocol/servers
- https://github.com/punkpeye/awesome-mcp-servers?tab=readme-ov-file#file-systems
- https://smithery.ai/

- This provides internet access, so you can get latest documentation and update code accordingly

```bash
git clone https://github.com/modelcontextprotocol/servers.git
cd servers
docker build -t mcp/puppeteer -f src/puppeteer/Dockerfile .
```

- vscode Settings
```json
{
    "mcp": {

      "inputs": [],
      "servers": {
        "puppeteer": {
          "command": "docker",
          "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
        }
      }
    }
    
  }
```

- Vscode Multiple MCP Settings
```json
{
    "mcp": {


      "inputs": [],
      "servers": {
        "puppeteer": {
          "command": "docker",
          "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
        },
      "Context7": {
        "command": "npx",
        "args": ["-y", "@upstash/context7-mcp@latest"]
      },
      "browsermcp": {
        "command": "npx",
        "args": ["-y", "@browsermcp/mcp@latest"]
      },
      "desktop-commander": {
      "command": "npx",
      "args": [
        "-y",
        "@wonderwhy-er/desktop-commander"
      ]
    }
      }
    },
    "chat.mcp.discovery.enabled": true
    
  }
```

- Claude Desktop Settings
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    }
  }
}
```

- Cursor
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    }
  }
}
```

- Codium Windsurf
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    }
  }
}
```

### Gemni-cli
- https://github.com/google-gemini/gemini-cli

```bash
npm install -g @google/gemini-cli
gemini
```

### Google Gemni Code Assistant

- Enable Agent Mode

```json
 "geminicodeassist.updateChannel": "Insiders"
```

- json
```json
{
    "mcpServers": {
      "puppeteer": {
        "command": "docker",
        "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
      }
    },
    "Context7": {
        "command": "docker",
        "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "context7-mcp"]
      },
      "geminicodeassist.updateChannel": "Insiders",
      "mcp": {
      
        "inputs": [],
        "servers": {
          "mcp-server-time": {
            "command": "python",
            "args": [
              "-m",
              "mcp_server_time",
              "--local-timezone=America/Los_Angeles"
            ],
            "env": {}
          }
        }
      }
  }
```

### Claude Code Installation

- https://docs.anthropic.com/en/docs/claude-code/setup

```bash
npm install -g @anthropic-ai/claude-code
```

##### Claude Code UI
- https://github.com/siteboon/claudecodeui
- https://github.com/getAsterisk/claudia
- https://github.com/BloopAI/vibe-kanban

### Azure MCP

- https://github.com/Azure/azure-mcp
```bash
npm install -g @azure/mcp
```

- json
```json
{
  "servers": {
    "Azure MCP Server": {
      "command": "npx",
      "args": [
        "-y",
        "@azure/mcp@latest",
        "server",
        "start"
      ]
    }
  }
}
```
