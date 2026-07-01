# Inventory Framework

Version: 1.0.0

Status: Planning

---

# Purpose

Provide a generic inventory system capable of storing and manipulating item stacks.

Every gameplay system uses the exact same inventory implementation.

---

# Responsibilities

The Inventory Framework is responsible for:

- Managing inventory slots
- Managing item stacks
- Validating insertions
- Validating removals
- Broadcasting inventory updates

---

# Non Responsibilities

The Inventory Framework never:

- Knows the player
- Knows machines
- Knows recipes
- Knows production
- Knows UI
- Knows networking ownership

---

# Framework Guarantees

The framework guarantees:

✔ Existing stacks are always filled first.

✔ Empty slots are used only if required.

✔ Inventory order is preserved unless explicitly changed.

✔ Stack sizes never exceed MaxStackSize.

✔ Inventory changes trigger ED_OnInventoryChanged exactly once.

✔ Inventory data remains deterministic across server and clients.

---

# Internal Data

InventorySlots

Array<S_AW_ItemStack>

MaxSlots

Integer

---

# Public API

Queries

Validation

Modification

Transfer

Events

---

# Network

Server Authoritative

Replicated Inventory

RepNotify

---

# Consumers

Player

Storage

Production

Machine

Drone

Vehicle

---

# Future Features

Inventory Filters

Sorting

Quick Transfer

Locked Slots

Slot Restrictions

Overflow Storage

---

# Framework Ready

☐ API

☐ Tests

☐ Replication

☐ Documentation

☐ Performance

☐ Multiplayer

☐ Locked