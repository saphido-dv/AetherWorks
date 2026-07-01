# Item Framework API

Version: 1.0.0

Status: Planning

Last Update: 2026-07-01

---

# Philosophy

Items are immutable data assets.

They describe gameplay objects but never execute gameplay.

The API defined here is considered stable.

Changes should remain backward compatible whenever possible.

---

# Base Asset

Primary Data Asset

Class

PDA_AW_Item

---

# Properties

## Identifier

Type

Gameplay Tag

Variable

ItemTag

Description

Unique identifier of the item.

Example

AW.Item.Resource.WoodLog

---

## Display Name

Type

Text

Variable

DisplayName

Description

Localized item name.

---

## Description

Type

Text

Variable

Description

Description shown in UI.

---

## Icon

Type

Texture2D

Variable

Icon

Description

Inventory icon.

---

## World Mesh

Type

Static Mesh

Variable

WorldMesh

Description

Mesh displayed in the world.

---

## Gameplay Tags

Type

Gameplay Tag Container

Variable

GameplayTags

Description

Collection of gameplay tags describing this item.

Examples

AW.Item.Resource

AW.Resource.Wood

---

## Maximum Stack Size

Type

Integer

Variable

MaxStackSize

Default

100

Description

Maximum quantity per inventory slot.

---

## Weight

Type

Float

Variable

Weight

Default

0.0

Description

Weight of one item.

Reserved for future logistics.

---

## Value

Type

Integer

Variable

Value

Default

0

Description

Trading or crafting value.

Reserved for future gameplay.

---

# Future Extensions

The following properties are intentionally excluded from Version 1.0.

Fuel

BurnTime

FuelValue

Equipment

Durability

Armor

Damage

Buildings

PlaceableData

Research

UnlockRequirements

Crafting

RecipeReferences

These will be added through child data assets when needed.

---

# Asset Naming

Base

PDA_AW_Item

Examples

PDA_AW_WoodLog

PDA_AW_Stone

PDA_AW_Plank

PDA_AW_IronOre

---

# Framework Rules

Items contain data only.

Items never contain gameplay logic.

Items never know inventories.

Items never know recipes.

Items never know machines.

Items never know players.

---

# Framework Ready Checklist

☑ Base asset created

☑ Properties implemented

☑ Gameplay Tags integrated

☑ Test assets created

☐ Documentation validated