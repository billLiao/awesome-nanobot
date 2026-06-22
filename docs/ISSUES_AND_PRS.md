# Open Issues & PRs

> 2026-06-23 07:01 | [HKUDS/nanobot](https://github.com/HKUDS/nanobot/issues)

---

## Issues (10)

| # | Labels | Title | Author | Created |
|---|--------|-------|--------|---------|
| [4457](https://github.com/HKUDS/nanobot/issues/4457) | - | feat(webui): add PWA support for mobile home screen installation | zpljd258 | 2026-06-22 |
| [4442](https://github.com/HKUDS/nanobot/issues/4442) | bug | Duplicate tool_use ids in streamed responses poison a session ("tool_use ids must be unique" 400) | tedyyan | 2026-06-21 |
| [4440](https://github.com/HKUDS/nanobot/issues/4440) | enhancement | Proposal: a read-only `search_history` tool for recalling `memory/history.jsonl` | waelantar | 2026-06-21 |
| [4435](https://github.com/HKUDS/nanobot/issues/4435) | - | [Security] nanobot MCP `enabledTools` allowlist bypass exposes resource and prompt capabilities | YLChen-007 | 2026-06-21 |
| [4434](https://github.com/HKUDS/nanobot/issues/4434) | - | [Security] Nanobot MCP `enabledTools` deny-all policy bypass exposes MCP resources and prompts to the model | YLChen-007 | 2026-06-21 |
| [4431](https://github.com/HKUDS/nanobot/issues/4431) | - | Add heartbeat-specific model override | steeveroucaute10-epping | 2026-06-21 |
| [4429](https://github.com/HKUDS/nanobot/issues/4429) | - | feat: Allow custom provider to configure thinking style | gkd2323c | 2026-06-20 |
| [4419](https://github.com/HKUDS/nanobot/issues/4419) | - | Feature: Automatic reasoning effort escalation (default + escalated levels) | orrinwitt | 2026-06-20 |
| [4418](https://github.com/HKUDS/nanobot/issues/4418) | - | Feature Request: Heartbeat tasks should deliver results to the channel where the task was added | orrinwitt | 2026-06-19 |
| [4413](https://github.com/HKUDS/nanobot/issues/4413) | enhancement | [Request] Telegram Bot API 10.1 rich messages | madIlama | 2026-06-19 |

## PRs (20)

| # | Labels | Title | Author | Created |
|---|--------|-------|--------|---------|
| [4459](https://github.com/HKUDS/nanobot/pull/4459) | enhancement, channel | feat: add Mattermost channel support | goodtiding5 | 2026-06-22 |
| [4458](https://github.com/HKUDS/nanobot/pull/4458) | webui | feat(webui): add PWA support for mobile home screen installation | zpljd258 | 2026-06-22 |
| [4452](https://github.com/HKUDS/nanobot/pull/4452) | - | [codex] enforce MCP enabledTools for resources and prompts | yu-xin-c | 2026-06-22 |
| [4447](https://github.com/HKUDS/nanobot/pull/4447) | fix | fix(gateway): handle lifecycle edge cases | chengyongru | 2026-06-22 |
| [4446](https://github.com/HKUDS/nanobot/pull/4446) | enhancement, channel | feat(dingtalk): gate private chats and mention sender in group replies | lmzopq | 2026-06-22 |
| [4444](https://github.com/HKUDS/nanobot/pull/4444) | fix | fix(providers): dedupe tool_use ids to prevent Anthropic 400s | tedyyan | 2026-06-21 |
| [4443](https://github.com/HKUDS/nanobot/pull/4443) | fix | fix: guard against duplicate tool_use ids in streamed responses (#4442) | michaelxer | 2026-06-21 |
| [4441](https://github.com/HKUDS/nanobot/pull/4441) | fix | fix(mcp): force-close streamable_http generator on reconnect failure | michaelxer | 2026-06-21 |
| [4439](https://github.com/HKUDS/nanobot/pull/4439) | enhancement | feat(tools): add read-only search_history tool | waelantar | 2026-06-21 |
| [4438](https://github.com/HKUDS/nanobot/pull/4438) | fix | fix(cli): show search engines (incl. Keenable) in onboard wizard | IlyaGusev | 2026-06-21 |
| [4437](https://github.com/HKUDS/nanobot/pull/4437) | enhancement | [codex] add heartbeat trigger command | yu-xin-c | 2026-06-21 |
| [4436](https://github.com/HKUDS/nanobot/pull/4436) | fix | fix(tools): gate MCP resource and prompt registration behind enabledTools | michaelxer | 2026-06-21 |
| [4433](https://github.com/HKUDS/nanobot/pull/4433) | fix | fix(pairing): normalize sender IDs to str in the pairing store | waelantar | 2026-06-21 |
| [4430](https://github.com/HKUDS/nanobot/pull/4430) | enhancement, webui | feat(web): configure web_fetch provider | ChachAloha | 2026-06-21 |
| [4424](https://github.com/HKUDS/nanobot/pull/4424) | - | [codex] feat(memory): gate archive facts with provenance context | yu-xin-c | 2026-06-20 |

## ⚠️ Needs attention

- [Duplicate tool_use ids in streamed responses poison a session ("tool_use ids must be unique" 400)](https://github.com/HKUDS/nanobot/issues/4442) by tedyyan

## Stats

- Open Issues: 10
- Open PRs: 20
- Needs attention: 1