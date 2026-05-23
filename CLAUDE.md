# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is an **Obsidian vault** for a homebrew TTRPG campaign (D&D 5e) called **Opus** — a dark, oppressive magical megacity. All content is in Spanish. The vault is edited through the Obsidian app; there are no build steps, tests, or scripts.

## Vault Structure

```
Worldbuilding/     ← Lore: city, districts, factions, mechanics
Campaign/
  Sesiones/        ← Session notes (use Template Sesiones.md)
  Sesiones/Opus 1.0/  ← Archived sessions from the first party
  PCs/             ← Player characters (Opus 1.0/ = old party, Opus 2.0.md = new)
  People/          ← NPCs, influential mediators (by grade), homebrew enemies
01_EVENTOS/        ← Upcoming or ongoing events
99_BANCO/          ← Reference tables, threat levels, misc mechanics
.obsidian/         ← Obsidian config and plugins (do not edit manually)
```

## Core World Lore

**Opus** is a continent-sized magical city enclosed in obsidian walls. Its ~70 million residents cannot leave. Divided into **12 Districts**, each governed by an **Ala** (Wing) that possesses a **Singularidad** — a reality-altering anomaly unique to that district. Social strata: Nidos (wealthy) → Afueras (middle) → Callejuelas (desperate).

**Mediadores** are licensed contractors who handle tasks civilians cannot (combat, assassination, negotiation, investigation). Managed by **Asociación Hana** (Association 1). Ranked **Grade 9** (weakest) through **Grade 1** (capable of eliminating a City Star). Above Grade 1 are the **Colores** (Colors) — elite mediators assigned a color title, the only ones with true freedom, though they cannot refuse the title.

**The 12 Associations** each have a number-name and specialty:
- 01 Hana ⚖️ — official oversight of mediators  
- 02 Zwei 🛡️  
- 03 Tris 🤝  
- 04 Shin 🩸  
- 05 Quinque  
- 06 Liu 🕵️  
- 07 Siebte 📊  
- 08 Asto ⚔️  
- 09 Neuf 🧪  
- 10 Desyat ⚕️  
- 11 Oufi 🚂  
- 12 Douze 💡  

**La Cabeza** is the supreme governing body above the Alas. **Singularidades** (Singularities) are anomalous entities/phenomena tied to each district. **Anormalidades** (Abnormalities) are dangerous entities that mediators may be assigned to neutralize.

## Campaign State

- **Opus 1.0** — First party. Sessions 001–018 archived in `Campaign/Sesiones/Opus 1.0/`. Party disbanded/retired after their arc concluded.
- **Opus 2.0** — New party at Level 5, just starting the **Examen 101 de Mediador** (101st Mediator Exam) in Los Callejones de Mercurio. Session 020 is the most recent. New PCs are documented in `Campaign/PCs/Opus 2.0.md`.

The transition rationale is in [Decisión Opus going forward.md](Decisión%20Opus%20going%20forward.md): the group changed characters while keeping the world and its consequences.

## Session Note Format

All sessions follow [Campaign/Template Sesiones.md](Campaign/Template%20Sesiones.md):

```markdown
## Resources
## Session Summary
## Housekeeping
## Recap
## Strong Start
> [!scene] **Strong Start**
## Scenes
> [!scene] **Escena N: [Título]**
> **Descripción:** ...
> **Opciones:**
> - [ ] ...
> **Objetivo:**
## Secrets and Clues
- [ ] pista
## Loot
- [ ] objeto
## Personajes importantes
> [!abstract] **NPC**
> **Descripción:** ...
> **Motivación:** ...
## Log
```

The `[!scene]` and `[!abstract]` callout syntax is rendered by the **obsidian-admonition** plugin.

## NPC File Format

Influential mediator files (in `Campaign/People/Mediadores influyentes/Grado N/`) typically contain:
- An `[!info]` callout with race, class, grade, personality, appearance
- Stats table (STR/DEX/CON/INT/WIS/CHA + skill bonuses)
- Equipment with special item descriptions
- Secrets and Clues checklist (`- [ ]`)

## YAML Frontmatter Schema

Every note should have frontmatter for Obsidian Dataview and graph coloring:

```yaml
---
type: <type>
campaign: <campaign>
tags: [<tag1>, <tag2>]
---
```

**`type` values:** `hub`, `npc`, `pc`, `session`, `district`, `association`, `ala`, `singularidad`, `enemy`, `event`, `faction`, `worldbuilding`, `reference`, `template`

**`campaign` values:** `opus-1` (sessions 001–018, first party), `opus-2` (session 020+, new party), `opus-general` (world lore that spans both)

**`tags` conventions:**
- Sessions: `[session, opus-1]` or `[session, opus-2]`
- NPCs: `[npc, opus-1]` or `[npc, mediador, grado-3]` etc.
- PCs: `[pc, opus-1]` or `[pc, opus-2]`
- Districts: `[district, <name>]`
- Enemies: `[enemy, anormalidad, opus-1]` etc.

**Hub link rule:** Every non-hub note should link to its parent hub in the body (not just frontmatter), so the Obsidian graph creates visible edges. Examples:
- Sessions → `*[[Opus 1.0]] · Sesión 00X*` or `*[[Opus 2.0]] · Sesión 020*`
- Influential mediators → `*[[Los Mediadores]] · Grado N*`
- PCs → `*[[Opus 1.0]] · PC*`

## Internal Links

Obsidian uses `[[Note Name]]` for internal links. When creating or editing notes, use this wikilink syntax to reference other documents. Link targets should match the filename (without extension). Many links currently use a mix of `[[Note Name]]` and `[Display Text]([[Note Name]])` syntax — both are valid.

## Installed Obsidian Plugins

- **obsidian-admonition** — `[!scene]`, `[!abstract]`, `[!info]`, `[!example]` callout blocks
- **obsidian-5e-statblocks** — D&D 5e stat block rendering
- **initiative-tracker** — combat initiative tracking
- **obsidian-dice-roller** — inline dice rolls
- **dataview** — query-based dynamic views
- **calendarium** — in-world calendar
- **fantasy-name** — name generation
