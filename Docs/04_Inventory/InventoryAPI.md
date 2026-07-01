# Inventory Framework API

Version: 1.0.0

Status: Planning

Last Update: 2026-07-01

---

# Philosophy

The Inventory API defines every public operation available on the Inventory Framework.

The Inventory Framework manipulates ItemStacks rather than Item / Quantity pairs whenever possible.

Every gameplay system communicates with inventories exclusively through this API.

InventorySlots remain private and are never accessed directly outside of the Inventory Component.

---

# API Categories

- Queries
- Validation
- Modification
- Transfer
- Events
- Internal Helpers

---

# Queries

## F_GetSlot

Category

Inventory|Queries

Access

Public

Purpose

Returns the ItemStack stored in a slot.

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

Access

Public

Purpose

Returns the total quantity of a specific item.

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

Access

Public

Purpose

Checks whether the inventory contains the requested ItemStack.

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

Access

Public

Purpose

Checks whether all requested ItemStacks exist.

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

Access

Public

Purpose

Returns true if every inventory slot is empty.

Returns

- Boolean

Networking

Pure

---

## F_IsFull

Category

Inventory|Queries

Access

Public

Purpose

Returns true if no additional ItemStack can fit.

Returns

- Boolean

Networking

Pure

---

# Validation

## F_CanAddItem

Category

Inventory|Validation

Access

Public

Purpose

Checks whether the provided ItemStack can completely fit into the inventory.

Behavior

Compatible stacks are filled before empty slots.

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

Access

Public

Purpose

Checks whether a slot index exists.

Parameters

- SlotIndex (Integer)

Returns

- Boolean

Networking

Pure

---

## F_IsSlotEmpty

Category

Inventory|Validation

Access

Public

Purpose

Checks whether a slot is empty.

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

Access

Public

Purpose

Checks whether two ItemStacks are compatible for merging.

Parameters

- StackA (S_AW_ItemStack)
- StackB (S_AW_ItemStack)

Returns

- Boolean

Networking

Pure

---

# Modification

## F_AddItem

Category

Inventory|Modification

Access

Public

Purpose

Attempts to insert an ItemStack into the inventory.

Behavior

Compatible stacks are filled first.

Remaining quantity is placed into empty slots.

Returns the remaining ItemStack if the inventory becomes full.

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

Access

Public

Purpose

Attempts to remove an ItemStack from the inventory.

Behavior

Items are removed until the requested quantity has been removed.

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

Access

Public

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

Access

Public

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

Access

Public

Purpose

Transfers an ItemStack between two inventory slots.

Behavior

The Inventory Framework automatically determines the correct transfer operation.

Possible outcomes

- Move
- Merge
- Partial Merge
- Swap
- Reject

Parameters

- SourceSlot (Integer)
- TargetSlot (Integer)

Returns

- Success (Boolean)

Networking

Server Only

Triggers

ED_OnInventoryChanged

---

# Events

## ED_OnInventoryChanged

Purpose

Broadcast whenever inventory content changes.

Triggered After

- Add Item
- Remove Item
- Remove From Slot
- Transfer Stack
- Clear Inventory

---

# Internal Helpers

Internal helper functions are implementation details.

They are:

- Private
- Never replicated
- Never broadcast dispatchers
- Never interact with UI

---

## F_InitializeInventory

Purpose

Creates every inventory slot.

Returns

None

---

## F_FindFirstEmptySlot

Purpose

Returns the first empty slot.

Returns

SlotIndex

Return Value

-1 if none exists.

---

## F_FindCompatibleStack

Purpose

Returns the first compatible stack that can receive the provided ItemStack.

Parameters

- ItemStack (S_AW_ItemStack)

Returns

SlotIndex

Return Value

-1 if none exists.

---

## F_InternalSetSlot

Purpose

Replaces the content of a slot.

Parameters

- SlotIndex
- ItemStack

Returns

None

---

## F_InternalClearSlot

Purpose

Resets a slot to an empty ItemStack.

Parameters

- SlotIndex

Returns

None

---

## F_InternalIncreaseQuantity

Purpose

Adds quantity to an existing stack.

Parameters

- SlotIndex
- Amount

Returns

None

---

## F_InternalDecreaseQuantity

Purpose

Removes quantity from an existing stack.

Automatically clears the slot when quantity reaches zero.

Parameters

- SlotIndex
- Amount

Returns

None

---

# Framework Guarantees

The Inventory API guarantees:

- Public functions never access UI.
- Internal helpers never broadcast dispatchers.
- InventorySlots remain private.
- Public functions orchestrate helpers.
- Helpers manipulate data only.
- Every successful modification broadcasts exactly one inventory update.
- Inventory remains deterministic across server and clients.

---

# Framework Ready Checklist

☐ API validated

☐ Blueprint implementation completed

☐ Multiplayer reviewed

☐ Documentation validated

☐ Ready for production