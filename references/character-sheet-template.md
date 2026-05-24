# Character Sheet Template

Use this skeleton when writing the combined .md file. Fill what you have. Omit any subsection where there is no source data. Keep tavern voice in the flavor text, keep numbers and tables scannable.

Banned: em-dash (—), en-dash (–). Use commas, colons, parens, or new sentences.

---

```
# {Adventurer Name}, {Class Title} of {Domain}

*A character sheet, scouted from the parchment they call a resume.*

## Identity
- **Name**: {name}
- **Current Title**: {title}
- **Location**: {city, region}
- **Age / Life Stage**: {age} ({Apprentice / Journeyman / Veteran / Sage})
- **Contact**: {email, links}

## Class
- **Primary**: {Class} ({one-sentence archetype})
- **Multi-class** (if applicable): {Second Class} ({why})

## Level and XP
- **Level**: {N} (based on {years} years of experience, age-calibrated)
- **XP to next level**: {short narrative line, e.g. "one major shipped initiative away from Level 8"}
- **Status flags** (if applicable): Inflation Debuff / Reborn / Wandering

## Stats
| Stat | Score | Modifier | One-line Justification |
|------|-------|----------|------------------------|
| STR  | {N}/20 | {+/-N} | {evidence} |
| DEX  | {N}/20 | {+/-N} | {evidence} |
| CON  | {N}/20 | {+/-N} | {evidence} |
| INT  | {N}/20 | {+/-N} | {evidence} |
| WIS  | {N}/20 | {+/-N} | {evidence} |
| CHA  | {N}/20 | {+/-N} | {evidence} |

## Vitals
- **HP (Burnout Resistance)**: {N}/{Max} ({one-line reason from role intensity signals})
- **MP (Creative Reserve)**: {N}/{Max} ({one-line reason from creative output signals})

## Resume Rarity Tier
**{Common / Uncommon / Rare / Epic / Legendary}** ({one-line reason: polish, uniqueness, signal density})

## Equipped Inventory
- **Certifications**: {list, omit if none}
- **Tools**: {list, omit if none}
- **Languages (Programming)**: {list, omit if none}
- **Languages (Human)**: {list, omit if none}
- **Frameworks**: {list, omit if none}

## Skill Tree
{Nested list of hard skills with prereqs shown by indentation. Example:
- Backend Engineering
  - Distributed Systems
    - Kafka
  - APIs
    - REST
    - GraphQL
- ML
  - PyTorch
}

## Active Buffs
- **{Buff name}**: {+N {stat}} ({why})

## Active Debuffs
- **{Debuff name}**: {-N {stat}} ({why, named not judged})

---

# Boss Scouting Report: {Target Role} at {Company or "Unknown"}

*The dungeon ahead, mapped from the job description.*

## Boss Stat Thresholds
| Stat | Boss Requires | One-line Reasoning |
|------|---------------|--------------------|
| STR  | {N}/20 | {from JD signal} |
| DEX  | {N}/20 | {from JD signal} |
| CON  | {N}/20 | {from JD signal} |
| INT  | {N}/20 | {from JD signal} |
| WIS  | {N}/20 | {from JD signal} |
| CHA  | {N}/20 | {from JD signal} |

## Stat Gap Table
| Stat | Adventurer | Boss | Gap |
|------|------------|------|-----|
| STR  | {N} | {N} | {+/-N} |
| DEX  | {N} | {N} | {+/-N} |
| CON  | {N} | {N} | {+/-N} |
| INT  | {N} | {N} | {+/-N} |
| WIS  | {N} | {N} | {+/-N} |
| CHA  | {N} | {N} | {+/-N} |

## Boss Notes
- **Dealbreakers**: {must-haves the JD names}
- **Nice-to-haves**: {bonus signals}
- **Hidden signals**: {culture, team size, stage, anything between the lines}

---

# Quest Board

*Quests ranked by stat-gain-per-effort, weighted toward the largest gaps.*

## Side Quests (Ranked)
1. **{Quest Name}** ({effort}, {primary gain}, {secondary gain})
   - Why: {one line tying to the boss}
   - Prereqs: {list}
2. **{Quest Name}** (...)
3. **{Quest Name}** (...)

## Main Quests (Ranked)
1. **{Quest Name}** ({effort}, {primary gain}, {secondary gain})
   - Why: {one line tying to the boss}
   - Prereqs: {list}
2. **{Quest Name}** (...)

---

# Adventurer's Choice

*Filled in after Phase 4.*

- **Stats chosen to grind**: {list, e.g. CHA, INT}
- **Why**: {one or two sentences, may be the adventurer's reason or the expert recommendation they confirmed}
- **Confirmed forge plan**:
  - {bullet on what the forged resume will emphasize}
  - {bullet on what gets cut or quieted}
  - {bullet on format and any easter-egg request}
```
