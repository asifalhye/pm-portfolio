# Conversational AI Agent Initiative

## Context

Hands-on spike building a conversational agent with **agentic RAG** — intent routing, tool use, and guardrails — as foundation for PM work on production chat products.

## Role

Product Manager — problem selection, UX flows, evaluation framing, eng partnership.

## Problem

Generic chatbots retrieve policy docs but fail on **transactional** questions (order status, account state, actions). The product gap is capability (lookup + structured UI + handoff), not model eloquence.

## Approach

- Scoped MVP around a real workflow: question → tool call → structured response → escalation path
- Separated **document RAG** (discovery) from **live data retrieval** (status)
- Defined evaluation: escalation, first-contact resolution, answer accuracy vs. source record

## Execution

- Built demo repo: [agentic-support-assistant](https://github.com/asifalhye/agentic-support-assistant)
- Paired with portfolio case study: [Sebastian — Order Status](../sebastian-order-status/)

## Impact / Outcomes

*[Add metrics if demo was user-tested — e.g., eval pass rate, latency, sample conversations]*

## Learnings

- Fixed UI cards + validated data contracts beat free-form LLM HTML for consistency and trust
- Ship read-only lookup before action buttons (subscribe, reschedule, return)
- Pre-specify business MDE; don't infer GP from observational NPS↔conversion correlation
