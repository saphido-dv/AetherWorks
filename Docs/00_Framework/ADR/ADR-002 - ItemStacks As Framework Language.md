# ADR-002 - ItemStacks As Framework Language

Status: Accepted

Date: 2026-07-01

---

# Context

Most gameplay systems exchange items.

Possible APIs:

Option A

(Item, Quantity)

Option B

ItemStack

---

# Decision

The framework uses S_AW_ItemStack as its common language.

Every gameplay system exchanges ItemStacks whenever possible.

---

# Rationale

The following systems all manipulate stacks:

Inventory

Production

Machines

Storage

Logistics

Crafting

Using a single structure keeps the framework consistent.

---

# Consequences

Functions become:

F_AddItem(ItemStack)

F_RemoveItem(ItemStack)

F_CanAddItem(ItemStack)

instead of

F_AddItem(Item, Quantity)

Only query functions may still use PDA_AW_Item.

Example:

F_GetItemCount(PDA_AW_Item)