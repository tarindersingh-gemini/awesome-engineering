# Asynchronous Processing & Queues — Orchestration Backbone

Summary
- Use message queues and task queues for large-scale orchestration: campaign scheduler -> per-shard workers -> per-server tasks.
- Important for survivability during transient link issues.

Design guidance
- Use durable on-moon queue (e.g., RabbitMQ/NSQ/Kafka lightweight footprint) to store upgrade tasks and state machine events.
- Ensure purging/compaction policies to avoid storage explosion.
- Implement exactly-once/at-least-once semantics carefully: idempotent server-side upgrade tasks are required.

Recommendation
- Orchestrator writes tasks to on-moon persistent queue. Workers pull tasks and report results; results are batched to Earth.
- Use exponential backoff and circuit-breaker patterns in worker retries.
