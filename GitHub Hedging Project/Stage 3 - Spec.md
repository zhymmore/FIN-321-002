# EUR/USD Receivable Hedge Model – Technical Specification

**Created by:** Zhymmore Paguirigan
**Updated by:** Zhymmore Paguirigan
**Date Created:** 2026-03-29
**Date Updated:** 2026-03-29
**Version:** 1.0
**LLM Used:** None

**Role:** Financial Analyst / Treasury Analyst
**Audience:** CFO or Director of Treasury

**Purpose:** Provide a professional, quantitative specification outlining the analytical structure for evaluating FX hedging alternatives on a EUR-denominated receivable held by a U.S. pharmaceutical exporter.

---

## 1. Problem Statement

A U.S. pharmaceutical exporter expects to receive **€7,272,727** from a European pharma client in **12 months**, creating direct exposure to EUR/USD exchange rate fluctuations. If the euro depreciates against the dollar between now and settlement, the USD-equivalent proceeds will fall below the anticipated target of approximately $8.35M (based on the spot rate at inception of 1.1508). This specification defines the analytical framework used to quantify, compare, and evaluate four hedging alternatives — a forward contract, a money market hedge, a EUR put option, and a zero-cost collar — to protect the USD value of that receivable while documenting trade-offs between certainty, cost, and upside participation for treasury decision-making.

---

## 2. Inputs (Known Variables)

All variables below are drawn directly from the Stage 2 Excel model. Named ranges follow the standardized convention used throughout the model.

| Named Range   | Description                           | Unit        | Value     | Source                                              |
|---------------|---------------------------------------|-------------|-----------|-----------------------------------------------------|
| `FC_AMT`      | EUR receivable from pharma client     | EUR         | 7,272,727 | Company data; derived from ~$8M USD target ÷ S₀    |
| `S0_in`       | EUR/USD spot rate at inception        | USD per EUR | 1.1508    | FT Markets, 2026-03-29                              |
| `F0_in`       | EUR/USD 1-year forward rate           | USD per EUR | 1.0890    | FT Markets, 2026-03-29                              |
| `R_USD`       | USD 1-year interest rate              | Annual %    | 3.75%     | Federal Reserve H.15; mid-range of 3.50–3.75%      |
| `R_EUR`       | EUR 1-year interest rate              | Annual %    | 2.15%     | ECB main refinancing rate                           |
| `T`           | Time to settlement                    | Years       | 1.0       | Derived from receivable terms                       |
| `K_PUT`       | EUR put option strike price           | USD per EUR | 1.1508    | At-the-money (K = S₀); Stage 1 assumption          |
| `PREM_PUT`    | Put premium per unit of EUR           | USD per EUR | 0.021     | Illustrative; Stage 1 scenario                      |
| `K_CALL`      | EUR call option strike price (collar) | USD per EUR | 1.1700    | Stage 1 approximation; to be market-validated       |
| `PREM_CALL`   | Call premium per unit of EUR          | USD per EUR | 0.026     | Illustrative; Stage 1 scenario                      |

---

## 3. Assumptions & Constraints

The following conventions were applied throughout the Stage 2 model. Any future rebuild must respect these assumptions to reproduce the results.

- All interest rates are quoted on a simple annual basis (Act/365 assumed); `T = 1.0` year exactly — no day-count adjustment applied.
- The forward rate `F0_in = 1.0890` is taken as given from the market source. It deviates significantly from the covered interest rate parity (IRP)-implied rate of ≈1.1688 (computed as S₀ × (1 + R_USD) ÷ (1 + R_EUR)). This ~6.8% gap is documented and treated as a known limitation attributable to market risk premium or data-source timing differences.
- Bid-ask spreads and transaction costs are excluded from all calculations.
- Counterparty credit risk on the forward contract is acknowledged but not quantified. ISDA/CSA netting agreements are assumed to apply in practice.
- Option premiums (`PREM_PUT`, `PREM_CALL`) are paid upfront in USD and carried forward to maturity using `R_USD`.
- The full receivable (`FC_AMT`) is hedged; partial hedge analysis is deferred.
- All exchange rates are expressed as USD per EUR (direct quote from a U.S. perspective).
- The put strike is set at-the-money (`K_PUT = S0_in = 1.1508`). The call strike (`K_CALL = 1.1700`) is an approximation pending market validation.
- The sensitivity range is ±5% of `S0_in` in 1% increments (11 scenarios total), per assignment specification.

---

## 4. Calculation Flow

The model executes the following logical sequence for each hedge type. Formulas are described conceptually — not as cell references.

**Forward Hedge**
1. Multiply `FC_AMT` by `F0_in` to compute locked-in USD proceeds.
2. Result is deterministic: USD proceeds are fixed regardless of the spot rate at maturity (`S_T`). No premium is paid; no upside participation exists.

**Money Market Hedge**
1. Compute the present value of the EUR receivable by dividing `FC_AMT` by `(1 + R_EUR)` — this is the EUR borrowing amount today.
2. Convert that EUR amount to USD at `S0_in` (sell EUR spot) to obtain USD proceeds today.
3. Invest those USD proceeds for one year at `R_USD`; the resulting balance at maturity is the locked-in USD outcome.
4. Run a parity check by subtracting the forward hedge proceeds from the money market proceeds. A non-zero result (≈$580,547 in this model) confirms the IRP deviation documented in Section 3.

**Put Option Hedge**
1. Compute total put premium cost: multiply `FC_AMT` by `PREM_PUT`.
2. Carry the premium forward to maturity: multiply by `(1 + R_USD)` to get the future value of the cost.
3. Compute the floor (minimum guaranteed USD proceeds): multiply `FC_AMT` by `K_PUT`, then subtract the future-value premium.
4. For scenarios where `S_T > K_PUT`, the put expires worthless; net proceeds equal `S_T × FC_AMT` minus the future-value premium, preserving full upside.

**Collar Hedge (Buy Put + Sell Call)**
1. Compute put premium paid: `FC_AMT × PREM_PUT`.
2. Compute call premium received: `FC_AMT × PREM_CALL`.
3. Compute net premium: put cost minus call income. Here, `PREM_CALL > PREM_PUT`, so the collar generates net income of $0.005 per EUR (≈$36,364 total).
4. Carry net premium to maturity using `R_USD` (future value ≈ −$37,727, i.e., net income).
5. Compute the floor: `FC_AMT × K_PUT` minus the future-value net premium.
6. Compute the cap: `FC_AMT × K_CALL` minus the future-value net premium.
7. For scenarios where `K_PUT ≤ S_T ≤ K_CALL`, proceeds equal `S_T × FC_AMT` minus the future-value net premium. Net income from the collar boosts all outcomes relative to the put-only hedge.

---

## 5. Outputs

The model produces the following specific results, tables, and charts.

| Output               | Description                                                                              | Format                                             | Purpose                                          |
|----------------------|------------------------------------------------------------------------------------------|----------------------------------------------------|--------------------------------------------------|
| `USD_forward`        | Locked-in USD proceeds under the forward hedge                                           | Scalar: $7,919,999.70                              | Certainty benchmark; no cost, no upside          |
| `USD_mm`             | Locked-in USD proceeds under the money market hedge                                      | Scalar: $8,500,547.00                              | IRP cross-check; deviation documented            |
| `Parity_Check`       | Difference between money market and forward proceeds                                     | Scalar: $580,547.30                                | Flags IRP deviation from given forward rate      |
| `USD_put_floor`      | Minimum guaranteed proceeds under the put hedge (put exercised)                          | Scalar: $8,210,999.69                              | Downside protection floor                        |
| `USD_collar_floor`   | Minimum guaranteed proceeds under the collar (put exercised)                             | Scalar: $8,407,181.50                              | Downside protection with net premium income      |
| `USD_collar_cap`     | Maximum capped proceeds under the collar (call exercised)                                | Scalar: $8,546,817.86                              | Upside cap; premium income offsets cap cost      |
| `Sensitivity Table`  | USD proceeds by strategy across 11 S_T scenarios (S₀ ± 5%, 1% steps)                   | Table: 11 rows × 5 strategies + Best Strategy col | Visual comparison of strategy payoffs            |
| `Best_Strategy`      | Identifies the highest-yielding hedge at each S_T scenario                               | Text per row                                       | Decision support at each exchange rate level     |
| `Chart_1`            | Sensitivity Chart: USD Proceeds by Strategy vs. S_T                                     | Line chart                                         | Executive-ready visual; illustrates crossover points |
| `Summary`            | Hedge recommendation with CFO-level rationale                                            | Narrative                                          | To be completed in Stage 4                       |

---

## 6. Model Review — What Worked & What to Improve

**What was built correctly:**
- All four hedge types (forward, money market, put, collar) are implemented with logically correct formulas and produce internally consistent results.
- The sensitivity table correctly applies payoff conditions for each strategy (floor activation, cap activation, and uncapped participation zones) across all 11 spot scenarios.
- The parity check is explicitly surfaced and documented rather than silently ignored — this is analytically honest and important for auditability.
- The collar correctly computes net premium income (PREM_CALL > PREM_PUT) and applies the future value of that income to both floor and cap, producing higher outcomes than the put-only hedge at all spot levels.
- Color-coding (inputs, assumptions, formulas, outputs) improves readability and reduces audit risk.

**What to improve in a rigorous rebuild:**
- The IRP gap between `F0_in = 1.0890` and the implied rate of ≈1.1688 should be formally reconciled. The model should offer a toggle between the given and IRP-implied forward rate so analysts can run both scenarios.
- `T = 1.0` should be parameterized as `T_DAYS / 365` to support non-annual tenors and improve real-world flexibility.
- Bid-ask spreads should be added as an explicit input (`BID_ASK_SPREAD`) and applied to the spot and forward rates used in each hedge calculation.
- Option premiums are currently illustrative. A Black-Scholes pricing module should be incorporated, taking implied volatility and tenor as inputs to produce market-calibrated premiums.
- The "Best Strategy" column should be formula-driven with a documented tiebreaker rule rather than relying on manual review.

**Naming, layout, and formula improvements:**
- Rename `S0` to `S0_in` consistently across all sections; naming is currently inconsistent across the worksheet.
- Add a dedicated `Inputs` sheet separate from calculation sheets to enforce clean separation of concerns and make the model more auditable.
- Add `T_DAYS` as an explicit input (e.g., 365) and derive `T = T_DAYS / 365` rather than hardcoding `T = 1`.
- Apply Excel named ranges to all key cells so the model is fully navigable without reading cell addresses.

**Additional scenarios worth including:**
- Worst-case stress testing: S_T at −10% and −15% of S₀, beyond the current ±5% range.
- Break-even analysis: the S_T level at which each hedged strategy equals the unhedged outcome.
- Partial hedge scenarios: hedging 50% or 75% of `FC_AMT` with the remainder left unhedged.

---

## 7. Sensitivity Plan

The sensitivity analysis varies the EUR/USD spot rate at maturity (`S_T`) from **0.95 × S₀** to **1.05 × S₀** in increments of **1% of S₀** (i.e., 0.011508 per step), producing 11 scenarios. The baseline row corresponds to `S_T = S₀ = 1.1508` (no change in EUR/USD), representing the case where the exporter's FX view proves exactly correct.

Rows above the baseline represent EUR depreciation — the adverse scenario for a USD-reporting exporter holding EUR receivables. Rows below the baseline represent EUR appreciation — the favorable scenario where unhedged proceeds exceed hedged outcomes.

For each `S_T` scenario, USD proceeds are computed under five strategies: No Hedge, Forward, Money Market, Put Only, and Collar. A "Best Strategy" column identifies the highest-yielding alternative at each rate level.

The sensitivity chart communicates three key insights: (1) the forward and money market hedges produce flat lines reflecting locked-in certainty, (2) the put and collar hedges produce kinked payoff profiles that activate floors below `K_PUT` and caps above `K_CALL`, and (3) the unhedged outcome is a straight diagonal line that outperforms all hedges when EUR appreciates significantly and underperforms when EUR depreciates. The most useful strategy comparisons are put vs. collar (illustrating the value of net premium income) and forward vs. money market (illustrating the IRP parity deviation).

---

## 8. Limitations & Next Steps

This specification and the underlying Stage 2 model exclude the following:

- **Implied volatility:** Option premiums are illustrative and do not reflect Black-Scholes or market-quoted pricing based on the current EUR/USD vol surface.
- **Dynamic hedging:** The model assumes a static, single-instrument hedge held to maturity. Delta-hedging or rolling strategies are not considered.
- **Credit and counterparty risk:** The forward contract exposes the firm to counterparty default risk. No CVA (Credit Valuation Adjustment) is applied.
- **Accounting treatment:** FAS 133 / ASC 815 hedge accounting designation, effectiveness testing, and P&L impact are not addressed.
- **Transaction costs:** Bid-ask spreads, dealer margins, and brokerage fees are excluded from all scenarios.
- **Tail risk:** The sensitivity range is capped at ±5%. Stress scenarios beyond this range (e.g., EUR/USD −15%) are not modeled.

**Next Steps — Stage 4:** This specification will serve as the primary input to the Stage 4 AI prompt. The named ranges, calculation flow, output definitions, and improvement notes defined here will instruct the AI to reconstruct an enhanced version of the model — incorporating the fixes identified in Section 6 — and produce a final hedge recommendation supported by full quantitative analysis and executive-ready output.
