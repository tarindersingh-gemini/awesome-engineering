# CAP Theorem — Quick Relevance to Lunar Upgrades

Summary
- CAP states you can only simultaneously guarantee two of: Consistency, Availability, Partition tolerance.
- In distributed lunar environment, network partitions (link blackouts) and latency are real constraints. Partition tolerance is mandatory.

Implications & Recommendations
- Prioritize Partition tolerance + Availability for telemetry/upgrade control during partition windows, but provide tunable strong-consistency operations (approval gates) when Earth-Moon link is available.
- For safety-critical operations (Tier 1), require local quorum decisions (on-moon) to avoid Earth link as a single point of failure.
- Implement modes:
  - Local-decide mode: critical approvals executed by local base when partitioned.
  - Global-consensus mode: Earth+Moon approvals for non-partitioned windows.

Trade-offs
- Accept eventual consistency for non-critical audit replication to Earth to save bandwidth.
- Strong consistency for approval and state transitions increases latency and Earth bandwidth but is required for life-critical steps.
