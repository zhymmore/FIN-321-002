# FX Hedging Strategy: EUR Receivables Exposure – U.S. Pharmaceutical Exporter

**Created by:** [Zhymmore Paguirigan]  
**Updated by:** [Zhymmore Paguirigan]  
**Date Created:** 2026-03-29  
**Date Updated:** 2026-03-29  
**Version:** 1.0  
**LLM Used:** GitHub Copilot

---

## Executive Summary (≤150 words)

Our pharmaceutical division has contracted to receive €7.3 million in one year, currently valued at approximately $8 million. This EUR receivable exposes the company to foreign exchange risk: if the euro weakens against the dollar, our actual USD proceeds decline, threatening revenue targets and earnings guidance. This memo evaluates three hedging strategies—forward contracts, protective puts, and collars—to mitigate downside risk while balancing cost and upside participation. Preliminary analysis of forward rates (1.0890 USD/EUR) and option premiums suggests feasible risk mitigation without excessive cost. We recommend proceeding to Stage 2 to build a quantitative model comparing payoff profiles and net USD proceeds across currency scenarios, enabling an evidence-based hedge recommendation to the CFO.

---

## Background & Objectives

**The Problem:** Our pharmaceutical division has secured a significant distribution contract generating a €7.3 million payment due in 12 months. At today's prevailing spot rate (approximately 1.08 USD/EUR), this represents ~$7.88 million in projected USD cash inflows. However, exchange rate volatility creates material risk. A 5% EUR depreciation (to 1.026 USD/EUR) reduces proceeds to $7.49 million; a 10% decline (to 0.972 USD/EUR) yields only $7.10 million—a $780K shortfall (9.9% loss). This uncertainty complicates financial planning, earnings forecasts, and shareholder communications.

**Why It Matters:** For a firm with multi-million-dollar revenue streams, unhedged currency exposure can produce volatile and unpredictable results. Treasury's role is to stabilize cash flows and protect budgeted profitability. A hedging framework demonstrates prudent financial management and insulates operations from FX shocks.

**Primary Objectives:**
1. Identify and compare three hedge families for the €7.3M receivable.
2. Quantify the trade-off between downside protection, upside participation, and cost.
3. Recommend an optimal strategy grounded in analysis and company risk tolerance.

---

## Methods

We will employ a four-stage analytical framework:

**Stage 1 – Executive Memo (This Document):** Define the exposure, introduce three hedge families with preliminary pros and cons, and outline the analytical roadmap.

**Three Hedge Families:**

1. **Forward Contract**  
   Lock in a fixed exchange rate (1.0890 USD/EUR per Scenario 2) today. Provides complete certainty: €7.3M × 1.0890 = $7,950,700 USD proceeds guaranteed. Pros: Simple, zero upfront cost, eliminates uncertainty. Cons: Forgoes upside if EUR strengthens; inflexible if transaction is cancelled or delayed.

2. **Protective Put (European Put Option)**  
   Purchase a put option on EUR with strike at/near current spot. Guarantees a floor price (strike × €7.3M) while allowing upside if EUR appreciates. Scenario 2 data: put premium = $0.021/EUR. Cost: €7.3M × $0.021 = $153,300 upfront. Pros: Downside protection with unlimited upside. Cons: Premium reduces net proceeds; requires monitoring and decision at expiry.

3. **Collar (Long Put + Short Call)**  
   Buy a protective put and sell a call to finance or reduce the premium. Creates a bounded payoff zone. Scenario 2: Put premium $0.021, Call premium $0.026. Net cost: ($0.021 – $0.026) × €7.3M = –$36,500 (actually generates a small credit). Pros: Reduced or zero net cost; defined risk. Cons: Caps upside at the call strike; more complex to execute and communicate.

**Stage 2 – Excel Model Build:** Construct a dynamic model calculating net USD proceeds for each hedge under EUR/USD spot rates ranging from 0.95 to 1.15, compare break-even rates, and quantify premium costs and effective rates.

**Stage 3 – Technical Specification:** Document model design, assumptions, and data sources; propose an improved, production-grade version suitable for reuse across future hedging decisions.

**Stage 4 – Final Analysis & Recommendation:** Interpret model results, present a clear recommendation aligned with company risk appetite, and deliver an executive-ready summary

