# Aetherworks Framework Rules

Version: 1.0.0

Status: Active

Last Update: 2026-07-01

---

# Philosophy

Aetherworks is developed as a reusable gameplay framework.

Framework systems must remain generic, modular and multiplayer-ready.

Gameplay systems consume framework systems but never modify them.

---

# Rule 001 - UI Never Changes Gameplay

Widgets never execute gameplay logic directly.

Always use:

Widget
↓
PlayerController
↓
Server RPC
↓
Gameplay Component
↓
Replication
↓
UI Refresh

Forbidden:

Widget
↓
Inventory Component

Widget
↓
Production Component

Widget
↓
Machine

---

# Rule 002 - Components Never Know Their Owner Type

Components are generic.

A component never knows if it belongs to:

- Player
- Machine
- Building
- Chest
- Drone
- Vehicle

Components only know their own data.

Example:

BPC_AW_Inventory stores inventory data.

It does not know who owns it.

---

# Rule 003 - One Class One Responsibility

Every class has a single responsibility.

Examples:

BPC_AW_Inventory
→ Inventory management

BPC_AW_Production
→ Production logic

WBP_AW_Inventory
→ Inventory display

BP_AW_ProductionMachine
→ Machine assembly

---

# Rule 004 - Multiplayer First

Every system must be designed for multiplayer before implementation.

Questions to answer before coding:

Who owns the object?

Who executes the RPC?

What is replicated?

What is local only?

Who is authoritative?

The server is always authoritative.

---

# Rule 005 - Event Driven Architecture

Avoid polling whenever possible.

Prefer:

- Event Dispatchers
- Interfaces
- RepNotify
- Timers

Avoid:

Tick

GetAllActorsOfClass

Continuous state checking

---

# Rule 006 - Data Driven Gameplay

Gameplay behavior is driven by data.

Prefer:

Data Assets

Data Tables

Gameplay Tags

Avoid hardcoded logic.

Example:

Sawmill does not know recipes.

Recipes come from data.

---

# Rule 007 - Documentation First

Documentation is written before implementation.

Blueprints must follow documentation.

Documentation is the source of truth.

---

# Rule 008 - Framework Before Gameplay

Framework systems are implemented first.

Gameplay systems are implemented afterwards.

Framework examples:

Inventory

Production

Interaction

Power

Save System

Gameplay examples:

Sawmill

Crusher

Assembler

Smelter

Generator

---

# Rule 009 - No Circular Dependencies

Low level systems cannot depend on higher level systems.

Allowed:

Inventory
↓
Production
↓
Machine
↓
Sawmill

Forbidden:

Inventory
↓
Machine
↓
Inventory

---

# Rule 010 - Locked Systems

Once a framework system reaches Framework Ready status it becomes Locked.

Locked systems are modified only for:

Critical bugs

Security issues

Architecture corrections

New gameplay features should consume the framework instead of changing it.