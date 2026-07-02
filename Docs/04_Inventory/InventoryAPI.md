# Inventory Framework API

Version: 1.0.0

Status: Locked

Last Update: 2026-07-02

---

# Philosophy

The Inventory API defines every public operation available on the Inventory Framework.

Gameplay systems interact exclusively through this API.

InventorySlots remain private.

Public functions orchestrate internal helper functions.

---

# Categories

Inventory|Queries

Inventory|Validation

Inventory|Modification

Inventory|Transfer

Inventory|Internal

---

# Queries

## F_GetSlot

Category

Inventory|Queries

Access

Public

Description

Returns the ItemStack stored in a slot.

Inputs

- SlotIndex (Integer)

Outputs

- ItemStack (S_AW_ItemStack)

Networking

Pure

---

## F_GetItemCount

Category

Inventory|Queries

Access

Public

Description

Returns the total quantity of a specific item.

Inputs

- Item (PDA_AW_Item)

Outputs

- Quantity (Integer)

Networking

Pure

---

## F_HasItem

Category

Inventory|Queries

Access

Public

Description

Returns true if the inventory contains the requested ItemStack.

Inputs

- ItemStack (S_AW_ItemStack)

Outputs

- Boolean

Networking

Pure

---

## F_HasItems

Category

Inventory|Queries

Access

Public

Description

Returns true if every requested ItemStack exists.

Inputs

- ItemStacks (Array<S_AW_ItemStack>)

Outputs

- Boolean

Networking

Pure

---

## F_IsEmpty

Category

Inventory|Queries

Access

Public

Description

Returns true if every inventory slot is empty.

Outputs

- Boolean

Networking

Pure

---

## F_IsFull

Category

Inventory|Queries

Access

Public

Description

Returns true if the inventory cannot receive additional items.

Outputs

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

Description

Checks whether an ItemStack can completely fit into the inventory.

Inputs

- ItemStack (S_AW_ItemStack)

Outputs

- Boolean

Networking

Pure

---

## F_IsValidSlot

Category

Inventory|Validation

Access

Public

Description

Checks whether a slot index exists.

Inputs

- SlotIndex (Integer)

Outputs

- Boolean

Networking

Pure

---

## F_IsSlotEmpty

Category

Inventory|Validation

Access

Public

Description

Checks whether a slot is empty.

Inputs

- SlotIndex (Integer)

Outputs

- Boolean

Networking

Pure

---

## F_CanStackTogether

Category

Inventory|Validation

Access

Public

Description

Checks whether two ItemStacks can be merged.

Inputs

- StackA (S_AW_ItemStack)

- StackB (S_AW_ItemStack)

Outputs

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

Description

Attempts to insert an ItemStack into the inventory.

Behavior

- Fill compatible stacks first.
- Use empty slots only if necessary.
- Never exceed MaxStackSize.
- Returns remaining items if inventory becomes full.

Inputs

- ItemStack (S_AW_ItemStack)

Outputs

- RemainingStack (S_AW_ItemStack)

Networking

Server Only

Broadcast

ED_OnInventoryChanged

---

## F_RemoveItem

Category

Inventory|Modification

Access

Public

Description

Attempts to remove an ItemStack from the inventory.

Inputs

- ItemStack (S_AW_ItemStack)

Outputs

- RemovedStack (S_AW_ItemStack)

Networking

Server Only

Broadcast

ED_OnInventoryChanged

---

## F_RemoveFromSlot

Category

Inventory|Modification

Access

Public

Description

Removes a quantity from a specific slot.

Inputs

- SlotIndex

- Quantity

Outputs

- RemovedStack (S_AW_ItemStack)

Networking

Server Only

Broadcast

ED_OnInventoryChanged

---

## F_ClearInventory

Category

Inventory|Modification

Access

Public

Description

Removes every ItemStack from the inventory.

Networking

Server Only

Broadcast

ED_OnInventoryChanged

---

# Transfer

## F_TransferStack

Category

Inventory|Transfer

Access

Public

Description

Transfers an ItemStack between two slots.

Behavior

Automatically determines whether the operation is:

- Move
- Merge
- Partial Merge
- Swap
- Reject

Inputs

- SourceSlot

- TargetSlot

Outputs

- Success (Boolean)

Networking

Server Only

Broadcast

ED_OnInventoryChanged

---

# Internal Helpers

Internal helper functions are implementation details.

They are:

- Private
- Never replicated
- Never broadcast dispatchers
- Never accessed outside BPC_AW_Inventory

---

## F_InitializeInventory

Description

Creates every inventory slot.

---

## F_InternalSetSlot

Description

Replaces the content of a slot.

Inputs

- SlotIndex

- ItemStack

---

## F_InternalClearSlot

Description

Resets a slot to an empty ItemStack.

Inputs

- SlotIndex

---

## F_InternalIncreaseQuantity

Description

Adds quantity to an existing stack.

Inputs

- SlotIndex

- Amount

---

## F_InternalDecreaseQuantity

Description

Removes quantity from an existing stack.

Automatically clears the slot when quantity reaches zero.

Inputs

- SlotIndex

- Amount

---

# Framework Guarantees

Public API functions never manipulate UI.

Internal helpers never broadcast dispatchers.

InventorySlots remain private.

Every successful modification triggers exactly one inventory update.

Inventory behavior remains deterministic across server and clients.

---

# Framework Ready Checklist

☑ API reviewed

☑ Naming validated

☑ Categories validated

☑ Networking reviewed

☐ Blueprint implementation

☐ Multiplayer validation

☐ Framework Locked