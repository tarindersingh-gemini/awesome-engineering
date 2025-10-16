# Partitioning & Sharding — Organizing Servers for Safe Upgrades

Summary
- Partition servers by geographic base, service type, and criticality.
- Shard upgrade campaigns by shard key (e.g., base + cluster + service) to limit blast radius.

Application
- Define shard keys that ensure independent redundancy groups (never upgrade two redundant instances).
- Use shards to schedule parallelism while respecting max concurrent downtime constraints.

Recommendation
- Conservative shard size for Tier 1 (small batches, single-redundant-instance rule).
- Larger parallelism for Tier 3 with automated rollback.
