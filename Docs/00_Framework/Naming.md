# Aetherworks Naming Conventions

Version: 1.0.0

Status: Active

Last Update: 2026-07-01

---

# Philosophy

Naming conventions exist to improve readability, maintainability and consistency.

All assets must follow these conventions.

---

# Blueprint Classes

Actor

BP_AW_

Examples

BP_AW_Character

BP_AW_Building

BP_AW_Sawmill

BP_AW_Crusher

---

Actor Component

BPC_AW_

Examples

BPC_AW_Inventory

BPC_AW_Production

BPC_AW_Interaction

---

Widget Blueprint

WBP_AW_

Examples

WBP_AW_Inventory

WBP_AW_Hotbar

WBP_AW_MachineWindow

---

Blueprint Interface

BPI_AW_

Examples

BPI_AW_Interactable

BPI_AW_InventoryOwner

---

Function Library

BFL_AW_

Examples

BFL_AW_Inventory

BFL_AW_Utility

---

Game Mode

BP_AW_GameMode

---

Game State

BP_AW_GameState

---

Player Controller

BP_AW_PlayerController

---

Player State

BP_AW_PlayerState

---

# Data Assets

DA_AW_

Examples

DA_AW_Item

DA_AW_Recipe

DA_AW_Machine

---

Primary Data Assets

PDA_AW_

Examples

PDA_AW_Item

PDA_AW_Recipe

---

# Data Tables

DT_AW_

Examples

DT_AW_Items

DT_AW_Recipes

DT_AW_Buildings

---

# Structs

S_AW_

Examples

S_AW_ItemStack

S_AW_RecipeInput

S_AW_RecipeOutput

---

# Enums

E_AW_

Examples

E_AW_ItemType

E_AW_MachineState

E_AW_InteractionType

---

# Gameplay Tags

AW.

Examples

AW.Item.Resource

AW.Item.Building

AW.Building.Production

AW.Machine.Sawmill

AW.Interaction.Open

---

# Variables

Boolean

bIs

Examples

bIsCrafting

bIsPowered

bIsRunning

---

Capability

bCan

Examples

bCanCraft

bCanInteract

bCanInsertItems

---

Arrays

Plural names

Examples

InventorySlots

InputSlots

OutputSlots

ConnectedMachines

Recipes

Players

---

Maps

Suffix Map

Examples

RecipeMap

InventoryMap

TagMap

---

Sets

Suffix Set

Examples

UnlockedRecipesSet

ResearchSet

---

# Functions

Prefix

F_

Examples

F_AddItem

F_RemoveItem

F_StartProduction

F_StopProduction

---

Pure Functions

Still use F_

Examples

F_CanAddItem

F_IsFull

F_IsEmpty

---

# Events

Prefix

EV_

Examples

EV_BeginProduction

EV_EndProduction

EV_OpenMachine

---

# Event Dispatchers

Prefix

ED_

Examples

ED_OnInventoryChanged

ED_OnRecipeChanged

ED_OnMachineStateChanged

---

# Networking

Server RPC

Server_

Examples

Server_AddItem

Server_SetRecipe

Server_StartProduction

---

Client RPC

Client_

Examples

Client_OpenMachine

Client_CloseMachine

---

Multicast RPC

Multicast_

Examples

Multicast_PlayEffect

Multicast_PlayAnimation

---

# Categories

Core

Inventory

Inventory|Queries

Inventory|Modification

Inventory|Transfer

Inventory|Validation

Inventory|Debug

Production

Production|Recipes

Production|Crafting

Production|Validation

Interaction

Networking

UI

Debug

---

# Widget Variables

Prefix

UI_

Examples

UI_InventoryGrid

UI_ProgressBar

UI_RecipeList

---

# Graph Comments

Validation

Replication

Inventory Modification

Production Logic

UI Refresh

Initialization

Cleanup

Networking

Debug

---

# Comments

Every function must contain a description.

Bad

Add Item

Good

Attempts to add an item stack into the inventory.

Returns remaining quantity if the inventory becomes full.

---

# Asset Naming

Meshes

SM_

Materials

M_

Material Instances

MI_

Textures

T_

Niagara

NS_

Animations

ABP_

Skeleton

SK_

Audio

SFX_

Music

MUS_

Icons

ICON_

---

# Golden Rule

If two developers create the same asset independently,
they should choose exactly the same name.