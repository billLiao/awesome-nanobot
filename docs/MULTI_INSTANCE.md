# Nanobot Multi-Instance Deployment Guide

> A comprehensive guide to running multiple nanobot instances simultaneously with separate configs and workspaces.

## Table of Contents

1. [What is Multi-Instance Deployment](#what-is-multi-instance-deployment)
2. [Why Use Multi-Instance](#why-use-multi-instance)
3. [Quick Start](#quick-start)
4. [Configuration Details](#configuration-details)
5. [Complete Examples](#complete-examples)
6. [Path Resolution](#path-resolution)
7. [Common Use Cases](#common-use-cases)
8. [Docker Multi-Instance](#docker-multi-instance)
9. [Linux Service Multi-Instance](#linux-service-multi-instance)
10. [Troubleshooting](#troubleshooting)

---

## What is Multi-Instance Deployment

Multi-instance deployment allows you to run multiple nanobot instances on the same server, each with:

- 📂 Separate configuration files
- 💾 Independent workspace (memory, sessions)
- 🔌 Different chat channels (Telegram, Discord, Feishu, etc.)
- 🤖 Different AI models
- ⏰ Independent scheduled tasks

---

## Why Use Multi-Instance

| Scenario | Description |
|----------|-------------|
| Multi-platform Support | Connect to Telegram, Discord, Feishu, DingTalk simultaneously |
| Environment Isolation | Separate production and testing environments |
| Multi-team Usage | Provide independent AI assistants for different teams |
| Multi-tenant Service | Serve different customers with isolated instances |
| Model Isolation | Use different AI models per instance for cost optimization |

---

## Quick Start

### Step 1: Create Instance Directories

```bash
# Create Telegram instance directory
mkdir -p ~/.nanobot-telegram
mkdir -p ~/.nanobot-telegram/workspace

# Create Discord instance directory
mkdir -p ~/.nanobot-discord
mkdir -p ~/.nanobot-discord/workspace

# Create Feishu instance directory
mkdir -p ~/.nanobot-feishu
mkdir -p ~/.nanobot-feishu/workspace
```

### Step 2: Create Configuration Files

Each instance needs its own `config.json`:

```bash
# Telegram instance config
cat > ~/.nanobot-telegram/config.json << 'EOF'
{
  "agents": {
    "defaults": {
      "workspace": "~/.nanobot-telegram/workspace",
      "model": "openai/gpt-4o-mini"
    }
  },
  "channels": {
    "telegram": {
      "enabled": true,
      "token": "YOUR_TELEGRAM_BOT_TOKEN"
    }
  },
  "gateway": {
    "port": 18790
  }
}
EOF

# Discord instance config
cat > ~/.nanobot-discord/config.json << 'EOF'
{
  "agents": {
    "defaults": {
      "workspace": "~/.nanobot-discord/workspace",
      "model": "anthropic/claude-sonnet-4-6"
    }
  },
  "channels": {
    "discord": {
      "enabled": true,
      "botToken": "YOUR_DISCORD_BOT_TOKEN",
      "channelIds": ["YOUR_CHANNEL_ID"]
    }
  },
  "gateway": {
    "port": 18791
  }
}
EOF
```

### Step 3: Start Instances

```bash
# Start Telegram instance
nanobot gateway --config ~/.nanobot-telegram/config.json

# Start Discord instance (different port)
nanobot gateway --config ~/.nanobot-discord/config.json --port 18791

# Start Feishu instance (different port)
nanobot gateway --config ~/.nanobot-feishu/config.json --port 18792
```

---

## Configuration Details

### Core Configuration Options

| Option | Description | Example |
|--------|-------------|---------|
| `agents.defaults.workspace` | Workspace directory | `~/.nanobot-telegram/workspace` |
| `gateway.port` | Gateway port | `18790`, `18791`, `18792` |
| `channels.*.enabled` | Enable channel | `true` / `false` |

### Minimal Config Example

```json
{
  "agents": {
    "defaults": {
      "workspace": "~/.nanobot-myinstance/workspace",
      "model": "openai/gpt-4o-mini"
    }
  },
  "channels": {
    "telegram": {
      "enabled": true,
      "token": "YOUR_BOT_TOKEN"
    }
  },
  "gateway": {
    "port": 18790
  }
}
```

---

## Complete Examples

### Three Instance Deployment Scenario

Assume you need:
- Instance 1: Telegram Customer Service Bot (using GPT-4o Mini)
- Instance 2: Discord Entertainment Bot (using Claude Sonnet)
- Instance 3: Feishu Internal Assistant (using DeepSeek)

### Directory Structure

```
~/.nanobot/
├── telegram/
│   ├── config.json
│   ├── workspace/
│   ├── cron/
│   └── media/
├── discord/
│   ├── config.json
│   ├── workspace/
│   ├── cron/
│   └── media/
└── feishu/
    ├── config.json
    ├── workspace/
    ├── cron/
    └── media/
```

### Startup Script

```bash
#!/bin/bash
# start-all-instances.sh

# Telegram instance
nanobot gateway --config ~/.nanobot-telegram/config.json &

# Discord instance
nanobot gateway --config ~/.nanobot-discord/config.json --port 18791 &

# Feishu instance
nanobot gateway --config ~/.nanobot-feishu/config.json --port 18792 &

echo "All instances started"
```

---

## Path Resolution

Understanding path resolution is crucial for proper multi-instance configuration:

| Component | Source | Example |
|-----------|--------|---------|
| **Config File** | `--config` argument | `~/.nanobot-telegram/config.json` |
| **Workspace** | `--workspace` or config's `agents.defaults.workspace` | `~/.nanobot-telegram/workspace/` |
| **Cron Jobs** | Config directory's `cron/` | `~/.nanobot-telegram/cron/` |
| **Media Files** | Config directory's `media/` | `~/.nanobot-telegram/media/` |

### Workspace Override

Use `--workspace` to temporarily override the workspace:

```bash
# Use workspace from config
nanobot gateway --config ~/.nanobot-telegram/config.json

# Temporarily override workspace (for testing)
nanobot gateway --config ~/.nanobot-telegram/config.json --workspace /tmp/test-workspace
```

### CLI Session

Use `nanobot agent` to connect to a specific instance:

```bash
# Connect to Telegram instance
nanobot agent -c ~/.nanobot-telegram/config.json -m "Hello"

# Connect to Discord instance
nanobot agent -c ~/.nanobot-discord/config.json -m "Hello"

# Temporarily override workspace
nanobot agent -c ~/.nanobot-telegram/config.json -w /tmp/test-workspace -m "Hello"
```

> ⚠️ Note: `nanobot agent` starts a local CLI agent and does not connect to a running `nanobot gateway` process.

---

## Common Use Cases

### Scenario 1: Multi-platform Customer Service

```
Instance A: Telegram Support → English customers
Instance B: Feishu Support → Chinese customers
Instance C: DingTalk Support → Internal company queries
```

### Scenario 2: Testing and Production Isolation

```
Instance A (Production): ~/.nanobot-production/
Instance B (Testing): ~/.nanobot-staging/
```

### Scenario 3: Multi-team Usage

```
Instance A: Team A's AI Assistant (GPT-4o)
Instance B: Team B's AI Assistant (Claude Sonnet)
Instance C: Team C's AI Assistant (DeepSeek)
```

---

## Docker Multi-Instance

### Docker Compose Configuration

```yaml
# docker-compose.yml
version: '3.8'

services:
  nanobot-telegram:
    image: nanobot-ai
    volumes:
      - ./telegram:/root/.nanobot
    ports:
      - "18790:18790"
    command: gateway

  nanobot-discord:
    image: nanobot-ai
    volumes:
      - ./discord:/root/.nanobot
    ports:
      - "18791:18790"
    command: gateway

  nanobot-feishu:
    image: nanobot-ai
    volumes:
      - ./feishu:/root/.nanobot
    ports:
      - "18792:18790"
    command: gateway
```

### Directory Structure

```
project/
├── docker-compose.yml
├── telegram/
│   └── config.json
├── discord/
│   └── config.json
└── feishu/
    └── config.json
```

### Startup Command

```bash
docker compose up -d
```

---

## Linux Service Multi-Instance

Create separate systemd services for each instance:

### Telegram Instance Service

```ini
# ~/.config/systemd/user/nanobot-telegram.service
[Unit]
Description=Nanobot Telegram Gateway
After=network.target

[Service]
Type=simple
ExecStart=%h/.local/bin/nanobot gateway --config %h/.nanobot-telegram/config.json
Restart=always
RestartSec=10

[Install]
WantedBy=default.target
```

### Discord Instance Service

```ini
# ~/.config/systemd/user/nanobot-discord.service
[Unit]
Description=Nanobot Discord Gateway
After=network.target

[Service]
Type=simple
ExecStart=%h/.local/bin/nanobot gateway --config %h/.nanobot-discord/config.json --port 18791
Restart=always
RestartSec=10

[Install]
WantedBy=default.target
```

### Enable Services

```bash
# Reload systemd
systemctl --user daemon-reload

# Enable and start
systemctl --user enable --now nanobot-telegram
systemctl --user enable --now nanobot-discord

# Check status
systemctl --user status nanobot-telegram
systemctl --user status nanobot-discord

# View logs
journalctl --user -u nanobot-telegram -f
```

---

## Troubleshooting

### Common Issues

#### 1. Port Conflict

```
Error: Port 18790 is already in use
```

**Solution**: Ensure each instance uses a different port

```bash
# Check port usage
lsof -i :18790
netstat -tlnp | grep 18790
```

#### 2. Workspace Conflict

**Symptom**: Memory/sessions from different instances get mixed up

**Solution**: Ensure each instance uses an independent workspace

```json
{
  "agents": {
    "defaults": {
      "workspace": "~/.nanobot-instance/workspace"
    }
  }
}
```

#### 3. Config File Path Error

**Symptom**: Cannot find config file

**Solution**: Use absolute paths

```bash
# Correct
nanobot gateway --config /home/user/.nanobot-telegram/config.json

# Wrong (relative path may cause issues)
nanobot gateway --config ~/.nanobot-telegram/config.json
```

#### 4. Permission Issues

**Symptom**: Cannot read config file or write to workspace

**Solution**: Check file permissions

```bash
chmod 600 ~/.nanobot-*/config.json
chmod 755 ~/.nanobot-*/workspace
```

---

## Related Links

- [Official README - Multiple Instances](https://github.com/HKUDS/nanobot#-multiple-instances)
- [Configuration Tutorial](./TUTORIAL.md)
- [Channel Configuration](./CHANNELS_CONFIG.md)

---

*Last updated: 2026-03-14*