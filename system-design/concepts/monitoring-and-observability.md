# Monitoring & Observability — Real-time and Campaign-level

Summary
- Two dashboards: on-moon real-time (zero latency) and Earth dashboard (2.5s acceptable).
- Need per-server, per-shard, and campaign metrics + distributed tracing for root cause.

Design guidance
- Local Prometheus + Grafana for on-moon alerting; long-term metrics replicated to VictoriaMetrics (batch to Earth).
- Capture: pre/post health check results, upgrade duration, rollback triggers, network usage, CPU/memory changes.
- Alerts: route tiered alerts (on-moon paging for Tier 1 immediately; Earth notifications for campaign-level anomalies).

Recommendation
- Implement synthetic checks and automated runbook links tied to alerts.
- Keep verbose logs locally and send compressed/deduplicated summaries to Earth to save bandwidth.
