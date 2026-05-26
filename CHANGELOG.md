# Changelog

All notable changes to the Reforged Professional Game (RPG) skill.

## [0.2.1] 2026-05-27, "The Rename"

### Changed
- Renamed skill from "Resume Perfection Generator (RPG)" to "Reforged Professional Game (RPG)". Invocation command `/rpg` is unchanged. Trigger phrase "resume perfection generator" replaced with "reforged professional game".

## [0.2.0] 2026-05-24, "The Campaign Update"

### Added
- **Persistent campaign file** at `~/Documents/Claude/Projects/RPG/{slug}-campaign.md` (or `RPG_CAMPAIGN_DIR`). Survives across sessions, weeks, and years. Never lands in any repo.
- **Mode router**: `/rpg map`, `/rpg log <quest> done`, `/rpg learned <skill>`, `/rpg goal <text>`, `/rpg sheet`.
- **Path Fork after Phase 1**: adventurer chooses between Path A (Boss Fight Arc, the v0.1.0 flow ending in a forged resume) and Path B (Professional Development Arc, no JD, no resume forge, goes straight to long-term goal + Quest Map).
- **Living Skill Tree** with canonical Domain → Branch → Skill taxonomy. Branches untouched 12+ months get a `⚠ Rusting` tag. Touching a skill via `/rpg learned` resets the timer.
- **Quest Map** rendered to the campaign file via `/rpg map`. Contains both a month-by-month ASCII Gantt timeline AND a sortable quest table, plus a Summary block, XP Trajectory, and Notes (capacity warnings, prereq blockers).
- **XP math system**: per-quest XP computed from stat gains × 50 × difficulty multiplier (Side 1.0, Main 2.0, Epic 3.5). Level thresholds (L2 = 100 XP, ×1.3 per level). Age-baseline penalty (over-baseline levels cost 1.5×). Stat ticks at level-up (+1 to chosen stat, capped by age ceiling).
- **Epic quest tier** for quests with effort 12+ months AND total stat gain ≥ 5. Promoted: *Take a 0-to-1 Role* (XP 1050), *Lead a Multi-Year Initiative* (XP 875).
- **Returning Adventurer Flow**: `/rpg` with no args on a known adventurer greets by name, surfaces level, XP-to-next, active quest, days-since-last-session, asks visit purpose.
- **Migration flow** from v0.1.0 sheets into campaign files (parses Identity, derives slug, copies sections, re-renders Skill Tree through taxonomy, seeds XP Ledger at 0).
- **New reference files**: `xp-math.md`, `skill-tree-taxonomy.md`, `campaign-modes.md`, `quest-map-template.md`, `campaign-file-template.md`.
- **`.gitignore`** at repo root blocks `*-campaign.md`, `*-rpg-sheet*.md`, `*-forged-*.*`, `.DS_Store`.
- **`CHANGELOG.md`** at repo root.

### Changed
- **`SKILL.md`** restructured: frontmatter expanded with new triggers, Mode Router at top, Campaign File Protocol, Path Fork in Phase 1, Returning Adventurer Flow, per-mode sections, Migration logic. Version bumped to `0.2.0`.
- **`README.md`** gains sections: Returning to the Tavern, Modes of Summoning, The Quest Map, Where Your Campaign Lives, Migrating From v0.1.0, What's Coming.
- **`references/quest-templates.md`** gains an `XP:` line on every quest, adventurer-hours notation on every Effort field, new `## Epic Quests (Catalog)` section, WebSearch trigger for Path B goal-aligned quests.
- **`references/character-sheet-template.md`** gains `Last Updated` stamp, restructured `Level and XP` block with XP percent and over-baseline flag, new `XP Ledger (recent)` section, new `Long-Term Goal` section, pointer to campaign file location, Quest Board gains XP per quest and an Epic Quests subsection.

### Reserved (for v0.3.0+)
Empty headings in the campaign file for: Interview Prep, Negotiation Log, Party (networking), Journal, Yearly Review, HP Watch. Future versions fill these in without restructure.

### Privacy
- Personal campaign data NEVER lives in the GitHub repo. `.gitignore` enforces. Canonical path is on the adventurer's machine only.

---

## [0.1.0] 2026-05-24, "First Forge"

### Added
- Initial release.
- Five-phase one-shot flow: Character Sheet → Boss Scouting → Quest Board → Adventurer's Choice → Forge.
- Eight classes (Warrior, Mage, Rogue, Bard, Cleric, Ranger, Artificer, Paladin) with multi-class support.
- Six D&D-style stats (STR, DEX, CON, INT, WIS, CHA) scored 1-20 with anchored examples.
- Resume Rarity Tier (Common / Uncommon / Rare / Epic / Legendary).
- Boss Scouting from JD or JD URL, with role-prior fallback for vague JDs.
- Quest Board (Side + Main) ranked by stat-gain-per-effort.
- Age calibration across XP, stat ceilings, and quest realism.
- Forge phase outputs `.docx`, `.md`, or `.pdf` via delegation to `anthropic-skills:docx` and `anthropic-skills:pdf`.
- Optional easter-egg medium-flavor resume (RPG-style section headers only).
- Six references: `classes.md`, `stat-rubric.md`, `role-priors.md`, `quest-templates.md`, `character-sheet-template.md`, `voice-guide.md`.
- Tavern voice in chat, professional voice in the forged resume.
- Zero em-dash / en-dash rule.
- Address user as "adventurer", self as "Guildmaster".
