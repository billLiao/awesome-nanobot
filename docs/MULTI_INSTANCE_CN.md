# Nanobot 多实例部署教程

> 详细指南：如何在同一台服务器上运行多个 nanobot 实例，每个实例使用独立配置和工作空间。

## 目录

1. [什么是多实例部署](#什么是多实例部署)
2. [为什么需要多实例](#为什么需要多实例)
3. [快速开始](#快速开始)
4. [配置详解](#配置详解)
5. [完整示例](#完整示例)
6. [路径解析规则](#路径解析规则)
7. [常见使用场景](#常见使用场景)
8. [Docker 多实例部署](#docker-多实例部署)
9. [Linux 服务多实例](#linux-服务多实例)
10. [故障排查](#故障排查)

---

## 什么是多实例部署

多实例部署允许你在同一台服务器上同时运行多个 nanobot 实例，每个实例：

- 📂 使用独立的配置文件
- 💾 拥有独立的工作空间（记忆、会话）
- 🔌 连接不同的聊天渠道（Telegram、Discord、飞书等）
- 🤖 可以使用不同的 AI 模型
- ⏰ 拥有独立的定时任务

---

## 为什么需要多实例

| 场景 | 说明 |
|------|------|
| 多平台支持 | 同时接入 Telegram、Discord、飞书、钉钉等不同渠道 |
| 环境隔离 | 分离测试环境和生产环境 |
| 多团队使用 | 为不同团队提供独立的 AI 助手 |
| 多租户服务 | 为不同客户提供独立的服务实例 |
| 模型隔离 | 不同实例使用不同的 AI 模型，优化成本 |

---

## 快速开始

### 步骤 1：创建实例目录

```bash
# 创建 Telegram 实例目录
mkdir -p ~/.nanobot-telegram
mkdir -p ~/.nanobot-telegram/workspace

# 创建 Discord 实例目录
mkdir -p ~/.nanobot-discord
mkdir -p ~/.nanobot-discord/workspace

# 创建飞书实例目录
mkdir -p ~/.nanobot-feishu
mkdir -p ~/.nanobot-feishu/workspace
```

### 步骤 2：创建配置文件

每个实例需要独立的 `config.json`：

```bash
# Telegram 实例配置
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
      "token": "YOUR_TEGRAM_BOT_TOKEN"
    }
  },
  "gateway": {
    "port": 18790
  }
}
EOF

# Discord 实例配置
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

### 步骤 3：启动实例

```bash
# 启动 Telegram 实例
nanobot gateway --config ~/.nanobot-telegram/config.json

# 启动 Discord 实例（不同端口）
nanobot gateway --config ~/.nanobot-discord/config.json --port 18791

# 启动飞书实例（不同端口）
nanobot gateway --config ~/.nanobot-feishu/config.json --port 18792
```

---

## 配置详解

### 核心配置项

| 配置项 | 说明 | 示例 |
|--------|------|------|
| `agents.defaults.workspace` | 工作空间目录 | `~/.nanobot-telegram/workspace` |
| `gateway.port` | 网关端口 | `18790`、`18791`、`18792` |
| `channels.*.enabled` | 启用渠道 | `true` / `false` |

### 最小配置示例

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

## 完整示例

### 三实例部署场景

假设你需要：
- 实例 1：Telegram 客服机器人（使用 GPT-4o Mini）
- 实例 2：Discord 娱乐机器人（使用 Claude Sonnet）
- 实例 3：飞书内部助手（使用 DeepSeek）

### 目录结构

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

### 启动脚本

```bash
#!/bin/bash
# start-all-instances.sh

# Telegram 实例
nanobot gateway --config ~/.nanobot-telegram/config.json &

# Discord 实例
nanobot gateway --config ~/.nanobot-discord/config.json --port 18791 &

# 飞书实例
nanobot gateway --config ~/.nanobot-feishu/config.json --port 18792 &

echo "所有实例已启动"
```

---

## 路径解析规则

理解路径解析对于正确配置多实例至关重要：

| 组件 | 来源 | 示例 |
|------|------|------|
| **配置文件** | `--config` 参数 | `~/.nanobot-telegram/config.json` |
| **工作空间** | `--workspace` 或配置文件中 `agents.defaults.workspace` | `~/.nanobot-telegram/workspace/` |
| **定时任务** | 配置目录下的 `cron/` | `~/.nanobot-telegram/cron/` |
| **媒体文件** | 配置目录下的 `media/` | `~/.nanobot-telegram/media/` |

### 工作空间覆盖

可以使用 `--workspace` 参数临时覆盖工作空间：

```bash
# 使用配置中的工作空间
nanobot gateway --config ~/.nanobot-telegram/config.json

# 临时覆盖工作空间（用于测试）
nanobot gateway --config ~/.nanobot-telegram/config.json --workspace /tmp/test-workspace
```

### CLI 会话

使用 `nanobot agent` 连接特定实例：

```bash
# 连接 Telegram 实例
nanobot agent -c ~/.nanobot-telegram/config.json -m "Hello"

# 连接 Discord 实例
nanobot agent -c ~/.nanobot-discord/config.json -m "Hello"

# 临时覆盖工作空间
nanobot agent -c ~/.nanobot-telegram/config.json -w /tmp/test-workspace -m "Hello"
```

> ⚠️ 注意：`nanobot agent` 启动的是本地 CLI Agent，不会连接到已运行的 `nanobot gateway` 进程。

---

## 常见使用场景

### 场景 1：多平台客服

```
实例 A: Telegram 客服 → 处理英文客户
实例 B: 飞书客服 → 处理中文客户
实例 C: 钉钉客服 → 处理企业内部咨询
```

### 场景 2：测试与生产隔离

```
实例 A (生产): ~/.nanobot-production/
实例 B (测试): ~/.nanobot-staging/
```

### 场景 3：多团队使用

```
实例 A: 团队 A 的 AI 助手 (GPT-4o)
实例 B: 团队 B 的 AI 助手 (Claude Sonnet)
实例 C: 团队 C 的 AI 助手 (DeepSeek)
```

---

## Docker 多实例部署

### Docker Compose 配置

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

### 目录结构

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

### 启动命令

```bash
docker compose up -d
```

---

## Linux 服务多实例

为每个实例创建独立的 systemd 服务：

### Telegram 实例服务

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

### Discord 实例服务

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

### 启用服务

```bash
# 重新加载 systemd
systemctl --user daemon-reload

# 启用并启动
systemctl --user enable --now nanobot-telegram
systemctl --user enable --now nanobot-discord

# 查看状态
systemctl --user status nanobot-telegram
systemctl --user status nanobot-discord

# 查看日志
journalctl --user -u nanobot-telegram -f
```

---

## 故障排查

### 常见问题

#### 1. 端口冲突

```
Error: Port 18790 is already in use
```

**解决方案**：确保每个实例使用不同端口

```bash
# 检查端口占用
lsof -i :18790
netstat -tlnp | grep 18790
```

#### 2. 工作空间冲突

**症状**：不同实例的记忆/会话混淆

**解决方案**：确保每个实例使用独立的工作空间

```json
{
  "agents": {
    "defaults": {
      "workspace": "~/.nanobot-instance/workspace"
    }
  }
}
```

#### 3. 配置文件路径错误

**症状**：找不到配置文件

**解决方案**：使用绝对路径

```bash
# 正确
nanobot gateway --config /home/user/.nanobot-telegram/config.json

# 错误（相对路径可能出问题）
nanobot gateway --config ~/.nanobot-telegram/config.json
```

#### 4. 权限问题

**症状**：无法读取配置文件或写入工作空间

**解决方案**：检查文件权限

```bash
chmod 600 ~/.nanobot-*/config.json
chmod 755 ~/.nanobot-*/workspace
```

---

## 相关链接

- [官方 README - Multiple Instances](https://github.com/HKUDS/nanobot#-multiple-instances)
- [配置文件说明](./TUTORIAL_CN.md)
- [渠道配置](./CHANNELS_CONFIG.md)

---

*本教程最后更新于 2026-03-14*