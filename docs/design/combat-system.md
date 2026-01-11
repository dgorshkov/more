# Combat System

## Overview

Combat is turn-based and token-driven, inspired by Darkest Dungeon 2. There is no grid or spatial positioning — tactical depth comes from ship abilities, token management, and initiative order.

---

## Fleet Limits

| Side | Max Ships per Encounter |
|------|-------------------------|
| Player | 5 |
| Enemy | 10 |

The player selects which ships to deploy from their available fleet before each encounter.

---

## Ship Classes

| Class | Size | Initiative | Actions/Turn | Notes |
|-------|------|------------|--------------|-------|
| **Gunship** | Small | Fastest | Most | High risk, high tempo |
| **Destroyer** | Medium | Medium | Medium | Balanced generalist |
| **Cruiser** | Large | Slowest | Fewest | Durable, never permanently lost |

### Initiative
Smaller ships act earlier in the turn. All ships (player and enemy) are interleaved in a single initiative order, similar to Battletech (Harebrained Schemes).

### Actions
Smaller ships have more actions per turn, allowing for rapid token manipulation or multiple attacks. Larger ships compensate with stronger individual abilities.

---

## Token System

Ships accumulate tokens representing their current state. Tokens are the core tactical currency.

### Token Types

| Type | Description | Examples |
|------|-------------|----------|
| **Positive** | Buffs and advantages | Shield Boost, Targeting Lock, Morale High |
| **Negative** | Debuffs and vulnerabilities | Hull Breach, Systems Offline, Crew Panic |
| **Special** | Situational states | Close Proximity, Marked for Death, Infection Risk |

### Token Mechanics
- Tokens can **stack** (multiple of the same type)
- Tokens can **expire** after a number of turns
- Tokens can **convert** (e.g., 3 Stress → 1 Breakdown)
- Abilities may **consume** tokens for enhanced effects
- Some tokens trigger effects at turn start/end

### Close Proximity
A special token representing a ship engaged at close range with the enemy. Ships with this token:
- May use melee-equivalent abilities
- Are vulnerable to certain attacks
- Cannot easily disengage

---

## Damage & Death

### Health
Each ship has an HP pool. Damage reduces HP.

### Critical Damage State
When a ship reaches 0 HP:
1. It enters **Critical Damage** state
2. The ship can still act normally
3. Any further damage destroys the ship

### Death Behavior by Class

| Class | At Critical | On Death |
|-------|-------------|----------|
| **Gunship** | Can still act | Destroyed permanently |
| **Destroyer** | Can still act | Destroyed permanently |
| **Cruiser** | Can still act | Exits combat damaged, stays in fleet, repairable |

Cruisers are strategic assets that can always be recovered, though repairs cost resources and time.

---

## Fighters & Bombers

Fighters and bombers are **not separate units**. They are implemented as abilities on larger ships (cruisers and destroyers).

Example abilities:
- **Launch Interceptors** — Apply "Intercepted" token to enemy, reducing their accuracy
- **Bomber Strike** — Deal direct damage, apply "Hull Breach" token
- **Fighter Screen** — Apply "Protected" token to an ally

This keeps combat focused on ship-to-ship decisions while preserving the fleet fantasy.

---

## Enemy Types

All enemy types use the same combat system (classes, tokens, initiative).

| Type | Description |
|------|-------------|
| **Infected Ships** | Human vessels corrupted by the Beast |
| **Pure Beast** | Alien-origin ships, fully non-human |
| **Hostile Humans** | Empire, Republic, or Commonwealth ships (see [Worldbuilding](../narrative/worldbuilding.md)) |
| **Hostile Synths** | Circle vessels or rogue AI (see [Worldbuilding](../narrative/worldbuilding.md)) |

Enemy encounters can mix types, creating varied tactical challenges.

---

## Turn Structure

1. **Initiative Phase** — Determine turn order (smallest ships first)
2. **Action Phase** — Ships act in initiative order, spending actions
3. **End Phase** — Resolve end-of-turn token effects, check for victory/defeat

### Victory Conditions
- Destroy or rout all enemy ships
- Survive a set number of turns (escape scenarios)
- Achieve mission objective

### Defeat Conditions
- All player ships destroyed
- Mission-specific failure conditions
