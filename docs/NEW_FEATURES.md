# Nanobot 新功能需求汇总（来自官方 Issues）

> 本文档汇总自 HKUDS/nanobot 官方仓库的 Open Issues，反映了用户最迫切需要的新功能和改进。

最后更新：2026-04-08

---

## 🚀 v0.1.5 新功能 (2026-04-06)

**66 个 PR 合并，27 位新贡献者**

### 主要更新
- **官方网站上线** - [nanobot.wiki](https://nanobot.wiki) 支持多语言（英、中、日、韩、西、法）
- **长时任务可靠性提升** - 处理 `CancelledError` 不再遗留子进程，重试分类使用结构化错误元数据
- **Memory 新架构 - Dream** - 两阶段记忆系统，分离实时对话历史和长期知识，git 版本化存储
- **生产环境优化** - `exec` 调用通过 `bwrap` 沙箱化，容器默认以非 root 运行，API 端口默认绑定 localhost
- **新 Provider 支持** - GPT-5、小米 MiMo、百度千帆、DeepSeek-R1 reasoning_content 支持
- **渠道更新** - Email 附件提取、WhatsApp 语音转录、Feishu 视频下载、Telegram 工具提示渲染

### 相关 PR
- #2733, #2762, #2759, #2761, #2765 - 长时任务可靠性
- #2717, #2779 - Dream 记忆系统
- #1940, #2831, #2830, #2841, #2715 - 生产环境优化
- #2788, #2495, #2811, #2840, #2770 - 新 Provider

---

## 🚀 v0.1.4.post6 新功能 (2026-03-27)

**57 个 PR 合并，27 位新贡献者**

### 主要更新
- **Agent Runtime 重构** - 分解为可组合组件，提取共享 `AgentRunner`，生命周期钩子统一为 `HookContext`
- **移除 litellm 依赖** - 使用原生 OpenAI + Anthropic SDK，支持 Anthropic Prompt Cache 和 OpenAI o1 `max_completion_tokens`
- **端到端流式支持** - Feishu CardKit 流式支持，队列流增量合并
- **安全漏洞修复**

### 相关 PR
- #2524, #2541, #2388, #2338 - Agent Runtime 重构
- #2448, #1109, #2468, #2550, #2453 - 原生 SDK 支持

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

## 📋 已关闭 Issues 高频分析

基于最近 200 个已关闭 Issues 的标题分析，统计出以下高频关键词：

### Top 20 高频关键词

| 关键词 | 出现次数 | 说明 |
|--------|----------|------|
| feat | 24 | 新功能实现 |
| support | 11 | 功能支持请求 |
| memory | 9 | 内存系统相关 |
| consolidation | 6 | 记忆整合问题 |
| subagent | 5 | 子代理相关 |
| provider | 4 | LLM 提供商相关 |
| wecom | 4 | 企业微信相关 |
| channel | 4 | 渠道相关 |
| message | 4 | 消息处理 |
| docs | 4 | 文档相关 |

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
---

## 🆕 New (2026-06-17)

- **PR #4371**: [fix(cache): add breakpoint before Recent History so the stable system prefix caches](https://github.com/HKUDS/nanobot/pull/4371) — sumleo


---

## 🆕 New (2026-06-19)

- **Issue #4390**: [Multi-instances for normies](https://github.com/HKUDS/nanobot/issues/4390) — bukit-kronik
- **Issue #4378**: [cron level model/preset](https://github.com/HKUDS/nanobot/issues/4378) — chengyongru
- **Issue #4376**: [user frendly wizard](https://github.com/HKUDS/nanobot/issues/4376) — chengyongru
- **Issue #4374**: [Project workspaces: SOUL.md/USER.md are read from the project but written to the default workspace (read/write asymmetry)](https://github.com/HKUDS/nanobot/issues/4374) — maximilize
- **PR #4399**: [feat(webui): add configurable hidden_settings_sections to strip UI noise](https://github.com/HKUDS/nanobot/pull/4399) — HaisamAbbas

