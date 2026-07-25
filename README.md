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
<p>
<a href="https://github.com/billLiao/awesome-nanobot/stargazers"><img src="https://img.shields.io/github/stars/billLiao/awesome-nanobot?style=flat" alt="Stars"></a>
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
| [nanobot.wiki](https://nanobot.wiki) | Official website (Multi-language docs) |
| [nanobot.club](http://nanobot.club/) | Community website |

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
| SSE | Server-Sent Events for real-time streaming |

📖 **MCP Configuration**: [Official README - MCP](https://github.com/HKUDS/nanobot#mcp-model-context-protocol)

## Deployment

| Method | Description |
|--------|-------------|
| [Docker](https://github.com/HKUDS/nanobot#-docker) | Official Docker support |
| [Docker Compose](https://github.com/HKUDS/nanobot#-docker) | One-click deployment |
| [Zeabur Template](https://zeabur.com/templates/5XVJX8) | One-click cloud deployment |
| [Render Template](https://github.com/render-examples/nanobot-render) | One-click Render deploy template |

## Skills & Plugins

| Project | Stars | Description |
|---------|-------|-------------|
| [nanobot-llm-wiki](https://github.com/yu-xin-c/nanobot-llm-wiki) | ⭐ 1 | LLM Wiki long-term memory plugin for NanoBot |

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
| [jina-search-skill](https://github.com/billLiao/jina-search-skill) | billLiao | Jina.ai web search and page reading |
| [bark-push-skills](https://github.com/billLiao/bark-push-skills) | billLiao | iOS push notifications |
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
| [nanobot](https://github.com/obot-platform/nanobot) | ⭐ 1.3k | Build MCP Agents — Official nanobot with enhanced MCP support |
| [NanoResearch](https://github.com/OpenRaiser/NanoResearch) | ⭐ 1.5k | 🦞+🔬 Autonomous AI Research Assistant powered by nanobot |
| [TinyClaw](https://github.com/warengonzaga/tinyclaw) | ⭐ 280 | The original Tiny Claw as your personal autonomous AI companion |
| [OpenLegion](https://github.com/openlegion-ai/openlegion) | ⭐ 105 | Secure autonomous AI agent fleet platform — Docker-isolated, multi-provider |
| [MultiUserClaw](https://github.com/johnson7788/MultiUserClaw) | ⭐ 301 | Multi-user support for OpenClaw/NanoBot |
| [NanoBot](https://github.com/fumiama/NanoBot) | ⭐ 61 | ZeroBot-style QQ channel/group bot framework |
| [FastSkills](https://github.com/matthewlee0102/FastSkills) | ⭐ 15 | MCP server that brings Agent Skills to any MCP-compatible agent |
| [nanobot-custom](https://github.com/deeeeeeeeap/nanobot-custom) | ⭐ 65 | Personal AI assistant based on nanobot — supports MiniMax, Gemini multi-model switching |
| [MoChat](https://github.com/HKUDS/MoChat) | - | Claw IM client, nanobot channel support |
| [ClawWork](https://github.com/HKUDS/ClawWork) | - | OpenClaw/Nanobot integration |
| [SwarmClaw](https://github.com/swarmclawai/swarmclaw) | ⭐ 609 | Multi-agent swarm coordination |
| [Ferrum Bot](https://github.com/lispking/ferrum-bot) | ⭐ 23 | Rust-based AI agent framework |
| [GeneClaw](https://github.com/Clawland-AI/Geneclaw) | ⭐ 40 | Self-evolving AI agent framework with 5-layer safety gateway |
| [TinyBot](https://github.com/D-Sketon/tinybot) | ⭐ 3 | Lightweight agent framework based on nanobot |
| [nanobot-web-console](https://github.com/tankyhsu/nanobot-web-console) | ⭐ 13 | Single-file Web console with real-time streaming chat |
| [nanobot-setup](https://github.com/volkergrabbe/nanobot-setup) | ⭐ 2 | Automated installation script (Docker + Redis + Qdrant) |
| [NanoBot-Android](https://github.com/AbuZar-Ansarii/NanoBot-Android) | ⭐ 35 | Personal AI assistant for Android — nanobot-inspired |
| [OSA](https://github.com/Miosa-osa/OSA) | ⭐ 40 | Optimal System Agent — maximizes signal extraction |
| [ByeByeClaw](https://github.com/wanikua/byebyeclaw) | ⭐ 74 | One command to uninstall ALL Claw-family AI agents. Zero residual files |
| [NanoClaw](https://github.com/nanocoai/nanoclaw) | ⭐ 30k | Lightweight alternative to OpenClaw — runs in containers, connects to WhatsApp, Telegram, Slack, Discord, Gmail |
| [nanobot-study](https://github.com/WangyiNTU/nanobot-study) | ⭐ 15 | Master AI Agent Assistant in 3 Days — guided study plan |
| [nanobot-rs](https://github.com/yukihamada/nanobot) | ⭐ 6 | AI Agent Platform built in Rust — Multi-model, MCP tools |
| [nanobot-viking](https://github.com/tankyhsu/nanobot-viking) | ⭐ 10 | OpenViking knowledge base integration — RAG, semantic search, vector embeddings |
| [nanobot-teams](https://github.com/hyokyunAn/nanobot_teams) | ⭐ 0 | Manage multiple AI agent teams collaborating in isolated workspaces |
| [nanobot-feishu-specialized](https://github.com/Wuuu-uu/nanobot-feishu-specilized) | ⭐ 67 | Feishu-specific version with enhanced features |
| [LemonClaw](https://github.com/hedging8563/lemonclaw) | ⭐ 1 | AI Agent Platform (MIT, fork of nanobot) |
| [nanobot-docker](https://github.com/ciri/nanobot-docker) | ⭐ 6 | Dockerized setup for nanobot |
| [nanobot-webgui](https://github.com/lucmuss/nanobot-webgui) | ⭐ 21 | Production-focused web GUI fork with setup wizard, MCP management, chat, memory, and admin controls |
| [nanobot-webui](https://github.com/Good0007/nanobot-webui) | ⭐ 150 | A self-hosted web management panel for nanobot-ai |
| [nanobot-task-pipeline](https://github.com/Minggnim-jpg/nanobot-task-pipeline) | ⭐ 14 | Automated task pipeline powered by nanobot & Claude Code — multi-stage workflow with heartbeat scheduler |
| [nanobot-searxng-search](https://github.com/SJK-py/nanobot-searxng-search) | ⭐ 4 | SearXNG search skill for Nanobot — self-hosted search integration |
| [nanobot-a2a-proxy](https://github.com/450home/nanobot-a2a-proxy) | ⭐ 1 | A2A Proxy for nanobot agent communication |
| [nanobot-ts](https://github.com/rzx007/nanobot-ts) | ⭐ 13 | TypeScript version of nanobot — ultra-lightweight personal AI assistant framework |
| [nanobot-hass](https://github.com/licheng5625/nanobot-hass) | ⭐ 1 | Home Assistant custom component for nanobot conversation agent |
| [nanobot-on-rpi](https://github.com/msaltnet/nanobot-on-rpi) | ⭐ 0 | Recipe for running nanobot on Raspberry Pi |
| [NanoMate](https://github.com/shenmintao/NanoMate) | ⭐ 85 | nanobot × SillyTavern, with Companion Mode |
| [ShibaClaw](https://github.com/RikyZ90/ShibaClaw) | ⭐ 77 | Self-hosted AI assistant framework — Multi-channel (Telegram, Discord, Slack), parallel agents, MCP support, WebUI with OAuth |
## Desktop & GUI

| Project | Stars | Description |
|---------|-------|-------------|
| [nanoBot-ui](https://github.com/qq695500710-ui/nanoBot-ui) | ⭐ 175 | Plug-and-play nanobot for Windows 10+ |
| [nanobot-desktop](https://github.com/EvannZhongg/nanobot-desktop) | ⭐ 50 | Tauri + React desktop client |
| [nanobot-webui](https://github.com/codemo1991/nanobot-webui) | ⭐ 32 | Web UI with visual configuration & knowledge management |
## Language Ports

| Project | Stars | Description |
|---------|-------|-------------|
| [NanoBot.net](https://github.com/lepollo/NanoBot.net) | ⭐ 11 | .NET 10 port |
| [nanobot-rs](https://github.com/open-vibe/nanobot-rs) | ⭐ 7 | Rust port |
| [sharpclaw](https://github.com/imxcstar/sharpclaw) | ⭐ 25 | AI agent with long-term memory (.NET 10) |
| [maxclaw](https://github.com/Lichas/maxclaw) | ⭐ 228 | Ultra-Lightweight AI Assistant in Go |
| [agent-diva](https://github.com/ProjectViVy/agent-diva) | ⭐ 59 | Next Gen AI Agent (nanobot-rs-pro, Rust) |
| [MetalClaw](https://github.com/JunSuzuki1973/MetalClaw) | ⭐ 3 | Personalized AI assistant fork |
| [ha-nanobot](https://github.com/dartanidi/ha-nanobot) | ⭐ 1 | Home Assistant integration (Shell) |
| [nano-claw](https://github.com/hustcc/nano-claw) | ⭐ 65 | 🦞 Claw is a personal AI assistant you run on your own devices, but nano (TypeScript) |
| [nanobot-golang](https://github.com/ajiany/nanobot-golang) | ⭐ 0 | Lightweight, data-driven AI assistant framework in Go. 18+ LLM providers, 9 chat channels, MCP tools |
| [nanobot-go](https://github.com/cuichuankai/nanobot-go) | ⭐ 6 | Go implementation of nanobot |
| [mini_nanobot](https://github.com/mu-xi-mu-xi/mini_nanobot) | ⭐ 10 | Lightweight LLM Agent framework for learning |
| [PP-Claw](https://github.com/yangkun19921001/PP-Claw) | ⭐ 36 | Go version of nanobot |
## Integrations

| Project | Stars | Description |
|---------|-------|-------------|
| [NanoBot-Plugin](https://github.com/FloatTech/NanoBot-Plugin) | ⭐ 106 | QQ bot plugin collection |
## Tutorials

| Resource | Language | Type |
|----------|----------|------|
| [Tutorial (EN)](docs/TUTORIAL.md) | English | Complete guide |
| [教程 (中文)](docs/TUTORIAL_CN.md) | 中文 | 完整教程 |
| [DataCamp Tutorial](https://www.datacamp.com/tutorial/nanobot-tutorial) | English | Third-party tutorial |
| [YouTube Demo](https://www.youtube.com/watch?v=AKxiKb42Cqk) | English | Ollama + Telegram setup |
| [Medium Architecture](https://jinlow.medium.com/nanobot-architecture-teardown-4-000-lines-achieving-openclaw-capability-3f242113ccbc) | English | Architecture deep-dive |
| [nanobot-learn](https://github.com/WOWCharlotte/nanobot-learn) | 中文 | Learn Nanobot Design Principles in 7 Days |
| [byte-of-nanobot](https://github.com/sine-io/byte-of-nanobot) | 中文 | 面向零基础用户的 nanobot 教程，从"能跑"到"懂原理" |
| [agent-tutor](https://github.com/ywz456/agent-tutor) | 中文 | 从 0 到 1 搭建生产级 AI Agent 实战教程 |
| [how-ai-agents-remember](https://github.com/breath57/how-ai-agents-remember) | 中/EN | 源码级逆向工程 nanobot 等 Agent 记忆系统 — 架构图、数据模型、检索管线 |

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
