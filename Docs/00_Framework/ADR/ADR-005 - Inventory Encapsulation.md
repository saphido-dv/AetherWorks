# ADR-005 - Inventory Encapsulation

Status: Accepted

Date: 2026-07-01

---

# Context

The Inventory Framework stores all inventory data inside InventorySlots.

Allowing external systems to modify InventorySlots directly would bypass validation, replication rules and event dispatchers.

---

# Decision

InventorySlots is private.

No external Blueprint may read or modify InventorySlots directly.

Every interaction with the inventory must go through the public Inventory API.

---

# Rationale

This guarantees:

- Data consistency
- Centralized validation
- Reliable replication
- Predictable behavior
- Easier maintenance

---

# Consequences

InventorySlots can only be modified by functions implemented inside BPC_AW_Inventory.

Gameplay systems communicate exclusively through the Inventory API.