# Speaker Notes — Vivecoding Workshop (English)

> Extended notes. What to say, where to pause, what to ask, where you might lose the audience.

**Audience**: upper-year CS students. They already code. They know what an API, a database, an HTTP request is.

**Duration**: 90 minutes. Keep a timer.

**Tone**: direct, first person, no fluff. Tell specific stories. When you don't know something, say so.

---

## Setup (min 0-5)

Have everyone run:

```bash
cd ~/workshop/astro-portfolio-demo && pnpm dev
```

While they verify it starts, open your first slide.

If someone shows up without having run `setup.md` first, **don't wait for them**. Let them catch up while you move on.

---

## Cold Open: "Did you vibe code it?" (min 5-10)

### What to say

Tell the story as it is in the manifesto. Don't dramatize, don't embellish — it's good on its own.

> "When I joined IT Audit Labs, my boss asked me: *Did you vibe code it?*. I didn't know what the term meant. Felt a little ashamed. Googled it that night.
>
> A few weeks later, he corrected me: *It's vibe coding, not vive coding.*
>
> He was right that I was saying it wrong. He was wrong that it was a mistake."

Long pause here. Let the line land.

### Why it matters

This isn't a talk about semantics. It's a talk about **discipline**. The whiteboard story gives you license to talk about the topic without sounding like just another AI evangelist.

---

## Act I: Vibecoding vs Vivecoding (min 10-20)

### The chart

When you show the table, **don't read it**. Comment row by row:

> "Philosophy. The vibecoder rolls a d20 and prays. The vivecoder treats AI as the most powerful junior they've ever managed.
>
> Specs. The vibecoder doesn't write them. The vivecoder writes them *before* the code. If you can't write the spec, you don't understand the change. Period."

Keep going. Three rows are enough — don't walk all seven or you lose them.

### Closing the chart

> "Same tools. Same models. Different discipline. **That's the whole talk.** The rest is 80 minutes of evidence."

### Quick discussion (3 min)

> "Raise your hand if you've used Copilot, Cursor, ChatGPT, or Claude to write code you later committed to production."

Wait. You'll see 80% of hands up.

> "Good. The question isn't *if* you use it. The question is **how**."

### Why now

Three quick points. If someone asks for specific benchmarks:

- GPT-4 (2023) — isolated functions
- Claude 3.5 / GPT-4o (2024) — navigate codebases
- Claude 4.x (2025-2026) — hours of agentic work

**Trap you'll see**: someone asks *"won't this replace us?"*. Answer:

> "It'll replace those who don't use AI. Not those who use it well. Same story as any productivity-multiplying tool. Work moves up the abstraction chain."

---

## Act II: The stack (min 20-25)

### Multi-model

This slide has five rows. **Comment on each in one line**:

- **Gemini**: planning. Long context, good structured output.
- **Claude**: building. The code that ships to production.
- **Workers AI**: edge fallback. Cheap. Fast. Good for iteration.
- **Codex**: hunting. Adversarial pass over diffs.
- **CodeRabbit + Copilot**: automatic review. Two opinions on every merge.

### The key point

> "Each one is wrong sometimes. The only way you find out is when another one disagrees."

That phrase is the heart. **Pause it.**

### The support agents

Three slides. One per agent. **Don't go deep** — students don't need to know how Engram works internally. Say it like this:

> "Engram is persistent memory — a RAG. The RAG isn't the point. The point is **nothing important lives only in chat history**."
>
> "Gentle is grounding — the agent that lands me. Last week, 10pm, a stakeholder asked me to rewrite a working product. Gentle said: *not tonight.* And it was right."
>
> "Warlock is security — auditing. Caught two real CVEs in 48 hours. We'll get to those."

---

## SDD pipeline (min 25-30)

### The DAG

When you show the diagram, say this:

> "Spec and design feed tasks **in parallel**. Verify is a gate, not a vibe. Archive syncs and closes.
>
> This is the same SDLC you see in school. **The difference is that now it's executable.** Each arrow is a command."

### Why it scales

> "No agent — and no human — has to hold the whole project in their head. The DAG holds it.
>
> This is the difference between 'I'm juggling five balls' and 'I have a system that knows where each ball is.'"

---

## Hands-on I: Astro Portfolio (min 30-45)

### Before you start

They should **already** have run `pnpm install` (it's in `setup.md`). If not, the first 5 min become 12.

### Your live plan

1. **Min 0-2**: you open the repo, run `pnpm dev`, show the site.
2. **Min 2-7**: tour the structure. `src/pages/`, `src/components/`. Stop on `index.astro` and show it's **not JSX — it's real HTML with frontmatter**.
3. **Min 7-12**: palette change exercise. Have them open `global.css`, change colors, watch the hot-reload.
4. **Min 12-15**: Astro vs Next slide.

### What NOT to do

- **Don't explain what Vite is.** Lose 5 min, not the point.
- **Don't explain CSS variables** unless asked. Assume they know.
- **Don't dive into SSR/SSG/ISR** — another rabbit hole.

### The pedagogical concept

> "Astro **inverts the React default**. In React everything is JS until you ask for static. In Astro everything is static until you ask for hydration.
>
> That inversion isn't performance. **It's design.** It changes which decisions you make without thinking. And the decisions you make without thinking are the ones that define your architecture long-term."

---

## Hands-on II: Library (min 45-70)

### The longest block. Watch the clock.

### Your live plan

1. **Min 0-3**: setup. Everyone runs:
   ```bash
   pnpm db:migrate:local
   pnpm db:seed:local
   pnpm dev
   ```
2. **Min 3-6**: UI tour. Register, login, add book.
3. **Min 6-15**: code tour. **Don't read everything. Show the key pieces**:
   - `wrangler.toml` — declarative binding of D1 and DO
   - `src/index.ts` — Hono routes, show a public endpoint and one with auth
   - `src/session-store.ts` — the full Durable Object (it's small, read it whole)
   - `src/auth.ts` — explain PBKDF2 in 30 seconds
4. **Min 15-25**: the DO discussion. This is the most important part of the workshop.

### When they reach the DO

**Long pause here.** It's the newest concept. They've probably never used anything like it.

> "Question for you: in any app you've built — where do you store sessions?
>
> [Wait for answers: 'in a table', 'in Redis', 'in JWT'.]
>
> OK. And why does each of those have **problems**?"

Guide them to:
- SQL → latency, load on the DB
- Redis → another service to maintain, single point of failure
- JWT → can't revoke without a blacklist

> "The Durable Object is **a new primitive**: it gives you consistent serverless state.
>
> This didn't exist 3 years ago. It's genuinely new. And it solves a problem that in other stacks you'd solve by stacking Redis + Postgres + custom logic."

### The rule that generalizes

This slide is core to your identity as a security engineer:

> "Every AI tool is an authenticated endpoint.
>
> If you wouldn't expose the operation as an unguarded REST call, you can't expose it as an unguarded tool either.
>
> The Zod schema isn't a security boundary. **The handler is.**"

Long pause. **This is what you learned in production**, not in a book. Tell them it's what you learned from CVE #2.

---

## Case studies: the two CVEs (min 70-78)

### How to tell them

Don't dramatize. Tell them like you tell them in the manifesto — direct, specific, with the lesson at the end.

### CVE #1

> "There was a function called `requireOrgAdmin()`. Any member of an organization was treated as admin automatically, regardless of role.
>
> Looked intentional. The pattern was old. Nobody questioned it.
>
> The security agent ran an unprompted audit. Chained with code-review. Confirmed: real privilege-escalation bug.
>
> **It would have lived in production for months.**
>
> Lesson: **what looks like a feature is sometimes a CVE.** Old code is not safe code. Old code is unaudited code with a longer rap sheet."

### CVE #2

> "The AI assistant had a tool called `get_ticket_detail`. Fetched any ticket by ID via service account. No ownership check.
>
> A user in org A could ask for a ticket from org B. And the assistant handed it over.
>
> Caught during the security audit phase of the overhaul, **before production**.
>
> Lesson that generalizes: **every AI tool is an authenticated endpoint.** That phrase is the only one you need to remember from the security block."

---

## The five scars (min 78-82)

### Why this block

Most AI talks only show wins. **You show scars.** That honesty is your credibility.

Read them fast. One by one. **Don't apologize for any of them.**

### Closing the block

> "The workflow is good. It's not magic. User feedback is still irreplaceable.
>
> If after today you think SDD will save you from everything, I failed. **It'll save you from 80%.** The 20% is still on you."

---

## The 5 rules (min 82-87)

### How to present

Five slides. One rule each. **Long pause after reading each rule.**

The rules are your signature — your manifesto. Read them with weight.

> **Rule 01 — Specs before code. Always.**
>
> If you can't write the spec, you don't understand the change. Stop typing prompts.

> **Rule 02 — One model is never the right answer.**
>
> Each model has a strength. The mix is the moat.

> **Rule 03 — Design is code. Merge it.**
>
> Architecture decisions live in version control. Not in Notion.

> **Rule 04 — "It compiles" ≠ "it works."**
>
> Verify is a phase, not a vibe.

> **Rule 05 — The AI is your junior, not your genius.**
>
> You wouldn't merge a junior's PR without reading it.

---

## The number + close (min 87-90)

### The number

> "From baseline to vivecoding: **6 months to 1 month**.
>
> Production. Multi-tenant. 78 tests passing. Two security audits.
>
> Speed **didn't come from skipping steps**. It came from parallelizing the right steps with the right models."

### Closing

> "Three things to take home.
>
> One: **discipline beats vibes.**
>
> Two: **right model, right job.**
>
> Three: **AI is an amplifier.** It doesn't replace the engineer. It makes a trained one six times faster."

Pause. Final slide:

> "Vibecoding is roleplay. **Vivecoding is a campaign with discipline.**
>
> Repos are public. Full manifesto at vivecoding.dev.
>
> Questions?"

---

## Q&A — likely questions

**Q: Which model is better, Claude or ChatGPT?**

> Depends on the work. Claude is better for long code and refactors. GPT is better for quick exploration and creativity. I use both. The right question isn't which is better — it's *for what*.

**Q: Won't we be replaced?**

> Those who don't use AI, yes. Those who use it well, no. Work moves from 'writing code' to 'designing systems and verifying AI'. More interesting, not less.

**Q: Is it worth learning React if AI writes it for me?**

> Yes. Without understanding React you can't **direct** the model when it writes React. You'll be publishing code without knowing what you publish. And when it breaks, you won't be able to fix it.

**Q: How much does this cost in production?**

> The stack I showed (Cloudflare free tier) handles up to 100k requests/day at zero cost. If your app grows, we're talking 5-20 USD/month. Cheaper than a VPS.

**Q: How do I learn fundamentals if AI gives me the answers?**

> Discipline, not technique. When you're learning something new, don't use it. When you already know what you want, use it. The difference is: am I learning, or am I executing?

**Q: Why Cloudflare and not AWS?**

> Free plan and edge model. AWS free lasts one year then charges you. Cloudflare free **is permanent** within the limits. For learning and small-to-medium apps, no contest.

**Q: What if Cloudflare shuts down one day?**

> Same answer as for any vendor: portability. Hono runs on Workers, Bun, Node, Deno. Astro generates static HTML that any server can serve. D1 is SQLite — data exports as a `.sqlite` file. The architecture I showed is portable.
