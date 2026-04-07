---
title: "Verdana Executive Strategy Summary — Design Spec"
version: 1.0
created: 2026-04-06
status: approved
---

# Verdana Executive Strategy Summary

## Purpose

A synthesized executive strategy document that reads all Verdana planning data — brand definition, OKR goals, market sizing, scenario model outputs, and competitive positioning — and presents a polished strategic recommendation for FY2027. Output as both a styled HTML scrolling narrative and a markdown document.

## Strategic Context

Verdana's leadership team has built four analytical tools during the planning process: OKR planner, market sizing calculator, scenario modeler, and competitive positioning map. Each tool explores one dimension of the strategy. This document synthesizes their outputs into a single coherent recommendation with financial projections, risks, contingency paths, and next steps — the artifact the board reviews and the team executes against.

## The Recommendation

**Selective Expansion: Wholesale + Cut Shield**

Enter Whole Foods regional (85 stores, Pacific NW + Northern California) while discontinuing the underperforming Shield SKU. Reallocate Shield resources 60% to marketing (CAC reduction), 40% to margin improvement. Hold new product launches (Metabolize, Glow) for Year 2 contingent on wholesale success.

**Why this path (sourced from each tool):**

- **Scenario Modeler:** WS + Cut Shield projects $12.4M Y3 revenue vs $9.8M baseline (+$2.6M). Medium risk level (2 moves). $420K 3-year investment. +4 headcount (net of Shield FTE). Adding new products would push to high risk for only $2.2M additional Y3 upside — not worth the bandwidth strain on a 60-person team.

- **Market Sizing:** Whole Foods at 85 stores, 24 units/store/month, 50% wholesale discount yields meaningful revenue with a 6-month ramp. Target national deferred until Whole Foods proves the model. DTC cannibalization estimated at 10% — net positive.

- **OKR Alignment:** Maps to Base Case objectives — reduce CAC from $58 to $45 (O1), grow subscription rate from 34% to 40% (O2), rationalize product portfolio (O5). Wholesale adds selective expansion objectives (O4 marketing, O10 ops). Shield discontinuation frees R&D and marketing resources for core SKU optimization.

- **Competitive Positioning:** Verdana's transparency moat (95/100 score) is its strongest differentiator. Whole Foods' premium health aisle reinforces clinical positioning — unlike Target, which risks brand dilution. Key threat: Ritual (85/100 transparency, $100M+ scale) could enter adaptogens. Strengthening retail presence now builds a distribution moat.

**Contingency paths:**

- **Path B — Escalate (All Three Moves):** If wholesale gross margin exceeds 42% by Q2 Y1, greenlight Metabolize launch in H2. Ceiling: $14.6M Y3 revenue. Risk: high (bandwidth, capital).

- **Path C — Retreat (DTC Only):** If wholesale revenue < 30% of projection by Q2 Y1, pause wholesale expansion, redirect investment to DTC optimization and subscription growth. Floor: $9.8M Y3 revenue. Risk: low, but growth ceiling limited.

## Output Files

Two files with identical content, different formats:

1. **`tools/executive_strategy_summary.html`** — Styled HTML scrolling narrative for browser viewing
2. **`output/executive_strategy_summary.md`** — Clean markdown for distribution, printing, and version control

Both are static documents with baked-in content (not dynamically computed from other tools).

## HTML Page Structure (Scrolling Narrative)

### Hero Header

- Full-width #2d6a4f background
- "Verdana FY2027 Strategic Plan" subtitle (uppercase, letterspaced)
- "Executive Strategy Summary" title (large, bold)
- "Prepared April 2026 · Confidential" date line

### Section 1: Executive Overview

Numbered section header (circled "1" + title).

**Narrative paragraph** summarizing the situation:
- Verdana is an $8M DTC adaptogen company with 60 employees
- Revenue flat for 2 quarters, CAC up 41% YoY to $58
- Leadership faces interconnected decisions: wholesale, product line, CAC optimization
- The company cannot pursue all options simultaneously

**4 KPI cards** in a horizontal row:
- Current Revenue: $8.0M
- Gross Margin: 76.4%
- CAC: $58 (▲41% YoY, red)
- Team: 60 people

### Section 2: Recommended Strategic Direction

Numbered section header (circled "2" + title).

**Recommendation callout box** — green left border, light green background:
- Title: "Selective Expansion: Wholesale + Cut Shield"
- Summary: Enter Whole Foods (85 stores, Pacific NW) while discontinuing Shield. Reallocate Shield resources 60% to marketing, 40% to margin. Hold new products for Year 2.

**"Why This Path" rationale** — 3 cards in a row:
- **Revenue Unlock:** Wholesale adds $2.1M Y3 revenue while DTC optimization continues
- **Margin Defense:** Cutting Shield reclaims 1.2% blended margin, partially offsets wholesale drag
- **Manageable Risk:** Two moves, not three. Keeps bandwidth focused for a 60-person team

**Supporting evidence** — 4 paragraphs sourcing the rationale from each tool (scenario modeler, market sizing, OKRs, competitive positioning). See "The Recommendation" section above for content.

### Section 3: 3-Year Financial Projections

Numbered section header (circled "3" + title).

**Comparison table** — 3 columns (Metric, Baseline, Recommended, Delta):

| Metric | Baseline (Stay the Course) | Recommended (WS + Cut Shield) | Delta |
|---|---|---|---|
| Y1 Revenue | $8.4M | $9.1M | +$700K |
| Y2 Revenue | $9.1M | $10.8M | +$1.7M |
| Y3 Revenue | $9.8M | $12.4M | +$2.6M |
| Y3 Gross Margin | 76.4% | 68.2% | -8.2% |
| Y3 Gross Profit | $7.5M | $8.5M | +$1.0M |
| 3Y Cumulative Investment | $0 | $420K | +$420K |
| Y3 Headcount | 60 | 64 (+3 WS ops, +2 mktg, -1 Shield) | +4 |

Note: Values sourced from the scenario modeler's computeProjection() output for the WS + Cut Shield configuration with default slider values.

**Net impact callout** — green-tinted box below the table:
"$2.6M additional Y3 revenue at the cost of 8.2% margin compression and $420K investment. Y3 gross profit: $8.5M (recommended) vs $7.5M (baseline) — a $1M improvement despite lower margin rate."

### Section 4: Key Risks & Mitigations

Numbered section header (circled "4" in red + title in red).

**Risk rows** — each in a red-tinted card with 3 columns (risk name, description, mitigation):

| Risk | Description | Mitigation |
|---|---|---|
| Brand Dilution | Retail shelf presence may undermine premium DTC positioning | Start regional (Whole Foods only), monitor brand sentiment quarterly, maintain premium in-store presentation |
| Margin Compression | Wholesale at ~38% gross vs 76% DTC drags blended margin | Track gross profit dollars not margin percentage; Shield savings offset ~1.2%; negotiate toward 45% wholesale discount at volume |
| Ops Complexity | EDI, retail compliance, chargebacks are new capabilities | Hire wholesale ops team before launch; budget $150K for systems buildout; 6-month ramp protects against early stumbles |
| DTC Cannibalization | Some DTC customers shift to retail at lower margin | Model 10% cannibalization (conservative); monitor DTC metrics weekly after wholesale launch; geographic analysis of overlap |
| Customer Disruption | Shield subscribers need migration; some will churn | Proactive communication plan; offer Focus or Calm as replacement with transition discount; target < 5% subscriber loss |

### Section 5: What If We're Wrong? Contingency Paths

Numbered section header (circled "5" in purple + title in purple).

**Two contingency cards** side by side:

**Path B — Escalate (All Three Moves):**
- Add Metabolize launch to WS + Cut Shield
- Ceiling: $14.6M Y3 revenue, but high risk (●●●), $720K investment, +7 headcount
- Trigger: Wholesale gross margin > 42% by Q2 Y1
- Why wait: Proves wholesale ops capability before adding product launch complexity

**Path C — Retreat (DTC Only):**
- Abandon wholesale, double down on DTC optimization + subscription growth
- Floor: $9.8M Y3 revenue, low risk (●○○), $0 investment
- Trigger: Wholesale revenue < 30% of projection by Q2 Y1
- Why this exists: Protects the business if retail doesn't work; preserves margin advantage

### Section 6: Immediate Next Steps (30 Days)

Numbered section header (circled "6" + title).

**Checkbox-style action items:**

1. Initiate Whole Foods partnership discussions — request terms sheet by April 30 (Owner: VP Operations)
2. Begin Shield wind-down analysis — customer migration plan draft by April 15 (Owner: VP Product)
3. Post wholesale ops job descriptions — target 2 hires by June 1 (Owner: COO)
4. Set up trigger-point dashboard — CAC, wholesale margin, and revenue vs plan tracked weekly (Owner: CFO)
5. Brief full team on strategic direction — all-hands by April 10 (Owner: CEO)
6. Engage Whole Foods broker/consultant for retail compliance readiness — by April 20 (Owner: VP Operations)

## Markdown Document Structure

The markdown file mirrors the HTML content exactly with:
- YAML frontmatter (title, version, date, status: confidential)
- H1 title, H2 per section
- Tables for projections and risks
- Blockquote for the recommendation callout
- Bullet lists for rationale, risks, and next steps
- No images or embedded content — pure text

## Visual Design (HTML)

Matches existing tool palette:
- Page background: #f8faf7
- Hero header: #2d6a4f background, white text
- Section numbers: circled badges (green for most, red for risks, purple for contingencies)
- Recommendation callout: #f0faf0 background, #2d6a4f 3px left border
- Risk cards: #fff5f5 background
- Contingency cards: white with #ddd border
- KPI cards: white with #e8e8e8 border
- Rationale cards: #f8faf7 background
- Typography: system font stack
- Max width: 800px, centered (narrower than tools — this is a reading document)
- Print-friendly: no fixed positioning, natural flow

## Technical Approach

- **Two static files** — no JavaScript needed, no interactivity, no computation
- HTML: self-contained with embedded CSS
- Markdown: clean formatting, no HTML embedded
- Both generated from the same content — the plan specifies the exact text for each section
- Output paths: `tools/executive_strategy_summary.html` and `output/executive_strategy_summary.md`

## Out of Scope

- Dynamic data binding to other tools (this is a static synthesis)
- PDF export
- Editable content through the UI
- Version comparison or change tracking
- Interactive charts or data visualization
