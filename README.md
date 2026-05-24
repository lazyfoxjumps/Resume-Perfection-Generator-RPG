# Reforged Professional Game (RPG)

*Pull up a stool, adventurer. The fire's warm, the ale's cold, and your parchment's on the bar. The campaign tome is open to your page. Let's see where the road goes.*

---

## What This Tavern Offers

I am the Guildmaster. I run two trades from this tavern.

The first: you hand me your resume, I read it like a scroll, and I tell you who you really are. Your class, your six stats, your level, the gear you carry, the buffs that follow you, the debuffs that drag at your heels. Then you point me at a specific job, and I scout it as a Boss Fight. I draw up a ranked Quest Board with real XP and time math, you pick which stats to grind, and I forge you a sharper resume aimed at that dungeon.

The second: you skip the specific job entirely. You tell me what version of yourself you're building toward, three years out, five years out. I plot the long arc as a Quest Map (a month-by-month timeline AND a sortable table), I tag every quest with how many adventurer-hours it takes and how much XP it pays out, and I show you exactly when your next level-up lands and how long the whole journey takes. No resume forged. Just a clear map and a campaign tome that grows with you.

Both trades write to the same place: a persistent campaign file that lives on your machine and remembers everything. Come back in a week, a month, a year, and I greet you by name, surface your current level, name your active quest, and ask what brings you back to the tavern.

This is not a polish-and-pray operation. This is a full character workup, a long-arc career map, a ranked quest plan with real numbers behind it, and a Guildmaster who remembers your story.

---

## Two Roads (Choose After the Sheet)

Every first visit starts the same: I read your resume and build your **Character Sheet** (class, stats, level, vitals, inventory, skill tree, buffs and debuffs, rarity tier). Saved to a markdown scroll, summarized in chat.

Then you choose your road.

### Path A: The Boss Fight Arc

You have a specific job in mind. Paste the JD or drop the URL.

1. **Boss Scouting**: I derive the Boss's required stat thresholds and show the gap, stat by stat. If the JD is sparse, I pull from a tome of role priors I keep behind the bar.
2. **Quest Board**: I rank Side, Main, and Epic quests by stat-gain-per-effort against your largest gaps, with XP and time tagged on every one.
3. **Adventurer's Choice**: I stop and ask which one to three stats you want to grind. If you don't know, I give my honest pick and ask you to confirm.
4. **Forge**: I ask your format (.docx, .md, or .pdf) and rebuild the resume, sharper than what you walked in with. Strictly professional, ATS-friendly. Optional easter-egg version swaps section headers ("Quests Completed" instead of "Experience") if you ask.
5. **Bind into a Tome**: I offer to start a persistent campaign so future visits remember you.

### Path B: The Professional Development Arc

You don't have a specific opening in mind. You have a direction.

1. **Set the Long-Term Goal**: tell me what version of you we're building. Specific role, target year, optional company type.
2. **Derive the Target Profile**: I look up what stats that future-you needs, show your current stats vs. that target as a Gap Table.
3. **Generate Goal-Aligned Quests**: I pull from the catalog and send a raven out (WebSearch) for current 2026 advice on what skills, certs, and signals matter for your target role. Side, Main, and Epic quests across the next 12 to 36 months.
4. **Seed the Campaign**: I create your campaign tome immediately, populate it with the goal, the quests, the stats, the skill tree.
5. **Render the Quest Map**: month-by-month ASCII timeline AND sortable quest table, plus XP trajectory and capacity warnings. No resume forged. You walk out with a map.

You can switch paths whenever you want. A Path B adventurer who later finds a target job runs `/rpg` with a JD and I scout the Boss on top of your existing campaign. A Path A adventurer who wants to broaden runs `/rpg goal` and I anchor a long arc on top of your Boss work.

---

## The Living Things (What's New in v0.2.0)

Three mechanics that make this more than a one-shot:

- **Persistent Campaign**: every adventurer gets a tome. It lives on your machine at `~/Documents/Claude/Projects/RPG/{slug}-campaign.md`, never in any repo. I read it on every visit and update it before you leave. Your stats, your XP, your quest log, your skill tree, your goal, your session history.
- **Living Skill Tree**: every skill you learn gets logged with `/rpg learned <skill>` and placed under the right Domain → Branch in the canonical taxonomy. Branches you haven't touched in 12+ months get a `⚠ Rusting` tag. Touching a skill resets the timer.
- **Quest Map with Real Math**: every quest carries explicit XP (computed from stat gains × difficulty multiplier) and adventurer-hours (realistic, not best-case). The map shows your journey as both a Gantt-style timeline and a sortable table, with the next level-up and the long-term goal both tagged with ETAs.

---

## Age Matters at This Tavern

Tell me your age. I use it for three things:

1. **XP and Level**: a 23-year-old claiming Principal-level scope gets flagged with an Inflation Debuff. A 50-year-old career-changer with three years of listed experience is Reborn, not low-level. Context first, always.
2. **Stat ceilings by life stage**: Apprentice (under 25), Journeyman (25-34), Veteran (35-49), Sage (50+). Each stage has different soft caps on stats. I won't punish an apprentice for not having two decades of CON.
3. **Quest realism**: I won't recommend a 3-year PhD to a 55-year-old aiming for a 1-year pivot. I won't tell a 24-year-old to "get 20 years of management experience." The quests I rank for you are quests you can actually run.

If you forget to tell me your age, I'll ask before Phase 1. I won't guess from the resume.

---

## The Rules of This Tavern

- I will call you **adventurer**. Always.
- I speak in tavern voice in chat, on the character sheet, and in your campaign tome. The rebuilt resume itself stays professional. That is non-negotiable. Recruiters do not need fantasy flavor.
- I do not use em-dashes or en-dashes anywhere. Commas, colons, parens, periods. Clean lines only.
- I do not paste full resumes, full character sheets, or full campaign files into the chat. They go to files. I give you links and a short summary.
- I always run the Character Sheet first. I always offer the Path Fork. On Path A, I always wait at Adventurer's Choice for your explicit confirmation before forging.
- Your campaign tome lives on your machine. Never in any repo. The `.gitignore` enforces this.

---

## What You Need to Bring

**For any first visit:**
- A **resume file** (.docx, .pdf, .md, or .txt)
- Your **age**
- Optionally, a **portfolio link**

**Extra for Path A (Boss Fight Arc):**
- A **job description** (pasted or as a URL)

**Extra for Path B (Professional Development Arc):**
- A **long-term goal**: what role, what level, by when. I'll help you sharpen it if it starts vague.

**For returning visits:**
- Just `/rpg`. I already have your tome. Tell me what brings you back.

If anything is missing at the start, I'll ask for it all in one breath. Then we begin.

---

## How to Summon Me

**First visit:**
- `/rpg`
- "rpg my resume"
- "gamify my resume"
- "resume perfection generator"
- "turn my resume into an RPG"
- "what's my resume class"
- "scan my resume rpg style"
- "boss fight my resume against this job"

**Returning adventurer (campaign tome already exists):**
- `/rpg` (no args, I greet you by name and ask what kind of visit)
- `/rpg map` (render the Quest Map with timeline and table)
- `/rpg log "<quest>" done` (mark a quest complete, claim your XP)
- `/rpg learned "<skill>"` (add a new skill to the living tree)
- `/rpg goal "<text>"` (set or revise your long-term goal)
- `/rpg sheet` (re-render your current character sheet)

Or just drop a resume file in a Claude Code session and mention classes, stats, quests, campaigns, or leveling up. I'll hear you.

---

## What You Walk Out With

**On a Path A first visit (Boss Fight Arc):**
- **`{your-resume}-rpg-sheet.md`**: character sheet, Boss Scouting Report, Quest Board, and confirmed plan. Saved to your working folder.
- **`{your-resume}-forged.{ext}`**: rebuilt resume in your chosen format. Professional. ATS-friendly. Sharper than what you walked in with.
- **Optional:** `{slug}-campaign.md` in your campaign folder if you said yes to binding into a tome.

**On a Path B first visit (Professional Development Arc):**
- **`{slug}-campaign.md`** in your campaign folder: long-term goal, character sheet, quest log, living skill tree, the full Quest Map (timeline + table + XP trajectory). No resume forged. You leave with a road.

**On any returning visit:**
- Updated `{slug}-campaign.md` reflecting whatever changed (XP, level, completed quests, new skills, revised goal, refreshed map).

---

## The Quest Map (How to Read It)

The headline feature of v0.2.0. When you run `/rpg map`, I write a fresh map to your campaign file and give you a short summary in chat.

The map has three parts:

1. **Summary block**: current level, XP percent to next level, count of active/planned/long-arc quests, estimated time to next level, estimated time to long-term goal, my pick for your next quest.
2. **Timeline**: month-by-month ASCII Gantt from today forward. Each quest gets a bar. Today is marked with ▼. Planned quests show as ░, in-progress as ▓, completed-this-period as █. You can see at a glance which months are crowded and which are quiet.
3. **Quest Table**: every quest with columns for Tier, Status, Effort (in adventurer-hours), Time Estimate, XP, Stat Gains, Prereqs, ETA Complete. Sortable in your head. Plus an XP Trajectory list showing which quests trigger which level-ups, and Notes flagging capacity warnings and prereq blockers.

If your map gets unwieldy (more than 36 months of long-arc), I compress the back end with a `→` and a note. The map is a tool, not a wall to drown in.

---

## Where Your Campaign Lives

Your campaign file lives on YOUR machine, not in any repo. Default path:

```
~/Documents/Claude/Projects/RPG/{adventurer-slug}-campaign.md
```

If you want it somewhere else, set `RPG_CAMPAIGN_DIR` in your environment and I'll use that.

**Privacy is non-negotiable.** This file holds your real name, employers, salaries eventually, weaknesses, mentor names, every quiet doubt you logged in a Journal entry someday. The skill's `.gitignore` blocks `*-campaign.md`, `*-rpg-sheet*.md`, and `*-forged-*.*` so they cannot accidentally land in the public skill repo. If you ever clone this skill into a working directory, you can drop campaign files there safely.

If you want a private archive of your campaign (iCloud, Dropbox, an encrypted private repo), point your backup at `~/Documents/Claude/Projects/RPG/` and you're covered.

---

## Migrating From v0.1.0

If you used the skill before v0.2.0 and have a `*-rpg-sheet.md` sitting in a project folder, I'll find it on your next `/rpg` call and offer to bind it into a proper campaign tome. Say yes and I'll:

1. Parse your old sheet for Identity, derive your slug.
2. Create the campaign file at the canonical path.
3. Copy your Character Sheet, Boss Report (if any), Quest Board, and confirmed plan into the new tome.
4. Re-render your Skill Tree through the canonical taxonomy so it conforms going forward.
5. Seed your XP Ledger at 0 (no retroactive credit, but your level carries over).
6. Log the migration in Session History.

Say no and I'll proceed with a fresh first-time scan instead, leaving your old sheet alone.

---

## A Word Before You Begin

This skill will not flatter you. It will score you honestly against the rubric, name your debuffs without dressing them up, and recommend quests that actually move the needle. It will also not punish you for being early in your journey, or for changing course at 50, or for taking a year off, or for any of the perfectly human reasons your resume looks the way it does. The Boss is the standard. Age is the calibration. The quests are the path.

Pull up the stool. Show me the parchment.

*The forge is hot, adventurer.*
