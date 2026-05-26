# Campaign File Template

The persistent campaign tome. One per adventurer. Lives at `~/Documents/Claude/Projects/RPG/{slug}-campaign.md` (or wherever `RPG_CAMPAIGN_DIR` points).

Never goes in the GitHub repo. Never inlined in chat.

The Guildmaster reads this file at the start of every session, mutates it during the session, writes it back at the end. Atomic writes only (write to a temp file, rename on success).

## Slug Rule

`slug = lowercase(first_name) + "-" + lowercase(last_name)`, with spaces and special chars stripped. Example: "Çanti Widyadhari" becomes `canti-widyadhari-campaign.md`. If only one name is provided, use it alone. Collisions: append a digit (`canti-widyadhari-2-campaign.md`).

## Schema

```markdown
# {Adventurer Name}, Campaign Log

> *A living chronicle, tended by the Guildmaster. Tavern voice throughout.*

**Campaign Started**: {YYYY-MM-DD}
**Last Updated**: {YYYY-MM-DD HH:MM}
**Schema Version**: 0.2.0
**Current Path**: {Boss Fight Arc / Professional Development Arc / Mixed}

---

## Long-Term Goal

- **Target**: {one-line goal, e.g. "Staff PM at a Series B climate company by 2028"}
- **Set**: {YYYY-MM-DD}
- **Time horizon**: {N} months
- **Status**: {Active / Paused / Achieved / Revised}

*(If no goal set: leave block with "Target: not set" and a one-line tavern prompt to set one via /rpg goal.)*

---

## Active Boss

- **Name**: {Role at Company, or "None scouted"}
- **Scouted**: {YYYY-MM-DD}
- **See**: Boss Scouting Report below for the full breakdown

*(If no Boss: this block reads "None scouted. Use /rpg with a JD to scout one.")*

---

## Character Sheet

*(Full structure from `references/character-sheet-template.md`. Kept current with every session. Includes Identity, Class, Level and XP, Stats, Vitals, Rarity Tier, Equipped Inventory, Active Buffs, Active Debuffs. The "Skill Tree" subsection is a pointer to the Living Skill Tree below.)*

### Identity
- **Name**: {name}
- **Current Title**: {title}
- **Location**: {city, region}
- **Age / Life Stage**: {age} ({Apprentice / Journeyman / Veteran / Sage})
- **Contact**: {email, links}

### Class
- **Primary**: {Class} ({one-sentence archetype})
- **Multi-class** (if applicable): {Second Class}

### Level and XP
- **Level**: {N}
- **XP**: {current} / {next-threshold} ({percent}%)
- **XP to next level**: {N}
- **Baseline (age-calibrated)**: Level {N} (over-baseline penalty: {applies / does not apply})
- **Status flags**: {Inflation Debuff / Reborn / Wandering, if any}

### Stats
| Stat | Score | Modifier | Justification |
|------|-------|----------|---------------|
| STR  | {N}/20 | {+/-N} | {evidence} |
| DEX  | {N}/20 | {+/-N} | {evidence} |
| CON  | {N}/20 | {+/-N} | {evidence} |
| INT  | {N}/20 | {+/-N} | {evidence} |
| WIS  | {N}/20 | {+/-N} | {evidence} |
| CHA  | {N}/20 | {+/-N} | {evidence} |

### Vitals
- **HP (Burnout Resistance)**: {N}/{Max} ({reason})
- **MP (Creative Reserve)**: {N}/{Max} ({reason})

### Resume Rarity Tier
**{Common / Uncommon / Rare / Epic / Legendary}** ({one-line reason})

### Equipped Inventory
- **Certifications**: {list, omit if none}
- **Tools**: {list, omit if none}
- **Languages (Programming)**: {list, omit if none}
- **Languages (Human)**: {list, omit if none}
- **Frameworks**: {list, omit if none}

### Active Buffs
- **{Buff Name}**: {+N stat} ({why}, {date acquired})

### Active Debuffs
- **{Debuff Name}**: {-N stat} ({why, named not judged}, {date acquired})

---

## Living Skill Tree

*(Rendered per `references/skill-tree-taxonomy.md`. Each skill: added date, last touched, Rusting flag if 12+ months stale.)*

- {Domain}
  - {Branch} (last touched: {date})
    - {Skill} (added {date}, touched {date})
    - {Skill} (added {date}, touched {date}) ⚠ Rusting in {N} months

*(Omit empty branches and empty domains.)*

---

## XP Ledger

| Date | Event | XP Delta | Running Total | Level After |
|------|-------|----------|---------------|-------------|
| {YYYY-MM-DD} | Campaign seeded | 0 | 0 | {N} |
| {YYYY-MM-DD} | Quest done: {Quest Name} | +{N} | {N} | {N} |
| {YYYY-MM-DD} | Skill learned: {Skill} | +{N} | {N} | {N} |
| {YYYY-MM-DD} | **Level Up to {N+1}** | 0 | {N} | {N+1} |

---

## Quest Log

### Completed
- **{Quest Name}** ({Tier}), completed {YYYY-MM-DD}, +{XP}, applied {stat ticks}

### In Progress
- **{Quest Name}** ({Tier}), started {YYYY-MM-DD}, target {YYYY-MM-DD}, {hours logged}/{total estimate} hrs

### Planned (next 90 days)
- **{Quest Name}** ({Tier}), earliest start {YYYY-MM-DD}, prereqs met: {yes / no, with details}

### Long-Arc (90+ days out)
- **{Quest Name}** ({Tier}), anchored to {goal milestone}

---

## Boss Scouting Report

*(Latest scouted Boss in full. Empty block if none.)*

### Boss Stat Thresholds
| Stat | Boss Requires | Reasoning |
|------|---------------|-----------|
| STR  | {N}/20 | {from JD} |
| DEX  | {N}/20 | {from JD} |
| CON  | {N}/20 | {from JD} |
| INT  | {N}/20 | {from JD} |
| WIS  | {N}/20 | {from JD} |
| CHA  | {N}/20 | {from JD} |

### Stat Gap Table
| Stat | Adventurer | Boss | Gap |
|------|------------|------|-----|
| STR  | {N} | {N} | {+/-N} |
| DEX  | {N} | {N} | {+/-N} |
| CON  | {N} | {N} | {+/-N} |
| INT  | {N} | {N} | {+/-N} |
| WIS  | {N} | {N} | {+/-N} |
| CHA  | {N} | {N} | {+/-N} |

### Boss Notes
- **Dealbreakers**: {list}
- **Nice-to-haves**: {list}
- **Hidden signals**: {culture, team size, stage, between-the-lines}

---

## Quest Map Snapshot

*(Latest output of `/rpg map`. Regenerated each time `/rpg map` runs. See `references/quest-map-template.md` for structure.)*

*(Empty until first /rpg map call.)*

---

## Adventurer's Choice

*(Latest confirmed stat-grind plan. Updated whenever the adventurer confirms a plan in Phase 4 or sets new priorities.)*

- **Stats chosen to grind**: {list}
- **Why**: {one or two sentences}
- **Confirmed forge plan** (if Boss Fight Arc):
  - {what the forged resume emphasizes}
  - {what gets cut or quieted}
  - {format and easter-egg flag}

---

## Session History

| Session | Date | Mode | Summary |
|---------|------|------|---------|
| 001 | {YYYY-MM-DD} | seed | Migrated from v0.1.0 sheet (or first scan) |
| 002 | {YYYY-MM-DD} | /rpg log | Quest done: {Name}, +{XP} |
| 003 | {YYYY-MM-DD} | /rpg learned | {Skill} placed under {Branch}, +{XP} |
| 004 | {YYYY-MM-DD} | /rpg map | Map regenerated, {N} quests visible |
| 005 | {YYYY-MM-DD} | /rpg goal | Goal updated to "{new goal}" |

---

## Reserved for Future Expansion

*(Empty sections held here for v0.3.0+ features. Headings present so future versions can fill in without restructure.)*

### Interview Prep
*(Reserved for v0.3.0)*

### Negotiation Log
*(Reserved for v0.3.0)*

### Party
*(Reserved for v0.3.0: networking contacts, mentors, references)*

### Journal
*(Reserved for v0.3.0: tavern confessions, reflection check-ins)*

### Yearly Review
*(Reserved for v0.3.0: end-of-season ritual)*

### HP Watch
*(Reserved for v0.3.0: burnout monitoring)*
```

---

## Write Protocol

1. Read campaign file fully on session start.
2. Compute all mutations in memory based on the session's actions.
3. Stamp `Last Updated` with current timestamp.
4. Write to a temp file at the same path with `.tmp` suffix.
5. Rename `.tmp` to the canonical name (atomic on POSIX).
6. If write fails, surface the error to the adventurer, do NOT leave a partial file.

## Read Protocol

1. Resolve canonical path.
2. If file exists, read fully and parse sections by markdown heading.
3. If file is malformed (missing required sections), ask adventurer for permission to repair or rebuild before proceeding.
