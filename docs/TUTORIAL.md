# Nanobot Complete Tutorial

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Configuration](#configuration)
- [Basic Usage](#basic-usage)
- [Advanced Features](#advanced-features)
- [Troubleshooting](#troubleshooting)

## Introduction

Nanobot is an ultra-lightweight AI assistant framework that supports multiple LLM providers and chat channels.

## Installation

### Method 1: Using uv (Recommended)
```bash
uv tool install nanobot-ai
```

### Method 2: Using pip
```bash
pip install nanobot-ai
```

### Method 3: From Source
```bash
git clone https://github.com/HKUDS/nanobot.git
cd nanobot
pip install -e .
```

## Configuration

### Initialize Configuration
```bash
nanobot onboard
```

### Configure LLM Provider
Edit `~/.nanobot/config.json`:
```json
{
  "llm": {
    "provider": "openrouter",
    "api_key": "your-api-key"
  }
}
```

### Configure Chat Channel
Add channel configuration to `config.json`:
```json
{
  "channels": {
    "telegram": {
      "token": "your-bot-token",
      "allowFrom": ["your-chat-id"]
    }
  }
}
```

## Basic Usage

### Start CLI Agent
```bash
nanobot agent
```

### Start Gateway
```bash
nanobot gateway
```

### Available Commands
- `nanobot onboard` - Initialize configuration
- `nanobot agent` - Start CLI conversation
- `nanobot gateway` - Start gateway for chat channels
- `nanobot skills` - List available skills

## Advanced Features

### Skills
Nanobot supports various skills:
- **memory**: Long-term memory system
- **cron**: Scheduled tasks
- **weather**: Weather forecasts
- **clawhub**: Skill registry search
- **skill-creator**: Create custom skills

### MCP Support
Nanobot supports Model Context Protocol (MCP) for extending capabilities via stdio or HTTP transport.

### Multiple LLM Providers
Supported providers include:
- OpenRouter
- Anthropic (Claude)
- OpenAI (GPT)
- DeepSeek
- Gemini
- Qwen/DashScope
- Moonshot (Kimi)
- Groq
- Custom endpoints

## Troubleshooting

### Common Issues

**API Key Error**
- Ensure your API key is correctly set in `config.json`
- Check file permissions: `chmod 600 ~/.nanobot/config.json`

**Channel Connection Failed**
- Verify bot token/credentials
- Check `allowFrom` whitelist configuration
- Ensure network connectivity

**Skill Not Found**
- Install skill via ClawHub: `nanobot skill install <skill-name>`
- Check skill availability in registry

### Getting Help
- GitHub Discussions: https://github.com/HKUDS/nanobot/discussions
- Discord: https://discord.gg/MnCvHqpUGB
- Official Documentation: https://github.com/HKUDS/nanobot
