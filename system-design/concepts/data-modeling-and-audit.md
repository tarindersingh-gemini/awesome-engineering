# Data Modeling & Audit Trail — Essential for Compliance & Debugging

Summary
- Audit trail must contain timestamped events: approvals, upgrade start/end, validation, rollback, artifact checksums, and operator actions.

Schema suggestions (minimal)
- UpgradeCampaign { id, start_ts, end_ts, scope, initiated_by, status }
- UpgradeTask { id, campaign_id, server_id, shard_id, start_ts, end_ts, status, error_code, artifact_checksum }
- ApprovalRecord { id, campaign_id, approver, time, mode (local/remote), signature }

Design guidance
- Store audit data locally and asynchronously replicate compressed deltas to Earth.
- Use append-only storage and digital signatures for non-repudiation.
- Ensure schema versioning to support future fields.

Recommendation
- Keep a lightweight local DB for audit (SQLite or small write-optimized datastore) and export regularly to long-term metrics store.
