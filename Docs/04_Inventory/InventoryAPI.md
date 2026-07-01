# Inventory Framework API

Version: 1.0.0

Status: Planning

Last Update: 2026-07-01

---

# Philosophy

The Inventory API exposes every operation available on the Inventory Framework.

The API is designed to be generic, deterministic and multiplayer-ready.

Every gameplay system must interact with inventories exclusively through this API.

The framework manipulates ItemStacks rather than individual item and quantity pairs whenever possible.

---

# API Categories

- Queries
- Validation
- Modification
- Transfer
- Events

---

# Queries

## F_GetSlot

Category

Inventory|Queries

Purpose

Returns the content of a slot.

Parameters

- SlotIndex (Integer)

Returns

- ItemStack (S_AW_ItemStack)

Networking

Pure

---

## F_GetItemCount

Category

Inventory|Queries

Purpose

Returns the total quantity of a specific item contained in the inventory.

Parameters

- Item (PDA_AW_Item)

Returns

- Quantity (Integer)

Networking

Pure

---

## F_HasItem

Category

Inventory|Queries

Purpose

Checks whether the inventory contains the specified ItemStack.

Parameters

- ItemStack (S_AW_ItemStack)

Returns

- Boolean

Networking

Pure

---

## F_HasItems

Category

Inventory|Queries

Purpose

Checks whether every required ItemStack exists inside the inventory.

Parameters

- ItemStacks (Array<S_AW_ItemStack>)

Returns

- Boolean

Networking

Pure

---

## F_IsEmpty

Category

Inventory|Queries

Purpose

Checks whether every inventory slot is empty.

Returns

- Boolean

Networking

Pure

---

## F_IsFull

Category

Inventory|Queries

Purpose

Checks whether the inventory can no longer receive additional items.

Returns

- Boolean

Networking

Pure

---

# Validation

## F_CanAddItem

Category

Inventory|Validation

Purpose

Determines whether the provided ItemStack can completely fit into the inventory.

Behavior

Existing compatible stacks are filled first.

Empty slots are used only if necessary.

Parameters

- ItemStack (S_AW_ItemStack)

Returns

- Boolean

Networking

Pure

---

## F_IsValidSlot

Category

Inventory|Validation

Purpose

Checks whether the specified slot index exists.

Parameters

- SlotIndex (Integer)

Returns

- Boolean

Networking

Pure

---

## F_CanStackTogether

Category

Inventory|Validation

Purpose

Checks whether two ItemStacks can be merged.

Parameters

- Stack A (S_AW_ItemStack)
- Stack B (S_AW_ItemStack)

Returns

- Boolean

Networking

Pure

---

## F_IsSlotEmpty

Category

Inventory|Validation

Purpose

Checks whether a slot contains an item.

Parameters

- SlotIndex (Integer)

Returns

- Boolean

Networking

Pure

---

# Modification

## F_AddItem

Category

Inventory|Modification

Purpose

Attempts to insert an ItemStack into the inventory.

Behavior

Existing stacks are filled before empty slots.

Stacks never exceed MaxStackSize.

Returns the remaining quantity if the inventory becomes full.

Parameters

- ItemStack (S_AW_ItemStack)

Returns

- RemainingStack (S_AW_ItemStack)

Networking

Server Only

Triggers

ED_OnInventoryChanged

---

## F_RemoveItem

Category

Inventory|Modification

Purpose

Attempts to remove an ItemStack from the inventory.

Behavior

Items are removed from existing stacks until the requested quantity has been removed.

Parameters

- ItemStack (S_AW_ItemStack)

Returns

- RemovedStack (S_AW_ItemStack)

Networking

Server Only

Triggers

ED_OnInventoryChanged

---

## F_RemoveFromSlot

Category

Inventory|Modification

Purpose

Removes items from a specific slot.

Parameters

- SlotIndex (Integer)
- Quantity (Integer)

Returns

- RemovedStack (S_AW_ItemStack)

Networking

Server Only

Triggers

ED_OnInventoryChanged

---

## F_ClearInventory

Category

Inventory|Modification

Purpose

Removes every ItemStack from the inventory.

Networking

Server Only

Triggers

ED_OnInventoryChanged

---

# Transfer

## F_TransferStack

Category

Inventory|Transfer

Purpose

Transfers an ItemStack between two slots.

Behavior

Attempts to merge first.

Swaps stacks if merging is impossible.

Parameters

- SourceSlot (Integer)
- TargetSlot (Integer)

Returns

- Boolean

Networking

Server Only

Triggers

ED_OnInventoryChanged

---

# Events

## ED_OnInventoryChanged

Purpose

Broadcast whenever the inventory content changes.

Called After

- Add Item
- Remove Item
- Transfer Stack
- Swap Slots
- Clear Inventory

---

# Framework Guarantees

The Inventory Framework guarantees that:

- Inventory order remains deterministic.
- Stack sizes never exceed MaxStackSize.
- Existing stacks are always filled before empty slots.
- Every successful modification broadcasts exactly one inventory update.
- Inventory logic remains independent from gameplay systems.

---

# Framework Ready Checklist

☐ API reviewed

☐ Categories validated

☐ Naming validated

☐ Documentation validated

☐ Ready for implementation