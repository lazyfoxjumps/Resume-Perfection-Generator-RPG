# Campaign Modes

The contract for every `/rpg` sub-command. SKILL.md's Mode Router delegates here. Each mode has: trigger phrases, required args, files to read before responding, sections of the campaign file to mutate, expected chat output shape, and failure modes.

---

## `/rpg` (no args)

**Triggers**: `/rpg`, "rpg my resume", "gamify my resume", etc.

**Args**: none

**Read first**:
- Resolve campaign dir (`RPG_CAMPAIGN_DIR` env var, fallback `~/Documents/Claude/Projects/RPG/`)
- Scan dir for `*-campaign.md`

**Branch**:
- Campaign file exists → run **Returning Adventurer Flow** (see SKILL.md)
- No campaign file, but `*-rpg-sheet.md` in working folder → offer **Migration**
- Neither → run **First-Time Scan with Path Fork**

**Writes**: depends on chosen path.

**Chat output**: greeting + question about visit purpose, or migration prompt, or Phase 1 of first-time scan.

**Failure modes**:
- Multiple campaign files in dir → list them, ask adventurer which one to load
- Campaign file is corrupt/unparseable → ask permission before overwriting, suggest a backup

---

## `/rpg map`

**Triggers**: `/rpg map`, "show my quest map", "render the map", "where am I on the journey"

**Args**: none

**Read first**:
- Campaign file (required, fail with friendly message if missing)
- `references/quest-map-template.md`
- `references/xp-math.md`

**Computes**:
- Summary block: level, XP to next, active/planned/long-arc counts, time to next level, time to long-term goal, top recommended next quest
- Timeline: ASCII Gantt month-by-month from today forward, all active + planned + long-arc quests
- Quest Table: columns Quest, Tier, Status, Effort (hrs), Time Est, XP, Stat Gains, Prereqs, ETA Complete
- XP Trajectory: bullet list showing level changes as quests complete in order
- Notes: capacity warnings (overlapping quests), prereq blockers

**Writes**: replaces the **Quest Map Snapshot** section in the campaign file. Stamps Last Updated.

**Chat output**: one paragraph summary (level, top recommended quest, ETA to goal) + markdown link to campaign file. Never inline the full map.

**Failure modes**:
- No quests planned → render the summary + a "the journey hasn't started yet, adventurer. Add quests via Path B or scout a Boss" prompt
- No long-term goal → render with "ETA to goal: not set. Use /rpg goal to anchor the long arc"

---

## `/rpg log <quest> done`

**Triggers**: `/rpg log "<quest name>" done`, `/rpg done "<quest name>"`, "mark <quest> complete", "I finished <quest>"

**Args**: quest name (string, matched case-insensitively against in-progress and planned quests in the campaign file)

**Read first**:
- Campaign file (required)
- `references/xp-math.md` (for XP and level math)
- `references/skill-tree-taxonomy.md` (for tree regrowth)

**Mutates**:
- Move quest from In Progress (or Planned) to Completed, stamp date
- Award XP to XP Ledger (new row: date, event, +XP, running total, level after)
- Recompute level. If level-up:
  - Apply +1 stat tick (ask adventurer which stat, cap by age ceiling per `stat-rubric.md`)
  - Announce level-up in tavern voice
  - Apply over-baseline penalty if applicable
- Reset Rusting timers on touched branches (cascade up)
- Append Session History row
- Stamp Last Updated

**Chat output**: short tavern-voice congrats, XP awarded, new total, level status, any debuffs cleared. Link to updated campaign file.

**Failure modes**:
- Quest name doesn't match → list close matches, ask
- Quest already Completed → ask if this is a re-log or a duplicate
- Quest only in Long-Arc (not yet started) → ask if they actually skipped ahead, confirm before moving

---

## `/rpg learned <skill>`

**Triggers**: `/rpg learned "<skill>"`, `/rpg add skill "<skill>"`, "I learned <skill>"

**Args**: skill name (string), optional depth flag (standard / cert-grade / mastery)

**Read first**:
- Campaign file (required)
- `references/skill-tree-taxonomy.md`
- `references/xp-math.md` (for skill-XP values)

**Placement**:
- Run placement algorithm from taxonomy
- If keyword match is ambiguous, ask ONE disambiguation question
- If no match, place under `Domain Expertise → Wild Skills`

**Mutates**:
- Add skill under correct Branch with `added: today` and `last touched: today`
- Award XP (25 standard, 50 cert-grade, 100 mastery) to XP Ledger
- Reset Rusting timer on parent Branch and Domain
- Append Session History row
- Stamp Last Updated

**Chat output**: confirm placement ("placed under Engineering → Infrastructure"), XP awarded, brief tavern flavor. Link to updated tree.

**Failure modes**:
- Same skill already present → confirm refresh vs. duplicate, refresh resets last-touched but awards no new XP
- Cert-grade depth claimed but skill name is generic → ask for cert name to confirm

---

## `/rpg goal <description>`

**Triggers**: `/rpg goal "<description>"`, `/rpg set goal "<description>"`, "my goal is <description>", "I want to become <description>"

**Args**: free-text goal description

**Read first**:
- Campaign file (required)

**Mutates**:
- Replace (or set) Long-Term Goal block: target, set date, time horizon (ask if not in description), status = Active
- If a prior goal existed, archive it to Session History with "goal revised" note
- Append Session History row
- Stamp Last Updated

**Chat output**: confirm new goal in tavern voice, mention that next `/rpg map` will recompute the long-arc math. Link to updated campaign file.

**Failure modes**:
- No time horizon implied → ask explicitly ("by when, adventurer?")
- Goal is vague ("be successful") → ask for a more concrete target before saving

---

## `/rpg sheet`

**Triggers**: `/rpg sheet`, "show my sheet", "render my character"

**Args**: none

**Read first**:
- Campaign file (required)

**Mutates**:
- Stamps Last Updated. No other mutations.
- Re-renders the Character Sheet section using current campaign state (level, XP, stats, vitals, inventory, tree, buffs, debuffs)

**Chat output**: short summary (class, level, XP percent, top buff, top debuff) + link to campaign file.

**Failure modes**:
- Campaign file missing → suggest first-time scan or migration

---

## Cross-mode rules

- Every mode that mutates the campaign file stamps Last Updated.
- Every mode that mutates appends a Session History row (date, mode, one-line summary).
- Every mode reads `references/voice-guide.md` before any chat output.
- No mode dumps the full campaign file inline in chat. Always: summary + link.
- No mode uses em-dashes or en-dashes. Ever.
