# Quest Map Template

The skeleton for `/rpg map` output. Written to the **Quest Map Snapshot** section of the campaign file. Chat output is one paragraph + a link to the file, never the full map inline.

The map MUST contain both views:
1. **Timeline** (ASCII Gantt, month-by-month)
2. **Table** (sortable columns)

Plus a Summary block at the top, an XP Trajectory list, and a Notes section for capacity and prereq warnings.

---

## Full Template

```markdown
# Quest Map, {Adventurer Name}

*Rendered {YYYY-MM-DD}. Refreshed on any /rpg log, /rpg learned, or /rpg map.*

## Summary

- **Level**: {N}  |  **XP**: {current} / {next-threshold} ({percent}% to Level {N+1})
- **Active Quests**: {N}  |  **Planned**: {N}  |  **Long-Arc**: {N}
- **Estimated time to Level {N+1}**: {weeks} weeks (≈ {hours} adventurer-hours remaining)
- **Estimated time to Long-Term Goal**: {months} months (across {N} quests, {XP} XP)
- **Guildmaster's pick for next quest**: *{Quest Name}* ({why: highest XP-per-hour against current largest stat gap})

---

## Timeline

*Month-by-month view from today forward. Today is marked with ▼.*
*Bar legend: ░ planned, ▓ in progress, █ completed-this-period.*

```
                  {Year-1}                            {Year-2}
        {M1} {M2} {M3} {M4} {M5} {M6} {M7} {M8} {M9} {M10} {M11} {M12}
Today    ▼
Q-01    ▓▓▓░░                                                    {Quest Name} ({Tier}, {Status})
Q-02    ▓▓▓▓▓▓                                                   {Quest Name} ({Tier}, {Status})
Q-03        ░░░░                                                 {Quest Name} ({Tier}, {Status})
Q-04           ░░░░░░░░░░░░                                      {Quest Name} ({Tier}, {Status})
Q-05                  ░░░░░░░░                                   {Quest Name} ({Tier}, {Status})
Q-06                           ░░░░░░░░░░░░░░░░░░░░              {Quest Name} ({Tier}, {Status})
```

*Bar width = quest duration in months. Bars start in the column for the planned start month.*

---

## Quest Table

| #    | Quest                              | Tier  | Status       | Effort (hrs) | Time Est | XP   | Stat Gains              | Prereqs            | ETA Complete |
|------|------------------------------------|-------|--------------|--------------|----------|------|-------------------------|--------------------|--------------|
| Q-01 | {Quest Name}                       | Side  | In Progress  | {N}          | {N wk}   | {N}  | {STR +N, CHA +N}        | {list}             | {YYYY-MM-DD} |
| Q-02 | {Quest Name}                       | Side  | In Progress  | {N}          | {N wk}   | {N}  | {CHA +N}                | {list}             | {YYYY-MM-DD} |
| Q-03 | {Quest Name}                       | Side  | Planned      | {N}          | {N wk}   | {N}  | {INT +N, CHA +N}        | {list}             | {YYYY-MM-DD} |
| Q-04 | {Quest Name}                       | Main  | Planned      | {N}          | {N mo}   | {N}  | {STR +N, WIS +N, CHA +N}| {list}             | {YYYY-MM-DD} |
| Q-05 | {Quest Name}                       | Main  | Planned      | {N}          | {N mo}   | {N}  | {DEX +N, INT +N}        | {list}             | {YYYY-MM-DD} |
| Q-06 | {Quest Name}                       | Epic  | Long-Arc     | {N}          | {N mo}   | {N}  | {DEX +N, STR +N, CON +N}| {list}             | {YYYY-MM-DD} |

*Sort hint: as listed = chronological by ETA. Re-sort by XP or Effort if you want a different view.*

---

## XP Trajectory

Walking the quests in order:
- Complete {Q-01} + {Q-02} → {running XP} XP (Level {N}, {percent}% to {N+1})
- Add {Q-03} → {running XP} XP (**Level {N+1}**, +1 stat tick available)
- Add {Q-04} → {running XP} XP (Level {N+2})
- Through {Q-06} → {running XP} XP (Level {N+M}, Long-Term Goal in reach)

---

## Notes

- *(capacity warning if two quests overlap in time)* Q-04 and Q-05 overlap by {N} months. Check capacity. Guildmaster recommends staggering.
- *(prereq blocker)* Q-06 prereqs not met until Q-04 completes ({reason}).
- *(stale quest)* Q-03 has been Planned for {N} months without a start. Demote, defer, or commit.
- *(goal alignment)* Q-{N} drifts from current Long-Term Goal. Consider re-anchoring.
```

---

## Rendering Rules

1. **Quest IDs**: assigned in chronological order by planned start date (Q-01 = next to start, Q-02 = after that, etc.). Re-number on every `/rpg map` run so IDs always reflect current order.
2. **Timeline width**: cover from today through the latest ETA in the campaign. Minimum 6 months, maximum 36 months (anything longer compresses to "→" with a note).
3. **Bar characters**: exactly `░` for planned, `▓` for in progress, `█` for completed inside the visible window. Never use other characters.
4. **Today marker**: `▼` always in the row labeled "Today", positioned at the current month column.
5. **Quest Name truncation**: in the timeline, quest names are right-aligned after the bar. Truncate to 50 characters with `...` if needed.
6. **Empty Map**: if no quests exist yet, render the Summary block + a tavern-voice line: *"The map is bare, adventurer. No quests sketched yet. Add some via /rpg learned, scout a Boss, or set a long-term goal with /rpg goal."*
7. **No Long-Term Goal**: replace "Estimated time to Long-Term Goal" line with "Long-Term Goal: not set. Use /rpg goal to anchor the long arc."
8. **No em-dashes or en-dashes anywhere**. Use commas, colons, parens, or new sentences.

---

## Worked Mini-Example

For an adventurer at Level 5 with 340 XP (619 to reach Level 6, so 55% there), 2 in-progress quests + 4 planned + 2 long-arc, the Summary line reads:

`**Level**: 5  |  **XP**: 340 / 619 (55% to Level 6)`

The "Guildmaster's pick" is computed by taking each in-progress + planned quest, dividing its XP by its effort hours, and surfacing the highest score AMONG quests whose primary stat gain matches the adventurer's current largest gap-to-boss (if a Boss is scouted) or largest gap-to-goal (if no Boss but a Long-Term Goal is set).
