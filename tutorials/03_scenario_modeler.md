---
title: "Tutorial: Building the Verdana Scenario Modeler"
tool: Scenario Modeler
sequence: 3
created: 2026-04-06
---

# Tutorial: Building the Verdana Scenario Modeler

## What We Built

An interactive HTML scenario modeler that lets leadership explore four strategic paths for Verdana — stay the course, expand into wholesale, launch new products, or cut the underperforming Shield SKU — and blend them in any combination.

## The Prompt

> Build a scenario modeler for Verdana. Model four strategic paths: stay the course (DTC only), expand into wholesale, launch two new products, or cut the underperforming SKU and reallocate resources. For each scenario, project 3-year revenue, margins, required investment, team headcount, and risk factors. Let me compare scenarios side by side and blend them — what if we do wholesale AND cut a SKU? Output as an interactive HTML file.

## Key Design Decisions

### 1. Toggle Model Over Fixed Scenarios

Instead of four rigid scenarios, we modeled it as a baseline plus three toggleable strategic moves. This gives 2^3 = 8 possible combinations, including "stay the course" (all off) and any blend like "wholesale + cut Shield."

**Why:** Leadership doesn't think in fixed scenarios — they think "what if we do this AND that?" The toggle model makes blending natural.

### 2. Quarterly Over Annual

We chose 12-quarter projections instead of 3 annual snapshots. This matters because:
- Wholesale has a 6-month ramp period
- New products launch mid-year (default Q3)
- Shield discontinuation has a transition quarter
- These timing effects disappear in annual views

### 3. Pinnable Comparison Drawer

Rather than a fixed two-panel comparison, users build a scenario, name it, pin it, then explore another configuration. All pinned scenarios appear in a slide-up comparison table.

**Why:** The blending mechanic means you'll want to explore many combinations freely. A fixed comparison forces rebuilding scenarios you already explored.

### 4. Full-Width Layout with Slide-Up Drawer

We chose a full-width builder with the comparison drawer sliding up from the bottom, rather than a sidebar layout or tabbed views.

**Why:** 12 quarters of stacked bar data need horizontal space. The drawer keeps comparison accessible without mode-switching.

## How to Replicate

1. Start with the brand definition (`brand/brand_definition.md`) — it provides all the baseline financial data
2. Brainstorm the design using the visual companion to explore layout options
3. Build incrementally: data model → header → toggle cards → sliders → charts → risk bar → pin/compare
4. Keep calculation logic as pure functions, separate from DOM rendering
5. Use slider `input` events (not `change`) for real-time recalculation

## Output

`tools/scenario_modeler.html` — open in any browser, no server required.
