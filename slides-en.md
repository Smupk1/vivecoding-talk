---
marp: true
theme: default
paginate: true
backgroundColor: "#0f172a"
color: "#e2e8f0"
style: |
  section { font-family: 'Inter', system-ui, sans-serif; padding: 60px; }
  h1 { color: #38bdf8; font-weight: 800; }
  h2 { color: #38bdf8; border-bottom: 2px solid #334155; padding-bottom: 8px; }
  code { background: #1e293b; padding: 2px 8px; border-radius: 4px; color: #fde68a; }
  pre { background: #1e293b !important; border-radius: 8px; padding: 16px; }
  blockquote { border-left: 4px solid #38bdf8; padding-left: 16px; color: #94a3b8; font-style: italic; }
  strong { color: #fde68a; }
  em { color: #f472b6; }
  table { font-size: 22px; }
  .center { text-align: center; }
  .small { font-size: 22px; }
---

<!-- _class: center -->

# Vibe Coding

## It's not "copy-pasting from ChatGPT"
## It's **directing models** to build real software

<br>

**Workshop · 90 min · Hands-on**

---

<!-- _class: center -->

## Who am I

**[Your name]** — Senior Architect, 15+ years building software

GDE · MVP · occasional teacher

Today: 90 min, two real demos, one core idea

---

## Workshop rules

1. **This is practice, not performance.** You'll clone, break, and fix.
2. **Questions don't wait.** Interrupt me.
3. **If I don't know something, I'll say so.** You can too.
4. **Don't copy what you don't understand.** That's the whole point of this talk.

---

# Block 1
## What is vibe coding?

<br>

> _"There's a new kind of coding I call vibe coding, where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."_
>
> — Andrej Karpathy, Feb 2025

---

## What vibe coding is NOT

❌ Copy-pasting from ChatGPT without reading

❌ "The model writes, I clap"

❌ Stop learning because "AI's got it now"

❌ Producing code you can't maintain

---

## What vibe coding IS

✅ **You** decide the architecture, the model executes

✅ Iterate 10× faster on **ideas you already understand**

✅ Use the model as a **judgment multiplier**, not a replacement

✅ **Constant push-back**: if the model's wrong, you argue with it

---

## The honest question

<br>

# Why NOW?

<br>

LLMs crossed a threshold in 2024-2025:

- Long context (1M tokens) → they understand your whole codebase
- Reliable tool use → multi-step task execution
- Code reasoning → not just autocomplete

**Prototyping cost dropped ~10×. Maintenance cost did not.**

---

# Block 2
## The two deadly traps

---

## Trap 1
### Vibe coding without foundations

<br>

You want to build an app with React.

You don't know what the DOM is.

You don't know what a bundler is.

You don't know what an HTTP request is.

<br>

> _How will you **debug** something you don't understand?_

---

## The uncomfortable truth

<br>

# The model doesn't teach you

<br>

The model **accelerates what you already know** and **hides what you don't**.

If you don't understand async/await, the code will "work" until it breaks in production at 3am.

**Fundamentals aren't optional. They're the difference between directing and being directed.**

---

## Trap 2
### Believing the model "knows"

<br>

The model is a **statistical predictor of text**.

It doesn't "reason" like you. It doesn't "verify" its output.

It confuses APIs. Invents functions. Forgets types.

> _If you don't read its code, you're not programming — you're **publishing**._

---

## Quick discussion (3 min)

<br>

When, in your experience, did an AI give you code that **looked right** but was wrong?

<br>

How did you discover it?

---

# Block 3
## Hands-on 1: Portfolio with Astro

<br>

**Repo**: `Smupk1/astro-portfolio-demo`

```bash
cd ~/workshop/astro-portfolio-demo
pnpm dev
```

Open `localhost:4321`

---

## What's here?

- **Astro 6** — component-based static site generator
- **Zero React, zero Vue** — HTML + CSS + JS vanilla with `.astro`
- **Deploy to Cloudflare Workers** — global, free

<br>

**Conceptual takeaways** (for CS upper-year):

1. **Islands Architecture**: the site is static HTML; only "islands" hydrate JS where needed. Compare mentally with Next.js pure SSR.
2. **Zero JS by default** — the opposite of "everything is React" SPA.

---

## Experiment (5 min)

<br>

Open `src/styles/global.css`.

Change the palette to **your university's colors**.

<br>

While doing it, **observe**: Astro's hot reload. The latency. How little it takes.

How many times did you deploy to prod to verify a color change when you started? 😅

---

## Why Astro instead of Next.js

| Astro | Next.js |
|---|---|
| HTML by default, JS optional | JS by default, HTML optional |
| Ideal for content sites | Ideal for stateful apps |
| Initial bundle: ~0 kb JS | Initial bundle: ~80-100 kb JS |
| Selective hydration | Full hydration |

**Rule**: if your site is 80% content, 20% interactivity → Astro. If it's the opposite → React/Next.

---

# Block 4
## Hands-on 2: Library with Cloudflare Workers

<br>

**Repo**: `Smupk1/biblioteca-cloudflare-demo`

**Stack**: Workers + D1 + Durable Objects + Hono

Three Cloudflare free-tier primitives in one project.

---

## Cloudflare free plan

| Service | Free tier |
|---|---|
| **Workers** | 100,000 requests/day |
| **D1** (SQL) | 5 GB · 25M reads/day · 50k writes/day |
| **Durable Objects** | 1M requests/month · 400k GB·s |
| **R2** (storage) | 10 GB |
| **KV** | 100k reads/day |

<br>

**Bottom line**: an entire class can hammer this without it costing a cent.

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
                            users,books    token→userId
```

---

## Live setup (5 min)

```bash
cd ~/workshop/biblioteca-cloudflare-demo
pnpm db:migrate:local
pnpm db:seed:local
pnpm dev
```

Open `localhost:8787`

Register · login · add book · refresh stats

---

## Why a Durable Object for sessions?

<br>

# This is **the** question of the talk

<br>

Let's discuss.

---

## Alternatives for storing sessions

| Option | Problem |
|---|---|
| `Map` in Worker memory | Each request may land on a different node. **No persistence.** |
| Signed cookie (JWT) | Works, but **can't be invalidated** without a blacklist |
| D1 (`sessions` table) | Works, but every token validation = 1 SQL query |
| **Durable Object** | ONE global instance, in-memory + persistent |

---

## The key mental model

<br>

**Workers** are **stateless** by design — execute and die.

**DOs** are **stateful** by design — live, remember, are consistent.

<br>

> When you need **a single consistent point** in the world (sessions, rate limiting, counters, chat rooms) → DO.
>
> For everything else → Worker + D1.

---

## DO consistency model

<br>

**Single-threaded per instance.** If two requests modify the same session, they serialize.

**No race conditions** inside a DO. This is huge.

<br>

> Compare with thinking about `SELECT ... FOR UPDATE` in Postgres.
>
> Inside a DO the problem doesn't exist — it's sequential by design.

---

# Block 5
## Vibe coding in action

<br>

## Let's add a feature **together**

<br>

**Feature**: mark a book as "loaned to user X"

We need: new column in D1, new endpoint, updated UI.

---

## Bad prompt vs good prompt

<br>

❌ **Bad prompt**:
> "Add loaning to the CRUD"

✅ **Good prompt**:
> "In the biblioteca repo, I want to add a loan system.
> Schema: new `loans` table (id, book_id, user_id, taken_at, returned_at).
> Endpoint: `POST /api/books/:id/borrow` (auth required) that creates the loan
> and sets `disponible=0`. If already loaned, return 409.
> Show me the plan before touching code."

---

## What changes between the two prompts

| Bad prompt | Good prompt |
|---|---|
| You leave everything to the model | You decide the shape |
| Model invents the schema | You pass the schema |
| Model picks the status code | You pick `409 Conflict` |
| Model gives you code | You ask for the **plan first** |

**Who's directing here?**

---

## Live exercise (10 min)

<br>

Each of you, on your machine, with your editor + AI:

**Add the endpoint `POST /api/books/:id/borrow`**

Rules:
1. Ask the model for the **plan before the code**
2. Push back on at least ONE decision
3. When the code compiles, **explain to your partner what it does**

---

# Block 6
## When NOT to vibe code

---

## The five danger zones

1. **Security-critical code** (auth, crypto, payments) — read every line
2. **Algorithms with invariants** — the model doesn't "reason" about invariants
3. **Production DB migrations** — one wrong drop table and it's over
4. **Code YOU couldn't write yourself** — if you don't understand it, you can't maintain it
5. **When the model defaults to "most common"** — old APIs, outdated patterns

---

## The $10,000 question

<br>

> _If this breaks at 3am, can you debug it?_

<br>

If the answer is **no** → it's not vibe coding, it's **vibe shipping**.

And vibe shipping will get you fired.

---

# Wrap up

## Takeaways from this workshop

1. **Vibe coding is a tool, not an identity.** Sometimes yes, sometimes no.
2. **Fundamentals are non-negotiable.** Concepts > code.
3. **The human leads.** If the model directs, you've lost.
4. **Constant push-back.** If the model's wrong, tell it.
5. **Astro + Cloudflare Workers** = beautiful stack, free, teaches modern concepts.

---

## Resources

- 📚 [Astro Docs](https://docs.astro.build)
- ⚡ [Cloudflare Workers Docs](https://developers.cloudflare.com/workers/)
- 🔥 [Hono](https://hono.dev/)
- 🤖 [Claude Code](https://www.anthropic.com/claude-code)
- 🎯 [Cursor](https://cursor.sh/)
- 📖 Karpathy on vibe coding: [twitter.com/karpathy](https://twitter.com/karpathy)

<br>

**Workshop repos:**
- `github.com/Smupk1/astro-portfolio-demo`
- `github.com/Smupk1/biblioteca-cloudflare-demo`

---

<!-- _class: center -->

# Thanks

## Questions?

<br>

Talk to each other too — the best way to understand something is to explain it to someone else.
