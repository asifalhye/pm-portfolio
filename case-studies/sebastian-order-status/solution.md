# Solution spec — Order-aware status cards

## Status card variants

| Variant | Customer ask | Card shows |
|---|---|---|
| Delivery | "Why delayed?" | Reason, new ETA (+ delta), fee reassurance, Track / Text me |
| Delivery (expanded) | "Where's my car?" | Timeline: Ordered → Verified → In transit → Delivered |
| Registration | "Registration status?" | DMV milestone, dates, temp tag validity |
| Title | "Where is my title?" | Cleared/mailing, address, ETA |
| Handoff | Data null/stale | Honest admission + Advocate context card |

## Architecture (plain language)

```
Customer message → LLM intent → Order API → Validate JSON → Render fixed card template
                                      ↓ missing data
                               Handoff card (no guess)
```

## Experiment (one paragraph)

Offline accuracy test first. Then 50/50 A/B on delivery-delay only: treatment = order-aware card + handoff; control = policy-only Sebastian; randomize by order. Ship if escalation drops ≥15% relative (78% → ~66%) with no accuracy regression. Four weeks (~34K conv/mo) yields MDE ~1.3 pp — power is not the constraint; accuracy auditing is. Extend to registration/title on same data layer if Phase 1 wins.
