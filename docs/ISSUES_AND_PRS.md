# Open Issues & PRs

> 2026-06-21 07:00 | [HKUDS/nanobot](https://github.com/HKUDS/nanobot/issues)

---

## Issues (8)

| # | Labels | Title | Author | Created |
|---|--------|-------|--------|---------|
| [4429](https://github.com/HKUDS/nanobot/issues/4429) | - | feat: Allow custom provider to configure thinking style | gkd2323c | 2026-06-20 |
| [4422](https://github.com/HKUDS/nanobot/issues/4422) | - | feat(telegram): Add Bot API 10.1 sendRichMessage support | zpljd258 | 2026-06-20 |
| [4420](https://github.com/HKUDS/nanobot/issues/4420) | enhancement | 性能优化：`estimate_prompt_tokens` 每轮迭代对工具定义做冗余 tiktoken 编码 | codeLong1024 | 2026-06-20 |
| [4419](https://github.com/HKUDS/nanobot/issues/4419) | - | Feature: Automatic reasoning effort escalation (default + escalated levels) | orrinwitt | 2026-06-20 |
| [4418](https://github.com/HKUDS/nanobot/issues/4418) | - | Feature Request: Heartbeat tasks should deliver results to the channel where the task was added | orrinwitt | 2026-06-19 |
| [4413](https://github.com/HKUDS/nanobot/issues/4413) | enhancement | [Request] Telegram Bot API 10.1 rich messages | madIlama | 2026-06-19 |
| [4410](https://github.com/HKUDS/nanobot/issues/4410) | bug | Even ask LLM dont send message, it still send message after upgrade from v0.15 | KennethYCK | 2026-06-19 |
| [4408](https://github.com/HKUDS/nanobot/issues/4408) | bug | Nanobot.run() per-run hooks are not concurrency-safe (shared _extra_hooks is clobbered) | waelantar | 2026-06-18 |

## PRs (22)

| # | Labels | Title | Author | Created |
|---|--------|-------|--------|---------|
| [4428](https://github.com/HKUDS/nanobot/pull/4428) | performance | perf(tokens): cache tool schema estimates | yu-xin-c | 2026-06-20 |
| [4425](https://github.com/HKUDS/nanobot/pull/4425) | fix | fix(sdk): use contextvars for per-call hooks to prevent concurrent run() race | michaelxer | 2026-06-20 |
| [4424](https://github.com/HKUDS/nanobot/pull/4424) | - | [codex] feat(memory): gate archive facts with provenance context | yu-xin-c | 2026-06-20 |
| [4423](https://github.com/HKUDS/nanobot/pull/4423) | - | fix(telegram): narrow rich capability error detection and fix misleading log | zpljd258 | 2026-06-20 |
| [4421](https://github.com/HKUDS/nanobot/pull/4421) | - | perf(utils): cache tool-definition JSON in estimate_prompt_tokens | michaelxer | 2026-06-20 |
| [4417](https://github.com/HKUDS/nanobot/pull/4417) | CI/CD | [codex] test(mcp): use resolvable timeout regression URL | yu-xin-c | 2026-06-19 |
| [4416](https://github.com/HKUDS/nanobot/pull/4416) | enhancement | [codex] feat(cron): support job model presets | yu-xin-c | 2026-06-19 |
| [4415](https://github.com/HKUDS/nanobot/pull/4415) | enhancement | [codex] feat(subagent): allow spawn model override | yu-xin-c | 2026-06-19 |
| [4414](https://github.com/HKUDS/nanobot/pull/4414) | enhancement | [codex] feat(subagent): add aggregated result mode | yu-xin-c | 2026-06-19 |
| [4412](https://github.com/HKUDS/nanobot/pull/4412) | enhancement, webui | Suppress routine cron job notifications (#4410) | HaisamAbbas | 2026-06-19 |
| [4411](https://github.com/HKUDS/nanobot/pull/4411) | enhancement | feat(agent): add SuspendTurn so a tool can pause a turn for async / human-in-the-loop continuations | vinit-patel-athena | 2026-06-19 |
| [4409](https://github.com/HKUDS/nanobot/pull/4409) | - | fix(sdk): pass per-run hooks to process_direct instead of mutating shared loop state | waelantar | 2026-06-18 |
| [4407](https://github.com/HKUDS/nanobot/pull/4407) | - | feat(whatsapp): seed LID->phone mappings on startup | franciscomaestre | 2026-06-18 |
| [4406](https://github.com/HKUDS/nanobot/pull/4406) | - | feat(web-search): add Serper.dev (Google Search API) provider | franciscomaestre | 2026-06-18 |
| [4405](https://github.com/HKUDS/nanobot/pull/4405) | - | feat(web): allow Keenable search without an API key | IlyaGusev | 2026-06-18 |

## ⚠️ Needs attention

- [Even ask LLM dont send message, it still send message after upgrade from v0.15](https://github.com/HKUDS/nanobot/issues/4410) by KennethYCK
- [Nanobot.run() per-run hooks are not concurrency-safe (shared _extra_hooks is clobbered)](https://github.com/HKUDS/nanobot/issues/4408) by waelantar
- [fix(webui): avoid slow settings route refreshes](https://github.com/HKUDS/nanobot/pull/4398) by chengyongru

## Stats

- Open Issues: 8
- Open PRs: 22
- Needs attention: 3