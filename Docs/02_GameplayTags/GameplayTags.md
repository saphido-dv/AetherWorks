# Gameplay Tags Framework

Version: 1.0.0

Status: Draft

Last Update: 2026-07-01

---

# Philosophy

Gameplay Tags are the common language of Aetherworks.

They provide a generic and scalable way to identify gameplay concepts.

Gameplay Tags replace:

- String comparisons
- Hardcoded enums
- Name checks
- Type casting chains

---

# Objectives

Gameplay Tags should allow systems to communicate without knowing each other.

Examples:

Items

Machines

Buildings

Recipes

Interactions

Power Networks

Research

Logistics

UI

---

# Rules

Tags are descriptive.

Tags never contain implementation logic.

Tags are hierarchical.

Tags are immutable identifiers.

Tags should be reusable.

---

# Root Categories

AW.Item

AW.Building

AW.Machine

AW.Recipe

AW.Interaction

AW.Inventory

AW.Power

AW.Research

AW.Logistics

AW.UI

AW.State

AW.Resource

---

# Item Tags

AW.Item.Resource

AW.Item.Component

AW.Item.Tool

AW.Item.Fuel

AW.Item.Building

AW.Item.Consumable

AW.Item.Equipment

---

# Resource Tags

AW.Resource.Wood

AW.Resource.Stone

AW.Resource.Iron

AW.Resource.Copper

AW.Resource.Coal

AW.Resource.Water

AW.Resource.Oil

---

# Building Tags

AW.Building.Production

AW.Building.Storage

AW.Building.Power

AW.Building.Logistics

AW.Building.Decoration

AW.Building.Infrastructure

---

# Machine Tags

AW.Machine.Sawmill

AW.Machine.Crusher

AW.Machine.Smelter

AW.Machine.Assembler

AW.Machine.Generator

AW.Machine.Refinery

---

# Recipe Tags

AW.Recipe.Wood

AW.Recipe.Smelting

AW.Recipe.Refining

AW.Recipe.Assembling

AW.Recipe.Crafting

---

# Interaction Tags

AW.Interaction.Open

AW.Interaction.Insert

AW.Interaction.Extract

AW.Interaction.Use

AW.Interaction.Pickup

AW.Interaction.Place

AW.Interaction.Rotate

AW.Interaction.Destroy

---

# Inventory Tags

AW.Inventory.Input

AW.Inventory.Output

AW.Inventory.Fuel

AW.Inventory.Storage

AW.Inventory.Buffer

---

# Power Tags

AW.Power.Consumer

AW.Power.Producer

AW.Power.Network

AW.Power.Battery

---

# Research Tags

AW.Research.Unlocked

AW.Research.Locked

AW.Research.Required

---

# Logistics Tags

AW.Logistics.Conveyor

AW.Logistics.Pipe

AW.Logistics.Drone

AW.Logistics.Vehicle

AW.Logistics.Inserter

---

# State Tags

AW.State.Idle

AW.State.Active

AW.State.Producing

AW.State.Paused

AW.State.Blocked

AW.State.Disabled

AW.State.NoPower

AW.State.NoInput

AW.State.OutputFull

---

# UI Tags

AW.UI.Inventory

AW.UI.Production

AW.UI.Storage

AW.UI.Power

AW.UI.Research

---

# Usage Examples

Item filtering

AW.Item.Resource

↓

Only resources are accepted.

---

Machine validation

AW.Inventory.Input

↓

Allowed slot.

---

Production state

AW.State.NoInput

↓

Display warning.

---

Building categorization

AW.Building.Power

↓

Power network registration.

---

# Naming Convention

Gameplay Tags always begin with:

AW.

Examples

AW.Item.Resource

AW.Inventory.Input

AW.State.Active

AW.Power.Consumer

---

# Future Extensions

Technology System

AW.Technology.*

Biomes

AW.Biome.*

NPC

AW.NPC.*

Combat

AW.Combat.*

Quest

AW.Quest.*

Achievements

AW.Achievement.*

---

# Framework Ready Checklist

☐ GameplayTags.ini configured

☐ Root hierarchy defined

☐ Documentation completed

☐ Naming conventions validated

☐ Initial tags created

☐ Multiplayer tested

☐ Integrated with Item Framework

☐ Framework Ready