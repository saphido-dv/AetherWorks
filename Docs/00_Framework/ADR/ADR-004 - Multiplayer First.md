# ADR-004 - Multiplayer First

Status: Accepted

Date: 2026-07-01

---

# Context

Retrofitting multiplayer after implementing gameplay creates unnecessary complexity and technical debt.

---

# Decision

Every framework system is designed for multiplayer before implementation.

---

# Rationale

Server-authoritative gameplay provides consistency, security and scalability.

Networking considerations are part of every architecture discussion.

---

# Consequences

Every system documents:

- Ownership
- Replication
- RPC flow
- Local-only logic

Solo gameplay is considered a subset of multiplayer gameplay.