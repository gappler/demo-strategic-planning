# Agency State — Project Notes

Insights captured during the build process. These inform marketing, curriculum design, and the Agency State methodology.

---

## Methodology: Foundation first, tools second

Every client engagement and every training cohort follows the same system — foundation first, then tools built sequentially on top.

**Foundation** = brand/business definition + data (historical performance, team structure, client portfolio, whatever the context requires).

**Tools** = built one at a time, each feeding the next. The sequence matters — a dashboard reads the data, a report interprets the dashboard, a budget allocator uses the report's insights.

Without the foundation, Claude Code produces generic outputs. With it, everything downstream is specific, consistent, and useful.

This methodology is the product differentiator. Anyone can show someone how to prompt Claude Code. Agency State teaches a *system* for building with it. The foundation-first approach is what makes the tools actually usable on Monday morning instead of impressive demos that gather dust.

**Teaching note:** This wasn't learned from documentation. It emerged from doing three demo builds in sequence and noticing the pattern. That's exactly how cohort participants will learn it too — by building, not by being told.

---

## Workflow: Claude for thinking, Claude Code for doing

The ideal workflow uses both Claude and Claude Code together as a desktop partnership:

- **Claude** (chat) — strategic thinking, planning, research, prompting guidance, troubleshooting, making decisions about what to build and why
- **Claude Code** (terminal) — execution, building tools, generating data, creating files, committing code

The two together are the desktop partner. One helps you figure out *what* to build, the other builds it.

This is worth teaching explicitly in cohorts. Students will naturally try to do everything in one tool. Showing them the split — think here, build there — makes both tools more effective and mirrors how experienced practitioners actually work.

---

## Git discipline: The non-negotiable rule

Always set up git before building anything. Commit after every tool. This was learned the hard way — files were built in the wrong project folder, and without git there was no clean way to reset.

**Project setup checklist (do every time):**
1. Create the GitHub repo first
2. `git init` in the local folder
3. Create CLAUDE.md with project rules
4. Commit the CLAUDE.md as the first commit
5. Add remote and push
6. Then start building

Add a git discipline rule to CLAUDE.md so Claude Code commits after every completed tool automatically.

---

## Demo architecture: The three-layer build

Each demo project follows the same three-layer structure:

1. **Foundation layer** — brand definition + historical data
2. **Tool layer** — 5-12 purpose-built tools, each solving a specific problem
3. **Presentation layer** — index.html guided tour page that showcases all tools with prompts, previews, and narrative

The presentation layer is what you share. The tool layer is what proves capability. The foundation layer is what makes it all real.

---

## Prompting lesson: "Build" not "design"

When Claude Code asks if you want to see mockups or design specs, it's shifting into design mode instead of build mode. If you want working tools, be explicit: say "build" not "design." Specs and mockups are useful for complex UI decisions, but they're not the deliverable — working HTML files are.

---

## The build is fast, the understanding is slow

A motivated person can build a brand definition, generate 12 months of data, and create a working dashboard in under an hour. The build speed is not the product. The product is:

- Knowing what to build and why
- Understanding what Claude Code decided and whether it's right
- Being able to troubleshoot when something breaks
- Adapting the approach to a different business context

Speed is the hook. Understanding is the value. The cohort exists to close the gap between the two.
