---
title: "Verdana Competitive Positioning Map — Design Spec"
version: 1.0
created: 2026-04-06
status: approved
---

# Verdana Competitive Positioning Map

## Purpose

An interactive HTML tool that plots Verdana against 8 real competitors in the DTC wellness/supplement space on a 2D positioning grid. Users choose any two of six dimensions for the X and Y axes — price, clinical rigor, lifestyle branding, ingredient transparency, DTC focus, or product breadth. Brand nodes animate to new positions when axes change. Hovering a node reveals a detail card with key metrics, products, and a Verdana-specific comparison line.

## Strategic Context

Verdana competes in a crowded DTC supplement market. The brand definition identifies four named competitors (AG1, Moon Juice, Thorne, Amazon brands) but leadership needs a broader competitive view to inform positioning decisions — especially as they evaluate wholesale expansion, new product launches, and how to differentiate against rising clinical-transparency competitors like Ritual and Seed. This tool makes competitive positioning tangible and explorable.

## Dimensions

Six positioning dimensions, each scored 0–100 per brand:

| Dimension | Low End (0) | High End (100) |
|---|---|---|
| Price Point | Budget ($10–20/mo) | Premium ($80+/mo) |
| Clinical Rigor | No evidence cited | RCTs, published dosages, third-party testing |
| Lifestyle Branding | Pure clinical/functional | Heavy aesthetic/aspirational identity |
| Ingredient Transparency | Proprietary blends, hidden doses | Full disclosure, COAs, named sourcing |
| DTC Focus | Primarily retail/Amazon | Primarily direct-to-consumer |
| Product Breadth | Single SKU or narrow category | Wide catalog across categories |

Users select any dimension for the X-axis and any for the Y-axis via dropdown selectors. All 30 possible axis combinations (6 choose 2, both orientations) are valid.

## Brand Data

### Dimension Scores

| Brand | Price | Clinical | Lifestyle | Transparency | DTC | Breadth |
|---|---|---|---|---|---|---|
| Verdana | 70 | 85 | 25 | 95 | 95 | 45 |
| Athletic Greens (AG1) | 75 | 40 | 70 | 30 | 90 | 10 |
| Moon Juice | 65 | 20 | 95 | 35 | 70 | 55 |
| Thorne | 60 | 90 | 10 | 75 | 40 | 95 |
| Amazon Supplement Brands | 15 | 10 | 15 | 10 | 15 | 80 |
| Ritual | 55 | 70 | 60 | 85 | 85 | 35 |
| Seed | 65 | 90 | 50 | 80 | 90 | 15 |
| Momentous | 75 | 75 | 45 | 65 | 75 | 40 |
| Onnit | 55 | 30 | 80 | 25 | 50 | 65 |

### Brand Profiles (Hover Card Data)

**Verdana**
- Color: #2d6a4f
- Abbreviation: V
- Tagline: "Clinical transparency adaptogens"
- Key Products: Focus, Calm, Restore, Endure, Shield
- Scale: $8M revenue, 60 employees, DTC-only
- Audience: Health-conscious skeptical professionals, 30–50
- vs. Verdana: (this is the reference brand — no comparison line)

**Athletic Greens (AG1)**
- Color: #c17817
- Abbreviation: AG
- Tagline: "All-in-one daily nutrition"
- Key Products: AG1 powder, AG1 travel packs
- Scale: $600M+ revenue, unicorn valuation, DTC-dominant
- Audience: Busy professionals and fitness enthusiasts, 25–45
- vs. Verdana: "AG1 is all-in-one; Verdana is targeted. AG1 hides behind proprietary blends; Verdana publishes every dose."

**Moon Juice**
- Color: #e9c46a
- Abbreviation: MJ
- Tagline: "Adaptogenic beauty and wellness"
- Key Products: SuperYou, Magnesi-Om, Brain Dust
- Scale: $50M+ revenue, retail + DTC, celeb partnerships
- Audience: Wellness-forward women, 25–40, aesthetic-driven
- vs. Verdana: "Moon Juice sells the lifestyle; Verdana sells the evidence. Overlapping adaptogens, opposite brand voice."

**Thorne**
- Color: #6b4c9a
- Abbreviation: Th
- Tagline: "Practitioner-grade supplements"
- Key Products: Basic Nutrients, MediClear, Creatine
- Scale: $200M+ revenue, 200+ SKUs, heavy retail and practitioner channel
- Audience: Healthcare practitioners and their patients, all ages
- vs. Verdana: "Thorne has clinical credibility but no consumer personality. Verdana is what Thorne would look like as a DTC brand."

**Amazon Supplement Brands**
- Color: #999999
- Abbreviation: Am
- Tagline: "Lowest price, maximum selection"
- Key Products: Nature Made, NOW Foods, Amazon Basics supplements
- Scale: Multi-billion $ category, thousands of brands, pure marketplace
- Audience: Price-sensitive general consumers
- vs. Verdana: "Amazon is the anti-Verdana — race to the bottom on price, zero transparency, no brand relationship."

**Ritual**
- Color: #2a9d8f
- Abbreviation: Rt
- Tagline: "Traceable, science-backed essentials"
- Key Products: Essential Multivitamin, Essential Protein, Synbiotic+
- Scale: $100M+ revenue, DTC-first with recent retail expansion
- Audience: Health-conscious women (expanding to men), 25–45
- vs. Verdana: "Closest positioning threat — transparency-led DTC, but vitamins not adaptogens. If Ritual enters adaptogens, they're the top competitor."

**Seed**
- Color: #e76f51
- Abbreviation: Sd
- Tagline: "Microbiome science for systemic health"
- Key Products: DS-01 Daily Synbiotic
- Scale: $100M+ revenue, single hero product, DTC-only
- Audience: Science-literate health optimizers, 28–45
- vs. Verdana: "Seed proves the clinical-transparency DTC model scales. Single SKU vs. Verdana's five — different breadth strategy, same trust playbook."

**Momentous**
- Color: #264653
- Abbreviation: Mo
- Tagline: "Performance supplements backed by science"
- Key Products: Creatine, Omega-3, Huberman-partnered line
- Scale: $50M+ revenue, DTC + practitioner partnerships
- Audience: Performance-focused men, 25–45, podcast-influenced
- vs. Verdana: "Momentous owns the male performance niche via podcast partnerships. Verdana could learn from their influencer strategy without the bro-science risk."

**Onnit**
- Color: #555555
- Abbreviation: On
- Tagline: "Total human optimization"
- Key Products: Alpha Brain, Shroom Tech, New Mood
- Scale: $100M+ revenue (acquired by Unilever), retail + DTC + Amazon
- Audience: Fitness and wellness enthusiasts, 25–45, Joe Rogan audience
- vs. Verdana: "Onnit pioneered adaptogen supplements but with proprietary blends and hype-driven marketing — the opposite of Verdana's transparency approach."

## Page Layout

### Header Bar (sticky)

- Verdana wordmark + "Competitive Positioning Map" subtitle (left)
- Axis dropdowns (right):
  - "X-Axis:" dropdown with all 6 dimensions
  - "Y-Axis:" dropdown with all 6 dimensions
  - Default: X = Price Point, Y = Clinical Rigor

### Map Area (fills remaining viewport)

- Full-width, full-height below header
- Subtle grid: thin solid border, dashed crosshairs at center (50% mark)
- Axis labels on edges: low-end label at the left/bottom, high-end label at the right/top
- Brand nodes positioned using percentage coordinates derived from dimension scores
- Padding of ~60px on left and bottom for axis labels, ~20px on top and right

### Brand Nodes

- **Verdana:** 40px diameter circle, #2d6a4f, white 3px border ring, displays "Verdana" label below the node always, z-index above other nodes
- **All others:** 28px diameter circle, brand color, displays 2-letter abbreviation inside the circle
- All nodes: subtle drop shadow (0 2px 6px rgba(0,0,0,0.15))
- On hover: scale to 1.15x, z-index boost, cursor pointer
- Positioned via CSS `left` and `top` percentages within the map container

### Hover Cards

Appear on mouseenter, disappear on mouseleave. Anchored to the hovered node.

Content:
- Brand name (bold, brand color) + tagline (gray, below)
- Key Products line
- Revenue/scale + audience line
- "vs. Verdana:" italic comparison line (only for non-Verdana brands)
- Left border colored to match brand

Positioning logic:
- Default: card appears to the right of the node, vertically centered
- If node is in the right 40% of the map: card appears to the left instead
- If node is in the top 20%: card anchors below the node
- If node is in the bottom 20%: card anchors above the node
- Card width: 220px, padding: 10px 12px

### Axis Change Animation

When either dropdown changes:
- All nodes transition to new positions via CSS `transition: left 500ms ease, top 500ms ease`
- Axis labels on edges update immediately
- Any open hover card closes during transition

## Data Model

```javascript
const DIMENSIONS = [
  { id: 'price', name: 'Price Point', low: 'Budget', high: 'Premium' },
  { id: 'clinical', name: 'Clinical Rigor', low: 'No Evidence', high: 'RCT-Backed' },
  { id: 'lifestyle', name: 'Lifestyle Branding', low: 'Clinical/Functional', high: 'Aspirational' },
  { id: 'transparency', name: 'Ingredient Transparency', low: 'Proprietary Blends', high: 'Full Disclosure' },
  { id: 'dtc', name: 'DTC Focus', low: 'Retail/Amazon', high: 'Direct-to-Consumer' },
  { id: 'breadth', name: 'Product Breadth', low: 'Single SKU', high: 'Wide Catalog' }
];

const BRANDS = [
  {
    id: 'verdana',
    name: 'Verdana',
    abbr: 'V',
    color: '#2d6a4f',
    tagline: 'Clinical transparency adaptogens',
    products: 'Focus, Calm, Restore, Endure, Shield',
    scale: '$8M revenue, 60 employees, DTC-only',
    audience: 'Skeptical professionals, 30–50',
    vs_verdana: null,
    scores: { price: 70, clinical: 85, lifestyle: 25, transparency: 95, dtc: 95, breadth: 45 },
    isHero: true
  },
  // ... 8 more brands with same structure
];
```

## Visual Design

Matches existing tool palette:

- Page background: #f8faf7
- Header: #2d6a4f background, white text
- Map border: #ddd solid, crosshair dashes #ddd
- Axis labels: #888, 11px
- Hover card: white background, subtle box-shadow (0 4px 16px rgba(0,0,0,0.12)), 3px left border in brand color, border-radius 8px
- Node colors: per brand (see Brand Profiles above)
- Typography: system font stack
- CSS transitions: 500ms ease for node repositioning, 200ms for hover scale

## Technical Approach

- **Single self-contained HTML file** — no external dependencies, no build step
- All CSS and JavaScript embedded
- Brand data as a JavaScript array at the top for easy editing
- Nodes rendered as absolutely-positioned divs within a relative container
- Position calculated as: `left = score[xAxis]%`, `top = (100 - score[yAxis])%` (inverted Y so high values are at the top)
- Hover card positioning computed on mouseenter based on node's position in the viewport
- Dropdown `change` events trigger position recalculation
- Output path: `tools/competitive_positioning_map.html`

## Out of Scope

- Dragging nodes to reposition manually
- Adding or editing brands through the UI
- Saving, exporting, or sharing the map
- Zooming or panning
- Filtering/hiding specific brands
- Weighted or composite dimensions
