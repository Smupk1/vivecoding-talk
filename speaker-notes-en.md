# Speaker Notes — Vibe Coding Workshop (English)

> Extended notes for the speaker. What to say, where to pause, what questions to ask, where you might lose the audience.

**Audience**: upper-year CS students. They already code. They know what an API, a database, an HTTP request is. Don't insult their intelligence with basics — but don't assume they've thought about architecture either.

**Total duration**: 90 minutes. Keep a discreet timer.

---

## Block 1: What is vibe coding? (min 5-15, 10 min)

### What to say

> "Before we touch code, let's agree on what we're talking about.
>
> In February 2025, Andrej Karpathy — one of the OpenAI founders, later at Tesla — tweeted a term: **vibe coding**.
>
> His original definition was almost a joke: 'you give in to the vibes, you forget the code exists'. But the term went viral and got distorted.
>
> Today two opposite camps use it:
> - The **fans**: 'this is the future, we don't need to know how to code'
> - The **critics**: 'this is a recipe for disaster'
>
> I think **both are wrong**, and that's why this talk."

### Pause and ask

> "Raise your hand if you've ever used GitHub Copilot, Cursor, ChatGPT or Claude to write code you later committed to production."

(Wait 5 seconds. You'll see 80% of hands up.)

> "Great. The question isn't **if** you use it. The question is **how**."

### What vibe coding is NOT (slide)

Go quick. It's obvious. But the point is to **anchor** that we're not talking about the naive version.

### What vibe coding IS (slide)

Slow down here. Especially the third point:

> "**Judgment multiplier**. That word is key. If your judgment is bad, the model multiplies it. If your judgment is good, it multiplies that too. AI is not a leveler — it's an amplifier."

### Why now

Three quick points. If someone asks for benchmarks, mention:
- GPT-4 (2023) could write isolated functions
- Claude 3.5 / GPT-4o (2024) could navigate codebases
- Claude 4.x / Sonnet 4.6+ (2025-2026) can run hours of agentic work

**Trap you've seen before**: someone will ask "so won't this replace programmers?". Answer:

> "It'll replace programmers who **don't use** AI. Not those who use it well. Same story as any productivity-multiplying tool — calculators, IDEs, the internet. The work moves up the abstraction chain."

---

## Block 2: The two deadly traps (min 15-25, 10 min)

### Trap 1: No foundations

**Put weight on this.** It's the central point of the talk. Don't rush.

> "I always use this analogy: imagine someone gives you an industrial excavator. You've never driven a car.
>
> Can you 'use it'? Sure. You can turn it on, pull a lever, make a move.
>
> Do you know **what you're doing**? No. And the first time something goes wrong — and it will — you won't know where to start.
>
> That's vibe coding without foundations."

### Pause and show "The model doesn't teach you"

> "This is counterintuitive. People believe that because the model 'explains', it teaches.
>
> It doesn't teach. It **gives you the answer**. And giving you the answer is the fastest way to **not learn**.
>
> Think: how many times in class did the prof say 'I won't give you the formula, try to derive it'? That friction is where you learn.
>
> The model removes all that friction. That's why it's dangerous unless you reinstall it on purpose."

### Trap 2: Believing the model "knows"

> "The model is a statistical predictor. That sounds dismissive, but it's not. It's a technical description.
>
> What it means: the model predicts **the most likely next token** given context. And sometimes, the most likely **is not the correct one**.
>
> Real example: ask any model to use an API that changed between versions. It'll use the old version, because that was 'most common' in its training data.
>
> The fix? Read its output. Question it. Pass it updated docs. **Direct it**."

### 3-minute discussion

This is key. **Make them talk to each other first** (2 min), then take 2-3 examples out loud.

If nobody speaks, share your own: once Claude invented a `crypto.subtle` function that doesn't exist. It compiled because TS didn't catch it. Broke at runtime.

---

## Block 3: Hands-on 1 — Astro Portfolio (min 25-40, 15 min)

### Before starting

**Have them run `pnpm install` beforehand** (it's in `setup.md`). If they didn't, the first 5 min become 12.

### Your live plan

1. **Min 0-2**: You open the repo, run `pnpm dev`, show the site.
2. **Min 2-7**: Tour the structure. `src/pages/`, `src/components/`. Stop on `index.astro` and show that **it's not JSX, it's real HTML with frontmatter**.
3. **Min 7-10**: The palette change exercise. Have them open `global.css`, change colors, watch the hot reload.
4. **Min 10-15**: Astro vs Next discussion.

### What NOT to do

- Don't explain what Vite is. Lose 5 min, not the point.
- Don't explain CSS variables unless asked. Assume they know.
- Don't dive into SSR/SSG/ISR. Another rabbit hole.

### Strong pedagogical point for upper-year

> "Astro does something React/Next don't do by default: **it forces you to justify the JavaScript you ship to the client**.
>
> In React, everything is a component, everything hydrates, everything ships. It's opt-out: you have to **explicitly ask** for something to be static (RSC).
>
> In Astro it's the reverse: everything is static, you have to **explicitly ask** for something to hydrate (`client:load`, `client:idle`, `client:visible`).
>
> That inversion of default is **design**. It changes which decisions you make without thinking."

---

## Block 4: Hands-on 2 — Library CRUD (min 40-65, 25 min)

### This is the longest block. Watch the clock.

### Your live plan

1. **Min 0-3**: Setup. Everyone runs:
   ```bash
   pnpm db:migrate:local
   pnpm db:seed:local
   pnpm dev
   ```
2. **Min 3-5**: Quick UI tour. Register, login, create book.
3. **Min 5-15**: Code tour. **Don't read everything. Show the key pieces**:
   - `wrangler.toml` — declarative binding of D1 and DO
   - `src/index.ts` — Hono routes, show a public endpoint and one with auth
   - `src/session-store.ts` — the full Durable Object (it's small, read it whole)
   - `src/auth.ts` — explain PBKDF2 briefly
4. **Min 15-25**: The DO discussion. "Alternatives for sessions" slide. This is where the talk shines.

### When they reach the DO

**Pause long here.** It's the newest concept. They probably never used something like this.

> "Question for you: in any app you've built — where do you store sessions?
>
> [Wait for answers: 'in a table', 'in Redis', 'in JWT'.]
>
> OK. And why does each of those have **problems**?"

Guide them to:
- SQL table → latency, load on DB
- Redis → another service to maintain, single point of failure
- JWT → can't revoke without blacklist

> "The Durable Object is **a new primitive**: it gives you consistent serverless state. You don't maintain Redis. You don't query Postgres. And it's transactional by design.
>
> This **didn't exist** 3 years ago. It's genuinely new."

### Consistency model

If you have time, go deeper:

> "Single-threaded per instance means inside a DO, **there are no race conditions**. If two requests hit the same session, they process in order.
>
> Compare with Postgres: `BEGIN; SELECT ... FOR UPDATE; UPDATE ...; COMMIT;` — all that dance is to emulate what the DO gives you for free."

### If you have spare time (rare)

Show `/api/stats` and how the DO keeps a count of active sessions that survives cold starts. That's **live distributed state**.

---

## Block 5: Vibe coding in action (min 65-80, 15 min)

### This block closes the loop

The first two blocks were "here are tools and concepts". This block is "now let's see how to build with AI **well**".

### Bad prompt vs good prompt

Stop on each row of the table. **Don't read it — comment on it**.

> "Look at the last row. 'Show me the plan before touching code'. That phrase changes the whole dynamic.
>
> Without it, the model dumps 200 lines on you. You copy them. Maybe they work, maybe not.
>
> With it, the model tells you **what it'll do** first. You review it. Question it. Then you ask for the code.
>
> That pause is **where you live**. It's where you direct."

### Live exercise

**Be clear about rules**:

1. Plan before code.
2. Push back on at least ONE decision.
3. Explain to your partner.

Walk between desks. Look at screens. When someone has a mediocre prompt, sit next to them and improve it together.

**Most important**: when someone accepts code without reading it, stop them:

> "Hold on. What does that line do?"

If they can't answer, let them think 30 seconds. Then tell them to go back to the model and ask it to explain. Make them **investigate**.

---

## Block 6: When NOT to (min 80-90, 10 min)

### This is the honest closer

This is where most "AI is the future!!!" talks fail. Don't fail.

> "If the only lesson you take from today is **AI is great, use it always** — I failed.
>
> There are zones where vibe coding is the **wrong** choice. Recognizing them is what separates someone who knows how to use AI from someone who thinks they do."

Go through the five zones. Stop especially on #4:

> "**Code YOU couldn't write yourself.** This is the golden rule. If you were handed a system and you don't understand how it works, you're not programming — you're **maintaining a mystery**. And mysteries become crises."

### The $10,000 question

Read slowly.

> "If this breaks at 3am, can you debug it?
>
> If the answer is no — it's not your code. It's code that lives in your repo. There's a difference.
>
> In your first job, you'll be on call. They'll page you at 3am. The system will be down. And the only person who can fix it is you.
>
> At that moment, you can't ask Claude to explain code you wrote yourself 3 months ago. **That knowledge is yours, or it doesn't exist.**"

### Closing

Final slide, 5 key points. Read slowly. Then:

> "The repos are public. You'll use them for the project. If someone builds something cool on top, show me.
>
> Questions?"

---

## Q&A — likely questions and how to answer

**Q: Which is better, Claude or ChatGPT?**

> Depends on the work. Claude is better for long code and refactors. ChatGPT/GPT is better for quick exploration. I use both.

**Q: Won't we be out of work?**

> Those who don't use AI, yes. Those who use it as a multiplier, no. Work moves from 'writing code' to 'designing systems' and 'verifying AI'. More interesting, not less.

**Q: Is it worth learning React if AI does it for me?**

> Yes. Without understanding React you can't **direct** the model when it writes React. You'll publish code without knowing what you publish.

**Q: How much does this cost in production?**

> The stack I showed (Cloudflare free tier) holds a real app up to ~100k requests/day at zero cost. If your app grows past that, we're talking $5-20/month. Much cheaper than a VPS.

**Q: How do I learn the fundamentals if AI gives me the answers?**

> Force yourself not to use it when learning something new. Use it when you already know what you want. It's discipline, not technique.
