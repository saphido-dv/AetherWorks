# Inventory Framework

Version: 1.0.0

Status: Locked

Last Update: 2026-07-02

---

# Purpose

The Inventory Framework provides a generic, reusable and multiplayer-ready inventory system.

Every gameplay system stores and manipulates items through this framework.

The inventory is completely independent from gameplay systems.

---

# Design Goals

The framework must be:

- Generic
- Multiplayer First
- Data Driven
- UI Independent
- Event Driven
- Deterministic
- Easy to extend
- Easy to test

---

# Responsibilities

The Inventory Framework is responsible for:

- Storing ItemStacks
- Managing inventory slots
- Validating insertions
- Validating removals
- Transferring stacks
- Broadcasting inventory updates

---

# Non Responsibilities

The Inventory Framework never:

- Knows the player
- Knows machines
- Knows buildings
- Knows recipes
- Knows production
- Knows UI
- Knows game rules

---

# Consumers

The Inventory Framework is used by:

- Player Inventory
- Storage Containers
- Production Machines
- Vehicles
- Drones
- Future Gameplay Systems

---

# Architecture

Gameplay Systems

↓

BPC_AW_Inventory

↓

InventorySlots

↓

S_AW_ItemStack

↓

PDA_AW_Item

---

# Internal Data

InventorySlots

Type

Array<S_AW_ItemStack>

Visibility

Private

Description

Stores every inventory slot.

---

MaxSlots

Type

Integer

Description

Maximum number of slots.

Configured once during initialization.

Never changes during gameplay.

---

# Framework Rules

InventorySlots is private.

Only BPC_AW_Inventory may modify inventory data.

External systems communicate exclusively through the public API.

Internal helper functions never:

- Replicate
- Broadcast dispatchers
- Modify UI
- Execute gameplay logic

Public API functions orchestrate internal helpers.

---

# Transfer Rules

The Inventory Framework automatically determines the correct transfer behavior.

Possible operations:

- Move
- Merge
- Partial Merge
- Swap
- Reject

Gameplay systems never decide transfer behavior.

---

# Networking

Server Authoritative

Inventory modifications execute on the server.

Inventory data replicates to clients.

Clients never modify replicated inventory data.

Widgets never modify inventories directly.

---

# Event Dispatchers

ED_OnInventoryChanged

Broadcast once after a successful inventory modification.

No dispatcher is fired when no inventory data changes.

---

# Public API

Queries

Validation

Modification

Transfer

---

# Internal Helpers

Initialization

Slot Manipulation

Internal Data Operations

These helpers remain private.

---

# Framework Guarantees

The Inventory Framework guarantees:

✓ Inventory size never changes during gameplay.

✓ Existing compatible stacks are filled before empty slots.

✓ Stack quantities never exceed MaxStackSize.

✓ Inventory order is deterministic.

✓ Inventory modifications are server authoritative.

✓ InventorySlots remain encapsulated.

✓ Every successful modification broadcasts exactly one inventory update.

✓ Gameplay systems never access inventory data directly.

---

# Future Features

Inventory Filters

Slot Restrictions

Locked Slots

Sorting

Quick Transfer

Weight Restrictions

Overflow Inventories

---

# Framework Ready Checklist

☑ Documentation completed

☑ Architecture reviewed

☑ API defined

☑ Networking defined

☐ Blueprint implementation

☐ Multiplayer validation

☐ Performance validation

☐ Framework Locked