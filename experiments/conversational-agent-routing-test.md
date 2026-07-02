# Conversational Agent Routing Test

## Context

When a conversational assistant handles both **discovery** (policy/knowledge) and **transactional** (order-specific) intents, routing determines whether the user gets a useful answer or escalates.

## Hypothesis

If we route status intents to **live order lookup + structured status cards** instead of policy RAG alone, then escalation on delivery/reg/title intents drops without increasing hallucination rate.

## Design

- **Population:** Active orders, status-related intents
- **Unit:** Order-level randomization
- **Treatment:** Order-aware lookup + fixed UI card + context handoff when data missing
- **Control:** Policy-only RAG (status quo)
- **Duration:** 4 weeks (~34K delivery-delay conv/mo in reference dataset)

## Metrics

- **Primary:** Escalation rate
- **Secondary:** tNPS, first-contact resolution, 48h repeat contact
- **Guardrail:** Answer accuracy vs. order record; latency <3s

## MDE (pre-calculated)

At 4 weeks, 50/50, 78% baseline escalation: **MDE ≈ 1.3 pp absolute** (80% power). Ship bar: **≥15% relative** (~11.7 pp) with clean accuracy.

## Decision rule

Ship if primary KPI hits bar and guardrails hold. Stop if accuracy regresses.

## Learnings

- Statistical power is rarely the bottleneck at high volume — accuracy auditing and business MDE pre-spec matter more.
