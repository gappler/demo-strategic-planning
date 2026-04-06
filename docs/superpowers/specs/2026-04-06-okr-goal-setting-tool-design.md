---
title: "Verdana OKR & Annual Goal Setting Tool — Design Spec"
version: 1.0
created: 2026-04-06
status: approved
---

# Verdana OKR & Annual Goal Setting Tool

## Purpose

An interactive HTML dashboard that presents Verdana's FY2027 annual objectives and key results organized by function (Marketing, Product, Operations, Finance) across three strategic scenarios (Base, Upside, Downside). Leadership can switch scenarios to see how objectives, KR targets, and resource requirements cascade — making trade-offs tangible rather than abstract.

## Strategic Context

Verdana is a $8M DTC adaptogen supplement company with 60 employees. Revenue has been flat for two quarters. CAC is rising (up 41% YoY to $58). The leadership team needs to align on annual priorities while navigating decisions about wholesale expansion, product line rationalization (Shield underperforming), and subscription growth. The company cannot pursue all options simultaneously — this tool forces those trade-offs into view.

## Three Scenarios

### Base Case — $9.5M — "Stabilize & Optimize"

Fix the growth engine before expanding. Conservative resource allocation.

- Reduce CAC from $58 to $45
- Grow subscription rate from 34% to 40%
- Discontinue Shield
- No wholesale this year
- ~10 objectives, ~32 key results

**Trigger points:**
- If CAC < $42 by Q2 → shift to Upside
- If CAC > $65 by Q2 → shift to Downside

### Upside — $12M — "Selective Expansion"

Everything in Base, plus selective growth bets.

- Whole Foods regional wholesale launch (85 stores, Pacific NW + NorCal)
- Launch Verdana Metabolize (berberine SKU)
- Wholesale operations buildout
- ~12 objectives, ~38 key results

**Trigger points:**
- If wholesale gross margin > 42% by Q2 → evaluate Target national
- If wholesale < 30% of revenue projection → pause expansion

### Downside — $7.5M — "Protect Margins"

Defensive posture focused on profitability and cash preservation.

- Cut marketing spend 20%
- Freeze hiring
- Consolidate to top 3 SKUs (Focus, Calm, Restore)
- Focus on subscriber LTV over new acquisition
- ~8 objectives, ~24 key results

**Trigger points:**
- If revenue > $8.5M annualized run rate by Q2 → shift to Base
- If cash runway < 9 months → restructure

## Objectives by Function

### Marketing (color: green #4ecca3)

**Shared across all scenarios:**

1. **Reduce Customer Acquisition Cost**
   - Addresses: Growth Plateau, Rising CAC
   - KRs vary by scenario (Base: $45, Upside: $48, Downside: $50 with 20% less spend)
   - Resources: 2 hires (Base/Upside), 0 hires (Downside) · $80K / $80K / $0

2. **Grow Subscription & Retention**
   - Addresses: Subscription Gap (34% vs 40% industry), Month-3 Churn
   - KRs: subscription rate target, 90-day retention target, loyalty program launch
   - Resources: 1 hire · $40K

3. **Diversify Acquisition Channels**
   - Addresses: Rising CAC, Channel Concentration
   - KRs: organic channel share growth, new channel pilots, attribution improvement
   - Resources: 0 hires · $30K

**Upside only:**

4. **Launch Wholesale Marketing Support**
   - Addresses: Wholesale Question (Whole Foods)
   - KRs: retail-ready packaging, in-store POS materials, co-marketing plan
   - Resources: 1 hire · $60K

### Product (color: purple #a78bfa)

**Shared across Base and Upside:**

5. **Rationalize Product Portfolio**
   - Addresses: Shield Underperformance, Margin Pressure
   - KRs: Shield ship-or-sunset decision by Q1, blended gross margin improvement
   - Resources: 0 hires · $20K

6. **Optimize Subscription Experience**
   - Addresses: Subscription Gap, Retention
   - KRs: flexible subscription cadence, bundle optimization, subscriber NPS
   - Resources: 0 hires · $15K

**Upside only:**

7. **Launch Verdana Metabolize**
   - Addresses: Growth Plateau (new revenue stream)
   - KRs: formulation finalized Q1, launch Q3, 500 units/month by Q4
   - Resources: 1 hire · $120K (R&D + launch)

**Downside only:**

8. **Consolidate to Core Three SKUs**
   - Addresses: Margin Pressure, Resource Constraints
   - KRs: sunset Shield and Endure by Q2, reallocate R&D to top 3, margin improvement
   - Resources: 0 hires · $10K (transition costs)

### Operations (color: orange #fc8621)

**Shared across all scenarios:**

9. **Reduce Fulfillment Cost per Order**
   - Addresses: Margin Pressure, Shipping Costs +15% YoY
   - KRs: shipping cost/order reduction, returns rate improvement, free shipping threshold optimization
   - Resources: 0 hires · $30K

**Upside only:**

10. **Build Wholesale Operations Capability**
    - Addresses: Wholesale Question (operational readiness)
    - KRs: EDI integration live, retail compliance certified, wholesale fulfillment process documented
    - Resources: 2 hires · $150K

**Shared Base and Upside:**

11. **Improve Supply Chain Resilience**
    - Addresses: KSM-66 cost increase (22%), ingredient sourcing risk
    - KRs: secondary supplier for top 3 ingredients, 90-day inventory buffer, COGS reduction
    - Resources: 0 hires · $20K

### Finance (color: blue #38bdf8)

**Shared across all scenarios:**

12. **Maintain Healthy Cash Position**
    - Addresses: Growth Plateau, Strategic Uncertainty
    - KRs: 12+ months cash runway, monthly P&L variance < 5%, scenario reporting cadence
    - Resources: 0 hires · $10K

**Shared Base and Upside:**

13. **Build Decision-Grade Financial Reporting**
    - Addresses: Strategic Planning needs
    - KRs: monthly scenario dashboard, trigger point monitoring, board reporting package
    - Resources: 1 hire (analyst) · $60K

**Downside only:**

14. **Execute Cost Reduction Program**
    - Addresses: Margin Protection, Cash Preservation
    - KRs: 15% opex reduction, renegotiate top 5 vendor contracts, zero non-essential spend
    - Resources: 0 hires · $5K

## UI Architecture

### Layout

- **Sidebar (fixed, 280px):** Scenario switcher, strategic context block, trigger points, live resource summary (headcount delta, budget delta, objective count, KR count)
- **Main area (fluid):** Function filter pill bar at top, card grid below (2 columns, responsive)

### Objective Cards

Each card shows:
- Function label (color-coded) + resource tag (hires + budget)
- Objective title
- "Addresses:" line linking to Verdana's strategic challenges
- Key results as bullet list (metric, from → to, timeline)
- Subtle on/off toggle in top-right corner

Click to expand inline: shows full KR detail with owner, timeline, and strategic challenge description.

### Interactions

1. **Scenario switcher** — Click sidebar buttons. Cards animate: shared objectives cross-fade with updated KR targets, scenario-specific cards slide in/out. Sidebar context, triggers, and resource summary update.

2. **Function filter** — Color-coded pills toggle card visibility. Multiple can be active. "All" resets.

3. **Objective toggle** — On/off switch per card. Disabled cards gray out. Resource summary recalculates in real-time.

4. **Card expand** — Click to expand inline with full detail. Click again to collapse.

### Branding

- Verdana wordmark in sidebar header (bold, primary green, lowercase)
- "FY2027 OKR Planning" subtitle beneath wordmark
- Brand presence is subtle — wordmark + context, not logo-heavy

### Visual Design

- **Wellness light theme** — designed to feel on-brand for a clinical wellness company
- Page background: #f8faf7 (warm off-white)
- Sidebar background: #eef4ec (soft sage)
- Cards: white (#fff) with subtle box-shadows
- Primary brand color: #2d6a4f (deep forest green)
- Secondary: #74a98c (muted sage)
- Function colors (earthy, muted):
  - Marketing: #2d6a4f (brand green)
  - Product: #6b4c9a (muted purple)
  - Operations: #c17817 (warm amber)
  - Finance: #2e7d9e (teal blue)
- CSS transitions for all state changes (300ms ease)
- Clean typography, generous spacing

## Data Model

```javascript
const DATA = {
  company: { name, revenue, employees, challenges[] },
  scenarios: {
    base: {
      id, name, revenue_target, posture, context_summary,
      triggers: [{ condition, direction, target_scenario }],
      objectives: [{
        id, function, title, addresses[],
        resources: { hires, budget, owner },
        key_results: [{ metric, from, to, timeline }],
        shared: boolean  // appears in multiple scenarios
      }]
    },
    upside: { ... },
    downside: { ... }
  }
};
```

## Technical Approach

- **Single self-contained HTML file** — no external dependencies, no build step
- All CSS and JavaScript embedded in the file
- OKR data as a JavaScript object at the top of the file for easy editing
- Rendering via DOM manipulation (no framework)
- CSS transitions for card animations
- All state in-memory (no persistence needed)
- Output path: `tools/okr_goal_setting.html`

## Out of Scope

- Data persistence / saving customizations
- Export to PDF or spreadsheet
- Editable OKR content through the UI (edit the JS data object directly)
- Full P&L financial model (complements, doesn't replace)
- User authentication or multi-user collaboration
