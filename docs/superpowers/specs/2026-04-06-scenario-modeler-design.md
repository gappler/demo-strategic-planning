---
title: "Verdana Scenario Modeler — Design Spec"
version: 1.0
created: 2026-04-06
status: approved
---

# Verdana Scenario Modeler

## Purpose

An interactive HTML tool that models four strategic paths for Verdana — stay the course (DTC only), expand into wholesale, launch new products, or cut the underperforming Shield SKU and reallocate resources. Each scenario projects revenue, margins, required investment, team headcount, and risk factors across 12 quarters (3 years). Users can toggle strategic moves on/off independently to create blended scenarios (e.g., wholesale AND cut Shield), tune assumptions via sliders, pin named configurations, and compare them side by side in a slide-up drawer.

## Strategic Context

Verdana is a $8M DTC adaptogen supplement company with 60 employees. Revenue has been flat for two quarters. CAC is rising (up 41% YoY to $58). The leadership team faces interconnected decisions about wholesale expansion (Whole Foods/Target interest), product line rationalization (Shield underperforming at -18% YoY), and new product launches (Metabolize and Glow in R&D pipeline). The company cannot pursue all options simultaneously — this tool quantifies each path and their combinations so trade-off decisions are grounded in projections, not intuition.

## Core Mechanic: Toggle + Tune + Pin + Compare

The modeler treats the current Verdana business as a baseline, with three strategic moves that can be independently toggled on/off:

1. **Expand into Wholesale** — Whole Foods regional (85 stores), optional Target national
2. **Launch New Products** — Metabolize (berberine) and/or Glow (beauty-from-within)
3. **Cut Shield & Reallocate** — Discontinue underperformer, redirect resources to marketing or margin

"Stay the course" is simply all three moves toggled off. Blended scenarios are any combination of enabled moves. This gives up to 8 configurations (2^3), each with tunable parameters via sliders.

Users build a scenario, name it, pin it, then build another. The comparison drawer shows all pinned scenarios side by side.

## Page Layout (5 Zones)

### Zone 1: Sticky Header Bar

Always visible at top. Contains:

- Verdana wordmark + "Scenario Modeler" subtitle (left)
- Five live KPIs (right), updating instantly when any toggle or slider changes:
  - Y3 Revenue
  - Blended Gross Margin
  - 3-Year Cumulative Investment
  - Headcount Delta
  - Risk Level (●○○ / ●●○ / ●●●)

### Zone 2: Strategic Move Cards

Three cards displayed horizontally below the header:

| Card | Color (enabled) | Description |
|---|---|---|
| Expand into Wholesale | #2d6a4f (brand green) | Whole Foods regional, optional Target national |
| Launch New Products | #6b4c9a (muted purple) | Metabolize and/or Glow expansion |
| Cut Shield & Reallocate | #c17817 (warm amber) | Discontinue underperformer, redirect resources |

Each card shows:
- Toggle state: checkmark (enabled) or dash (disabled)
- Move name and one-line description
- Impact summary when enabled: revenue delta, margin delta, hires delta
- When disabled: grayed out at 70% opacity, impact metrics show dashes

Clicking a card toggles it on/off. All downstream calculations, slider panels, projections, and header KPIs update immediately.

### Zone 3: Slider Panels

Horizontal row of panels, one per enabled move. Disabled moves show a placeholder ("Enable above to configure"). Each panel has:

- Color-coded left border matching the move's card
- Primary sliders (always visible)
- "Advanced settings" toggle revealing detailed inputs
- All sliders use `input` event for real-time recalculation

#### Wholesale Sliders

**Primary:**

| Input | Range | Default | Unit |
|---|---|---|---|
| Whole Foods stores | 0–85 | 85 | stores |
| Units per store per month | 10–50 | 24 | units |
| Target: include? | toggle | off | yes/no |
| Wholesale discount off retail | 45–60% | 50% | percent |

**Advanced:**

| Input | Range | Default | Unit |
|---|---|---|---|
| Target stores (if enabled) | 100–1,800 | 500 | stores |
| Target units/store/month | 5–30 | 12 | units |
| Target discount off retail | 50–60% | 55% | percent |
| Slotting fees (one-time) | $0–$500K | $50K | dollars |
| DTC cannibalization | 0–30% | 10% | percent |
| Ramp months to full velocity | 1–12 | 6 | months |

#### New Products Sliders

**Primary:**

| Input | Range | Default | Unit |
|---|---|---|---|
| Launch Metabolize? | toggle | off | yes/no |
| Metabolize price | $55–$85 | $70 | dollars |
| Launch Glow? | toggle | off | yes/no |
| Glow price | $55–$85 | $65 | dollars |
| Year 1 penetration (existing customers) | 5–30% | 15% | percent |

**Advanced:**

| Input | Range | Default | Unit |
|---|---|---|---|
| R&D cost per product | $50K–$200K | $100K | dollars |
| Launch quarter | Q1–Q4 | Q3 | quarter |
| New customer acquisition from new SKU | 0–500/month | 150 | customers/month |
| Metabolize COGS | $12–$22 | $16 | dollars |
| Glow COGS | $10–$18 | $13 | dollars |
| Cannibalization of existing SKUs | 0–15% | 5% | percent |

#### Cut Shield Sliders

**Primary:**

| Input | Range | Default | Unit |
|---|---|---|---|
| Transition quarter | Q1–Q4 | Q2 Y1 | quarter |
| Reallocate to marketing | 0–100% | 60% | percent |
| Retain as margin improvement | 0–100% | 40% | percent |

The marketing/margin split is a linked pair — adjusting one updates the other to maintain 100% total.

### Zone 4: Projection Area

Four components in this zone:

#### Stacked Bar Chart — Quarterly Revenue by Source

- 12 bars (Q1–Q12), each showing revenue contribution stacked by source
- Colors: DTC (#2d6a4f), Wholesale (#6b4c9a), New Products (#c17817)
- Vertical dividers between Y1/Y2 and Y2/Y3
- Year labels below
- Legend in the chart header

#### Margin Trend — Small Bar Chart

- 12 quarterly bars showing blended gross margin percentage
- Color gradient by year (dark → medium → light green)
- Current margin (76.4%) to projected Y3 margin labeled below

#### Investment & Headcount — Summary Cards

- Cumulative investment card with breakdown (ops buildout, slotting, R&D, marketing)
- Headcount card showing Y3 total with delta breakdown (+X hires, -Y from cuts)

#### Risk Factors — Alert Bar

- Red-tinted bar at the bottom of the projection area
- Shows risk factor chips that activate based on enabled moves
- Each chip: risk name (bold) + one-line description

### Zone 5: Pin Bar + Comparison Drawer

#### Pin Bar (always visible)

- "Pin Current Scenario" button + text input for naming
- Right side: "Compare N Pinned Scenarios" toggle to expand drawer

#### Comparison Drawer (expandable)

- Slides up from the bottom when expanded
- Full-width comparison table with columns for each pinned scenario
- Rows: Y1 Revenue, Y2 Revenue, Y3 Revenue, Y3 Gross Margin, 3Y Investment, Headcount Delta, Risk Level
- Current/most-recently-pinned scenario highlighted with green background column
- Pinned scenarios can be deleted (X button in column header)

## Data Model

### Baseline (Current Verdana)

```javascript
const BASELINE = {
  annual_revenue: 8000000,
  monthly_revenue: 667000,
  employees: 60,
  products: [
    { id: 'focus', name: 'Verdana Focus', price: 65, cogs: 14.30, margin: 0.78, monthly_units: 3200 },
    { id: 'calm', name: 'Verdana Calm', price: 55, cogs: 12.10, margin: 0.78, monthly_units: 2800 },
    { id: 'endure', name: 'Verdana Endure', price: 75, cogs: 18.75, margin: 0.75, monthly_units: 1600 },
    { id: 'shield', name: 'Verdana Shield', price: 45, cogs: 13.05, margin: 0.71, monthly_units: 1100 },
    { id: 'restore', name: 'Verdana Restore', price: 85, cogs: 19.55, margin: 0.77, monthly_units: 2100 }
  ],
  metrics: {
    new_customers_monthly: 1400,
    aov: 120,
    subscription_rate: 0.34,
    retention_90day: 0.62,
    cac: 58,
    blended_gross_margin: 0.764
  }
};
```

### Scenario State

```javascript
const scenario = {
  wholesale: {
    enabled: false,
    wf_stores: 85,
    wf_units_per_store: 24,
    target_enabled: false,
    target_stores: 500,
    target_units_per_store: 12,
    wholesale_discount: 0.50,
    target_discount: 0.55,
    slotting_fees: 50000,
    dtc_cannibalization: 0.10,
    ramp_months: 6
  },
  new_products: {
    enabled: false,
    metabolize_enabled: false,
    metabolize_price: 70,
    metabolize_cogs: 16,
    glow_enabled: false,
    glow_price: 65,
    glow_cogs: 13,
    penetration_rate: 0.15,
    rd_cost_per_product: 100000,
    launch_quarter: 3,
    new_acquisition_monthly: 150,
    existing_cannibalization: 0.05
  },
  cut_shield: {
    enabled: false,
    transition_quarter: 2,
    reallocate_to_marketing: 0.60,
    retain_as_margin: 0.40
  }
};
```

### Pinned Scenario

```javascript
const pinned = {
  name: "Wholesale + Cut Shield",
  config: { /* deep copy of scenario state */ },
  results: {
    quarterly: [
      { quarter: 1, revenue: { dtc: X, wholesale: Y, new_products: Z, total: T }, gross_margin: M, investment: I, headcount_delta: H },
      // ... 12 quarters
    ],
    summary: {
      y1_revenue: X, y2_revenue: X, y3_revenue: X,
      y3_gross_margin: X,
      total_investment: X,
      headcount_delta: X,
      risk_level: 'medium',
      risk_factors: ['brand_dilution', 'margin_compression', 'customer_disruption']
    }
  }
};
```

## Projection Logic

### DTC Baseline Projection

```
For each quarter q (1-12):
  year = ceil(q / 4)
  annual_growth_rate = { 1: 0.05, 2: 0.08, 3: 0.10 }[year]
  quarterly_growth_factor = (1 + annual_growth_rate) ^ (q / 4)
  dtc_revenue[q] = (baseline_annual_revenue / 4) * quarterly_growth_factor
  
  If cut_shield enabled and q >= transition_quarter:
    dtc_revenue[q] -= (shield_monthly_units * shield_price * 3)  // remove Shield quarterly revenue
    shield_quarterly_savings = shield_monthly_units * (shield_price - shield_cogs) * 3
    marketing_reinvestment = shield_quarterly_savings * reallocate_to_marketing
    additional_customers = marketing_reinvestment / cac  // CAC from baseline metrics ($58)
    dtc_revenue[q] += additional_customers * aov
  
  If wholesale enabled:
    dtc_revenue[q] -= dtc_revenue[q] * dtc_cannibalization
```

### Wholesale Projection

```
For each quarter q:
  If not enabled: wholesale_revenue[q] = 0
  
  ramp_quarter = ceil(ramp_months / 3)
  velocity = min(1, q / ramp_quarter)  // linear ramp
  
  wf_quarterly = wf_stores * wf_units_per_store * 3 * avg_retail_price * (1 - wholesale_discount) * velocity
  target_quarterly = target_enabled ? target_stores * target_units * 3 * avg_price * (1 - target_discount) * velocity : 0
  
  wholesale_revenue[q] = wf_quarterly + target_quarterly
  wholesale_cogs[q] = units * weighted_avg_cogs_of_offered_skus
  
  // Quarterly growth after ramp
  if q > ramp_quarter: wholesale_revenue[q] *= (1.03) ^ (q - ramp_quarter)
```

### New Products Projection

```
For each quarter q:
  If not enabled or q < launch_quarter: new_product_revenue[q] = 0
  
  quarters_active = q - launch_quarter + 1
  launch_velocity = quarters_active == 1 ? 0.5 : 1.0
  
  For each enabled product (metabolize, glow):
    existing_customer_units = existing_base * penetration_rate / 4 * launch_velocity
    new_customer_units = new_acquisition_monthly * 3 * launch_velocity
    product_revenue = (existing_customer_units + new_customer_units) * product_price
    product_revenue *= (1.05) ^ max(0, quarters_active - 1)  // 5% quarterly growth
  
  // Cannibalization of existing SKU volume
  dtc_revenue[q] -= dtc_revenue[q] * existing_cannibalization * launch_velocity
```

### Margin Calculation

```
For each quarter q:
  dtc_gross_profit = dtc_revenue[q] * baseline_gross_margin
  wholesale_gross_profit = wholesale_revenue[q] - wholesale_cogs[q]
  new_product_gross_profit = new_product_revenue[q] - new_product_cogs[q]
  
  total_revenue = dtc + wholesale + new_products
  total_gross_profit = dtc_gp + wholesale_gp + new_product_gp
  blended_margin[q] = total_gross_profit / total_revenue
```

### Investment Calculation

```
cumulative_investment = 0

If wholesale enabled:
  + ops_buildout: $150K (amortized over ramp period)
  + slotting_fees (one-time)
  + EDI_integration: $50K
  + retail_compliance: $30K
  + marketing_support: $20K/quarter while active

If new_products enabled:
  + rd_cost_per_product * number_of_enabled_products
  + launch_marketing: $30K per product
  + initial_inventory: $20K per product

If cut_shield enabled:
  + transition_costs: $15K (inventory write-down, customer communication)
  - savings: shield operational costs eliminated after transition
```

### Headcount Calculation

```
headcount_delta = 0

If wholesale enabled:
  + 2 ops/logistics hires
  + 1 wholesale account manager

If new_products enabled:
  + 1 product developer (if both products, still 1 — shared resource)

If cut_shield enabled:
  - 1 FTE equivalent (redistributed from Shield-related work)
```

### Risk Factors

| Risk | Triggered By | Description |
|---|---|---|
| Brand Dilution | Wholesale enabled | Retail shelf presence may undermine premium DTC positioning |
| Margin Compression | Wholesale enabled | Wholesale at ~38% gross vs 76% DTC drags blended margin |
| Ops Complexity | Wholesale enabled | EDI, retail compliance, chargebacks are new capabilities for the team |
| DTC Cannibalization | Wholesale enabled | Some DTC customers shift to retail purchases at lower margin |
| Execution Distraction | New Products enabled | R&D + launch while trying to fix the growth plateau |
| Category Drift | Glow enabled | Beauty-from-within moves away from core adaptogen positioning |
| Inventory Risk | New Products enabled | New SKU demand is unvalidated |
| Customer Disruption | Cut Shield enabled | Shield subscribers need migration path; some will churn entirely |
| Revenue Gap | Cut Shield enabled | Immediate revenue loss before marketing reallocation yields returns |
| Team Morale | Cut Shield enabled | Discontinuing a product can signal uncertainty to the team |
| Bandwidth Risk | 2+ moves enabled | 60-person team stretched across multiple strategic initiatives simultaneously |
| Capital Risk | Investment > $500K | Significant capital deployment on an $8M revenue base |

**Risk level formula:**
- 0–1 moves enabled: Low (●○○)
- 2 moves enabled: Medium (●●○)
- 3 moves enabled: High (●●●)

## Visual Design

Matches the existing tool palette (OKR planner, market sizing calculator):

- Page background: #f8faf7 (warm off-white)
- Header bar: #2d6a4f background, white text
- Cards: white (#fff) with subtle box-shadow
- Move colors:
  - Wholesale: #2d6a4f (brand green)
  - New Products: #6b4c9a (muted purple)
  - Cut Shield: #c17817 (warm amber)
- Risk bar: #fff5f5 background, #e74c3c left border
- Comparison drawer: #f0f4ee background
- Typography: system font stack, clean spacing
- CSS transitions for all state changes (300ms ease)
- Max content width: 1200px (wider than other tools to accommodate the horizontal card layout)

## Technical Approach

- **Single self-contained HTML file** — no external dependencies, no build step
- All CSS and JavaScript embedded in the file
- Baseline data and scenario defaults as JavaScript objects at the top
- Pure calculation functions (inputs → outputs), separate from DOM rendering
- Slider `input` events trigger recalculation → DOM update cycle
- Pinned scenarios stored as in-memory array of snapshot objects
- Stacked bar chart rendered via CSS (no canvas/SVG library needed)
- Output path: `tools/scenario_modeler.html`

## Out of Scope

- Data persistence / saving to disk or localStorage
- Export to PDF, spreadsheet, or presentation
- Monte Carlo or probabilistic ranges
- Editable risk factor text through the UI
- Integration with OKR planner or market sizing calculator
- User authentication or multi-user collaboration
- Detailed P&L below gross profit (no opex, EBITDA, net income)
