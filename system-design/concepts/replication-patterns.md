# Replication Patterns — Leader-follower, Multi-leader, Leaderless

Summary
- Leader-follower: single writer, many readers (good for consistency).
- Multi-leader: writes accepted in multiple locations (higher availability, conflict resolution needed).
- Leaderless (gossip): high availability at cost of convergence.

For lunar system
- Use leader-follower for control-plane state (upgrade orchestration): one authoritative controller per cluster with read replicas.
- Use multi-leader sparingly for on-moon mirrored registries (artifact caches) to allow local writes/refreshes without Earth round-trips.
- For telemetry and metrics, use eventual replication (gossip or batched transfer) to minimize constant Earth-bandwidth use.

Recommendation
- Strong leader/follower for approval and rollback control.
- Multi-leader for artifact registries on multiple bases to reduce Earth downloads.
