---
title: "Tutorial 06: Market Sizing Calculator"
version: 1.0
created: 2026-04-06
---

# Tutorial 06: Market Sizing Calculator

## What This Tool Does

The Market Sizing Calculator models Verdana's addressable market across three channels: DTC supplements (current business), wholesale retail (Whole Foods/Target), and new product expansion (Metabolize/Glow). Users adjust assumptions via sliders and see Year 1 revenue projections update in real-time. A TAM/SAM/SOM funnel provides market context alongside the bottom-up model.

## The Prompt Used

> Build the Verdana Market Sizing Calculator as a single self-contained interactive HTML file.
> Read the full design spec at: `docs/superpowers/specs/2026-04-06-market-sizing-calculator-design.md`
> Also read the brand definition for Verdana's data: `brand/brand_definition.md`
> Create `tools/market_sizing_calculator.html` with the complete implementation.

## Key Decisions and Rationale

1. **Subscriber accumulation model for DTC**: Rather than a simple multiplier, the DTC channel models 12 months of subscriber accumulation with monthly churn derived from the 90-day retention rate. This gives a more realistic projection that accounts for compounding subscription growth.

2. **Cross-channel cannibalization**: Wholesale cannibalization subtracts a percentage of wholesale revenue from DTC. New product cannibalization similarly reduces existing SKU revenue. Both effects are displayed as notices in the affected channel sections.

3. **Linear ramp for wholesale**: Wholesale revenue ramps linearly over the configured ramp months, then runs at full velocity for the remainder of Year 1. This models the realistic store rollout timeline.

4. **SKU pill selection for wholesale**: Clickable pill buttons let users select which products are offered in wholesale, which dynamically updates the average retail price and COGS calculations.

5. **Progressive disclosure**: Advanced inputs are hidden by default behind expandable sections, keeping the primary interface clean while making detailed assumptions accessible.

6. **Wellness theme consistency**: Matches the visual language of the OKR tool and other planning tools — #f8faf7 background, #2d6a4f header, channel-specific accent colors for borders and slider thumbs.

## How to Replicate From Scratch

### Step 1: Read the Spec and Brand Data
Read the design spec to understand all three channels, their inputs, defaults, and calculation logic. Read the brand definition for Verdana's actual business data (product prices, COGS, monthly units, customer metrics).

### Step 2: Build the HTML Structure
Create the sticky header with three KPIs, the TAM funnel bar, and three channel card sections. Each channel card has a header with title and live outputs, primary sliders, an advanced toggle, and a reset button.

### Step 3: Implement Slider and Toggle Controls
Use `<input type="range">` for sliders and styled checkbox switches for toggles. Bind `input` events (not `change`) for real-time updates. Display current values next to each slider.

### Step 4: Write Pure Calculation Functions
Create separate functions for each channel that take inputs and return revenue/margin/profit objects. Keep calculation logic separate from DOM manipulation.

### Step 5: Add Cross-Channel Effects
After computing individual channel results, apply wholesale cannibalization (reduces DTC) and new product cannibalization (reduces existing SKU revenue). Show notices when these effects are active.

### Step 6: Wire Everything Together
The main `recalculate()` function gathers all inputs, runs all three channel calculations, applies cross-channel effects, and updates all DOM elements including the header KPIs and funnel SOM.

## Final Output

`tools/market_sizing_calculator.html` — a single self-contained HTML file that opens in any browser with no dependencies.
