---
title: "Tutorial: Building the Verdana OKR Goal Setting Tool"
tool: OKR Goal Setting Tool
sequence: 6
created: 2026-04-06
---

# Tutorial: Building the OKR Goal Setting Tool

## Overview

This tutorial walks through building an interactive OKR planning dashboard that presents Verdana's FY2027 objectives and key results across three strategic scenarios, letting leadership toggle objectives on/off and see resource implications in real-time.

## Step 1: Design the Data Model

**Prompt used:** "Build the Verdana OKR Goal Setting Tool as a single self-contained interactive HTML file" (with full spec reference).

**Key decision:** Store objectives as a flat array with per-scenario resources and key results. Each scenario references objectives by ID. This avoids duplicating shared objectives (like "Reduce Customer Acquisition Cost" which appears in all three scenarios) while allowing scenario-specific KR targets (e.g., CAC target of $45 in Base vs $48 in Upside vs $50 in Downside).

```javascript
const DATA = {
  scenarios: {
    base: { objectives: [1, 2, 3, 5, 6, 9, 11, 12, 13] },
    upside: { objectives: [1, 2, 3, 4, 5, 6, 7, 9, 10, 11, 12, 13] },
    downside: { objectives: [1, 2, 3, 8, 9, 12, 14] }
  },
  objectives: [{
    id: 1,
    resources: { base: { hires: 2, budget: 80000 }, downside: { hires: 0, budget: 0 } },
    key_results: { base: [...], upside: [...], downside: [...] }
  }]
};
```

## Step 2: Build the Layout

The layout uses a fixed 280px sidebar and a fluid main area. The sidebar contains:
- Brand wordmark ("verdana" in lowercase, primary green)
- Scenario switcher buttons
- Strategic context block
- Trigger points
- Resource summary grid

The main area has:
- Filter pill bar at top
- 2-column responsive card grid

## Step 3: Implement Scenario Switching

When a scenario button is clicked, the app:
1. Updates `state.currentScenario`
2. Re-renders sidebar (context, triggers, resource summary)
3. Re-renders cards with slide-in animation
4. Cards that exist in the new scenario appear; others disappear

**Key decision:** Cards animate with CSS `slideIn` keyframes on scenario switch to visually signal which objectives changed.

## Step 4: Implement Function Filtering

Filter pills support multi-select. Clicking a function pill toggles it. Clicking "All" resets to show everything. If all individual pills are deselected, "All" re-activates automatically.

## Step 5: Implement Objective Toggles

Each card has an on/off toggle switch in the top-right corner. Toggling an objective:
- Grays out the card (opacity + grayscale filter)
- Removes its resources from the sidebar summary
- Resource summary recalculates immediately

## Step 6: Implement Card Expansion

Clicking a card (not the toggle) expands it inline to show full KR detail with from/to targets, timelines, resource breakdown, and addressed challenges. Uses `max-height` CSS transition for smooth animation.

## Step 7: Apply Wellness Brand Theme

- Page background: #f8faf7 (warm off-white)
- Sidebar: #eef4ec (soft sage)
- Cards: white with subtle box-shadows
- Primary: #2d6a4f (deep forest green)
- Function colors: Marketing green, Product purple, Operations amber, Finance teal blue
- All transitions: 300ms ease

## Final Output

- **File:** `tools/okr_goal_setting.html`
- **Self-contained:** No external dependencies, works when opened directly in a browser
- **Data:** All 14 objectives with scenario-specific key results baked into a JavaScript object at the top of the file

## Replication Checklist

1. Read the design spec and brand definition for all OKR data
2. Define a flat objectives array with per-scenario resources and KRs
3. Define scenarios as sets of objective IDs
4. Build fixed sidebar with scenario switcher, context, triggers, resource summary
5. Build main area with filter pills and card grid
6. Wire up scenario switching with animation
7. Wire up function filtering with multi-select
8. Wire up objective toggles with resource recalculation
9. Wire up card expand/collapse
10. Apply wellness brand theme colors and typography
