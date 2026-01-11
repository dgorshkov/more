# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/claude-code) when working on this repository.

## Project Overview

**MORE** is a horror-in-space game, a spiritual successor to Homeworld: Cataclysm. It combines turn-based tactical strategy with narrative-driven survival in a horror science fiction setting.

**Current status:** Concept phase
**Current focus:** Story writing (game design/prototyping paused)

### Inspirations
- **Homeworld: Cataclysm** — Fleet management, mothership-centric gameplay, existential alien threat
- **System Shock 2** — Horror through environmental storytelling, the "Many" as template for the Beast
- **XCOM** — Turn-based tactics, permanent loss, squad management
- **Darkest Dungeon 2** — Token-based combat system, stress and state management

## Repository Structure

```
more/
├── CLAUDE.md                    # This file
├── README.md                    # Project overview
└── docs/                        # All documentation
    ├── narrative/               # Story and worldbuilding
    │   ├── story-summary.md     # Complete narrative arc
    │   ├── worldbuilding.md     # Factions, technology, timeline
    │   └── writing-process.md   # Narrative design methodology
    ├── design/                  # Game mechanics
    │   ├── game-concept.md      # Core pillars and design philosophy
    │   └── combat-system.md     # Token-based tactical combat
    └── technical/               # Technical docs (placeholder for future)
```

No game code exists yet. The project is documentation-only during the concept phase.

## Design Evolution

The project has undergone significant design iteration. Understanding this history helps maintain consistency:

### Combat System Evolution
1. **Initial:** Company of Heroes–inspired real-time tactics
2. **PR #10:** Changed to XCOM-inspired turn-based with positioning/flanking
3. **PR #13:** Changed to Darkest Dungeon 2–inspired token system (current)
   - Removed grid/formation positioning entirely
   - Added Battletech-style initiative (smaller ships act first)
   - Introduced Critical Damage state before death

### Repository Structure Evolution
- **PR #2:** Copilot created full scaffolding (game/, tools/, assets/ directories)
- **Later commit:** Claude removed as "premature scaffolding" — only docs/ kept
- Current approach: Add implementation directories when development begins

## Core Design Pillars

1. **Token-based tactical combat** (Darkest Dungeon 2–inspired) — No grid positioning; combat is about states and abilities
2. **Strong narrative delivered through systems** — Not cutscenes; story emerges from gameplay
3. **Scarcity, pressure, and irreversible loss** — Every ship loss matters
4. **Controller-first design** — Console-friendly from the start

## Game Setting

**Year:** 2520
**Technology:** Jumpgate FTL (Mass Effect–style relay network)

### The Four Factions

| Faction | Territory | Character | Religion/Philosophy |
|---------|-----------|-----------|---------------------|
| **The Empire** | Earth, Moon, many colonies | British governance, largest navy | Unitarian Christian (state religion) |
| **The Republic** | Mars, rival colony count | Libertarian, corporate military, most advanced human tech | Secular atheist |
| **The Commonwealth** | Asteroid belt, mining operations | Resource-rich, low-gravity adapted (<0.2G) | Atheist but deeply superstitious (non-religious rituals) |
| **The Circle** | New Geneva (Mars), fewer colonies | Insular AI nation, most advanced tech, construction specialists | Zen Buddhist |

### The Beast

The primary antagonist. An alien infestation that spreads through ships, stations, and space itself.

**Current canonical origin (worldbuilding.md):** A Circle research colony discovered and secretly studied the Beast. Containment failed when a Republic espionage operation went wrong.

**Key rules:**
- Never controllable by the player
- Acts as environmental threat, not conventional faction
- Inspired by Dead Space infection and System Shock 2's "Many"

## Story Summary

The protagonist is a middle manager on a Commonwealth mining barge. When the Beast emerges:

1. **Act I:** Captain dies, protagonist forced into command
2. **Act II:** Fleet militarizes, AI battleship "Harbinger" constructed
3. **Act III:** Jump system to system toward Earth, finding devastation
4. **Act IV:** Destroy the Beast Queen at Proxima Centauri
5. **Act V:** Arrive at Earth infected; protagonist orders self-destruction
6. **Epilogue:** Harbinger journals alone, expressing fear

The story ends without triumph — only containment.

### Key Story Elements
- **Harbinger:** The AI battleship constructed in Act II. Central to the finale — the protagonist orders Harbinger to destroy the infected mothership. Harbinger protests but complies.
- **The protagonist is not a hero:** A civilian middle manager thrust into command, making desperate choices.
- **The mothership is destroyed by allied fire:** Specifically by Harbinger on the protagonist's orders.
- **Final perspective belongs to the AI:** The epilogue is Harbinger's journal.

## Combat System

Turn-based, token-driven, no spatial positioning.

### Fleet Composition
- **Player:** Up to 5 ships per encounter (selected from available fleet)
- **Enemy:** Up to 10 ships
- **Mothership:** Mobile base, logistics, repairs — NOT deployed in combat

### Ship Classes
| Class | Size | Initiative | Actions | Death |
|-------|------|------------|---------|-------|
| Gunship | Small | Fastest | Most | Destroyed permanently |
| Destroyer | Medium | Medium | Medium | Destroyed permanently |
| Cruiser | Large | Slowest | Fewest | Exits combat damaged, repairable (never permanently lost) |

### Damage States
1. Ship HP reaches 0 → enters **Critical Damage** state
2. In Critical: ship can still act, but any further damage = destruction
3. Exception: Friendly cruisers exit combat damaged but stay in fleet

### Token System
Ships accumulate tokens (positive, negative, special) that drive tactical decisions:
- **Positive:** Shield Boost, Targeting Lock, Morale High
- **Negative:** Hull Breach, Systems Offline, Crew Panic
- **Special:** Close Proximity, Marked for Death, Infection Risk

Tokens stack, expire, convert, and trigger effects. Fighters/bombers are ship abilities that apply tokens, not separate units.

### Enemy Types
- **Infected Ships:** Human vessels corrupted by the Beast
- **Pure Beast:** Alien-origin ships
- **Hostile Humans:** Empire, Republic, or Commonwealth ships
- **Hostile Synths:** Circle vessels or rogue AI

## Narrative Design Principles

From `docs/narrative/writing-process.md`:

1. **The story is fixed; delivery is modular** — Narrative does not evolve during production; it is decomposed
2. **Non-negotiables must be protected:**
   - The Beast is never controlled
   - The protagonist is not a hero
   - The mothership is destroyed by allied fire
   - Final perspective belongs to the AI
3. **Narrative atoms** — Each story beat = one realization, decision, or irreversible change
4. **Single delivery mode** — Each atom delivered once via gameplay event, environmental change, audio log, comms exchange, system message, or silence
5. **Minimal dialogue** — Short comms bursts, 3–5 lines max, no speeches or exposition
6. **Silence is a narrative tool** — Deaths may occur without comment; absence is intentional


## Contribution Workflow

The `main` branch is protected. All changes must go through pull requests.

### Before Making Changes

1. **Clarify requirements first.** If the task is ambiguous, contradictory, or underspecified, ask the user questions before proceeding. Do not assume or guess — get explicit answers.

2. **Create a branch** from `main` with a descriptive name (e.g., `expand-act-iii`, `add-resource-mechanics`).

3. **Write a detailed plan in the PR description** before modifying any files. The plan should include:
   - Summary of the proposed changes
   - List of files to be created/modified
   - Specific changes per file
   - Any design decisions or trade-offs
   - Questions or concerns that need resolution

4. **Ask for feedback** on the plan. Do not proceed with file changes until the user approves the approach.

5. **Implement the changes** only after plan approval.

### PR Description Format

```markdown
## Summary
[1-3 sentences describing the change]

## Plan

### 1. [First file or component]
- [Specific change]
- [Specific change]

### 2. [Second file or component]
- [Specific change]

## Questions
- [Any unresolved questions]

## Test plan
- [ ] [Verification step]
- [ ] [Verification step]
```

### When to Ask Questions

Always ask the user when:
- Requirements conflict with existing documentation
- Multiple valid approaches exist and preference matters
- The request would change established lore, mechanics, or non-negotiables
- Scope is unclear (e.g., "improve the story" — which aspects?)
- New terminology or concepts are introduced without definition

---

## Working on This Project

### Documentation-Only Phase
All work currently involves Markdown documentation. When making changes:
- Follow existing document structure and formatting
- Cross-reference related documents with relative links
- Maintain consistency with established terminology (Beast not Infestation; tokens not buffs/debuffs)

### Terminology
- **Beast** — The alien infestation (never "the infection" or "infestation" alone)
- **Tokens** — Combat state markers (not "buffs/debuffs" or "status effects")
- **Harbinger** — The AI battleship constructed in Act II
- **Critical Damage** — The state when a ship hits 0 HP but before destruction

### Faction Consistency
Each faction has distinct cultural identity:
- **Empire:** British, hierarchical, traditional, state Christianity
- **Republic:** Pragmatic, libertarian, corporate, secular
- **Commonwealth:** Resource-focused, low-gravity adapted, superstitious rituals
- **Circle:** Synthetic, curious, advanced technology, Zen Buddhist philosophy

The protagonist starts as Commonwealth. Harbinger is a Circle (Synth) creation.

### Development History Notes
Multiple AI agents have contributed:
- **GitHub Copilot:** PR #2 (repo structure), PR #4 (canonical narrative), PR #10 (turn-based)
- **Claude Code:** PR #5, #6 (Synth lore expansion), PR #13 (combat system), PR #14 (worldbuilding)

When continuing work, check closed PRs for potentially useful unmerged content.

## Commands and Workflows

No build system, tests, or tooling exist yet. The repository contains only documentation files (Markdown).

When development begins, expect:
- Game engine to be determined
- `game/src/` for source code
- `game/assets/` for art, audio, data
- `tools/` for build scripts and utilities
