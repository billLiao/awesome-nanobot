# Open Issues & PRs

> 2026-06-19 07:00 | [HKUDS/nanobot](https://github.com/HKUDS/nanobot/issues)

---

## Issues (7)

| # | Labels | Title | Author | Created |
|---|--------|-------|--------|---------|
| [4408](https://github.com/HKUDS/nanobot/issues/4408) | bug | Nanobot.run() per-run hooks are not concurrency-safe (shared _extra_hooks is clobbered) | waelantar | 2026-06-18 |
| [4390](https://github.com/HKUDS/nanobot/issues/4390) | enhancement, feature request | Multi-instances for normies | bukit-kronik | 2026-06-17 |
| [4389](https://github.com/HKUDS/nanobot/issues/4389) | question | Feature Request: Per-model contextWindowTokens for fallback models | orrinwitt | 2026-06-17 |
| [4388](https://github.com/HKUDS/nanobot/issues/4388) | bug | [WebUI] iOS Safari 点击输入框触发页面放大 | zpljd258 | 2026-06-17 |
| [4378](https://github.com/HKUDS/nanobot/issues/4378) | feature request | cron level model/preset | chengyongru | 2026-06-17 |
| [4376](https://github.com/HKUDS/nanobot/issues/4376) | enhancement | user frendly wizard | chengyongru | 2026-06-17 |
| [4374](https://github.com/HKUDS/nanobot/issues/4374) | feature request | Project workspaces: SOUL.md/USER.md are read from the project but written to the default workspace (read/write asymmetry) | maximilize | 2026-06-16 |

## PRs (23)

| # | Labels | Title | Author | Created |
|---|--------|-------|--------|---------|
| [4409](https://github.com/HKUDS/nanobot/pull/4409) | - | fix(sdk): pass per-run hooks to process_direct instead of mutating shared loop state | waelantar | 2026-06-18 |
| [4407](https://github.com/HKUDS/nanobot/pull/4407) | - | feat(whatsapp): seed LID->phone mappings on startup | franciscomaestre | 2026-06-18 |
| [4406](https://github.com/HKUDS/nanobot/pull/4406) | - | feat(web-search): add Serper.dev (Google Search API) provider | franciscomaestre | 2026-06-18 |
| [4405](https://github.com/HKUDS/nanobot/pull/4405) | - | feat(web): allow Keenable search without an API key | IlyaGusev | 2026-06-18 |
| [4404](https://github.com/HKUDS/nanobot/pull/4404) | - | [codex] feat(exec): allow extra bwrap bind roots | yu-xin-c | 2026-06-18 |
| [4402](https://github.com/HKUDS/nanobot/pull/4402) | - | [codex] feat(memory): add opt-in eager consolidation | yu-xin-c | 2026-06-18 |
| [4401](https://github.com/HKUDS/nanobot/pull/4401) | - | fix(providers): use non-descriptive placeholder when stripping images | michaelxer | 2026-06-18 |
| [4399](https://github.com/HKUDS/nanobot/pull/4399) | enhancement, webui | feat(webui): add configurable hidden_settings_sections to strip UI noise | HaisamAbbas | 2026-06-18 |
| [4398](https://github.com/HKUDS/nanobot/pull/4398) | bug, enhancement, webui | fix(webui): avoid slow settings route refreshes | chengyongru | 2026-06-18 |
| [4397](https://github.com/HKUDS/nanobot/pull/4397) | invalid | fix(runner): add system hint when mid-turn user messages are injected | DreamShepherd2006 | 2026-06-18 |
| [4396](https://github.com/HKUDS/nanobot/pull/4396) | enhancement, channel, webui | Add optional Nanobot feature enablement | chengyongru | 2026-06-18 |
| [4395](https://github.com/HKUDS/nanobot/pull/4395) | documentation, enhancement, channel | Improve onboard wizard setup flow | chengyongru | 2026-06-18 |
| [4394](https://github.com/HKUDS/nanobot/pull/4394) | provider | fix: support OpenAI image reference edits | sbyinin | 2026-06-18 |
| [4393](https://github.com/HKUDS/nanobot/pull/4393) | - | test(exec): cover git commands in workspace subdirectories | yu-xin-c | 2026-06-17 |
| [4392](https://github.com/HKUDS/nanobot/pull/4392) | - | fix(agent): make tool microcompaction configurable | yu-xin-c | 2026-06-17 |

## ⚠️ Needs attention

- [Nanobot.run() per-run hooks are not concurrency-safe (shared _extra_hooks is clobbered)](https://github.com/HKUDS/nanobot/issues/4408) by waelantar
- [[WebUI] iOS Safari 点击输入框触发页面放大](https://github.com/HKUDS/nanobot/issues/4388) by zpljd258
- [fix(webui): avoid slow settings route refreshes](https://github.com/HKUDS/nanobot/pull/4398) by chengyongru
- [[codex] fix MCP malformed progress notifications](https://github.com/HKUDS/nanobot/pull/4372) by yu-xin-c
- [fix(providers): mark stripped images as unviewable instead of leaking the path](https://github.com/HKUDS/nanobot/pull/4346) by BearMett

## Stats

- Open Issues: 7
- Open PRs: 23
- Needs attention: 5