---
title: "Verdana Market Sizing Calculator — Design Spec"
version: 1.0
created: 2026-04-06
status: approved
---

# Verdana Market Sizing Calculator

## Purpose

An interactive HTML calculator that models Verdana's addressable market across three channels: DTC supplements (current business), wholesale (Whole Foods/Target), and new product line expansion (Metabolize/Glow). Users adjust assumptions via sliders and see revenue projections update in real-time. A TAM/SAM/SOM funnel provides market context alongside the bottom-up model.

## Strategic Context

Verdana is at $8M annual revenue with a growth plateau. The leadership team needs to evaluate three growth levers — optimizing the existing DTC channel, entering wholesale retail, and launching new SKUs — both independently and in combination. This tool quantifies each lever so trade-off decisions are grounded in numbers, not intuition.

## Page Structure

### 1. Floating Header Bar (sticky)

Always visible at top of page. Contains:

- Verdana wordmark + "Market Sizing Calculator" subtitle (left)
- Three live KPIs (right):
  - Combined Revenue (sum of all three channels)
  - Blended Gross Margin (weighted average across channels)
  - Gross Profit (combined)
- Updates instantly when any slider changes

### 2. TAM Funnel (static reference section)

Horizontal funnel visualization showing market narrowing:

- **TAM:** US Supplements Market — $58B
- **SAM:** Adaptogens segment — $4.2B
- **SAM narrowed:** Premium DTC + Retail adaptogens — $840M
- **SOM:** Verdana's projected share — dynamic, matches combined revenue total

The SOM box updates when sliders change. All other funnel values are static context. Section is labeled "Reference only" to distinguish from the interactive model below.

### 3. Channel Sections

Three stacked sections, each with a colored left border, containing:

- Channel name and description
- Live revenue and margin output (top-right of section)
- Primary sliders (always visible)
- "Advanced" toggle revealing detailed inputs
- "Reset to defaults" button

---

## Channel 1: DTC Supplements

**Color:** #2d6a4f (brand green)
**Description:** Current direct-to-consumer business

### Primary Sliders

| Input | Range | Default | Unit |
|---|---|---|---|
| Monthly new customers | 800–2,500 | 1,400 | customers |
| Average order value | $90–$160 | $120 | dollars |
| Subscription rate | 20–60% | 34% | percent |
| 90-day retention | 40–85% | 62% | percent |

### Advanced Inputs (hidden by default)

| Input | Range | Default | Unit |
|---|---|---|---|
| Customer acquisition cost | $30–$80 | $58 | dollars |
| Blended COGS % | 18–30% | 23.6% | percent |
| Organic channel share | 15–50% | 25% | percent |
| Orders per retained customer/year | 4–12 | 6 | orders |
| Free shipping threshold | $50–$120 | $75 | dollars |
| Orders qualifying for free shipping | 70–95% | 87% | percent |
| Avg shipping cost per order | $4–$12 | $7 | dollars |

### Calculation Logic

```
monthly_revenue = (new_customers * aov) + (retained_subscribers * aov * subscription_frequency)
retained_subscribers = cumulative_customers * subscription_rate * retention_rate
annual_revenue = monthly_revenue * 12
gross_profit = annual_revenue * (1 - cogs_pct)
```

Subscriber base accumulates over 12 months with churn applied at the retention rate. Month 1 starts with the current base (~10,800 units/month equivalent).

---

## Channel 2: Wholesale

**Color:** #6b4c9a (muted purple)
**Description:** Whole Foods (regional) + Target (national)

### Primary Sliders

| Input | Range | Default | Unit |
|---|---|---|---|
| Whole Foods stores | 0–85 | 85 | stores |
| Units per store per month | 10–50 | 24 | units |
| Target: include? | toggle | off | yes/no |
| Wholesale discount off retail | 45–60% | 50% | percent |

### Advanced Inputs (hidden by default)

| Input | Range | Default | Unit |
|---|---|---|---|
| Target stores (if enabled) | 100–1,800 | 500 | stores |
| Target units/store/month | 5–30 | 12 | units |
| Target discount off retail | 50–60% | 55% | percent |
| Slotting fees (one-time) | $0–$500K | $50K | dollars |
| DTC cannibalization | 0–30% | 10% | percent |
| Ramp months to full velocity | 1–12 | 6 | months |
| SKUs offered | multi-select | Focus, Calm | product list |
| Average retail price (pre-discount) | read-only | $60 | dollars |

### Calculation Logic

```
wf_annual = wf_stores * units_per_store * 12 * avg_retail_price * (1 - wholesale_discount)
target_annual = (target_enabled ? target_stores * target_units * 12 * avg_price * (1 - target_discount) : 0)
ramp_factor = average velocity over ramp period (linear ramp)
gross_revenue = (wf_annual + target_annual) * ramp_factor
dtc_cannibalization_offset = gross_revenue * cannibalization_pct (subtracted from DTC channel)
wholesale_cogs = based on selected SKU COGS at wholesale volume
gross_profit = gross_revenue - wholesale_cogs - slotting_fees_amortized
```

Cannibalization is modeled as a percentage reduction applied to the DTC channel's revenue when wholesale is active. This cross-channel effect is reflected in both the DTC section output and the combined totals.

---

## Channel 3: New Product Line

**Color:** #c17817 (warm amber)
**Description:** Metabolize and/or Glow expansion

### Primary Sliders

| Input | Range | Default | Unit |
|---|---|---|---|
| Launch Metabolize? | toggle | off | yes/no |
| Metabolize price | $55–$85 | $70 | dollars |
| Launch Glow? | toggle | off | yes/no |
| Glow price | $55–$85 | $65 | dollars |
| Year 1 penetration (existing customers) | 5–30% | 15% | percent |

### Advanced Inputs (hidden by default)

| Input | Range | Default | Unit |
|---|---|---|---|
| R&D cost per product | $50K–$200K | $100K | dollars |
| Launch quarter | Q1–Q4 | Q3 | quarter |
| Cross-sell rate (existing → new) | 5–25% | 12% | percent |
| New customer acquisition from new SKU | 0–500/month | 150 | customers/month |
| Metabolize COGS | $12–$22 | $16 | dollars |
| Glow COGS | $10–$18 | $13 | dollars |
| Cannibalization of existing SKUs | 0–15% | 5% | percent |

### Calculation Logic

```
months_active = 12 - launch_quarter_start_month + 1
existing_customer_units = existing_customer_base * penetration_rate * months_active
new_customer_units = new_acquisition_monthly * months_active
total_units = existing_customer_units + new_customer_units (per product if enabled)
revenue = sum(product_units * product_price) for each enabled product
gross_profit = revenue - (units * cogs) - r_and_d_costs
```

---

## Cross-Channel Effects

- **Wholesale cannibalization** — When wholesale channel is active, a configurable percentage of wholesale revenue is subtracted from DTC to model customers shifting from online to in-store
- **New product cannibalization** — When new SKUs launch, a small percentage of existing SKU volume shifts to new products (net-neutral for revenue but affects per-product metrics)
- These effects are reflected in real-time as sliders change

## UI Details

### Slider Behavior

- HTML `<input type="range">` elements styled to match the wellness theme
- Current value displayed to the right of each slider label
- Dragging recalculates channel output AND floating header in real-time via `input` event (not `change`)
- Toggle inputs (Target, Metabolize, Glow) use styled checkbox switches
- SKU multi-select uses clickable pill buttons

### Progressive Disclosure

- Each channel section has an "Advanced" toggle at the bottom
- Click reveals additional inputs with a slide-down animation
- Advanced inputs have slightly muted styling to visually distinguish from primary sliders
- Collapsing advanced inputs does not reset their values

### Default Values

All defaults are pre-loaded from Verdana's brand definition:
- DTC: current actuals ($8M, 1,400 new customers/month, $120 AOV, 34% subscription, 62% retention)
- Wholesale: terms from Whole Foods/Target discussions (85 stores, 50%/55% discount)
- New Products: R&D estimates and pricing informed by current product line ($45-$85 range)

### Number Formatting

- Revenue: `$X.XM` for millions, `$XXK` for thousands
- Percentages: `XX.X%`
- Integers: comma-separated (`1,400`)
- All via `Intl.NumberFormat`

## Visual Design

- **Wellness light theme** — matches OKR tool palette
- Page background: #f8faf7
- Card backgrounds: white with subtle box-shadow
- Channel border colors: DTC #2d6a4f, Wholesale #6b4c9a, New Products #c17817
- Floating header: #2d6a4f background, white text
- Slider track: channel's light tint; slider thumb: channel's primary color
- Typography: system font stack, clean spacing
- Max content width: 900px, centered

## Data Model

```javascript
const DEFAULTS = {
  dtc: {
    monthly_new_customers: 1400,
    aov: 120,
    subscription_rate: 0.34,
    retention_90day: 0.62,
    // advanced
    cac: 58,
    cogs_pct: 0.236,
    organic_share: 0.25,
    orders_per_retained: 6,
    free_shipping_threshold: 75,
    free_shipping_qualifying_pct: 0.87,
    avg_shipping_cost: 7
  },
  wholesale: {
    wf_stores: 85,
    wf_units_per_store: 24,
    target_enabled: false,
    wholesale_discount: 0.50,
    // advanced
    target_stores: 500,
    target_units_per_store: 12,
    target_discount: 0.55,
    slotting_fees: 50000,
    dtc_cannibalization: 0.10,
    ramp_months: 6,
    skus_offered: ['focus', 'calm']
  },
  new_products: {
    metabolize_enabled: false,
    metabolize_price: 70,
    glow_enabled: false,
    glow_price: 65,
    penetration_rate: 0.15,
    // advanced
    rd_cost_per_product: 100000,
    launch_quarter: 3,
    cross_sell_rate: 0.12,
    new_acquisition_monthly: 150,
    metabolize_cogs: 16,
    glow_cogs: 13,
    existing_cannibalization: 0.05
  }
};

// Products reference (for wholesale SKU selection and cross-channel calcs)
const PRODUCTS = [
  { id: 'focus', name: 'Verdana Focus', price: 65, cogs: 14.30, monthly_units: 3200 },
  { id: 'calm', name: 'Verdana Calm', price: 55, cogs: 12.10, monthly_units: 2800 },
  { id: 'endure', name: 'Verdana Endure', price: 75, cogs: 18.75, monthly_units: 1600 },
  { id: 'shield', name: 'Verdana Shield', price: 45, cogs: 13.05, monthly_units: 1100 },
  { id: 'restore', name: 'Verdana Restore', price: 85, cogs: 19.55, monthly_units: 2100 }
];
```

## Technical Approach

- **Single self-contained HTML file** — no external dependencies, no build step
- All CSS and JavaScript embedded
- Calculation functions are pure (inputs → outputs), separate from DOM rendering
- Slider `input` events trigger recalculation → DOM update cycle
- Cross-channel effects computed after individual channel calculations
- Output path: `tools/market_sizing_calculator.html`

## Out of Scope

- Saving/exporting scenarios or generating reports
- Multi-year projections (Year 1 model only)
- Detailed P&L below gross profit (no opex, EBITDA, etc.)
- Monte Carlo or probabilistic ranges
- Comparison mode (side-by-side scenarios)
