# OPE Pricing – Competition-Aware Track

## Context
Wayfair needed to incorporate competitive price signals into our Own Price Elasticity (OPE) system to protect share and margin in highly elastic categories, without overfitting to noisy competitor data.

## Role
Product Manager, Pricing Systems – owned problem framing, requirements, roadmap, and experiment design. Partnered with Data Science (elasticity models), Engineering (pricing services), and Finance.

## Problem
- Existing OPE system optimized prices based on internal elasticity estimates only.
- In high-competition categories, we occasionally priced far above key competitors, hurting conversion and share.
- Manual overrides and ad hoc rules created inconsistency and operational overhead.

## Approach
- Defined success metrics: **incremental gross profit vs. OPE baseline** at fixed traffic share, with no negative impact on CSAT.
- Segmented categories by competition intensity and data quality.
- Evaluated options: rule-based adjustments, blended competition-aware elasticities, and multi-track strategies.
- Chose a track-based approach so we could:
  - Keep the core OPE system stable.
  - Run controlled experiments by category and elasticity bucket.
  - Roll out incrementally with clear guardrails.

## Execution
- Wrote a PRD covering:
  - New input schema for competitor prices and availability.
  - Track assignment logic based on competition intensity and elasticity buckets.
  - Guardrails for margin floors, price volatility, and max change per period.
- Partnered with DS to:
  - Define how competition signals adjust elasticities or optimal prices.
  - Set expectations on data gaps and latency.
- Partnered with Eng to:
  - Integrate competitor data into pricing services.
  - Expose configuration toggles for experiments and rollback.
- Designed an A/B test:
  - Split by category and elasticity bucket.
  - Primary metric: gross profit.
  - Secondary metrics: CVR, revenue, returns, CS contacts, price perception where available.

## Impact
- +<ADD NUMBER>% incremental GP vs. OPE baseline in high-competition categories.
- Reduced "price outlier" incidents in long-tail assortment.
- Established a simplified-inputs track for easier rollout across teams.

## Learnings
- Competition data volatility required conservative guardrails and monitoring.
- Clear decision logs around trade-offs (margin vs. share) made exec reviews faster.
- Framing this as a track within OPE (vs. a separate system) simplified adoption.

## Artifacts
- [PRD (sanitized)](./prd.md)
- [Experiment Design](./experiment-design.md)
- [Example Dashboard Screenshot](./dashboard.png) <!-- placeholder -->
