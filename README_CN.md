<div align="center">
<h1>Awesome Nanobot</h1>
<p><strong>nanobot 资源大全 - 精选工具、技能、插件与项目</strong></p>
<p>
<a href="https://github.com/HKUDS/nanobot">官方仓库</a> •
<a href="#官方资源">资源</a> •
<a href="#技能与插件">技能</a> •
<a href="#社区">社区</a>
</p>
<p>
简体中文 | <a href="README.md">English</a>
</p>
<p>
<a href="https://github.com/billLiao/awesome-nanobot/stargazers"><img src="https://img.shields.io/github/stars/billLiao/awesome-nanobot?style=flat" alt="Stars"></a>
</p>
</div>

---

> **注意**：本文档聚焦于 [HKUDS/nanobot](https://github.com/HKUDS/nanobot)（Python 项目）。GitHub 上还有一个名称相似的项目，请确保你使用的是正确的仓库。

## 目录

- [项目简介](#项目简介)
- [官方资源](#官方资源)
- [快速上手](#快速上手)
- [LLM 提供商](#llm-提供商)
- [聊天渠道](#聊天渠道)
- [MCP 支持](#mcp-支持)
- [部署方式](#部署方式)
- [技能与插件](#技能与插件)
- [生态项目](#生态项目)
- [桌面客户端](#桌面客户端)
- [语言移植版](#语言移植版)
- [教程资源](#教程资源)
- [安全指南](#安全指南)
- [社区交流](#社区交流)
- [贡献指南](#贡献指南)

---

## 项目简介

**nanobot** 是一个超轻量个人 AI Assistant / Agent 框架，灵感来自 OpenClaw。

**核心特点：**
- 📦 约 ~4,000 行核心代码，强调可读性与研究友好
- 🔌 多 LLM Provider、多 Chat Channel、多工具支持
- 💾 长期记忆、定时任务
- 🚀 MCP 支持、进度流式输出

---

## 官方资源

| 资源 | 说明 |
|------|------|
| [GitHub 仓库](https://github.com/HKUDS/nanobot) | 官方主仓库 |
| [Releases](https://github.com/HKUDS/nanobot/releases) | 版本更新日志 |
| [安全策略](https://github.com/HKUDS/nanobot/blob/main/SECURITY.md) | 生产环境必读 |
| [用户画像模板](https://github.com/HKUDS/nanobot/blob/main/workspace/USER.md) | 个性化配置模板 |
| [nanobot.club](http://nanobot.club/) | 官方网站 |

## 快速上手

| 安装方式 | 命令 |
|----------|------|
| **uv（推荐）** | `uv tool install nanobot-ai` |
| **PyPI** | `pip install nanobot-ai` |
| **源码安装** | `git clone https://github.com/HKUDS/nanobot.git && cd nanobot && pip install -e .` |

**基本命令：**
```bash
nanobot onboard    # 初始化配置
nanobot agent      # 启动 CLI 对话
nanobot gateway    # 启动网关（接入聊天渠道）
```

📁 **详细教程**：[docs/TUTORIAL_CN.md](docs/TUTORIAL_CN.md) | [English Tutorial](docs/TUTORIAL.md)

### CLI 命令参考

| 命令 | 说明 |
|------|------|
| `nanobot onboard` | 初始化配置和工作空间 |
| `nanobot agent -m "..."` | 与 Agent 对话 |
| `nanobot agent` | 交互式对话模式 |
| `nanobot agent --no-markdown` | 纯文本回复 |
| `nanobot agent --logs` | 显示运行时日志 |
| `nanobot gateway` | 启动网关（接入聊天渠道） |
| `nanobot status` | 显示状态 |
| `nanobot provider login openai-codex` | OAuth 登录 |
| `nanobot channels login` | 链接 WhatsApp（扫码） |
| `nanobot channels status` | 显示渠道状态 |

### 心跳任务（Periodic Tasks）

网关每 30 分钟自动唤醒，检查 `HEARTBEAT.md` 文件并执行任务：

```markdown
## Periodic Tasks
- [ ] Check weather forecast and send a summary
- [ ] Scan inbox for urgent emails
```

Agent 也可以自行管理此文件（告诉它"添加一个周期性任务"即可）。

## LLM 提供商

nanobot 支持多种大语言模型提供商：

| 提供商 | 类型 | 说明 |
|--------|------|------|
| OpenRouter | API | 单一 API 接入多种模型 |
| Anthropic | API | Claude 系列模型 |
| OpenAI | API | GPT 系列模型 |
| Azure OpenAI | API | 微软 Azure OpenAI |
| DeepSeek | API | DeepSeek 模型 |
| Gemini | API | Google Gemini 模型 |
| VolcEngine | API | 火山引擎 |
| Qwen / DashScope | API | 阿里通义千问 |
| Moonshot | API | Kimi 模型 |
| Groq | API | 高速推理 |
| Ollama | 本地 | 本地模型支持 |
| Mistral | API | Mistral AI 模型 |
| 自定义端点 | API | OpenAI 兼容 API |
| GitHub Copilot | OAuth | OAuth 认证 |
| OpenAI Codex | OAuth | OAuth 认证 |

📖 **配置详情**：[官方 README - Providers](https://github.com/HKUDS/nanobot#providers)

## 聊天渠道

| 渠道 | 状态 | 说明 |
|------|------|------|
| Telegram | ✅ 稳定 | 推荐新手使用，支持草稿流式输出 |
| Discord | ✅ 稳定 | 完整支持，长消息自动分割 |
| 飞书 | ✅ 稳定 | 国内企业 IM，多模态文件接收 |
| 钉钉 | ✅ 稳定 | 国内企业 IM，媒体消息支持 |
| WhatsApp | ✅ 稳定 | 需要 Node.js 桥接，媒体收发 |
| Slack | ✅ 稳定 | 企业聊天，文件发送 |
| Email | ✅ 稳定 | IMAP/SMTP |
| QQ | ✅ 稳定 | 通过 go-cqhttp/NapCat |
| MoChat | ✅ 稳定 | Claw IM |
| Matrix | ✅ 稳定 | 去中心化通讯协议 |

📖 **渠道配置**：[官方 README - Chat Apps](https://github.com/HKUDS/nanobot#-chat-apps)

## MCP 支持

nanobot 支持 Model Context Protocol (MCP) 扩展能力，可连接外部工具服务器：

| 传输方式 | 说明 |
|----------|------|
| stdio | 本地 MCP 服务器（通过 npx/uvx） |
| HTTP | 远程 MCP 服务器（SSE 协议） |

### MCP 配置示例

```json
{
  "tools": {
    "mcpServers": {
      "filesystem": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/dir"]
      },
      "my-remote-mcp": {
        "url": "https://example.com/mcp/",
        "headers": { "Authorization": "Bearer xxxxx" }
      }
    }
  }
}
```

### 高级配置

- **工具超时**：`toolTimeout` 设置单个工具调用超时时间（默认 30s）
- **工具筛选**：`enabledTools` 只注册 MCP 服务器的部分工具
- **配置兼容**：格式兼容 Claude Desktop / Cursor，可直接复制配置

📖 **MCP 配置**：[官方 README - MCP](https://github.com/HKUDS/nanobot#mcp-model-context-protocol)

## 部署方式

| 方式 | 说明 |
|------|------|
| [Docker](https://github.com/HKUDS/nanobot#-docker) | 官方 Docker 支持 |
| [Docker Compose](https://github.com/HKUDS/nanobot#-docker) | 一键部署 |
| [Zeabur 模板](https://zeabur.com/templates/5XVJX8) | 一键云端部署 |
| [Render 模板](https://github.com/render-examples/nanobot-render) | 一键 Render 部署模板 |
| [nanobot-docker](https://github.com/maruf009sultan/nanobot-docker) | ⭐ 17 | nanobot 的非交互式 Docker 一键部署（非官方）|
| [Linux Service](https://github.com/HKUDS/nanobot#-linux-service) | systemd 用户服务 |

### 多实例支持

nanobot 支持同时运行多个实例，每个实例使用独立配置：

```bash
# 实例 A - Telegram bot
nanobot gateway --config ~/.nanobot-telegram/config.json

# 实例 B - Discord bot
nanobot gateway --config ~/.nanobot-discord/config.json --port 18791

# 实例 C - 飞书 bot
nanobot gateway --config ~/.nanobot-feishu/config.json --port 18792
```

📖 **多实例配置**：[官方 README - Multiple Instances](https://github.com/HKUDS/nanobot#-multiple-instances)

## 技能与插件

| 项目 | Stars | 说明 |
|------|-------|------|
| [nanobot-llm-wiki](https://github.com/yu-xin-c/nanobot-llm-wiki) | ⭐ 1 | NanoBot 的 LLM Wiki 长期记忆插件 |
| [nanobot-hindsight-memory](https://github.com/bmtrnavsky/nanobot-hindsight-memory-and-skill-review) | ⭐ 1 | Hindsight 记忆插件（受控 Recall/Retain）+ 夜间自我改进技能审查 |

### 官方内置技能

| 技能 | 说明 | 状态 |
|------|------|------|
| [memory](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/memory) | 长期记忆系统 | 内置 |
| [cron](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/cron) | 定时任务 | 内置 |
| [weather](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/weather) | 天气预报 | 内置 |
| [clawhub](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/clawhub) | 技能注册中心搜索 | 内置 |
| [skill-creator](https://github.com/HKUDS/nanobot/tree/main/nanobot/skills/skill-creator) | 创建自定义技能 | 内置 |

### 社区技能

| 技能 | 作者 | 说明 |
|------|------|------|
| [jina-search-skill](https://github.com/billLiao/jina-search-skill) | billLiao | Jina.ai 联网搜索和网页阅读 |
| [bark-push-skills](https://github.com/billLiao/bark-push-skills) | billLiao | iOS 推送通知 |
| [nanobot-skills](https://github.com/ruslanstarikov/nanobot-skills) | ruslanstarikov | 自定义技能集合 |
| [nanobot-skills](https://github.com/CCAgentOrg/nanobot-skills) | CCAgentOrg | github-watcher, youtube-recommender |
| [nanobot-skill-weather](https://github.com/kombalarasoftware-cmd/nanobot-skill-weather) | kombalarasoftware | 天气技能 |
| [nanobot-skill-finance](https://github.com/kombalarasoftware-cmd/nanobot-skill-finance) | kombalarasoftware | 金融数据技能 |
| [nanobot-skill-notes](https://github.com/kombalarasoftware-cmd/nanobot-skill-notes) | kombalarasoftware | 笔记管理 |
| [nanobot-skill-calendar](https://github.com/kombalarasoftware-cmd/nanobot-skill-calendar) | kombalarasoftware | 日历集成 |
| [nanobot-skill-translator](https://github.com/kombalarasoftware-cmd/nanobot-skill-translator) | kombalarasoftware | 翻译技能 |
| [nanobot-channel-weixin](https://github.com/alvis233/nanobot-channel-weixin) | alvis233 | 个人微信频道插件（基于 iLink Bot API）|

### 技能注册中心

| 平台 | 说明 |
|------|------|
| [ClawHub](https://clawhub.ai/) | 官方技能注册中心，搜索和安装技能 |

## 生态项目

| 项目 | Stars | 描述 |
|---------|-------|-------------|
| [nanobot](https://github.com/obot-platform/nanobot) | ⭐ 1.3k | 构建 MCP Agents — 官方 nanobot，增强的 MCP 支持 |
| [NanoResearch](https://github.com/OpenRaiser/NanoResearch) | ⭐ 1.4k | 🦞+🔬 基于 nanobot 的自主 AI 研究助手 |
| [TinyClaw](https://github.com/warengonzaga/tinyclaw) | ⭐ 287 | 原始 Tiny Claw，你的个人自主 AI 伴侣 |
| [OpenLegion](https://github.com/openlegion-ai/openlegion) | ⭐ 116 | 安全自主 AI 代理舰队平台 — Docker 隔离、多提供商 |
| [MultiUserClaw](https://github.com/johnson7788/MultiUserClaw) | ⭐ 317 | OpenClaw/NanoBot 多用户支持 |
| [NanoBot](https://github.com/fumiama/NanoBot) | ⭐ 60 | 类 ZeroBot 的 QQ 频道/群聊机器人框架 |
| [FastSkills](https://github.com/matthewlee0102/FastSkills) | ⭐ 15 | 将 Agent Skills 引入任何 MCP 兼容代理的 MCP 服务器 |
| [nanobot-custom](https://github.com/deeeeeeeeap/nanobot-custom) | ⭐ 65 | 基于 nanobot 的个人 AI 助手 — 支持 MiniMax、Gemini 多模型切换 |
| [MoChat](https://github.com/HKUDS/MoChat) | - | Claw IM 客户端，nanobot 频道支持 |
| [ClawWork](https://github.com/HKUDS/ClawWork) | - | OpenClaw/Nanobot 集成 |
| [SwarmClaw](https://github.com/swarmclawai/swarmclaw) | ⭐ 656 | 多代理群体协调 |
| [Ferrum Bot](https://github.com/lispking/ferrum-bot) | ⭐ 25 | Rust 编写的 AI 代理框架 |
| [GeneClaw](https://github.com/Clawland-AI/Geneclaw) | ⭐ 44 | 具有 5 层安全网关的自我进化 AI 代理框架 |
| [TinyClaw](https://github.com/D-Sketon/tinyclaw) | ⭐ 3 | 基于 nanobot 的轻量级代理框架 |
| [nanobot-web-console](https://github.com/tankyhsu/nanobot-web-console) | ⭐ 13 | 单文件 Web 控制台，实时流式聊天 |
| [nanobot-setup](https://github.com/volkergrabbe/nanobot-setup) | ⭐ 2 | 自动化安装脚本（Docker + Redis + Qdrant）|
| [NanoBot-Android](https://github.com/AbuZar-Ansarii/NanoBot-Android) | ⭐ 37 | Android 个人 AI 助手 — 灵感来自 nanobot |
| [OSA](https://github.com/Miosa-osa/OSA) | ⭐ 46 | 最优系统代理 — 最大化信号提取 |
| [ByeByeClaw](https://github.com/wanikua/byebyeclaw) | ⭐ 76 | 一键卸载所有 Claw 系列 AI 代理，无残留文件 |
| [NanoClaw](https://github.com/nanocoai/nanoclaw) | ⭐ 31k | OpenClaw 轻量替代方案 — 容器化运行，支持 WhatsApp、Telegram、Slack、Discord、Gmail |
| [nanobot-study](https://github.com/WangyiNTU/nanobot-study) | ⭐ 17 | 3 天掌握 AI 代理助手 — 学习计划 |
| [nanobot-viking](https://github.com/tankyhsu/nanobot-viking) | ⭐ 10 | OpenViking 知识库集成 — RAG、语义搜索、向量嵌入 |
| [nanobot-teams](https://github.com/hyokyunAn/nanobot_teams) | ⭐ 0 | 管理多个在隔离工作空间中协作的 AI 代理团队 |
| [nanobot-feishu-specialized](https://github.com/Wuuu-uu/nanobot-feishu-specilized) | ⭐ 70 | 飞书专用版本，增强功能 |
| [LemonClaw](https://github.com/hedging8563/lemonclaw) | ⭐ 1 | AI Agent Platform (MIT, fork of nanobot) |
| [nanobot-docker](https://github.com/ciri/nanobot-docker) | ⭐ 6 | nanobot 的 Docker 部署配置 |
| [nanobot-webgui](https://github.com/lucmuss/nanobot-webgui) | ⭐ 22 | 生产级 Web GUI 分支，包含设置向导、MCP 管理、聊天、记忆和管理控制 |
| [nanobot-webui](https://github.com/Good0007/nanobot-webui) | ⭐ 151 | nanobot 自托管 Web 管理面板 |
| [nanobot-task-pipeline](https://github.com/Minggnim-jpg/nanobot-task-pipeline) | ⭐ 14 | nanobot & Claude Code 驱动的自动化任务流水线 — 多阶段工作流，心跳调度器 |
| [nanobot-searxng-search](https://github.com/SJK-py/nanobot-searxng-search) | ⭐ 4 | Nanobot 的 SearXNG 搜索技能 — 自托管搜索集成 |
| [nanobot-a2a-proxy](https://github.com/450home/nanobot-a2a-proxy) | ⭐ 1 | nanobot 代理通信的 A2A 代理 |
| [nanobot-ts](https://github.com/rzx007/nanobot-ts) | ⭐ 14 | nanobot 的 TypeScript 版本 — 超轻量个人 AI 助手框架 |
| [nanobot-hass](https://github.com/licheng5625/nanobot-hass) | ⭐ 1 | Home Assistant 的 nanobot 对话代理自定义组件 |
| [nanobot-on-rpi](https://github.com/msaltnet/nanobot-on-rpi) | ⭐ 0 | 在树莓派上运行 nanobot 的配方 |
| [NanoMate](https://github.com/shenmintao/NanoMate) | ⭐ 87 | nanobot × SillyTavern，伴侣模式 |
| [ShibaClaw](https://github.com/RikyZ90/ShibaClaw) | ⭐ 80 | 自托管 AI 助手框架 — 多渠道（Telegram、Discord、Slack）、并行代理、MCP 支持、带 OAuth 的 WebUI |
| [nanoorabot](https://github.com/valenwong-exa/nanoorabot) | ⭐ 15 | 基于 nanobot & nanobot-webui 的 AI 系统管理员机器人，可长期自主运行 |
| [clawos](https://github.com/mrytsr/clawos) | ⭐ 17 | 支持 openclaw、nanobot、picoclaw、nullclaw 的 Linux 面板 |
| [Finclaw](https://github.com/martinpmm/Finclaw) | ⭐ 12 | 基于 nanobot 的主动式金融助手 |
| [smith](https://github.com/vseplet/smith) | ⭐ 8 | 可定制的轻量级 Telegram Clawdbot |
| [Claude-Zeroclaw](https://github.com/vaskesvo5321/Claude-Zeroclaw) | ⭐ 7 | 轻量级守护进程 — 将 Claude Code 变为任务调度器和 Telegram 助手 |
| [KnowAct](https://github.com/HITsz-TMG/KnowAct) | ⭐ 484 | 基于 nanobot 的递归自我改进个人助手 |
| [Syll](https://github.com/THU-SAGE/syll) | ⭐ 303 | 自托管伴侣运行时（nanobot 分支）— Web UI、聊天频道、主动仪式、Markdown 技能 |
## 桌面客户端

| 项目 | Stars | 描述 |
|---------|-------|-------------|
| [nanobot-desktop](https://github.com/EvannZhongg/nanobot-desktop) | ⭐ 51 | Tauri + React 桌面客户端 |
| [nanobot-webui](https://github.com/codemo1991/nanobot-webui) | ⭐ 31 | Web UI，可视化配置和知识管理 |
| [nanoBot-ui](https://github.com/qq695500710-ui/nanoBot-ui) | ⭐ 173 | 即开即用的 nanobot UI — Windows 10+ 可直接使用 |
| [huanzhen-secretary](https://github.com/kuhua7902-debug/huanzhen-secretary) | ⭐ 19 | 基于 nanobot 的 Windows 桌面 AI 智能秘书 |
## 语言移植版

| 项目 | Stars | 描述 |
|---------|-------|-------------|
| [NanoBot.net](https://github.com/lepollo/NanoBot.net) | ⭐ 13 | .NET 10 移植版 |
| [nanobot-rs](https://github.com/open-vibe/nanobot-rs) | ⭐ 9 | Rust 移植版 |
| [sharpclaw](https://github.com/imxcstar/sharpclaw) | ⭐ 25 | 具有长期记忆的 AI 代理（.NET 10）|
| [maxclaw](https://github.com/Lichas/maxclaw) | ⭐ 231 | 超轻量级 Go 语言 AI 助手 |
| [agent-diva](https://github.com/ProjectViVy/agent-diva) | ⭐ 62 | 下一代 AI 代理（nanobot-rs-pro，Rust）|
| [MetalClaw](https://github.com/JunSuzuki1973/MetalClaw) | ⭐ 3 | 个性化 AI 助手分支 |
| [nano-claw](https://github.com/hustcc/nano-claw) | ⭐ 67 | 🦞 Claw 是你在自己的设备上运行的个人 AI 助手，但更轻量（TypeScript）|
| [nanobot-golang](https://github.com/ajiany/nanobot-golang) | ⭐ 0 | Go 语言轻量级、数据驱动的 AI 助手框架。18+ LLM 提供商、9 个聊天频道、MCP 工具 |
| [nanobot-go](https://github.com/cuichuankai/nanobot-go) | ⭐ 6 | nanobot 的 Go 语言实现 |
| [mini_nanobot](https://github.com/mu-xi-mu-xi/mini_nanobot) | ⭐ 12 | 用于学习的轻量级 LLM 代理框架 |
| [PP-Claw](https://github.com/yangkun19921001/PP-Claw) | ⭐ 37 | Go 语言版 nanobot |
| [nanobot-eino](https://github.com/iamclancyliang/nanobot-eino) | ⭐ 40 | 基于 Golang 和 Cloudwego Eino 框架的 AI Agent 个人助手 |
| [Krill.jl](https://github.com/whanyu1212/Krill.jl) | ⭐ 29 | 纯 Julia 编写的轻量级 nanobot/OpenClaw 变体 |
| [nanobot-rs](https://github.com/yjhmelody/nanobot-rs) | ⭐ 15 | 极简 openclaw 风格 AI 代理（Rust）|
## 集成项目

| 项目 | Stars | 描述 |
|---------|-------|-------------|
| [NanoBot-Plugin](https://github.com/FloatTech/NanoBot-Plugin) | ⭐ 105 | QQ 机器人插件集合 |
| [agentclub](https://github.com/dantezhu/agentclub) | ⭐ 5 | 开源聊天服务器 — 支持人类与 AI 代理，含 Nanobot 频道 |
| [Nanobot-Feishu](https://github.com/auenger/Nanobot-Feishu) | ⭐ 13 | Nanobot 集成 GLM 和飞书 |
| [Codex-Listener](https://github.com/TalexCK/Codex-Listener) | ⭐ 15 | 帮助 nanobot 等代理使用 Codex 的监听器 |
## 教程资源

| 资源 | 语言 | 类型 |
|------|------|------|
| [完整教程](docs/TUTORIAL_CN.md) | 中文 | 从安装到部署完整指南 |
| [Tutorial](docs/TUTORIAL.md) | English | Complete guide |
| [DataCamp 教程](https://www.datacamp.com/tutorial/nanobot-tutorial) | English | 第三方教程 |
| [YouTube 演示](https://www.youtube.com/watch?v=AKxiKb42Cqk) | English | Ollama + Telegram 安装演示 |
| [架构解读](https://jinlow.medium.com/nanobot-architecture-teardown-4-000-lines-achieving-openclaw-capability-3f242113ccbc) | English | 架构深度分析 |
| [nanobot-learn](https://github.com/WOWCharlotte/nanobot-learn) | 中文 | 七天学会 Nanobot 设计原理 |
| [byte-of-nanobot](https://github.com/sine-io/byte-of-nanobot) | 中文 | 面向零基础用户的 nanobot 教程，从"能跑"到"懂原理" |
| [agent-tutor](https://github.com/ywz456/agent-tutor) | 中文 | 从 0 到 1 搭建生产级 AI Agent 实战教程 |
| [how-ai-agents-remember](https://github.com/breath57/how-ai-agents-remember) | 中/EN | 源码级逆向工程 nanobot 等 Agent 记忆系统 — 架构图、数据模型、检索管线 |
| [learn-nanobot](https://github.com/bcefghj/learn-nanobot) | 中文 | nanobot 面试学习指南 — 17章深度教程、134道八股文、哆啦A梦漫画图解 |
| [agent-unpacked](https://github.com/yu-xin-c/agent-unpacked) | 中文 | Agent 源码拆解教程：DSH、PI Agent 与 nanobot |

## 安全指南

> ⚠️ **重要**：生产环境部署前请务必阅读 [安全策略](https://github.com/HKUDS/nanobot/blob/main/SECURITY.md)

**关键安全实践：**

| 实践 | 说明 |
|------|------|
| API Key 管理 | 不要提交到仓库；设置 `chmod 600 ~/.nanobot/config.json` |
| 渠道访问控制 | 生产环境必须配置 `allowFrom` 白名单（v0.1.4.post4+ 空数组默认拒绝所有人） |
| 工作空间限制 | 设置 `tools.restrictToWorkspace=true` 限制所有工具访问范围 |
| 命令执行 | 使用受限用户运行；开启审计日志 |
| 依赖安全 | 定期运行 `pip-audit` / `npm audit` |
| 路径追加 | 使用 `tools.exec.pathAppend` 添加额外 PATH 目录 |

## 社区交流

| 平台 | 链接 |
|------|------|
| GitHub Discussions | [github.com/HKUDS/nanobot/discussions](https://github.com/HKUDS/nanobot/discussions) |
| Discord | [discord.gg/MnCvHqpUGB](https://discord.gg/MnCvHqpUGB) |
| 微信 / 飞书群 | 查看 [COMMUNICATION.md](https://github.com/HKUDS/nanobot/blob/main/COMMUNICATION.md) |

## 贡献指南

欢迎贡献！提交 PR 前请阅读 [贡献指南](CONTRIBUTING.md)。

**规范要求：**
- 只添加可验证的链接
- 每条资源附带简要说明
- 第三方内容需明确标注
- 定期检查链接可用性

---

## 许可证

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

在法律允许的范围内，贡献者已放弃本作品的所有版权和相关权利。
