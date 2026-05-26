# Skill Tree Taxonomy

The Guildmaster's canonical tree. Every skill an adventurer logs via `/rpg learned <skill>` gets placed somewhere on this map. The tree has three tiers: **Domain → Branch → Skill**.

## The Domains (top level)

Eleven domains, broad enough that any career fits, specific enough to route a logged skill correctly.

1. **Engineering**
2. **Design**
3. **Product**
4. **Data**
5. **Marketing**
6. **Sales**
7. **Operations**
8. **People and Leadership**
9. **Finance**
10. **Communication**
11. **Domain Expertise** (catch-all for vertical knowledge: law, medicine, climate, fintech, gaming, etc.)

## The Branches

### Engineering
Backend, Frontend, Mobile, Infrastructure, ML, Security, QA, Embedded, Web3, DevTools

### Design
Product Design, Visual Design, UX Research, Design Systems, Motion, Brand Design, Service Design, Design Ops, Tooling

### Product
Discovery, Roadmapping, Prioritization, Analytics, Growth, Platform PM, Technical PM, AI Product, Hardware PM

### Data
Analytics, Engineering, Science, MLOps, Visualization, Governance, Modeling, Experimentation

### Marketing
Brand, Content, Growth, Performance, SEO, Social, Lifecycle, PR, Events, Community

### Sales
Outbound, Inbound, AE, Enterprise, Channel, Sales Engineering, BD, Revenue Ops, Customer Success

### Operations
Process, Supply Chain, Project Management, Program Management, Vendor Management, Facilities, Logistics, Compliance

### People and Leadership
Recruiting, HRBP, L&D, DEI, Coaching, Organizational Design, Performance Management, Compensation, Culture

### Finance
FP&A, Accounting, Treasury, Audit, Tax, Investor Relations, Corporate Development, Fundraising

### Communication
Writing, Public Speaking, Storytelling, Internal Comms, External Comms, Crisis Comms, Translation, Editing

### Domain Expertise
(Branches added as the adventurer logs them. Examples: Healthcare, Legal, Climate, Finance Sector, Gaming, Education, Aerospace, Government, Nonprofit, Manufacturing.)

## Placement Algorithm

When the adventurer runs `/rpg learned <skill>`:

1. **Keyword scan**: match the skill name against branch keyword lists below. If exactly one branch matches strongly, place there.
2. **Disambiguation**: if two or more branches match, ask the adventurer ONE question: "Was this more on the {Branch A} side or the {Branch B} side?" Place per their answer.
3. **No match**: place under `Domain Expertise → Wild Skills` (new branch created if needed) and flag for review next session.
4. **Always**: stamp the skill with `added: YYYY-MM-DD` and `last touched: YYYY-MM-DD`.

### Branch Keyword Hints (non-exhaustive)

- Backend → Python, Go, Java, Ruby, Node, PostgreSQL, Redis, REST, GraphQL, microservices
- Frontend → React, Vue, Svelte, CSS, Tailwind, Next.js, accessibility, web performance
- Infrastructure → Kubernetes, Terraform, AWS, GCP, Docker, CI/CD, Helm, Pulumi
- ML → PyTorch, TensorFlow, JAX, LangChain, RAG, fine-tuning, embeddings, transformers
- Tooling (Design) → Figma, Sketch, Framer, Adobe Suite, Webflow, Penpot
- Analytics (Data) → SQL, dbt, Looker, Mode, Tableau, Power BI, Mixpanel, Amplitude
- Growth (Marketing) → A/B testing, attribution, funnels, retention math, paid acquisition
- Writing (Communication) → blog posts, technical writing, copywriting, ghostwriting, editing

When in doubt, ask. Don't guess silently.

## Rusting Rule

If a Skill has not been touched in **12+ months**, the Guildmaster appends `⚠ Rusting` to its line in the Living Skill Tree.

The Rusting tag is a flag, not a punishment. It tells the adventurer: "this branch has gone quiet. Time to either prune it or refresh it."

When ALL skills under a Branch are Rusting, the Branch itself gets the Rusting tag. Same for Domains.

## Regrowth Rule

Any of these actions resets the `last touched` timer on a skill (and cascades up to its parent Branch and Domain):

- `/rpg learned <skill>` on that exact skill (refresh logged)
- `/rpg log <quest> done` for a quest whose stat gains include INT or DEX in that skill's domain
- The adventurer mentions actively using the skill during a `/rpg sheet` or returning-adventurer session, and the Guildmaster confirms before refreshing

The Guildmaster does NOT silently refresh timers based on inference. The adventurer's explicit action or confirmed mention is required.

## Rendering Rules

When rendering the Living Skill Tree (in the campaign file or via `/rpg sheet`):

- Show all touched skills with `(added DATE, touched DATE)`
- Suffix Rusting skills with `⚠ Rusting`
- Suffix Wild Skills with `🌿 Wild (review)`
- Indent: 2 spaces per tier
- Omit empty Branches (no logged skills under them)
- Omit empty Domains entirely

Example output:
```
- Engineering
  - Backend (last touched: 2026-05-10)
    - Python (added 2024-01-04, touched 2026-05-10)
    - Kafka (added 2025-06-02, touched 2025-09-18) ⚠ Rusting in 4 months
  - Infrastructure (last touched: 2026-03-12)
    - Kubernetes (added 2025-04-01, touched 2026-03-12)
- Design
  - Tooling (last touched: 2026-04-22)
    - Figma autolayout (added 2026-04-22, touched 2026-04-22)
- Domain Expertise
  - Wild Skills 🌿
    - Tarot reading (added 2026-05-24, touched 2026-05-24) 🌿 Wild (review)
```
