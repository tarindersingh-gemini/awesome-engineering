# Load Balancing — Role in Zero-Downtime Upgrades

Summary
- L4 vs L7 load balancing: L7 (HTTP) allows draining and health-aware routing.
- Session affinity considerations during rolling upgrades.

Application
- Use L7 proxies for stateless services for graceful drain/redirect during Blue-Green/rolling updates.
- Ensure session state is externalized (Redis, DB) or migrate sessions to avoid user disruption.
- For critical services, prefer active-active multi-instance topology; ensure upgrades respect redundancy rules.

Recommendation
- Implement pre-upgrade drain + health-check gating and post-upgrade traffic increase steps.
