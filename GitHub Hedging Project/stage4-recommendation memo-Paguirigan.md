# FX Hedge Analysis — Executive Memo
**EUR/USD Receivable | U.S. Pharmaceutical Exporter**

**Prepared by:** Zhymmore Paguirigan
**Date:** 2026-03-29
**Course:** FIN 321 – Chapter 8, Stage 4
**Audience:** CFO / Director of Treasury

---

## A. Exposure Summary

A U.S.-based pharmaceutical exporter holds a confirmed **EUR 7,272,727 receivable** from a European pharma client, expected to settle on **March 29, 2027** — exactly twelve months from the model inception date. At the prevailing spot rate of **1.1508 USD/EUR**, the anticipated USD value of this receivable is approximately **$8.37 million**, which aligns with the firm's internal USD cash flow target of ~$8M.

The exposure is structurally **long EUR / short USD**: the company has already completed delivery and is owed euros, but its reporting currency is dollars. Every 1% depreciation in EUR/USD reduces USD-equivalent proceeds by approximately **$83,700** — a material impact relative to budget. In a volatile macro environment (Fed rate trajectory, ECB divergence, geopolitical uncertainty), a EUR/USD swing of ±3–5% is well within historical annual ranges, and leaving this exposure unhedged could result in a miss of $250,000–$420,000 against the firm's USD revenue target.

The hedging decision is therefore both a risk management and a financial planning issue — the CFO requires a defensible, quantified strategy to lock in USD cash flows, preserve optionality where warranted, and communicate certainty to the board.

---

## B. Summary of Hedge Outcomes

The table below presents locked-in or floor USD proceeds for each strategy, derived directly from the Stage 2 model. The baseline spot at maturity is assumed equal to today's spot (S₀ = 1.1508).

| Strategy | USD Proceeds | Nature of Outcome |
|---|---|---|
| **No Hedge** | $8,369,454 at baseline S_T = S₀ | Fully variable; tracks EUR/USD linearly |
| **Forward Hedge** | **$7,920,000** (locked in) | Certain; zero cost; zero upside |
| **Money Market Hedge** | **$8,500,547** (locked in) | Certain; balance sheet intensive |
| **Put Option (ATM)** | Floor: **$8,211,000**; upside unlimited | Flexible; premium cost $158,455 (FV) |
| **Collar (Net-Credit)** | Floor: **$8,407,182**; cap: **$8,546,818** | Bounded upside; **net premium income** |

**Forward Hedge:** Sells EUR 7,272,727 forward at F₀ = 1.0890, locking in $7,920,000 with absolute certainty. No premium is paid and no upside exists. Notably, the forward rate ($1.0890) is significantly below the current spot ($1.1508), reflecting a wide IRP deviation (documented below), which makes this the *lowest-certainty outcome* of all hedging strategies.

**Money Market Hedge:** The exporter borrows the present value of the EUR receivable (EUR 7,119,654) today, converts to USD at spot, and invests in USD for one year — locking in $8,500,547. This is $580,547 above the forward hedge, a deviation attributable to the documented gap between the given forward rate (1.0890) and the IRP-implied rate (≈1.1688). While this strategy produces the highest locked-in outcome, it requires EUR borrowing capacity and introduces balance sheet complexity.

**Put Option (ATM):** Purchasing a EUR put at K_PUT = 1.1508 guarantees minimum proceeds of $8,211,000 after the future value of the $0.021/EUR premium ($158,455). If EUR appreciates above 1.1508, the put expires worthless and the firm captures full upside net of the sunk premium cost — retaining flexibility at a defined cost.

**Collar (Net-Credit):** Buying the 1.1508 put and simultaneously selling a 1.1700 call generates **net premium income** of $0.005/EUR ($36,364 gross; $37,727 FV), since the call premium ($0.026) exceeds the put premium ($0.021). This income *raises* the floor above the put-only floor to $8,407,182 and caps upside at $8,546,818. The collar is the only strategy that costs the firm nothing out-of-pocket — it is self-financing.

---

## C. Sensitivity Interpretation

The sensitivity table spans S_T from **1.09326** (−5% vs. S₀) to **1.20834** (+5% vs. S₀) in 1% increments — eleven scenarios total.

**EUR Depreciation Scenarios (S_T < 1.1508):**
In all five depreciation scenarios, the unhedged position is the *worst* performer, falling as low as $7,950,982 at S_T = 1.09326 — roughly $419,000 below baseline. All four hedging strategies outperform the no-hedge position in every depreciation scenario. The Money Market Hedge is the top performer in all depreciation cases, locking in $8,500,547 regardless of EUR movement. The Collar Floor ($8,407,182) provides the second-best outcome, meaningfully better than the Put Floor ($8,211,000) and far better than the Forward ($7,920,000). In adverse EUR scenarios, the Collar's net-credit structure gives it a $196,000 advantage over the put-only hedge at the floor.

**EUR Appreciation Scenarios (S_T > 1.1508):**
At mild appreciation (S_T = 1.162308), the Money Market Hedge still dominates. At S_T = 1.173816, the Collar is the best hedged outcome ($8,546,818 cap). Beyond S_T = 1.185324, the unhedged position produces the highest nominal proceeds — but this ignores the fundamental purpose of hedging: budget protection, not speculation. The Put Option retains unlimited upside beyond its premium cost, outperforming the Collar's cap in strong EUR appreciation scenarios.

**Key Crossover Insight:**
The Forward Hedge is the clear underperformer in every scenario — locked in at $7,920,000 while all other strategies (including no hedge at baseline) produce higher outcomes. This is a direct consequence of the IRP deviation in the given forward rate data. If the IRP-implied forward of 1.1688 were used, the Forward and Money Market outcomes would converge to approximately $8,496,000, and the forward would become a competitive choice.

---

## D. Strategic Recommendation

**Recommended Strategy: Net-Credit Collar**
*(Buy EUR Put at K_PUT = 1.1508 + Sell EUR Call at K_CALL = 1.1700)*

The collar is the most appropriate hedge for this exposure given the firm's priorities of cash flow certainty, budget protection, and cost minimization. Supporting rationale:

1. **Highest floor of any option-based hedge** — $8,407,182 guaranteed minimum, $196,000 above the put-only floor, providing meaningful downside protection in EUR depreciation scenarios.
2. **Zero net premium cost** — The collar is self-financing. With PREM_CALL ($0.026) exceeding PREM_PUT ($0.021) by $0.005/EUR, the firm receives net income of $37,727 (FV), making this the only strategy with a *negative* cost of protection.
3. **Meaningful upside preserved** — Proceeds can reach $8,546,818 if EUR appreciates past 1.1700, providing $177,000 of upside participation above baseline.
4. **Outperforms the forward in every scenario** — The collar's floor ($8.41M) is $487,000 above the forward's locked-in rate ($7.92M), which is an anomalous outcome driven by the IRP deviation in the given data.
5. **Competitive with the Money Market Hedge** — The MM Hedge produces $8.50M locked in, approximately $93,000 more than the collar floor. However, the MM Hedge requires EUR borrowing capacity and has balance sheet implications (new EUR liability, liquidity use) that may not be desirable for treasury. The collar achieves a comparable risk profile with no balance sheet impact.

**Secondary Alternative:** If the firm has EUR borrowing capacity and the CFO prioritizes absolute certainty over flexibility, the **Money Market Hedge** at $8,500,547 is the highest locked-in outcome and is worth serious consideration — with the caveat that the IRP deviation driving this result should be reconciled with the bank's actual forward quotation before execution.

---

## E. Executive Justification

**Cash Flow Stability:** The collar guarantees a minimum of **$8,407,182** in USD proceeds — $407,182 above the firm's USD target of ~$8M. This buffer provides the CFO with confidence that even in a worst-case EUR depreciation scenario (−5%), the USD cash flow target is met and exceeded.

**Budget Certainty:** The floor-and-cap structure aligns perfectly with budget planning. The treasury team can communicate to the board a USD receivable range of $8.41M–$8.55M, a tight band relative to the $8.37M baseline, supporting accurate revenue forecasting and investor guidance.

**Liquidity Impact:** Unlike the money market hedge, the collar requires no upfront borrowing and does not tie up EUR credit lines. The net premium *income* of $37,727 is a small but positive cash inflow — this hedge pays the firm to implement it.

**Optionality Value:** The collar preserves $139,000 of upside above baseline ($8.55M cap vs. $8.41M floor), compared to the forward hedge, which forfeits all upside at a much lower locked-in rate. If the EUR strengthens to 1.17 or beyond, the firm still benefits — the call is simply a cap, not a loss.

**Premium Costs:** The collar generates net income. There is no out-of-pocket cost to implement this hedge. In contrast, the put-only strategy costs $158,455 in FV premium, which directly reduces net USD proceeds below all collar outcomes.

**Accounting Implications (Optional):** Under ASC 815, the collar qualifies for hedge accounting designation as a cash flow hedge of a foreign currency receivable, with changes in fair value deferred in Other Comprehensive Income (OCI) until settlement. The net-credit collar's income character may simplify premium amortization schedules. Formal designation, contemporaneous documentation, and quarterly effectiveness testing are required for hedge accounting treatment.

---

## F. Structured AI Prompt

---

### APPENDIX — Structured AI Prompt for FX Hedge Spreadsheet Reconstruction

---

# GOAL

Reconstruct a complete, professional Excel workbook modeling four FX hedging alternatives for a EUR-denominated receivable held by a U.S. pharmaceutical exporter. The model must be fully formula-driven, color-coded, and produce a sensitivity table and recommendation summary. Use the exact variable names and values defined in `# INPUT VARIABLES` below. Do not infer, estimate, or substitute any values.

---

# INPUT VARIABLES

Use the following named ranges and values exactly as specified. All values are drawn from confirmed market data as of 2026-03-29.

| Named Range   | Value       | Unit        | Description                                         |
|---------------|-------------|-------------|-----------------------------------------------------|
| `FC_AMT`      | 7272727     | EUR         | EUR receivable from European pharma client          |
| `S0_in`       | 1.1508      | USD per EUR | EUR/USD spot rate at inception (FT Markets)         |
| `F0_in`       | 1.0890      | USD per EUR | EUR/USD 1-year forward rate (FT Markets)            |
| `R_USD`       | 0.0375      | Annual      | USD 1-year interest rate (Federal Reserve H.15)     |
| `R_FC`        | 0.0215      | Annual      | EUR 1-year interest rate (ECB main refi rate)       |
| `T_DAYS`      | 365         | Days        | Days to settlement; derive T = T_DAYS / 365 = 1.0  |
| `K_PUT`       | 1.1508      | USD per EUR | EUR put option strike (at-the-money, K = S0_in)    |
| `PREM_PUT`    | 0.021       | USD per EUR | Put option premium per unit of EUR                  |
| `K_CALL`      | 1.1700      | USD per EUR | EUR call option strike (collar upper bound)         |
| `PREM_CALL`   | 0.026       | USD per EUR | Call option premium per unit of EUR                 |

All interest rates are simple annual rates. Day-count convention: Act/365. Time fraction: T = T_DAYS / 365 — always compute as a formula, never hardcode 1.0.

---

# SPREADSHEET REQUIREMENTS

## Layout & Color Coding

Apply the following background colors consistently across all cells:

- **Yellow** (`#FFFF00`) — All input cells containing named range values (editable by user)
- **Blue** (`#ADD8E6`) — Assumption cells (interest rates, day-count convention, IRP note)
- **Green** (`#90EE90`) — All formula/intermediate calculation cells
- **Gray** (`#D3D3D3`) — Final output/summary KPI cells

Use bold Arial 10pt for section headers. Freeze the top row. Apply number formatting: USD values as `$#,##0.00`; rates as `0.0000`; days as integers.

## Sheet Structure

Create two sheets: `Receivable Hedge` (main model) and `Notes & Assumptions`.

---

# MODEL LOGIC

## Section 1 — Inputs

Create a clearly labeled input block with one named range per row. Label each row with the variable description and named range in brackets (e.g., "EUR/USD Spot Rate [S0_in]"). All cells in this section are Yellow. Derive `T = T_DAYS / 365` as a formula in a Blue assumption cell immediately below the inputs.

## Section 2 — Forward Hedge

Compute locked-in USD proceeds:

```
USD_forward = FC_AMT × F0_in
```

Label the result as `USD_forward`. Output cell is Gray. Add a text note: "Zero premium cost. Zero upside participation. Certainty is absolute."

## Section 3 — Money Market Hedge (3-Step)

```
Step [a]: EUR_borrow = FC_AMT / (1 + R_FC × T)         → PV of EUR receivable
Step [b]: USD_today  = EUR_borrow × S0_in               → Convert EUR to USD at spot
Step [c]: USD_mm     = USD_today × (1 + R_USD × T)      → Invest USD to maturity
Parity_Check = USD_mm − USD_forward                      → Expect ≈ $0 if IRP holds
```

Label `USD_mm` and `Parity_Check` as Gray outputs. Add a note that the non-zero parity check reflects the IRP deviation between F0_in = 1.0890 and the IRP-implied rate ≈ S0_in × (1 + R_USD) / (1 + R_FC) ≈ 1.1688.

## Section 4 — Put Option Hedge

```
PREM_PUT_total = FC_AMT × PREM_PUT
PREM_PUT_FV    = PREM_PUT_total × (1 + R_USD × T)
USD_put_floor  = FC_AMT × K_PUT − PREM_PUT_FV
```

Label `USD_put_floor` as Gray. Add a note: "If S_T > K_PUT, put expires worthless; net proceeds = S_T × FC_AMT − PREM_PUT_FV (full upside retained, net of premium)."

## Section 5 — Collar Hedge (Net-Credit: Buy Put + Sell Call)

```
PUT_paid        = FC_AMT × PREM_PUT
CALL_received   = FC_AMT × PREM_CALL
NET_PREM        = PUT_paid − CALL_received             → Negative = net income when PREM_CALL > PREM_PUT
NET_PREM_FV     = NET_PREM × (1 + R_USD × T)
USD_collar_floor = FC_AMT × K_PUT − NET_PREM_FV
USD_collar_cap   = FC_AMT × K_CALL − NET_PREM_FV
```

Label `USD_collar_floor` and `USD_collar_cap` as Gray outputs. Add a note: "PREM_CALL > PREM_PUT here, so NET_PREM is negative (net income). This income raises both floor and cap vs. put-only hedge. If K_PUT ≤ S_T ≤ K_CALL, proceeds = S_T × FC_AMT − NET_PREM_FV."

## Section 6 — Sensitivity Analysis Table

Vary S_T from `0.95 × S0_in` to `1.05 × S0_in` in increments of `0.01 × S0_in` — 11 rows total. For each S_T, compute USD proceeds under five strategies:

```
No Hedge:  S_T × FC_AMT
Forward:   USD_forward (constant)
MM Hedge:  USD_mm (constant)
Put Only:  MAX(USD_put_floor, S_T × FC_AMT − PREM_PUT_FV)
Collar:    MIN(USD_collar_cap, MAX(USD_collar_floor, S_T × FC_AMT − NET_PREM_FV))
```

Add a "Best Strategy" column using a formula-driven MAX + INDEX/MATCH approach to identify the highest-yielding strategy at each S_T. Highlight the baseline row (S_T = S0_in) in light yellow. Add column headers and a row note distinguishing depreciation rows (above baseline) from appreciation rows (below baseline).

## Section 7 — Summary Output

Create a Gray summary block listing:
1. Forward Hedge USD Proceeds (linked from Section 2)
2. Money Market Hedge USD Proceeds (linked from Section 3)
3. Put Option Floor (linked from Section 4)
4. Collar Floor and Cap (linked from Section 5)
5. Hedge Recommendation: "Net-Credit Collar — Self-financing; highest option-based floor; bounded upside."

---

# VERIFICATION

Include the following checks, clearly labeled:

1. **IRP Parity Check:** `Parity_Check = USD_mm − USD_forward`. Document that non-zero result reflects IRP deviation; show IRP-implied forward = `S0_in × (1 + R_USD) / (1 + R_FC)` for reference.
2. **Collar Income Verification:** Confirm `PREM_CALL > PREM_PUT` → collar generates net income; flag with a note if PREM_PUT > PREM_CALL (cost collar).
3. **Floor/Cap Ordering:** Confirm `USD_collar_floor < USD_collar_cap` via formula check.
4. **Sensitivity Range Verification:** Confirm 11 rows spanning exactly ±5% of S0_in.

---

# EXPORT

- Save as `.xlsx` with sheet tab names: `Receivable Hedge` and `Notes & Assumptions`
- Apply print area to cover Sections 1–7 on one landscape page (scale to fit)
- Freeze top row and first column
- Add a header row: "FX Hedge Model — EUR/USD Receivable | Zhymmore Paguirigan | FIN 321"
- Named ranges must be registered in Excel's Name Manager matching the names defined in `# INPUT VARIABLES`

---

---

## Extra Credit — Areas for Further Study & Improvement

### 1. AI Skills & Automation

AI tools like Claude Code or code interpreter environments could transform this static, one-time model into a continuously updated analytical engine. Currently, the Stage 2 spreadsheet requires manual input updates whenever market rates change — a new spot rate, forward rate, or option premium means reopening the file and editing yellow cells by hand. An AI-powered version could instead connect to live FX data APIs (e.g., Bloomberg, Refinitiv, or open sources like the ECB's SDMX feed) and pull `S0_in`, `F0_in`, `R_USD`, and `R_FC` automatically at model open. Beyond data ingestion, Claude could be prompted to re-run the sensitivity table on demand across any spot range — not just ±5%, but ±10%, ±15%, or even Monte Carlo simulations drawing S_T from a lognormal distribution calibrated to EUR/USD implied volatility. The result would be a probability-weighted expected outcome for each hedge strategy, enabling the CFO to make decisions based on distributional outcomes rather than point estimates. A fully automated pipeline could generate a fresh hedge recommendation memo every morning using this same Stage 4 prompt structure — pulling live data, re-running the model, and delivering a revised recommendation to the CFO's inbox before the trading day opens. This eliminates the manual rebuild cycle entirely and transforms the prompt written in Section F into the firm's standing analytical infrastructure.

### 2. Multi-File Reasoning & GitHub as an Audit Trail

This project produced three interdependent files: the Stage 3 specification (`.md`), the Stage 2 model (`.xlsx`), and the Stage 4 prompt and memo (`.md`). In a production environment, inconsistencies between these files — a named range defined as `R_EUR` in the spec but implemented as `R_FC` in the model, for example — create audit risk and model error. AI tools capable of multi-file reasoning (reading all three documents simultaneously) could automatically cross-reference every named range, formula description, and output value, flagging discrepancies before they propagate. More powerfully, an AI agent could use the Stage 3 spec as a source of truth and the Stage 4 prompt as the rebuild instruction — automatically regenerating the Stage 2 spreadsheet from scratch whenever the spec is updated, ensuring the model always reflects the latest analytical decisions. Committing all three files to GitHub with meaningful commit messages creates a fully auditable version history: every change to an assumption (e.g., updating `PREM_PUT` from 0.021 to a market-quoted value) is timestamped, attributed, and reversible. For corporate treasury teams subject to SOX internal controls or hedge effectiveness documentation requirements under ASC 815, this version-controlled artifact chain constitutes a defensible audit trail — the model can be traced back to its source assumptions at any point in time, and the AI prompt serves as the human-readable instruction set that any analyst could use to reproduce the model independently.

### 3. Accounting & Audit Integration

The collar hedge recommended in this analysis qualifies for hedge accounting designation under ASC 815 (formerly FAS 133) as a cash flow hedge of a foreign currency receivable. Proper designation requires contemporaneous documentation at hedge inception, formal designation of the hedged item (the EUR 7,272,727 receivable) and the hedging instrument (the collar), and a prospective effectiveness assessment confirming the hedge is expected to be highly effective (80–125% offset ratio). The GitHub repository built across Stages 1–4 supports all of these requirements: the Stage 1 memo documents the business rationale and risk management objective, the Stage 3 spec documents the analytical methodology and named range conventions, and the Stage 2 model provides the quantitative effectiveness evidence. Under the simplified dollar-offset method, the collar's payoff exactly mirrors the receivable's FX exposure within the floor-to-cap band, establishing high effectiveness by design. Quarterly effectiveness testing results could be logged as new commits to the GitHub repository — each quarter's test producing a new version of the Stage 2 model with updated fair values — creating a time-stamped record that satisfies both internal audit and external auditor documentation requirements. The net-credit income from the collar ($37,727 FV) would initially be deferred in Other Comprehensive Income (OCI) and reclassified to revenue when the receivable settles, consistent with the hedged item's income recognition pattern. GitHub's version control infrastructure turns what is typically a scattered collection of PDFs and emails into a structured, searchable, reproducible documentation system — exactly the kind of auditable model governance that Big 4 firms and corporate controllers expect in regulated treasury environments.

---

*End of Stage 4 Deliverable — Zhymmore Paguirigan | FIN 321 | 2026-03-29*
