---
title: "Tutorial: Building the Verdana Competitive Positioning Map"
tool: Competitive Positioning Map
sequence: 4
created: 2026-04-06
---

# Tutorial: Building the Verdana Competitive Positioning Map

## What We Built

An interactive positioning map that plots Verdana against 8 real competitors on a 2D grid. Users select any two of six dimensions for the axes, and brand nodes animate to new positions. Hovering reveals detailed brand profiles.

## The Prompt

> Build a competitive positioning map for Verdana. Plot Verdana against 6-8 real and fictional competitors in the DTC wellness/supplement space on an interactive 2D grid. Let me choose the axes — price vs. quality, clinical rigor vs. lifestyle branding, DTC vs. retail distribution, ingredient transparency vs. proprietary blends. Show each brand as a node with key details on hover. Output as an interactive HTML file.

## Key Design Decisions

### 1. Free-Form Axis Selection

Rather than four fixed axis pairings, we made all six dimensions available for either axis. This gives 30 possible views and lets leadership explore unexpected angles like "transparency vs. price" or "lifestyle branding vs. DTC focus."

### 2. All Real Competitors

We used 9 real brands (including Verdana) rather than mixing in fictional ones. Real brands are more useful for actual positioning conversations — the leadership team already knows these names.

### 3. Full-Screen Map Layout

The map takes the full viewport below the header. Hover cards float next to nodes rather than using a sidebar or bottom panel. A positioning map is fundamentally a visual tool — maximize the map space.

### 4. "vs. Verdana" Comparison Line

Each competitor's hover card ends with a Verdana-specific comparison. This turns every node into a strategic prompt: "What would it take to close this gap?" or "Why are we different here?"

## How to Replicate

1. Define your dimensions (the axes you want to compare brands on) with clear low/high anchors
2. Score each brand 0-100 on every dimension — this is the hardest part, be honest
3. Write brand profiles with the comparison angle that matters to your strategy
4. Position nodes using percentage coordinates from scores
5. Use CSS transitions for smooth axis-change animations

## Output

`tools/competitive_positioning_map.html` — open in any browser, no server required.
