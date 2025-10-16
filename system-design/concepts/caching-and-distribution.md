# Caching & Distribution — P2P Artifact Distribution and Bandwidth Optimization

Summary
- Bandwidth is the key constraint: Earth->Moon transfer is expensive and limited (30 Mbps for upgrades).
- P2P distribution (local mirrors, BitTorrent-like or registry proxies) reduces Earth bandwidth usage.

Design guidance
- Maintain on-moon artifact registry (mirrors) and use P2P/peer-cache among servers within a base to achieve >90% peer distribution.
- Implement delta updates (binary diffs) and layered images to reduce bytes transferred.
- Lease-and-validate model: servers download from local peers, then verify checksums signed by Earth-mirror to maintain integrity.

Recommendation
- Primary strategy: seed artifacts on a small set of high-availability nodes, then P2P distribute within lunar mesh.
- Fallback: controlled Earth downloads with rate-limiting when local peers insufficient.

Security
- Sign artifacts, enforce TLS, and verify checksums locally to avoid malware injection.
