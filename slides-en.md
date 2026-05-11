---
marp: true
theme: default
paginate: true
backgroundColor: "#0a0a0a"
color: "#e8e8e8"
style: |
  section { font-family: 'Inter', system-ui, sans-serif; padding: 60px; }
  h1 { color: #d4af37; font-weight: 800; letter-spacing: -0.02em; }
  h2 { color: #d4af37; border-bottom: 1px solid #2a2a2a; padding-bottom: 10px; font-weight: 700; }
  h3 { color: #8b9eff; }
  code { background: #1a1a1a; padding: 2px 8px; border-radius: 3px; color: #f4d03f; font-size: 0.85em; }
  pre { background: #111 !important; border: 1px solid #2a2a2a; border-radius: 6px; padding: 18px; font-size: 0.7em; }
  blockquote { border-left: 3px solid #d4af37; padding-left: 18px; color: #a0a0a0; font-style: italic; margin: 20px 0; }
  strong { color: #f4d03f; }
  em { color: #c084fc; }
  table { font-size: 22px; border-collapse: collapse; }
  th, td { padding: 8px 14px; border-bottom: 1px solid #2a2a2a; }
  th { color: #d4af37; text-align: left; }
  .center { text-align: center; }
  .small { font-size: 22px; }
  .mono { font-family: 'JetBrains Mono', monospace; }
  ul li { margin: 6px 0; }
---

<!-- _class: center -->

# Vivecoding

## AI-assisted engineering as a **campaign**, not a roll of the dice

<br>

**Workshop · 90 min · Hands-on**

<br>

<span class="mono" style="color:#666;font-size:14px">Samuel Cala · vivecoding.dev</span>

---

## Who I am

**Samuel Cala** — Security Engineer at IT Audit Labs

SOC operations · SOAR automation · Security development

Today: 90 minutes. Two real projects. One thesis.

<br>

> Vibecoding is roleplay. **Vivecoding is a campaign with discipline.**

---

## Workshop rules

01. This is **practice**, not performance. You'll clone, break, fix.
02. Questions don't wait. Interrupt me.
03. If I don't know something, I'll say so. You can too.
04. **Don't copy what you don't understand.** That's the whole talk in one line.

---

<!-- _class: center -->

# Cold Open

## *"Did you vibe code it?"*

---

## The story

When I joined IT Audit Labs, the first question my boss asked me was:

> *"Did you *vibe code* it?"*

I didn't know what the term meant. Went home and googled it. Felt a little ashamed for using ChatGPT to help me ship.

A few weeks later, my boss stood at a whiteboard and said:

> *"You're pronouncing it wrong. It's **vibe** coding, not **vive** coding."*

He was right that I was saying it wrong.

**He was wrong that it was a mistake.**

---

# Act I
## Vibecoding vs Vivecoding

---

## The thesis, in one chart

| | **Vibecoding** | **Vivecoding** |
|---|---|---|
| **Philosophy** | Roll a d20. Pray. | Engineering discipline + AI as amplifier |
| **Specs** | None | Before code. Always. |
| **Pipeline** | Prompt → ship | explore → spec → design → apply → verify |
| **Models** | One, for everything | Multi-model with cross-check |
| **Tests** | Optional | Strict TDD. Authz invariants. |
| **Code review** | "It compiles, so it works" | On every PR. No exceptions. |
| **Tech debt** | Grows faster than you can write | AI amplifies the engineer, not the reverse |

**Same tools. Same models. *Different discipline.***

---

## The vibecoder

Rolls a d20. Ships whatever the model spits out.

<br>

## The vivecoder

Treats AI as **the most powerful junior they've ever managed**, and applies the same engineering rigor they'd apply to any other contributor.

Because the alternative is **tech debt that compounds faster than you can write code.**

---

## Why does this matter NOW?

LLMs crossed a threshold between 2024 and 2025:

- **Long context** (1M+ tokens) → understand entire codebases
- **Reliable tool use** → execute multi-step work
- **Code reasoning** → not just autocomplete

<br>

**Prototyping cost dropped ~10×.**
**Maintenance cost did not.**

That gap is where vivecoding lives.

---

# Act II
## The stack: specialized agents

---

## One model is never the right answer

Each model has a strength. **The mix is the moat.**

| Model | Role | What for |
|---|---|---|
| **Gemini** | Planner | Documentation, planning, SDDs, long context |
| **Claude** | Builder | Implementation, refactor, the code that ships |
| **Cloudflare Workers AI** | Fallback | Llama/Kimi at the edge, cheap fast iteration |
| **Codex** | Hunter | Bug bounty, error hunting, adversarial diff pass |
| **CodeRabbit + Copilot** | Safety net | Two reviewers, every merge. No exceptions. |

The vibecoder picks one and prays.

The vivecoder runs five — **because each one is wrong sometimes, and the only way you find out is when another one disagrees.**

---

## The support agents

**Engram** — Persistent memory (RAG). Every decision, observation, and CVE persists. Next session knows what the last session learned. Nothing important lives only in chat history.

**Gentle** — Grounding companion. Lands me when I'm spiraling. *"No, we're not doing that tonight at 10pm."*

**Warlock** — Security auditor. Caught **two real CVEs in 48 hours** that human review wouldn't have caught.

<br>

Each does their job. I orchestrate.

---

## The SDD pipeline (Spec-Driven Development)

```
/sdd-init     →  detect stack & conventions
   ↓
/sdd-explore  →  scout the terrain
   ↓
/sdd-propose  →  intent + scope + approach
   ↓
/sdd-spec     →  requirements + scenarios   ──┐
   ↓                                           ├→ /sdd-tasks → /sdd-apply → /sdd-verify → /sdd-archive
/sdd-design   →  architecture decisions     ──┘
```

Spec and design feed tasks **in parallel**. Verify is a gate, not a vibe. Archive syncs and closes.

**The same SDLC you learned in school. Now executable.**

---

## Why it scales

No agent — and no human — has to hold the whole project in their head.

**The DAG holds it.**

Each phase has clear preconditions, clear outputs, and a clear handoff to the next.

<br>

> This is the difference between "I'm juggling five balls" and "I have a system that knows where each ball is."

---

# Hands-on I
## Astro Portfolio

---

## The first project

**Repo**: `Smupk1/astro-portfolio-demo`

```bash
cd ~/workshop/astro-portfolio-demo
pnpm dev
# → localhost:4321
```

**Stack**: Astro 6 + Cloudflare Workers, global edge deploy in one command.

---

## Why Astro instead of Next.js?

| Astro | Next.js |
|---|---|
| HTML by default, JS optional | JS by default, HTML optional |
| Initial bundle: ~0 kb JS | Initial bundle: 80-100 kb JS |
| Selective hydration (islands) | Full hydration |
| Ideal for content sites | Ideal for stateful apps |

**Rule**: if your site is 80% content, 20% interactivity → Astro. Reverse → Next.

---

## Key technical concept

Astro **inverts the React model's default**:

- In React/Next, **everything is JS** until you explicitly ask for static (Server Components, RSC).
- In Astro, **everything is HTML** until you explicitly ask for hydration (`client:load`, `client:idle`, `client:visible`).

<br>

> This inversion isn't just performance. It's **design**: it changes which decisions you make without thinking.

---

## Live practice · 5 minutes

Open `src/styles/global.css`.

Change the palette to your university's colors.

While doing it, **observe**: the hot-reload latency. How little it takes. How cheap iteration is.

<br>

How many times did you deploy to production to verify a color change when you started?

---

# Hands-on II
## Library with Cloudflare Workers + D1 + Durable Objects

---

## The second project

**Repo**: `Smupk1/biblioteca-cloudflare-demo`

**Stack**: Workers + D1 (SQL) + Durable Objects + Hono

Three Cloudflare free-tier primitives in one project.

```bash
cd ~/workshop/biblioteca-cloudflare-demo
pnpm db:migrate:local
pnpm db:seed:local
pnpm dev
# → localhost:8787
```

---

## Cloudflare's free plan

| Service | Free tier |
|---|---|
| **Workers** | 100,000 requests/day |
| **D1** (SQL) | 5 GB · 25M reads/day · 50k writes/day |
| **Durable Objects** | 1M requests/month · 400k GB·s |
| **R2** (storage) | 10 GB |
| **KV** | 100k reads/day |

<br>

A whole class can hammer this stack and it costs zero.

---

## Architecture

```
┌────────────┐    HTTPS    ┌────────────────────────────────┐
│  Browser   │────────────▶│  Worker (Hono router)          │
└────────────┘             │    /api/login, /api/books      │
                           └──────┬──────────────┬──────────┘
                                  ▼              ▼
                            ┌─────────┐    ┌──────────────┐
                            │   D1    │    │ Durable Obj  │
                            │ (SQL)   │    │  Sessions    │
                            └─────────┘    └──────────────┘
                            users,books    token → userId
```

---

## Why a Durable Object for sessions?

| Option | Problem |
|---|---|
| `Map` in Worker memory | Each request may hit a different node. No persistence. |
| Signed cookie (JWT) | Works, but can't be invalidated without a blacklist |
| D1 (`sessions` table) | Works, but every validation = one SQL query |
| **Durable Object** | ONE global instance, in-memory + persistent |

<br>

> **Workers** are stateless by design. **DOs** are stateful by design. For sessions, rate limiting, counters, rooms — always DO.

---

## DO consistency model

**Single-threaded per instance.** If two requests modify the same session, they serialize.

**Zero race conditions** inside a DO. This is huge.

<br>

Compare with having to think about `SELECT ... FOR UPDATE` in Postgres.

Inside a DO the problem **doesn't exist** — it's sequential by design.

---

## The rule that generalizes

# Every AI tool is an authenticated endpoint.

<br>

If you wouldn't expose the underlying operation as an unguarded REST call, **you can't expose it as an unguarded tool either.**

The Zod schema on a tool is not a security boundary. **The handler is.**

---

# Case study
## Two real CVEs in 48 hours

---

## CVE #1 — `requireOrgAdmin()`

**The bug.** Any member of an organization was treated as **admin automatically**, regardless of role.

Looked intentional. The pattern was old. Nobody questioned it.

It would have lived in production for months.

<br>

**How the system caught it:** the security agent ran an unprompted audit, chained with the code-review skill. Confirmed: *this is a real privilege-escalation bug, not a design choice.*

**Lesson:** *What looks like a feature is sometimes a CVE.*

---

## CVE #2 — Cross-tenant leak in an AI tool

**The bug.** The `get_ticket_detail` tool of an AI assistant fetched **any ticket by ID via service account**. No ownership check.

A user in tenant A could ask the assistant for a ticket from tenant B, and the assistant handed it over.

<br>

**How the system caught it:** during the security audit phase of the overhaul, **before production**.

**Fix:** replicate the REST endpoint's access control inside the tool.

**Lesson generalizes:** *every AI tool is an authenticated endpoint.*

---

# The five scars
## If a talk only shows wins, they're selling you something

---

## Scars from the same campaign

01. **CF Workers AI** too slow + bad at instructions. Migrated to Anthropic API with fallback.

02. **`ts-node` broke on extensionless ESM imports.** One session lost. Fix: switch to `tsx`.

03. **14 components rendering raw HTML entities.** MS Graph returns them encoded. Decode in every component.

04. **`client:load` hydration mismatch with `sessionStorage`.** Switched to `client:only="react"`.

05. **Zendesk POST had no retry.** SDD didn't catch it. **The user did.**

<br>

> The workflow is good. **It's not magic.** User feedback is still irreplaceable.

---

# The 5 rules
## What the vibecoder gets wrong

---

## Rule 01

# Specs before code. Always.

If you can't write the spec, **you don't understand the change.**

Stop typing prompts.

---

## Rule 02

# One model is never the right answer.

Each model has a strength. The mix is the moat.

Plan, build, audit — **different agents.**

---

## Rule 03

# Design is code. Merge it.

Architecture decisions live in version control, **next to the code that proves them.**

Not in Notion. Not in Confluence. **In the repo.**

---

## Rule 04

# "It compiles" ≠ "it works."

Verify is a phase, not a vibe.

Tests, invariants, authz checks. **Don't skip verification.**

---

## Rule 05

# The AI is your junior, not your genius.

You wouldn't merge a junior's PR without reading it.

**Don't merge the AI's either.**

---

# The number

## From baseline to vivecoding

<br>

# 6 months → 1 month

<br>

Production. Multi-tenant. 78 tests passing. Two security audits.

**Speed didn't come from skipping steps.**

It came from **parallelizing the right steps with the right models.**

---

# Three things to take home

---

<!-- _class: center -->

## 01 · The Thesis

# Discipline beats vibes.

Specs, design, TDD, verify.

The classical SDLC — now executable.

---

<!-- _class: center -->

## 02 · The Stack

# Right model, right job.

One model is never the right answer.

The mix is the moat.

---

<!-- _class: center -->

## 03 · The Math

# AI is an amplifier.

It doesn't replace the engineer.

It makes a trained one **6× faster.**

---

<!-- _class: center -->

<br><br>

# Vibecoding is roleplay.

# Vivecoding is a campaign with discipline.

<br>

<span class="mono" style="color:#666">vivecoding.dev</span>

---

## Resources

**Workshop repos:**
- `github.com/Smupk1/astro-portfolio-demo`
- `github.com/Smupk1/biblioteca-cloudflare-demo`

**Full manifesto:**
- vivecoding.dev/writing/vibecoding-vs-vivecoding

**Workshop stack:**
- [Astro](https://docs.astro.build) · [Cloudflare Workers](https://developers.cloudflare.com/workers/) · [Hono](https://hono.dev/) · [Drizzle](https://orm.drizzle.team/)

---

<!-- _class: center -->

# Questions

<br>

Disagree publicly. I'll listen.

<br>

<span class="mono" style="color:#666;font-size:14px">Samuel Cala · linkedin.com/in/samuelsapontec</span>
