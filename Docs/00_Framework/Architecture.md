# Aetherworks Architecture

Version: 1.0.0

Status: Active

Last Update: 2026-07-01

---

# Philosophy

Aetherworks is designed as a modular gameplay framework.

Framework systems are generic.

Gameplay systems consume framework systems.

Gameplay never modifies framework architecture.

---

# Layered Architecture

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

# Dependency Rules

Low level systems must never depend on higher level systems.

Allowed

Inventory
↓
Production
↓
Machine
↓
Sawmill

Forbidden

Inventory
↓
Machine
↓
Inventory

Forbidden

UI
↓
Machine

Allowed

UI
↓
PlayerController
↓
Gameplay Component

---

# Framework Hierarchy

BP_AW_GameMode

↓

BP_AW_PlayerController

↓

BP_AW_Character

↓

Gameplay Components

↓

Data Assets

↓

UI

---

# Ownership

Server

Authoritative

PlayerController

Input authority

Character

Movement authority

Components

Gameplay authority

Widgets

Display only

---

# Multiplayer Architecture

Client

↓

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

Dispatcher

↓

Widget Refresh

---

# Rule

Widgets never modify gameplay directly.

Widgets only send requests.

Gameplay validates requests.

Server executes gameplay.

Replication updates clients.

Widgets refresh.

---

# Building Framework

BP_AW_Building

↓

BP_AW_InteractableBuilding

↓

BP_AW_ProductionMachine

↓

Gameplay Machines

Sawmill

Crusher

Smelter

Assembler

Generator

---

# Inventory Architecture

BPC_AW_Inventory

↓

Storage Logic

↓

Dispatchers

↓

UI Refresh

Inventory does not know:

Character

Machine

Building

Drone

Vehicle

Player

Inventory only manages item stacks.

---

# Production Architecture

BPC_AW_Production

↓

Recipe Validation

↓

Resource Consumption

↓

Progression

↓

Craft Completion

↓

Dispatchers

↓

UI Refresh

Production does not know:

Widgets

Characters

Buildings

Specific Machines

Recipes are data.

Machines are configuration.

---

# UI Architecture

Widgets display data.

Widgets do not own gameplay.

Widgets subscribe to dispatchers.

Widgets unsubscribe on destruction.

---

Allowed

Dispatcher
↓
Widget Refresh

Forbidden

Widget
↓
Inventory Modification

Widget
↓
Production Logic

Widget
↓
Machine Logic

---

# Interaction Architecture

Character

↓

Line Trace

↓

Interactable Actor

↓

PlayerController

↓

Server RPC

↓

Gameplay Validation

↓

Gameplay Execution

---

# Data Architecture

Gameplay Tags

↓

Data Assets

↓

Components

↓

Machines

↓

Widgets

---

Examples

PDA_AW_Item

↓

S_AW_ItemStack

↓

Inventory

↓

Production

↓

Machine

↓

UI

---

# Event Driven Architecture

Prefer

Event Dispatchers

Interfaces

RepNotify

Timers

Delegates

Avoid

Tick

Polling

GetAllActorsOfClass

Continuous State Checking

---

# Save Architecture

Save System

↓

Framework Components

↓

Serializable Data

↓

Gameplay State

↓

World State

UI is never saved.

Widgets are recreated.

---

# Testing Pipeline

Architecture

↓

Documentation

↓

Implementation

↓

Solo Testing

↓

Multiplayer Testing

↓

Framework Ready

↓

Locked

---

# Locked Systems

Once a framework reaches Framework Ready status it becomes Locked.

Allowed modifications

Critical bugs

Replication fixes

Architecture corrections

Forbidden modifications

Feature creep

Machine-specific logic

Temporary hacks

---

# Long Term Goal

Any developer should understand the project architecture within one hour.

Any gameplay feature should be implemented without modifying framework systems.

New gameplay should consume the framework.

The framework should remain stable for the lifetime of the project.