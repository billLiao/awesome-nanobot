# Nanobot 新功能需求汇总（来自官方 Issues）

> 本文档汇总自 HKUDS/nanobot 官方仓库的 Open Issues，反映了用户最迫切需要的新功能和改进。

最后更新：2026-03-14

---

## 🔥 高优先级功能需求

### 1. 企业微信 (WeCom) 支持
- **Issue**: [#2011](https://github.com/HKUDS/nanobot/issues/2011)
- **标签**: question
- **描述**: 添加企业微信应用渠道支持
- **状态**: Open

### 2. 多个自定义 Custom Provider 支持
- **Issue**: [#1991](https://github.com/HKUDS/nanobot/issues/1991)
- **描述**: 希望 nanobot 可以支持多个自定义 custom provider
- **状态**: Open

### 3. NapCat QQ 频道支持
- **Issue**: [#2016](https://github.com/HKUDS/nanobot/issues/2016)
- **描述**: 添加 NapCat QQ 渠道支持，包含消息去抖和输入模拟
- **状态**: Open

### 4. QQ 图片识别功能
- **Issue**: [#2000](https://github.com/HKUDS/nanobot/issues/2000)
- **标签**: enhancement
- **描述**: nanobot 接 QQ，增加图片识别功能
- **状态**: Open

### 5. Token/Cost 跟踪日志
- **Issue**: [#2020](https://github.com/HKUDS/nanobot/issues/2020)
- **标签**: feature request, good first issue
- **描述**: 简单的使用日志功能，用于 token/成本跟踪
- **状态**: Open

---

## ⚡ 中优先级功能需求

### 6. Tavily Web Search Provider
- **Issue**: [#2012](https://github.com/HKUDS/nanobot/issues/2012)
- **描述**: 启用 web search provider 并支持 Tavily
- **状态**: Open

### 7. Nano Team Mode - 多 Worker 异步协作
- **Issue**: [#2013](https://github.com/HKUDS/nanobot/issues/2013)
- **标签**: enhancement
- **描述**: 添加 nano team 模式，支持 LLM 规划的多 worker 异步协作
- **状态**: Open (标记为 invalid，可能是功能已实现)

### 8. 交互式配置向导 (nanobot onboard)
- **Issue**: [#2018](https://github.com/HKUDS/nanobot/issues/2018) / [#2019](https://github.com/HKUDS/nanobot/issues/2019)
- **标签**: enhancement
- **描述**: 新的交互式配置向导
- **状态**: Open

### 9. 飞书多 Bot 群组感知
- **Issue**: [#1990](https://github.com/HKUDS/nanobot/issues/1990)
- **描述**: 飞书多 Bot 群组感知，静默记录和历史同步
- **状态**: Open

### 10. WhatsApp 媒体发送/接收支持
- **Issue**: [#2010](https://github.com/HKUDS/nanobot/issues/2010)
- **描述**: 添加 WhatsApp 媒体消息发送和接收支持
- **状态**: Open

---

## 📋 已关闭的高频问题（参考）

### 常见问题分类

| 类别 | 描述 | 相关 Issue |
|------|------|------------|
| MCP 对接 | MCP 服务对接问题 | 多个 |
| Provider | 自定义 provider 兼容性问题 | #1987 |
| 渠道稳定性 | QQ/飞书/钉钉消息问题 | 多个 |
| Windows 兼容 | Windows 平台路径和重启问题 | 多个 |
| Memory | 内存 consolidation 问题 | 多个 |
| 执行输出 | exec 工具输出截断配置 | #1871 |

---

## 📝 建议添加到文档的内容

基于以上 Issues 分析，建议在 awesome-nanobot 文档中补充：

1. **多 Provider 配置指南** - 多个 custom provider 的配置方法
2. **企业微信配置教程** - 等待官方支持
3. **NapCat QQ 部署教程** - 使用 NapCat 部署 QQ 机器人
4. **成本跟踪配置** - Token 使用统计配置
5. **常见问题排查** - 基于已关闭 Issues 的高频问题

---

## 🔗 相关链接

- [Nanobot 官方仓库](https://github.com/HKUDS/nanobot)
- [Open Issues 列表](https://github.com/HKUDS/nanobot/issues?state=open)
- [Release Notes](https://github.com/HKUDS/nanobot/releases)