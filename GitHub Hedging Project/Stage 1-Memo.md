# EUR/USD FX Receivables Hedging Strategy - U.S. Pharmaceutical Exporter

**Created by:** Zhymmore Paguirigan  
**Updated by:** Zhymmore Paguirigan  
**Date Created:** 2026-03-29  
**Date Updated:** 2026-03-29  
**Version:** 1.0  
**LLM Used:** Claude (Anthropic)

---

## Executive Summary

Our pharmaceutical division is exposed to a €7,272,727 receivable due in one year from a major European client, representing approximately $8.35 million in current USD proceeds. EUR/USD volatility, currently trading at 1.1508, poses material downside risk to our cash forecasts and profit margins. A 5% depreciation would reduce proceeds by $418,000. This memo outlines three hedging families (forward contracts, put options, call options) and recommends advancing through Stages 2-4 to build a working model, document specifications, and deliver a data-driven recommendation to the CFO.

---

## Background & Objectives

### The Exposure

We have committed to receive €7,272,727 (approximately $8.35M USD at today's spot rate of 1.1508) from a European pharmaceutical client in exactly one year. This receivable is contractually fixed and material to our 2027 revenue guidance.

### Why It Matters

Exchange rate movements directly impact our reported earnings and operating cash flow. EUR has shown elevated volatility in recent months, with trading ranges exceeding +/- 4% annually. A depreciation to 1.08 (3% move) would eliminate $245,000 in expected proceeds. A sharper move to 1.05 (8.6% depreciation) would cost us $918,000, unacceptable given our current margin profile.

### Primary Objectives

1. **Protect downside:** Lock in a minimum USD floor to ensure cash flow sufficiency for our debt covenants and shareholder commitments.
2. **Optimize cost:** Balance hedge protection against premium/funding costs and opportunity costs if EUR appreciates.
3. **Maintain flexibility:** Preserve upside participation if EUR strengthens, or minimize sunk costs if business conditions change.

---

## Methods

### Three Hedging Families

#### **1. Forward Contract Hedge**
- **Mechanics:** Lock in an exchange rate (Forward = 1.0890) today; exchange EUR for USD at maturity at that fixed rate.
- **Upside:** No upfront premium; full downside protection; operationally simple.
- **Downside:** Zero upside participation if EUR appreciates; inflexible commitment; counterparty credit risk.
- **Pros/Cons Summary:** Ideal for firms that want certainty and can absorb the opportunity cost; most cost-efficient protection.

#### **2. Put Option (EUR Put, USD Call)**
- **Mechanics:** Buy the right (not obligation) to sell EUR at strike K = 1.1508, premium = $0.021 per EUR.
- **Upside:** Downside protection + participation in EUR strength beyond the strike.
- **Downside:** Upfront premium cost (~$151,727 for 7.27M EUR); lower effective floor due to option cost.
- **Pros/Cons Summary:** Preserves optionality; appealing if EUR likely to strengthen; higher cost but highest flexibility.

#### **3. Collar / Participation Structure**
- **Mechanics:** Buy a EUR put (strike = 1.1508, premium $0.021) and sell a EUR call (strike approximately 1.17, premium $0.026).
- **Upside:** Near-zero net premium if premiums offset; retains limited upside up to call strike; lower cost hedge.
- **Downside:** Caps upside participation above call strike; requires finding acceptable strike pair.
- **Pros/Cons Summary:** Cost-neutral or negative cost; best for firms neutral to slightly bullish on EUR; moderate complexity.

---

## Limitations & Next Steps

### Known Constraints
- Forward rate of 1.0890 may not reflect true market consensus; we will validate against Bloomberg/ECB data before Stage 2.
- Option premiums provided (0.021-0.026) are illustrative; actual quotes depend on volatility, credit, and institutional relationships.
- This memo assumes the full receivable is hedged; a partial hedge analysis will be explored in Stage 2.

### Project Timeline: Stages 2-4

#### **Stage 2: Excel Model Build (Responsible: Treasury FX Analyst)**
1. Validate market parameters (spot, forwards, interest rates) as of Stage 2 start date using Bloomberg/ECB data.
2. Build a comparative Excel prototype (`.xlsx`) that computes outcomes for all three hedge strategies across multiple FX scenarios.
3. Create sensitivity tables showing:
   - Unhedged proceeds at rates: 1.00, 1.05, 1.10, 1.15, 1.20 EURUSD.
   - Hedged proceeds for forward, put, and collar strategies under identical scenarios.
   - Net cost (premium, funding, or income) for each hedge.
   - Effective floor and upside cap for each strategy.
4. Identify break-even analysis: at what exchange rate does each hedging strategy outperform others?
5. Model extensions: partial hedge ratios (50%, 75%, 100%), delayed payment scenarios, and margin impact analysis.

**Deliverable:** Working `.xlsx` model committed to `docs/templates/excel/`.

#### **Stage 3: Technical Specification (Responsible: FX Analyst with Documentation Lead)**
1. Document the Stage 2 model with complete technical specifications including:
   - Input parameters (spot, strike, forward, interest rates, premium, notional).
   - Formulas and calculations for each hedge payoff.
   - Assumptions and limitations clearly stated.
   - User guide for modifying scenarios or hedge ratios.
2. Design an improved version of the model with enhanced features:
   - Separate input sheet from calculation sheets for easier maintenance.
   - Data validation and error checking.
   - Dynamic charts and scenario dashboards.
   - Integration with real-time Bloomberg/ECB data feeds (if feasible).
3. Write the spec with enough precision and detail that an AI system or junior analyst could reconstruct the improved model from scratch.

**Deliverable:** Technical specification Markdown file (`.md`) committed to `docs/` or repository root.

#### **Stage 4: Final Analysis, Prompt Engineering & Recommendation (Responsible: Treasury Manager with CFO liaison)**
1. Analyze Stage 2 model results:
   - Compare all three hedge strategies under base case, bullish EUR, and bearish EUR scenarios.
   - Quantify the cost/benefit trade-off of each approach.
   - Assess alignment with firm's risk tolerance, debt covenants, and strategic objectives.
2. Select recommended hedge strategy based on:
   - Downside protection requirements.
   - Expected EUR volatility and market outlook.
   - Cost-benefit alignment with corporate financial targets.
   - Operational and counterparty considerations.
3. Write a structured AI prompt (using insights from Stage 2 model and Stage 3 spec) that captures the hedging decision framework and can guide future similar analyses.
4. Prepare final executive memo/presentation to CFO that includes:
   - Summary of model findings.
   - Recommended hedge strategy with justification.
   - Implementation roadmap (execution timeline, counterparties, documentation).
   - Risk disclosures and contingency plans.

**Deliverable:** Final analysis Markdown file and CFO-ready presentation committed to repository.

---

## References

- **Spot Rate & Forward:** EURUSD 1.1508 (spot); 1.0890 (1-year forward) as of 2026-03-29; source: FT Markets, Federal Reserve H.15 daily rates.
- **Interest Rates:** USD 1-year rate approximately 3.75% (Federal Reserve target range 3.50-3.75%); EUR 1-year rate approximately 2.15% (ECB main refinancing rate).
- **Scenario Parameters:** U.S. Pharmaceutical Exporter scenario, FIN-321 project materials.
- **Option Premiums:** Stage 1 scenario inputs (put premium $0.021, call premium $0.026 per EUR, no multiplier).
- **References:**
  - Hull, J. C. (2021). Options, Futures, and Other Derivatives (11th ed.). Pearson.
  - Federal Reserve Board. (2026). Selected Interest Rates (Daily) - H.15. https://www.federalreserve.gov/releases/h15/
  - European Central Bank. (2026). Key ECB Interest Rates. https://www.ecb.europa.eu/stats/policy_and_exchange_rates/key_ecb_interest_rates/html/index.en.html
  - Financial Times Markets. FX Cross Rates. https://markets.ft.com/data/currencies/
