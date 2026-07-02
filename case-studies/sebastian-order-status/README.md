# Sebastian — Order Status Transparency

> Portfolio case study (Carvana PM exercise). Sanitized — illustrative metrics from provided dataset.

## Context

Sebastian is Carvana's conversational AI. It performs well on discovery (~1.5M conv/mo, +29 tNPS) and fails when customers need **their order** — delivery ETA, registration milestone, title status. Post-purchase status intents cluster at −35 NPS and up to 78% escalation.

## Role

Product Manager — problem framing, opportunity sizing, hypothesis design, solution spec, experiment plan, UI direction (Figma).

## Problem

Customers ask operational questions (*"Why is my delivery delayed?"*) and get policy paragraphs. Sebastian cannot read live order records — only help docs. Empathy and wording fixes don't close the gap; capability does.

**Sample failure (verbatim pattern):**
> *"While I don't have specific details about your vehicle's delay, I can assure you that our team is working hard…"*

## Approach

Prioritized **Area C — Order status transparency** over doc upload, financing, and return workflows: worst NPS, high escalation (~36.6K/mo across three intents), lowest build complexity (read-only lookup vs. full workflows).

**Solution — order-aware status cards (one product, three pieces):**

1. **Live order lookup** — API pull for delivery / registration / title (not document RAG)
2. **Status card** — fixed UI template, three data variants; LLM routes intent and fills slots, app renders consistent layout
3. **Context handoff** — when data is missing, no guess; Advocate gets order # + question pre-loaded

## Execution

- Sized four opportunity areas with defensible support-cost math (~$10/esc); flagged NPS↔conv correlation as directional only
- Wrote testable if/then hypotheses per area with transcript evidence
- Designed status card UX (delivery, tracker expand, registration, title, honest handoff)
- Specified experiment: 50/50 A/B on delivery delay, randomize by order, ship bar ≥15% relative escalation reduction with accuracy guardrail
- Calculated MDE: ~1.3 pp at 4 weeks (80% power) vs. 11.7 pp ship threshold

## Impact (targets / illustrative)

| Metric | Baseline | Target |
|---|---|---|
| Escalation (delivery delay) | 78% | ≥15% relative reduction (→ ~66%) |
| tNPS (status intents) | −35 / −40 / −30 | Directional improvement |
| Support cost | ~$4.4M/yr esc load (Area C) | ~$480K+/yr at 15% cut @ $10/esc |

## Learnings

- Discovery RAG ≠ transactional lookup — status answers need tool calling + structured cards, not retraining
- Card UI must be app-rendered from a data contract; never LLM-generated layout
- Pre-specify business MDE before launch; high volume makes statistical power a non-issue

## Artifacts

- [Solution spec](./solution.md)
- [Hypotheses (full portfolio)](../../README.md#featured-case-studies)
