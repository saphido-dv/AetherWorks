# Aetherworks Changelog

Version: 1.0.0  
Status: Active  
Last Update: 2026-07-01

---

# Changelog Philosophy

This document tracks major framework milestones.

Minor bug fixes should not appear here.

Only architectural changes, completed systems and important framework updates are recorded.

---

# Framework 2.0.0

Status: 🟢 Active

Release Date: 2026-07-01

Description:

Complete restart of the Aetherworks framework.

Transition from prototype architecture to production-ready architecture.

Documentation-first workflow adopted.

Framework systems are now designed before implementation.

---

## Sprint 0 — Foundation

Status: 🟢 COMPLETE

Completed:

### Documentation

- README.md
- Rules.md
- Naming.md
- FolderStructure.md
- Architecture.md
- Roadmap.md
- Changelog.md

### Development Rules

- Documentation First
- Multiplayer First
- Data Driven
- Event Driven
- Framework Before Gameplay
- One Class = One Responsibility

### Architecture Decisions

UI

↓

PlayerController

↓

Server RPC

↓

Gameplay Components

↓

Replication

↓

Dispatchers

↓

UI Refresh

---

Gameplay Layers

Core

↓

Gameplay Tags

↓

Items

↓

Inventory

↓

Character

↓

Interaction

↓

Buildings

↓

Production

↓

Machines

↓

UI

↓

Gameplay Features

---

### Locked Rules

Rule 001

UI Never Changes Gameplay

Rule 002

Components Never Know Their Owner Type

Rule 003

One Class = One Responsibility

Rule 004

Multiplayer First

Rule 005

Event Driven Architecture

Rule 006

Data Driven Gameplay

Rule 007

Documentation First

Rule 008

Framework Before Gameplay

Rule 009

No Circular Dependencies

Rule 010

Locked Systems

---

## Sprint 2 — GameplayTags Framework

Status: 🟢 COMPLETE

Added:

- AW.Item.Resource
- AW.Item.Fuel
- AW.Item.Product
- AW.Item.Tool
- AW.Item.Building
- AW.Resource.Stone
- AW.Resource.Wood

---

## Sprint 2 — Item Framework

Status: 🟢 COMPLETE

Added:

- PDA_AW_Item
- PDA_AW_Item_WoodLog
- PDA_AW_Item_Plank
- S_AW_ItemStack

Implemented:

- Gameplay Tag integration
- Primary Data Asset architecture
- Item API v1.0

Status:

🔒 LOCKED

---
# Upcoming Milestones
---
Sprint 3

Inventory Framework

Status:

⏳ Planned

---

Sprint 4

Character Framework

Status:

⏳ Planned

---

Sprint 5

Interaction Framework

Status:

⏳ Planned

---

Sprint 6

Building Framework

Status:

⏳ Planned

---

Sprint 7

Production Framework

Status:

⏳ Planned

---

Sprint 8

UI Framework

Status:

⏳ Planned

---

Sprint 9

Machine Framework

Status:

⏳ Planned

---

Sprint 10

First Machine

Status:

⏳ Planned

Sawmill