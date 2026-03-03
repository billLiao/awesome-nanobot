<div align="center">
<h1>Awesome Nanobot</h1>
<p><strong>A curated collection of resources, tools, skills, and projects for nanobot - the ultra-lightweight AI assistant framework.</strong></p>
<p>
<a href="https://github.com/HKUDS/nanobot">Official Repo</a> •
<a href="#official-resources">Resources</a> •
<a href="#skills--plugins">Skills</a> •
<a href="#community">Community</a>
</p>
<p>
<a href="README_CN.md">简体中文</a> | English
</p>
</div>

---

> **Note**: This list focuses on [HKUDS/nanobot](https://github.com/HKUDS/nanobot) (Python). There's another project with a similar name on GitHub - please make sure you're using the correct repository.

## Contents

- [Official Resources](#official-resources)
- [Quick Start](#quick-start)
- [LLM Providers](#llm-providers)
- [Chat Channels](#chat-channels)
- [MCP Support](#mcp-support)
- [Deployment](#deployment)
- [Skills & Plugins](#skills--plugins)
- [Ecosystem Projects](#ecosystem-projects)
- [Desktop & GUI](#desktop--gui)
- [Language Ports](#language-ports)
- [Tutorials](#tutorials)
- [Security](#security)
- [Community](#community)
- [Contributing](#contributing)

---

## Official Resources

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/HKUDS/nanobot) | Official nanobot repository |
| [Releases](https://github.com/HKUDS/nanobot/releases) | Changelog and version history |
| [Security Policy](https://github.com/HKUDS/nanobot/blob/main/SECURITY.md) | Security guidelines for production |
| [User Profile Template](https://github.com/HKUDS/nanobot/blob/main/workspace/USER.md) | Personalization configuration |
| [nanobot.club](http://nanobot.club/) | Official website |

## Quick Start

| Method | Command |
|--------|---------|
| **uv (Recommended)** | `uv tool install nanobot-ai` |
| **PyPI** | `pip install nanobot-ai` |
| **From Source** | `git clone https://github.com/HKUDS/nanobot.git && cd nanobot && pip install -e .` |

**Basic Commands:**
```bash
nanobot onboard    # Initialize configuration
nanobot agent      # Start CLI conversation
nanobot gateway    # Start gateway for chat channels
```

📁 **Detailed Tutorial**: [docs/TUTORIAL.md](docs/TUTORIAL.md) | [中文教程](docs/TUTORIAL_CN.md)

## LLM Providers

nanobot supports multiple LLM providers:

| Provider | Type | Notes |
|----------|------|-------|
| OpenRouter | API | Multiple models via single API |
| Anthropic | API | Claude models |
| OpenAI | API | GPT models |
| DeepSeek | API | DeepSeek models |
| Gemini | API | Google Gemini |
| Qwen / DashScope | API | Alibaba models |
| Moonshot | API | Kimi models |
| Groq | API | Fast inference |
| Custom Endpoint | API | OpenAI-compatible APIs |
| GitHub Copilot | OAuth | Via OAuth |
| OpenAI Codex | OAuth | Via OAuth |

📖 **Provider Configuration**: [Official README - Providers](https://github.com/HKUDS/nanobot#providers)

## Chat Channels

| Channel | Status | Notes |
|---------|--------|-------|
| Telegram | ✅ Stable | Recommended for beginners |
| Discord | ✅ Stable | Full support |
| Feishu (飞书) | ✅ Stable | Chinese enterprise IM |
| DingTalk (钉钉) | ✅ Stable | Chinese enterprise IM |
| WhatsApp | ✅ Stable | Requires Node.js bridge |
| Slack | ✅ Stable | Enterprise chat |
| Email | ✅ Stable | IMAP/SMTP |
| QQ | ✅ Stable | Via go-cqhttp |
| MoChat | ✅ Stable | Claw IM |

📖 **Channel Setup**: [Official README - Chat Apps](https://github.com/HKUDS/nanobot#-chat-apps)

## MCP Support

nanobot supports Model Context Protocol (MCP) for extending capabilities:

| Transport | Description |
|-----------|-------------|
| stdio | Local MCP servers via standard I/O |
| HTTP | Remote MCP servers via HTTP |

📖 **MCP Configuration**: [Official README - MCP](https://github.com/HKUDS/nanobot#mcp-model-context-protocol)

## Deployment

| Method | Description |
|--------|-------------|
| [Docker](https://github.com/HKUDS/nanobot#-docker) | Official Docker support |
| [Docker Compose](https://github.com/HKUDS/nanobot#-docker) | One-click deployment |
| [Zeabur Template](https://zeabur.com/templates/5XVJX8) | One-click cloud deployment |

## Skills & Plugins

### Official Skills

| Skill | Description | Status |
|-------|-------------|--------|
| [memory](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/memory) | Long-term memory system | Built-in |
| [cron](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/cron) | Scheduled tasks | Built-in |
| [weather](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/weather) | Weather forecasts | Built-in |
| [clawhub](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/clawhub) | Skill registry search | Built-in |
| [skill-creator](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/skill-creator) | Create custom skills | Built-in |

### Community Skills

| Skill | Author | Description |
|-------|--------|-------------|
| [nanobot-skills](https://github.com/ruslanstarikov/nanobot-skills) | ruslanstarikov | Custom skills collection |
| [nanobot-skills](https://github.com/CCAgentOrg/nanobot-skills) | CCAgentOrg | github-watcher, youtube-recommender |
| [nanobot-skill-weather](https://github.com/kombalarasoftware-cmd/nanobot-skill-weather) | kombalarasoftware | Weather skill |
| [nanobot-skill-finance](https://github.com/kombalarasoftware-cmd/nanobot-skill-finance) | kombalarasoftware | Financial data skill |
| [nanobot-skill-notes](https://github.com/kombalarasoftware-cmd/nanobot-skill-notes) | kombalarasoftware | Notes management |
| [nanobot-skill-calendar](https://github.com/kombalarasoftware-cmd/nanobot-skill-calendar) | kombalarasoftware | Calendar integration |
| [nanobot-skill-translator](https://github.com/kombalarasoftware-cmd/nanobot-skill-translator) | kombalarasoftware | Translation skill |

### Skill Registry

| Platform | Description |
|----------|-------------|
| [ClawHub](https://clawhub.ai/) | Official skill registry for discovering and installing skills |

## Ecosystem Projects

| Project | Stars | Description |
|---------|-------|-------------|
| [MoChat](https://github.com/HKUDS/MoChat) | - | Claw IM client, nanobot channel support |
| [ClawWork](https://github.com/HKUDS/ClawWork) | - | OpenClaw/Nanobot integration |
| [CrewClaw](https://github.com/Vistiqx/CrewClaw) | ⭐ 1 | Enterprise AI platform for multi-business holdings |
| [OpenLegion](https://github.com/openlegion-ai/openlegion) | ⭐ 60 | Secure autonomous AI agent fleet platform — Docker-isolated, multi-provider |
| [SwarmClaw](https://github.com/swarmclawai/swarmclaw) | ⭐ 16 | Multi-agent swarm coordination |
| [Ferrum Bot](https://github.com/lispking/ferrum-bot) | ⭐ 17 | Rust-based AI agent framework |
| [GeneClaw](https://github.com/Clawland-AI/Geneclaw) | ⭐ 14 | AI agent framework |
| [TinyBot](https://github.com/D-Sketon/tinybot) | ⭐ 2 | Lightweight agent framework based on nanobot |
| [nanobot-web-console](https://github.com/tankyhsu/nanobot-web-console) | ⭐ 5 | Single-file Web console with real-time streaming chat |
| [nanobot-setup](https://github.com/volkergrabbe/nanobot-setup) | ⭐ 2 | Automated installation script (Docker + Redis + Qdrant) |

## Desktop & GUI

| Project | Stars | Description |
|---------|-------|-------------|
| [nanoboard](https://github.com/Freakz3z/nanoboard) | ⭐ 11 | Tauri-based management dashboard |
| [nanobot-desktop](https://github.com/EvannZhongg/nanobot-desktop) | ⭐ 13 | Tauri + React desktop client |
| [MyxAI-Desk](https://github.com/myxai/MyxAI-Desk) | ⭐ 1 | Desktop GUI client for nanobot |
| [nanobot-webui](https://github.com/codemo1991/nanobot-webui) | ⭐ 6 | Web UI with visual configuration & knowledge management |

## Language Ports

| Project | Stars | Description |
|---------|-------|-------------|
| [NanoBot.net](https://github.com/lepollo/NanoBot.net) | ⭐ 10 | .NET 10 port |
| [nanobot-rs](https://github.com/open-vibe/nanobot-rs) | ⭐ 4 | Rust port |
| [sharpclaw](https://github.com/imxcstar/sharpclaw) | ⭐ 12 | AI agent with long-term memory (.NET 10) |
| [maxclaw](https://github.com/Lichas/maxclaw) | ⭐ 5 | Ultra-Lightweight AI Assistant in Go |
| [agent-diva](https://github.com/ProjectViVy/agent-diva) | ⭐ 6 | Next Gen AI Agent (nanobot-rs-pro, Rust) |
| [MetalClaw](https://github.com/JunSuzuki1973/MetalClaw) | ⭐ 2 | Personalized AI assistant fork |
| [ha-nanobot](https://github.com/dartanidi/ha-nanobot) | ⭐ 0 | Home Assistant integration (Shell) |
| [nano-claw](https://github.com/hustcc/nano-claw) | ⭐ 18 | 🦞 Claw is a personal AI assistant you run on your own devices, but nano (TypeScript) |
| [nanobot-golang](https://github.com/ajiany/nanobot-golang) | ⭐ 18 | Lightweight, data-driven AI assistant framework in Go. 18+ LLM providers, 9 chat channels, MCP tools |

## Integrations

| Project | Stars | Description |
|---------|-------|-------------|
| [NanoBot-Plugin](https://github.com/FloatTech/NanoBot-Plugin) | ⭐ 94 | QQ bot plugin collection |

## Tutorials

| Resource | Language | Type |
|----------|----------|------|
| [Tutorial (EN)](docs/TUTORIAL.md) | English | Complete guide |
| [教程 (中文)](docs/TUTORIAL_CN.md) | 中文 | 完整教程 |
| [DataCamp Tutorial](https://www.datacamp.com/tutorial/nanobot-tutorial) | English | Third-party tutorial |
| [YouTube Demo](https://www.youtube.com/watch?v=AKxiKb42Cqk) | English | Ollama + Telegram setup |
| [Medium Architecture](https://jinlow.medium.com/nanobot-architecture-teardown-4-000-lines-achieving-openclaw-capability-3f242113ccbc) | English | Architecture deep-dive |

## Security

> ⚠️ **Important**: Read the [Security Policy](https://github.com/HKUDS/nanobot/blob/main/SECURITY.md) before production deployment.

**Key Security Practices:**

| Practice | Description |
|----------|-------------|
| API Key Management | Never commit to repo; set `chmod 600 ~/.nanobot/config.json` |
| Channel Access Control | Configure `allowFrom` whitelist in production |
| Workspace Restriction | Set `tools.restrictToWorkspace=true` |
| Command Execution | Run with restricted user; enable audit logs |
| Dependency Security | Run `pip-audit` / `npm audit` regularly |

## Community

| Platform | Link |
|----------|------|
| GitHub Discussions | [github.com/HKUDS/nanobot/discussions](https://github.com/HKUDS/nanobot/discussions) |
| Discord | [discord.gg/MnCvHqpUGB](https://discord.gg/MnCvHqpUGB) |
| WeChat / Feishu | See [COMMUNICATION.md](https://github.com/HKUDS/nanobot/blob/main/COMMUNICATION.md) |

## Contributing

Contributions are welcome! Please read the [Contributing Guidelines](CONTRIBUTING.md) before submitting a PR.

**Guidelines:**
- Only add verifiable links
- Include a brief description for each resource
- Mark third-party content clearly
- Check link availability regularly

---

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related rights to this work.