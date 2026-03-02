# Nanobot 完整教程

## 目录
- [简介](#简介)
- [安装](#安装)
- [配置](#配置)
- [基本使用](#基本使用)
- [高级功能](#高级功能)
- [故障排除](#故障排除)

## 简介

Nanobot 是一个超轻量级 AI 助手框架，支持多种大语言模型提供商和聊天频道。

## 安装

### 方法 1：使用 uv（推荐）
```bash
uv tool install nanobot-ai
```

### 方法 2：使用 pip
```bash
pip install nanobot-ai
```

### 方法 3：从源码安装
```bash
git clone https://github.com/HKUDS/nanobot.git
cd nanobot
pip install -e .
```

## 配置

### 初始化配置
```bash
nanobot onboard
```

### 配置 LLM 提供商
编辑 `~/.nanobot/config.json`：
```json
{
  "llm": {
    "provider": "openrouter",
    "api_key": "your-api-key"
  }
}
```

### 配置聊天频道
在 `config.json` 中添加频道配置：
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

## 基本使用

### 启动 CLI 代理
```bash
nanobot agent
```

### 启动网关
```bash
nanobot gateway
```

### 可用命令
- `nanobot onboard` - 初始化配置
- `nanobot agent` - 启动 CLI 对话
- `nanobot gateway` - 启动聊天频道网关
- `nanobot skills` - 列出可用技能

## 高级功能

### 技能（Skills）
Nanobot 支持各种技能：
- **memory**：长期记忆系统
- **cron**：定时任务
- **weather**：天气预报
- **clawhub**：技能注册表搜索
- **skill-creator**：创建自定义技能

### MCP 支持
Nanobot 支持模型上下文协议（MCP），可通过 stdio 或 HTTP 传输扩展功能。

### 多 LLM 提供商
支持的提供商包括：
- OpenRouter
- Anthropic（Claude）
- OpenAI（GPT）
- 深度求索（DeepSeek）
- Gemini
- 通义千问（Qwen/DashScope）
- 月之暗面（Moonshot/Kimi）
- Groq
- 自定义端点

## 故障排除

### 常见问题

**API 密钥错误**
- 确保 `config.json` 中正确设置了 API 密钥
- 检查文件权限：`chmod 600 ~/.nanobot/config.json`

**频道连接失败**
- 验证机器人令牌/凭据
- 检查 `allowFrom` 白名单配置
- 确保网络连接正常

**找不到技能**
- 通过 ClawHub 安装技能：`nanobot skill install <skill-name>`
- 在注册表中检查技能可用性

### 获取帮助
- GitHub 讨论区：https://github.com/HKUDS/nanobot/discussions
- Discord: https://discord.gg/MnCvHqpUGB
- 官方文档：https://github.com/HKUDS/nanobot
