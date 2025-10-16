# Consistency Models — Relevance & Choice

Summary
- Strong consistency: immediate, readable everywhere (higher latency, more coordination).
- Eventual consistency: updates propagate asynchronously (lower bandwidth/latency cost).
- Causal consistency: useful for ordered operations without global sync.

Application to upgrades
- Approval records and upgrade state machine transitions for Tier 1 must be strongly consistent locally (on-moon) and durably stored.
- Audit logs and analytics can be eventual-consistent and batched to Earth to minimize bandwidth.
- Use causal ordering for staged rollouts so dependent updates follow the correct order.

Recommendation
- Hybrid model: Strong/local consistency for safety-critical state; eventual/casual for telemetry, artifacts, and long-term storage.
