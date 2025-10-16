# Reliability Patterns — Failure Detection, Circuit Breakers, Rate Limiting

Summary
- Expect partial failures. Use guardrails: circuit breakers, bulkheads, retries with backoff, and isolation.

Design guidance
- Circuit breakers around upgrade operations per-shard to stop cascades.
- Bulkheads per-service and per-shard to limit concurrent failures and protect Tier 1 systems.
- Rate-limit Earth downloads and orchestrator commands to avoid saturating the 30 Mbps upgrade budget.

Recommendation
- Default breakers trip on health-check or error-rate thresholds matching requirements (error >1% or perf degradation >20%).
- Use automatic rollback on detected dangerous conditions; require human approval for Tier 1 rollback unless life-critical failure.
