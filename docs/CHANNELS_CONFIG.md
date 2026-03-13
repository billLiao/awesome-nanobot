# Nanobot 渠道配置详细教程

> 本教程详细介绍 Nanobot（超轻量级 OpenClaw）的各种渠道配置方法，重点讲解飞书渠道的完整配置流程。

## 目录

1. [Nanobot 简介](#nanobot-简介)
2. [渠道配置概述](#渠道配置概述)
3. [飞书渠道配置](#飞书渠道配置)
4. [Telegram 渠道配置](#telegram-渠道配置)
5. [Discord 渠道配置](#discord-渠道配置)
6. [Slack 渠道配置](#slack-渠道配置)
7. [钉钉渠道配置](#钉钉渠道配置)
8. [WhatsApp 渠道配置](#whatsapp-渠道配置)
9. [邮件渠道配置](#邮件渠道配置)
10. [多渠道同时启用](#多渠道同时启用)
11. [安全与权限设置](#安全与权限设置)
12. [常见问题排查](#常见问题排查)

---

## Nanobot 简介

Nanobot 是 HKUDS 开发的超轻量级 AI Agent，代码量仅为 OpenClaw 的 2%，但提供完整的核心 Agent 功能。它支持多种消息平台，包括 Telegram、Discord、Slack、飞书、钉钉、WhatsApp 等。

### 核心特性

- **有状态记忆**：构建本地历史图谱，跨会话记住上下文
- **模型无关**：支持 OpenAI、Anthropic、Google、Ollama 等多种模型
- **即时 UI**：可在常用消息应用中直接使用

---

## 渠道配置概述

Nanobot 的渠道配置在 `~/.nanobot/config.json` 文件的 `channels` 字段中完成。每个渠道都有以下通用配置项：

| 配置项 | 类型 | 说明 |
|--------|------|------|
| `enabled` | boolean | 是否启用该渠道 |
| `allowFrom` | array | 允许发送消息的用户 ID 列表，`["*"]` 表示允许所有人 |

---

## 飞书渠道配置

飞书（Lark）是企业级协作平台，Nanobot 支持通过飞书开放平台集成。

### 步骤 1：创建飞书应用

1. 访问 [飞书开放平台开发者控制台](https://open.feishu.cn/app)
2. 点击「创建应用」，选择「企业自建应用」
3. 填写应用名称和描述，提交创建

### 步骤 2：获取应用凭证

1. 在应用详情页，点击「凭证与基础信息」
2. 记录 `App ID` 和 `App Secret`

### 步骤 3：添加 Bot 能力

1. 在「功能」页面，点击「添加能力」
2. 选择「Bot」能力并添加

### 步骤 4：申请权限

在「开发配置 > 权限管理」中，需要开启以下权限：

| 权限名称 | 权限码 | 说明 |
|----------|--------|------|
| 接收私聊消息 | `im:message.p2p_msg:readonly` | 获取用户发送给机器人的私聊消息 |
| 发送消息 | `im:message:send_as_bot` | 以机器人身份发送消息 |
| 接收群消息 | `im:message.group_at_msg:readonly` | 获取群聊中 @机器人的消息 |

### 步骤 5：配置事件订阅

1. 在「开发配置 > 事件与回调」中
2. 点击「添加事件」
3. 选择「接收消息 (im.message.receive_v1)」事件
4. 设置回调 URL（需要公网可访问）

### 步骤 6：发布应用

1. 在「版本管理与发布」中创建新版本
2. 填写版本信息并发布
3. 如需企业管理员审核

### 步骤 7：配置 Nanobot

在 `~/.nanobot/config.json` 中添加飞书配置：

```json
{
  "channels": {
    "feishu": {
      "enabled": true,
      "appId": "你的App ID",
      "appSecret": "你的App Secret",
      "encryptKey": "可选，加密密钥",
      "verificationToken": "可选，验证Token",
      "allowFrom": ["*"]  // 或指定用户 ID 列表
    }
  }
}
```

### 飞书配置完整示例

```json
{
  "channels": {
    "feishu": {
      "enabled": true,
      "appId": "cli_xxxxxxxxxxxxxx",
      "appSecret": "你的AppSecret",
      "encryptKey": "",
      "verificationToken": "",
      "allowFrom": ["ou_1234567890", "ou_0987654321"]
    }
  }
}
```

> **注意**：`allowFrom` 中可以使用用户 ID（`ou_xxx` 格式）或 `*` 表示允许所有人。

---

## Telegram 渠道配置

### 步骤 1：创建机器人

1. 在 Telegram 中搜索 @BotFather
2. 发送 `/newbot` 命令
3. 按照提示设置机器人名称和用户名
4. 获取机器人 Token

### 步骤 2：获取用户 ID

1. 在 Telegram 中搜索 @userinfobot
2. 启动机器人，获取你的 User ID

### 步骤 3：配置 Nanobot

```json
{
  "channels": {
    "telegram": {
      "enabled": true,
      "token": "你的Telegram Bot Token",
      "allowFrom": ["你的User ID"],
      "proxy": null  // 可选，如需代理可配置
    }
  }
}
```

---

## Discord 渠道配置

### 步骤 1：创建 Discord 应用

1. 访问 [Discord Developer Portal](https://discord.com/developers/applications)
2. 点击「New Application」
3. 填写应用名称

### 步骤 2：创建机器人

1. 在应用页面点击「Bot」
2. 点击「Reset Token」获取 Token
3. 启用「Message Content Intent」

### 步骤 3：邀请机器人

1. 点击「OAuth2 > URL Generator」
2. 选择 `bot` 和 `messages.read` 权限
3. 复制生成的 URL 并在浏览器中打开
4. 选择要添加机器人的服务器

### 步骤 4：获取频道 ID

1. 在 Discord 设置中启用「Developer Mode」
2. 右键点击频道，选择「Copy Channel ID」

### 步骤 5：配置 Nanobot

```json
{
  "channels": {
    "discord": {
      "enabled": true,
      "botToken": "你的Discord Bot Token",
      "channelIds": ["你的频道ID"],
      "allowFrom": [],
      "replyInThread": true,
      "reactEmoji": "eyes"
    }
  }
}
```

---

## Slack 渠道配置

### 步骤 1：创建 Slack 应用

1. 访问 [Slack API](https://api.slack.com/apps)
2. 点击「Create New App」
3. 选择「From scratch」
4. 填写应用名称和 workspace

### 步骤 2：配置权限

在「OAuth & Permissions」中添加以下 scopes：

- `chat:write` - 发送消息
- `channels:history` - 读取频道历史
- `groups:history` - 读取群组历史
- `im:history` - 读取私信历史
- `mpim:history` - 读取群私信历史

### 步骤 3：安装应用

1. 点击「Install to Workspace」
2. 授权并获取 Bot User OAuth Token

### 步骤 4：配置 Nanobot

```json
{
  "channels": {
    "slack": {
      "enabled": true,
      "mode": "socket",
      "botToken": "xoxb-你的Bot-Token",
      "appToken": "xapp-你的App-Token",
      "replyInThread": true,
      "reactEmoji": "eyes",
      "dm": {
        "enabled": true,
        "policy": "open"
      }
    }
  }
}
```

---

## 钉钉渠道配置

钉钉（DingTalk）是阿里巴巴集团推出的企业通讯和协作平台，Nanobot 支持通过钉钉开放平台集成。

### 步骤 1：创建钉钉应用

1. 登录 [钉钉开放平台](https://open.dingtalk.com/)
2. 点击「应用开发 > 企业内部开发」
3. 点击「创建应用」
4. 填写应用名称（如「Nanobot AI 助手」）和图标
5. 选择应用类型为「企业内部开发」

### 步骤 2：获取应用凭证

1. 在应用详情页，点击「凭证与基础信息」
2. 记录 `Client ID`（应用 ID）和 `Client Secret`（应用密钥）

### 步骤 3：添加机器人能力

1. 在「能力配置」页面，点击「添加能力」
2. 选择「机器人」能力并添加

### 步骤 4：申请权限

在「权限管理」中，需要开启以下权限：

| 权限名称 | 权限码 | 说明 |
|----------|--------|------|
| 接收消息 | `im:message` | 获取用户发送给机器人的消息 |
| 发送消息 | `im:message:send` | 以机器人身份发送消息 |
| 通讯录只读权限 | `contact:readonly` | 获取企业成员信息 |

### 步骤 5：配置回调地址

1. 在「开发配置 > 消息事件」中
2. 点击「添加回调地址」
3. 填写你的公网回调 URL（如 `https://your-domain.com/webhook/dingtalk`）
4. 订阅以下事件：
   - `im.message.receive` - 接收消息事件

### 步骤 6：发布应用

1. 在「版本管理与发布」中创建新版本
2. 填写版本信息
3. 提交发布申请
4. 企业管理员审核通过后生效

### 步骤 7：配置 Nanobot

在 `~/.nanobot/config.json` 中添加钉钉配置：

```json
{
  "channels": {
    "dingtalk": {
      "enabled": true,
      "clientId": "你的Client ID",
      "clientSecret": "你的Client Secret",
      "allowFrom": ["*"]
    }
  }
}
```

### 钉钉配置完整示例

```json
{
  "channels": {
    "dingtalk": {
      "enabled": true,
      "clientId": "dingo_xxxxxxxxxxxxxx",
      "clientSecret": "你的ClientSecret",
      "allowFrom": ["manager1234"]
    }
  }
}
```

> **注意**：`allowFrom` 中可以使用用户 ID（格式：`manager1234`）或 `*` 表示允许所有人。钉钉的用户 ID 通常是员工号或企业内唯一标识。

---

## WhatsApp 渠道配置

WhatsApp 渠道需要通过 WhatsApp Business API 或第三方服务（如 Twilio）配置。

### 配置示例

```json
{
  "channels": {
    "whatsapp": {
      "enabled": true,
      "phoneNumberId": "你的Phone Number ID",
      "accessToken": "你的Access Token",
      "verifyToken": "你的Verify Token",
      "allowFrom": ["*"]
    }
  }
}
```

---

## 邮件渠道配置

### 配置示例

```json
{
  "channels": {
    "email": {
      "enabled": true,
      "imapHost": "imap.example.com",
      "imapPort": 993,
      "imapUsername": "your-email@example.com",
      "imapPassword": "your-password",
      "imapUseSsl": true,
      "smtpHost": "smtp.example.com",
      "smtpPort": 587,
      "smtpUsername": "your-email@example.com",
      "smtpPassword": "your-password",
      "smtpUseTls": true,
      "fromAddress": "nanobot@example.com",
      "autoReplyEnabled": true,
      "pollIntervalSeconds": 30,
      "allowFrom": ["*"]
    }
  }
}
```

---

## 多渠道同时启用

Nanobot 支持同时启用多个渠道，以下是完整的多渠道配置示例：

```json
{
  "channels": {
    "feishu": {
      "enabled": true,
      "appId": "cli_xxx",
      "appSecret": "xxx",
      "allowFrom": ["*"]
    },
    "telegram": {
      "enabled": true,
      "token": "xxx",
      "allowFrom": ["123456789"]
    },
    "dingtalk": {
      "enabled": true,
      "clientId": "xxx",
      "clientSecret": "xxx",
      "allowFrom": ["*"]
    },
    "discord": {
      "enabled": false,
      "botToken": "xxx",
      "channelIds": []
    },
    "slack": {
      "enabled": false,
      "botToken": "xoxb-xxx"
    }
  }
}
```

---

## 安全与权限设置

### allowFrom 配置

`allowFrom` 字段用于控制哪些用户可以与 Nanobot 交互：

| 值 | 说明 |
|----|------|
| `["*"]` | 允许所有人 |
| `["user1", "user2"]` | 只允许指定用户 |
| `[]` | 禁止所有人（需配合其他机制） |

### 飞书用户 ID 获取方式

1. 在飞书中打开与机器人的对话
2. 点击机器人头像，查看个人资料
3. 复制用户 ID（格式：`ou_xxx`）

### 敏感操作建议

1. **限制允许用户**：生产环境建议指定具体用户 ID
2. **使用审批模式**：exec 工具可启用审批模式
3. **限制工作目录**：设置 `restrictToWorkspace: true`

---

## 常见问题排查

### 1. 渠道无法启动

检查日志输出：
```bash
nanobot gateway --verbose
```

常见错误：
- Token/凭证无效
- 网络连接问题
- 权限不足

### 2. 消息发送失败

- 检查 `allowFrom` 配置
- 确认机器人有发送消息权限
- 检查目标用户是否允许接收消息

### 3. 飞书回调无法接收

- 确认回调 URL 可公网访问
- 检查防火墙/安全组配置
- 验证 encryptKey 和 verificationToken

### 4. 多渠道消息混乱

- 每个渠道独立处理消息
- 使用 `memory` 功能保持会话上下文

---

## 启动 Nanobot Gateway

配置完成后，启动 Nanobot Gateway：

```bash
# 启动网关
nanobot gateway

# 或指定端口
nanobot gateway --port 18790

# 调试模式
nanobot gateway --verbose
```

启动成功后，你会看到类似输出：

```
🐈 Starting nanobot gateway on port 18790...
✓ Channels enabled: feishu, telegram, dingtalk
✓ Heartbeat: every 30m
```

---

## 参考资源

- [Nanobot GitHub](https://github.com/HKUDS/nanobot)
- [飞书开放平台文档](https://open.feishu.cn/document/)
- [Telegram Bot API](https://core.telegram.org/bots/api)
- [Discord Developer Portal](https://discord.com/developers/applications)
- [Slack API](https://api.slack.com/)

---

*本教程最后更新于 2026-03-13*