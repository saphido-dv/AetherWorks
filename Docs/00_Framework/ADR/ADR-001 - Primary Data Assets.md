# ADR-001 - Primary Data Assets

Status: Accepted

Date: 2026-07-01

---

# Context

Every gameplay system needs to reference items.

Several approaches were considered:

- Data Tables
- Blueprint Objects
- Data Assets
- Primary Data Assets

---

# Decision

All items are implemented as Primary Data Assets.

Each gameplay item owns its own asset.

Examples:

PDA_AW_Item_WoodLog

PDA_AW_Item_Stone

PDA_AW_Item_Plank

---

# Rationale

Primary Data Assets provide:

- Better scalability
- Strong asset references
- Asset Manager integration
- Cleaner organization
- Easy future expansion

Data Tables remain useful for bulk data,
but individual gameplay objects are better represented as assets.

---

# Consequences

Items become independent assets.

Framework systems reference PDA_AW_Item directly.

No Item IDs.

No string comparisons.

No enum-based item identification.

Gameplay Tags describe the item.

Primary Asset IDs identify the asset.