# AI Agents in Container

# kasm Desktop
```bash
docker run \
  --name browser-use \
  --shm-size=4096m \
  -w /mnt \
  -p 6905:6901 \
  -e VNC_PW=password \
  -id kasmweb/ubuntu-noble-desktop:1.16.1
  ```

  ### browser-use
  - https://github.com/browser-use/browser-use.git

# Install latest version of python
```bash
docker exec -u root -it browser-use bash
sudo su
cd /root
apt update -y
apt install -y python3-venv git xvfb python3-full
```

### web-ui
- https://github.com/browser-use/web-ui.git
```bash
git clone https://github.com/browser-use/web-ui.git

# Install UV Package https://docs.astral.sh/uv/getting-started/installation/

cd web-ui

python3 -m venv .venv

source .venv/bin/activate

curl -LsSf https://github.com/astral-sh/uv/releases/latest/download/uv-installer.sh | sh

export PATH="/root/.local/bin:$PATH"

uv --version

python3 --version

uv pip install -r requirements.txt

playwright install-deps 

playwright install

cp .env.example .env

xvfb-run python webui.py --ip 127.0.0.1 --port 7788

http://localhost:7788
```

### Install OLLAMA
```bash
curl -fsSL https://ollama.com/install.sh | sh

ollama serve &

http://localhost:11434

ollama pull deepseek-r1:14b

ollama pull deepseek-r1:8b  # I used this

ollama run deepseek-r1:8b
```