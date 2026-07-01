# Item Framework

Version: 1.0.0

Status: Implementation

Last Update: 2026-07-01

---

# Philosophy

Items are the foundation of Aetherworks.

Every gameplay system consumes items.

Items are completely data-driven.

Items contain data only.

Items never contain gameplay logic.

---

# Goals

The Item Framework must:

- Be reusable
- Be data-driven
- Be multiplayer friendly
- Be easily extendable
- Support future content without architecture changes

---

# Architecture

Primary Data Asset

↓

PDA_AW_Item

↓

Gameplay Systems

Inventory

Production

Machines

Buildings

UI

Save System

---

# Item Hierarchy

PDA_AW_Item

↓

Gameplay-specific item assets

Examples

PDA_AW_WoodLog

PDA_AW_Plank

PDA_AW_Stone

PDA_AW_IronOre

---

# Responsibilities

Items are responsible for describing themselves.

Examples

Display Name

Description

Icon

Mesh

Gameplay Tags

Stack Size

Weight

Value

Rarity

---

# Items Never

Contain gameplay logic

Know inventories

Know machines

Know recipes

Know players

Know UI

Spawn actors

Execute gameplay

---

# Gameplay Tags

Every item owns a Gameplay Tag Container.

Examples

AW.Item.Resource

AW.Resource.Wood

AW.Item.Fuel

Gameplay systems use tags instead of enums.

---

# Public Data

Every item provides:

Identifier

Display Name

Description

Icon

World Mesh

Gameplay Tags

Maximum Stack Size

Weight

Value

---

# Future Extensions

Fuel

Burn Time

Fuel Value

Equipment

Durability

Armor

Weapon

Damage

Buildings

Placeable Data

Machine Data

Research

Unlock Requirements

Crafting

Recipe References

---

# Framework Ready Checklist

☑ Base item asset created

☑ Gameplay Tags integrated

☐ Documentation completed

☑ Test items created

☐ Framework validated