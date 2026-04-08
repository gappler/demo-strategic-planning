---
title: project_notes
description: Ongoing log of skills inventory, build methodology, and project insights
version: 1
created: 2026-04-08
updated: 2026-04-08
---

# Project Notes

Ongoing log of insights, methodology notes, and tooling inventory for the strategic planning demo project.

---

## Skills Inventory

### Superpowers Skills Invoked

| Skill | Usage |
|-------|-------|
| `superpowers:brainstorming` | 4 brainstorm sessions in `.superpowers/brainstorm/` — layout approaches, UI design, positioning map, executive summary |
| `superpowers:writing-plans` | 3 implementation plans in `docs/superpowers/plans/` — scenario modeler, competitive positioning map, executive strategy summary |
| `superpowers:subagent-driven-development` | Referenced in implementation plans as recommended execution method |
| `superpowers:executing-plans` | Referenced as alternative execution method in plans |

### Design Specs Generated

5 specs in `docs/superpowers/specs/`, one per tool:

- Scenario modeler
- Competitive positioning map
- Executive strategy summary
- Market sizing calculator
- OKR goal setting tool

### Agents and Sub-Agents

No external sub-agents were dispatched. Implementation plans recommended `superpowers:subagent-driven-development` or `superpowers:executing-plans` for execution, but actual builds were done inline in conversation sessions.

### MCP Servers and External Tools

None used. All 5 tools were built as self-contained single-file HTML with vanilla JS — no external dependencies, no MCP server calls, no third-party APIs.

### Tools Built (5 Interactive HTML Apps)

| Tool | File | Notes |
|------|------|-------|
| Scenario Modeler | `tools/scenario_modeler.html` | Built zone-by-zone across 5 incremental commits |
| Competitive Positioning Map | `tools/competitive_positioning_map.html` | 9 brand nodes, 6 selectable dimensions |
| Executive Strategy Summary | `tools/executive_strategy_summary.html` | Also generated `output/executive_strategy_summary.md` |
| Market Sizing Calculator | `tools/market_sizing_calculator.html` | TAM/SAM/SOM funnel with cross-channel effects |
| OKR Goal Setting Tool | `tools/okr_goal_setting.html` | 14 objectives, scenario switcher, resource summary |

### Supporting Artifacts

| Artifact | File |
|----------|------|
| Brand definition | `brand/brand_definition.md` |
| Guided tour | `index.html` |
| Tutorials | `tutorials/03_scenario_modeler.md` through `tutorials/06_okr_goal_setting.md` |
| Process log | `docs/process_log.md` |

### Build Timeline

All work completed in a single session on April 6, 2026 (16:58–21:52), across 27 commits.

---

## Build Methodology Pattern (Reusable Reference)

### Three-Layer Architecture

Every project follows the same structure:

1. **Foundation layer** — Brand definition + historical data. Without this, Claude Code produces generic outputs. With it, everything downstream is specific, consistent, and useful.
2. **Tool layer** — 5–12 purpose-built tools, each solving a specific problem. Built one at a time, each feeding the next. Sequence matters.
3. **Presentation layer** — `index.html` guided tour page showcasing all tools with prompts, previews, and narrative. This is what you share externally.

### Workflow Pattern

| Phase | Tool | Purpose |
|-------|------|---------|
| Think | Claude (chat) | Strategic thinking, planning, research, deciding what to build and why |
| Build | Claude Code (terminal) | Execution — building tools, generating files, committing code |

The two together form a desktop partnership. One helps you figure out *what* to build, the other builds it.

### Superpowers Workflow Sequence

For each tool in the project:

1. **Brainstorm** (`superpowers:brainstorming`) — Explore intent, requirements, and design before implementation
2. **Spec** — Design specification written to `docs/superpowers/specs/`
3. **Plan** (`superpowers:writing-plans`) — Implementation plan written to `docs/superpowers/plans/`
4. **Build** — Inline execution or via `superpowers:subagent-driven-development`
5. **Document** — Tutorial in `tutorials/`, entry in `docs/process_log.md`
6. **Commit** — Git commit after every completed tool

### Project Setup Checklist

1. Create the GitHub repo
2. `git init` in the local folder
3. Create `CLAUDE.md` with project rules (process logging, tutorials, git discipline)
4. Commit `CLAUDE.md` as the first commit
5. Add remote and push
6. Build foundation layer (brand definition)
7. Build tools sequentially
8. Generate presentation layer last

### Key Lessons

- **"Build" not "design"** — When you want working tools, say "build." Specs and mockups are useful for complex UI decisions, but working HTML files are the deliverable.
- **Foundation first** — Generic prompts produce generic outputs. A solid brand definition makes every downstream tool specific and useful.
- **Git discipline is non-negotiable** — Commit after every tool. Set this up before building anything.
- **The build is fast, the understanding is slow** — Speed is the hook. Knowing what to build, verifying what Claude decided, and adapting the approach to new contexts is the real value.
