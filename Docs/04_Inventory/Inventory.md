# Inventory Framework

Version: 1.0.0

Status: Planning

Last Update: 2026-07-01

---

# Philosophy

The Inventory Framework is the backbone of item storage within Aetherworks.

It provides a generic, reusable and multiplayer-ready inventory system.

The framework is completely independent from gameplay systems.

Every inventory in the game uses the exact same component.

---

# Goals

The Inventory Framework must be:

- Generic
- Reusable
- Event Driven
- Multiplayer First
- Data Driven
- UI Independent

---

# Responsibilities

The Inventory Framework is responsible for:

- Managing inventory slots
- Managing item stacks
- Validating insertions
- Validating removals
- Validating transfers
- Broadcasting inventory changes

---

# Non Responsibilities

The Inventory Framework never:

- Knows the player
- Knows machines
- Knows buildings
- Knows recipes
- Knows production
- Knows UI
- Knows gameplay rules
- Knows networking ownership

---

# Consumers

The Inventory Framework is used by:

- Players
- Chests
- Machines
- Storage Buildings
- Conveyors
- Vehicles
- Drones
- Future gameplay systems

---

# Architecture

Gameplay

↓

Inventory Component

↓

Inventory Slots

↓

Item Stacks

↓

Primary Data Assets

---

# Internal Data

InventorySlots

Array<S_AW_ItemStack>

MaxSlots

Integer

---

# Framework Guarantees

The Inventory Framework guarantees:

✔ Inventory size never changes during gameplay.

✔ Existing compatible stacks are always filled before empty slots are used.

✔ Stack quantities never exceed MaxStackSize.

✔ Inventory order remains deterministic.

✔ Inventory modifications are server authoritative.

✔ Inventory modifications trigger exactly one inventory update.

✔ Gameplay systems never modify InventorySlots directly.

---

# Transfer Rules

The Inventory Framework automatically determines the correct transfer behavior.

Possible outcomes are:

- Move
- Merge
- Partial Merge
- Swap
- Reject

Gameplay systems never decide which transfer behavior should occur.

The Inventory Framework is solely responsible for transfer logic.

---

# Public API

Queries

Validation

Modification

Transfer

Events

---

# Internal Helpers

The Inventory Framework exposes internal helper functions used only by the component implementation.

These helpers are:

- Private
- Non replicated
- UI independent
- Dispatcher independent

They are responsible for manipulating inventory data while the public API orchestrates gameplay behavior.

---

# Event Dispatchers

ED_OnInventoryChanged

Broadcast whenever the inventory content changes.

---

# Networking

The Inventory Framework is fully server authoritative.

Inventory modifications execute exclusively on the server.

Inventory data is replicated to clients.

UI refreshes through replicated data and Event Dispatchers.

Widgets never modify inventory data directly.

---

# Future Features

Inventory Filters

Sorting

Quick Transfer

Locked Slots

Slot Restrictions

Overflow Inventories

Weight Restrictions

Auto Sort

---

# Framework Ready Checklist

☐ Documentation completed

☐ Component created

☐ Internal helpers implemented

☐ Public API implemented

☐ Replication implemented

☐ Multiplayer validated

☐ Performance validated

☐ Documentation reviewed

☐ Framework Ready

☐ Locked