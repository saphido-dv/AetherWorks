# Aetherworks Folder Structure

Version: 1.0.0

Status: Active

Last Update: 2026-07-01

---

# Philosophy

Folders exist to improve discoverability.

Assets should be easy to find without requiring prior knowledge of the project.

Every asset belongs to exactly one module.

---

# Root Structure

Content/

Aetherworks/

Docs/

---

# Content Structure

Content
└── Aetherworks

    Art
    Audio
    Blueprints
    Data
    FX
    Maps
    UI
    Developer

---

# Art

Art/

Materials

MaterialFunctions

MaterialInstances

Textures

Icons

Meshes

Animations

VFX

---

# Audio

Audio/

Music

Ambient

SFX

UI

Machines

Footsteps

Voices

---

# Blueprints

Blueprints/

Core

Character

Components

Interfaces

Items

Interaction

Buildings

Production

Machines

Logistics

Power

SaveSystem

Debug

Developer

---

# Core

Core/

BP_AW_GameMode

BP_AW_GameState

BP_AW_PlayerController

BP_AW_PlayerState

FunctionLibraries

Subsystems

Utilities

---

# Character

Character/

Player

Movement

Equipment

Abilities

Components

---

# Components

Components/

Inventory

Production

Interaction

Power

Health

Storage

Logistics

---

# Interfaces

Interfaces/

Interaction

Inventory

Machines

Power

Production

---

# Items

Items/

DataAssets

Definitions

Icons

Recipes

Categories

---

# Buildings

Buildings/

Base

Production

Storage

Power

Decoration

Infrastructure

---

# Production

Production/

Recipes

Machines

Components

States

---

# Machines

Machines/

Sawmill

Crusher

Smelter

Assembler

Generator

Refinery

Common

---

# Logistics

Logistics/

Conveyors

Inserters

Pipes

Containers

Vehicles

Drones

---

# Power

Power/

Generators

Consumers

Networks

Batteries

---

# Save System

SaveSystem/

Profiles

World

Player

Settings

---

# Data

Data/

DataAssets

DataTables

Structs

Enums

GameplayTags

Curves

Configs

---

# Data Assets

DataAssets/

Items

Recipes

Machines

Buildings

Research

Power

---

# Data Tables

DataTables/

Items

Recipes

Buildings

Localization

---

# Structs

Structs/

Inventory

Production

Interaction

Networking

Power

---

# Enums

Enums/

Items

Machines

Power

UI

---

# Gameplay Tags

GameplayTags/

Definitions

Documentation

---

# UI

UI/

Common

HUD

Inventory

Machines

Production

Interaction

Power

Menus

Settings

Debug

---

# FX

FX/

Niagara

Particles

Materials

MachineEffects

Environment

---

# Maps

Maps/

Persistent

Gameplay

Test

Developer

Benchmark

---

# Developer

Developer/

TestMaps

Experimental

Sandbox

Temporary

---

# Golden Rules

Never place assets directly under Aetherworks.

Always use folders.

Avoid generic names.

Bad:

Blueprints/

Stuff/

Assets/

Misc/

Things/

Good:

Production/

Machines/

Storage/

Interaction/

Power/

---

# Example

Correct

Blueprints/

Components/

Inventory/

BPC_AW_Inventory

Incorrect

Blueprints/

BPC_AW_Inventory

---

# Long Term Goal

After two years of development,
a developer should still be able to locate any asset within seconds.