# XP and Time Math

The Guildmaster's ledger. Every quest's XP value, every level threshold, every time estimate. Use this file as the single source of truth.

## XP per Quest

```
XP = (sum of primary + secondary stat gains) × 50 × difficulty_multiplier
```

**Difficulty multipliers:**
- Side: 1.0
- Main: 2.0
- Epic: 3.5

**Worked examples:**
- *Add Hard Metrics to Three Bullets* (Side, STR +1, CHA +0.5 = 1.5 total): 1.5 × 50 × 1.0 = **75 XP**
- *Earn One Targeted Cert* (Main, INT +2 = 2 total): 2 × 50 × 2.0 = **200 XP**
- *Lead a Visible End-to-End Project* (Main, STR +3 + WIS +1 + CHA +1 = 5 total): 5 × 50 × 2.0 = **500 XP**
- *Take a 0-to-1 Role* (Epic, DEX +3 + STR +2 + CON +1 = 6 total): 6 × 50 × 3.5 = **1,050 XP**
- *Lead a Multi-Year Initiative* (Epic, CON +3 + STR +1 + WIS +1 = 5 total): 5 × 50 × 3.5 = **875 XP**

Always round to the nearest 25 XP for clean ledger math.

## Level Thresholds

Level 1 starts at 0 XP. Each subsequent level threshold is the previous × 1.3.

| Level | XP to Reach | Cumulative XP |
|-------|-------------|---------------|
| 1 | 0 | 0 |
| 2 | 100 | 100 |
| 3 | 130 | 230 |
| 4 | 169 | 399 |
| 5 | 220 | 619 |
| 6 | 286 | 905 |
| 7 | 372 | 1,277 |
| 8 | 483 | 1,760 |
| 9 | 628 | 2,388 |
| 10 | 817 | 3,205 |
| 11 | 1,062 | 4,267 |
| 12 | 1,380 | 5,647 |
| 13 | 1,794 | 7,441 |
| 14 | 2,332 | 9,773 |
| 15 | 3,032 | 12,805 |
| 16 | 3,941 | 16,746 |
| 17 | 5,124 | 21,870 |
| 18 | 6,661 | 28,531 |
| 19 | 8,659 | 37,190 |
| 20 | 11,257 | 48,447 |

All values rounded to whole XP.

## Age-Calibrated Baseline

Years of experience set a baseline level. Pushing above the baseline costs more XP.

**Baseline by experience:**
- 0 to 2 years: Level 3
- 3 to 5 years: Level 5
- 6 to 9 years: Level 7
- 10 to 14 years: Level 10
- 15 to 19 years: Level 13
- 20 to 29 years: Level 16
- 30+ years: Level 18

**Over-baseline penalty:** XP cost to reach any level above the baseline is multiplied by 1.5. This caps unrealistic leveling without blocking it.

## Stat Ticks at Level-Up

On every level-up, the adventurer picks one stat to raise by +1. Capped by the age-band ceiling defined in `stat-rubric.md`. If the chosen stat is already at the ceiling, the Guildmaster surfaces the cap and asks for a different pick.

## Adventurer-Hours Normalization

Quest effort fields in `quest-templates.md` use ranges like "3-6 months" or "1-2 hours." For Quest Map math, normalize to **adventurer-hours**: realistic focused-work hours, not best-case.

**Conversion rule of thumb:**
- 1 month of part-time quest work = 6 focused hours/week × 4 weeks = **24 adventurer-hours**
- 1 month of full-time-equivalent quest work = 40 hours × 4 weeks = **160 adventurer-hours**

Default to part-time conversion unless the quest description implies full-time (sabbatical, dedicated learning sprint, full role change).

**Examples:**
- "3-6 months" Main quest = 72 to 144 hours part-time, midpoint **108 hours**
- "1-2 hours" Side quest = **2 hours**, no range smoothing needed
- "12 weeks" = 12 × 6 = **72 hours**

The Guildmaster always shows the midpoint estimate in the Quest Map table, with the range visible if asked.

## XP from Logged Skills

`/rpg learned <skill>` awards minor XP based on depth:

- Standard skill (a tool, a framework, a technique): **25 XP**
- Cert-grade skill (formal certification, completed course with assessment): **50 XP**
- Domain mastery milestone (degree, fellowship, recognized credential): **100 XP**

The Guildmaster judges depth from how the adventurer describes the skill. When unclear, ask.

## Quest Map Rollups

`/rpg map` computes:
- **XP to next level** = next threshold minus current XP
- **Time to next level** = sum of adventurer-hours across the smallest set of in-progress + planned quests whose combined XP closes the gap
- **Time to long-term goal** = sum of adventurer-hours across all quests (active + planned + long-arc) tagged to the goal
- **Total XP to goal** = sum of XP across the same set

When a quest spans more than one rollup category (e.g., its XP partially closes the level gap), prorate by percent contribution.
