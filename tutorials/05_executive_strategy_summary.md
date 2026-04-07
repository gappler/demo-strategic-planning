---
title: "Tutorial: Building the Verdana Executive Strategy Summary"
tool: Executive Strategy Summary
sequence: 5
created: 2026-04-06
---

# Tutorial: Building the Verdana Executive Strategy Summary

## What We Built

A polished executive strategy document that synthesizes all Verdana planning data into a single coherent recommendation — output as both a styled HTML scrolling narrative and a markdown document.

## The Prompt

> Build a tool that reads all the Verdana data — the brand definition, OKR goals, market sizing results, scenario model outputs, and competitive positioning — and generates a polished executive strategy summary. Include an executive overview, recommended strategic direction with rationale, 3-year financial projections, key risks, and immediate next steps. Output as both a formatted HTML presentation and a markdown document.

## Key Design Decisions

### 1. Recommend, Don't Just Present

Executives want a thesis they can react to, not a menu of options. We led with a clear recommendation (Wholesale + Cut Shield) backed by evidence from each planning tool, then added contingency paths with trigger points for when to pivot.

### 2. Scrolling Narrative Over Slides

A strategy summary is a reading document, not a presentation deck. The scrolling format controls pacing (context, then recommendation, then evidence, then risks), works in email, and prints cleanly.

### 3. Baseline vs Recommended Comparison

Two columns, not three. The contrast between "do nothing" ($9.8M Y3) and "recommended path" ($12.4M Y3) is the most powerful argument for action. The aggressive alternative is covered in the contingencies section.

### 4. Static Synthesis, Not Dynamic

Unlike the scenario modeler or market sizing calculator, this document has baked-in content. It's the output of the planning process, not another input. The analytical tools do the exploring; this document does the deciding.

## How to Replicate

1. Build the analytical tools first (scenario modeler, market sizing, OKR planner, competitive positioning)
2. Run each tool to identify the strongest strategic path
3. Write the recommendation as a thesis with evidence sourced from each tool
4. Add financial projections comparing baseline vs recommended
5. Include risks with mitigations and contingency paths with quantified trigger points
6. End with concrete next steps — owners, dates, actions

## Output

- `tools/executive_strategy_summary.html` — open in any browser
- `output/executive_strategy_summary.md` — for distribution and version control
