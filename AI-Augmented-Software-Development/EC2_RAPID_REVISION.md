# EC-2 — Last-Minute Notes (AI-Augmented SDLC, SEZG534)

**Read this top to bottom. It takes about 25 minutes. If you read nothing else, this is enough to write the paper.**

Nothing here is a list to memorise. Everything is explained, so if you forget the exact words in the exam, you can still work the answer out from scratch.

This paper has **zero recall questions**. Every question drops you into a situation and asks *what works, what breaks, and why*. So understanding is the only thing that scores — and understanding is exactly what this file gives you.

---

## PART 1 — The one idea the whole subject is built on

Everything in this course comes from a single clash:

> **Production software must be 100% deterministic. Generative AI is 100% probabilistic.**

A bank transfer, an auth check, a compiler build — same input, same output, every single time. But an LLM *samples* the next token from a probability distribution. Ask it the same thing twice and you can get code that quietly differs in how it handles an edge case.

You cannot pour probabilistic output into a deterministic system and hope. So the entire discipline is: **how do we build a deterministic cage around a probabilistic engine?**

Three things follow from this, and they explain almost the whole syllabus:

1. **You never trust the model — you verify it with something that cannot hallucinate.** Compilers, linters, type checkers, AST parsers, schemas, contract tests, sandboxes. Never validate an LLM with another LLM prompt alone.
2. **The bottleneck has inverted.** Writing code used to be the hard part. Now generating it is nearly free, so **reviewing, verifying and governing it** is the constraint. Every "we got faster but shipped nothing sooner" scenario lives here.
3. **Value moved to the two ends.** If the middle (typing) is free, the money is upstream in **precise intent** and downstream in **verification**. That's the *Inversion of Engineering Value*.

If a question confuses you, come back to these three. Most answers are somewhere in here.

---

## PART 2 — The whole course as one story

Read this once and the sessions stop feeling separate.

1. **A business wants something, and says it vaguely.** "Make it fast and secure."
2. **You turn vague intent into a precise, machine-readable spec** — because an agent will execute it *literally*. Say "clean up old data" and it may delete your integration tests.
3. **AI generates the code in seconds.** This part is now genuinely cheap.
4. **The code floods downstream into review, QA and deploy — which did NOT get faster.** *The pipeline jams.* This is the single most-examined idea in the course.
5. **So you mechanise the downstream:** deterministic sensors (compilers, linters, tests), contract tests, ephemeral environments per PR.
6. **To let an agent act at all, you wrap the model in a harness:** tools, permissions, sandboxes, feedback loops. `Agent = Model + Harness`.
7. **You place human gates where the blast radius is big:** production, schemas, auth, new dependencies.
8. **And you watch the money,** because every inference call has a price and software is no longer zero-marginal-cost.

That's it. That's the subject. Everything below just fills in each step.

---

## PART 3 — Why AI didn't make anyone faster

This is the heart of the paper. Expect at least one question on it.

**The 40/60 split.** A developer spends only **40% of the day writing code**. The other **60%** is understanding ambiguous requirements, cross-team API debates, deciphering legacy systems, code review, debugging distributed race conditions, and waiting on CI runners, QA environments and security sign-off.

AI accelerates the 40% by maybe 50–80%. **It does nothing for the 60%.** So halve the coding time and you've saved very little — and if unreviewed AI code doubles review time, **net productivity goes down**.

**The capability–productivity gap.** Raw generation capability is exploding. Deployed productivity — features actually earning revenue — is flat. A 500% surge in code volume yields maybe 5–10% more shipped features.

**Goldratt's Theory of Constraints** explains why, and you should name it by name:

> *The throughput of any pipeline is set by its slowest stage.*

```
Requirements → Design → CODING → Review & QA → CI/CD & deploy
 (manual)      (manual)  (AI:10x)  (BOTTLENECK)   (BOTTLENECK)
                            │            ▲              ▲
                            └─► PR flood (WIP) ─────────┘
                        traffic jam · reviewer fatigue · lead time unchanged
```

Speeding up a stage that was **never the bottleneck** doesn't help — it just piles up inventory (**WIP**, work-in-progress: open PRs, unreviewed branches) in front of the real constraint. That's a **local optimisation**.

**The fix is systemic, not local.** Stop measuring lines written and PRs opened; measure **flow efficiency** — idea to production. Subordinate the pipeline to the bottleneck: throttle creation to match validation capacity, and spend the money on automating review, staging and deployment instead of on more generation tools.

**Measure it with DORA metrics**, not activity metrics: **Lead Time for Changes, Change Failure Rate, MTTR, Deployment Frequency.** The killer line: *if lead time doesn't shrink and change failure rate rises, AI is destroying value, not creating it.*

**The analogy that scores well: Kafka backpressure.** An unthrottled producer pushing 100,000 events/sec into a consumer that writes 500/sec doesn't speed anything up — lag explodes, the broker stalls. AI is the producer; code review is the consumer.

**Also remember the honest data:**
* Only **4%** of software AI usage is extensive/autonomous; **57% is augmentative** (Anthropic Economic Index).
* **76% of developers avoid AI for deployment and monitoring; 69% avoid it for architecture** (Stack Overflow).
* Experienced maintainers were **19% slower** with early AI tools on complex tasks (METR study) — prompting and debugging unfamiliar AI code took longer than writing it.

Read all of that as one sentence: **people trust AI where the blast radius is small and refuse it where it's large.**

---

## PART 4 — How the SDLC got here

SDLC = planning, developing, testing, deploying and maintaining software, to ship **quality software that meets customer needs within cost and time**.

**Five eras. Each one killed the previous era's bottleneck — that's the only thing you need to remember, because the rest follows.**

1. **Waterfall (1970s).** Sequential, phase-gated, document-heavy. Nothing moves until the last phase is frozen. *Bottleneck:* rigid handoffs, late integration surprises, no early feedback. A defect found in production costs ~100× what it costs in requirements.
2. **V-Model (1980s).** Same sequence, but **every design stage is paired upfront with its test stage**. *Bottleneck:* still rigid; requirement changes still hurt.
3. **Agile/Scrum (2000s).** 2–4 week sprints, working software over documentation, fast customer feedback. (Descended from the Iterative (1975) and Incremental (1978) models.) *Bottleneck:* ceremonies, communication overhead, manual story writing, deploy still manual.
4. **DevOps/CI-CD (2010s).** Dev and Ops merged: automated pipelines, Infrastructure-as-Code, automated monitoring. *Bottleneck:* pipeline maintenance, flaky tests, release coordination.
5. **AI-Native/Agentic (2020s+).** Continuous synthesis of artifacts from human intent. *New bottleneck:* **verification debt, reviewer fatigue, architectural governance.**

**The hook that gets you full marks on "how has the role changed":**
> *In Waterfall you wrote specs. In Agile you wrote user stories. In DevOps you wrote pipelines. In the Agentic SDLC you write **intent and verification guardrails**.*

**The V-Model, because it comes up a lot.** Left arm decomposes (business requirements → system spec → architecture → module design), right arm verifies (unit → integration → system → acceptance). Each level pairs across.

* **Verification = "are we building the product right?"** Does it match the spec, schema, types?
* **Validation = "are we building the right product?"** Does it meet the actual customer need?

The AI angle: **AI massively accelerates the bottom of the V** (implementation, unit tests). But if the **top-left is ambiguous, AI builds the wrong system faster.** The symmetry breaks when verification is automated and human validation is neglected.

The trap this creates has a name: **circular validation**. If the AI writes both the endpoint *and* its test mock, both pass in isolation and both fail under real traffic. The AI tested its own assumptions against themselves.

**Three words people confuse — learn this, it's cheap marks:**

* **Continuous Delivery** — always in a deployable state, but production needs **a human approval click**.
* **Continuous Deployment** — every commit that passes CI goes to production, **zero humans**.
* **Release** — the **business act** of switching it on for users (flipping the feature flag).

*Deployment is technical; release is business.* A payment feature sits deployed behind a dead flag for weeks before it's released. And because AI output is probabilistic, enterprises mandate **Continuous Delivery with a human gate** — not blind Continuous Deployment — for anything high-risk.

**Four operational paradigms that sound alike:**
* **DevOps** — automates *deterministic software*: builds, tests, containers, CI/CD.
* **MLOps** — operationalises *models*: data pipelines, feature stores, training, drift monitoring. (*Data + Code = Model*.)
* **AIOps** — uses AI *on operational telemetry*: ingest logs/metrics/traces, detect anomalies, correlate a spike with a recent commit, automate root-cause analysis.
* **Agentic SDLC** — uses AI *on the engineering process itself*: eliciting requirements, writing specs, synthesising code, running test-fix loops.

> *DevOps manages code · MLOps manages models · AIOps uses models to manage operations · Agentic SDLC uses models to do the engineering.*

**And what AI actually changes per phase** — each one has a named trap, which is what the exam wants:
* **Requirements** → Intent-to-Spec (audio/notes → OpenAPI, schemas, ADRs). Trap: **omission risk** — AI misses *negative* requirements, what the system must NOT do.
* **Architecture** → AI scaffolds ADRs, suggests patterns. Trap: **architectural drift** — locally sensible fixes that violate global boundaries.
* **Coding** → copilots became multi-file agents. Trap: **review fatigue**.
* **Testing** → self-healing tests (agents fix locators when the UI changes), auto edge-case generation. Trap: **circular validation**.
* **Review** → semantic bots flag OWASP issues before a human is paged. Trap: they're advisory, never the final gate.
* **Operations** → AIOps correlates errors with recent PRs and drafts a rollback. Trap: **hallucinated fixes** — a bot must never run destructive commands.

---

## PART 5 — The five shifts, the money, and the risks

**The 5 paradigm shifts.** Don't memorise five bullets — they're one argument.

1. **Dev effort is no longer the bottleneck.** Effort scarcity used to drive MVP scope-cutting and ruthless prioritisation. Now you build three prototypes in parallel and test them with real users. Design docs stop being human coordination artifacts and become **machine-executable specifications**.
2. **Roles are less siloed.** The PM/Dev/QA/SRE walls blur. A PM ships a working prototype; a developer generates E2E tests and K8s manifests.
3. **Decisions are less "hard to change."** Regenerating code is cheap, so "disposable microservices" become tempting. **But: code logic is disposable, persistent data is NOT.** Rewriting a service is an afternoon; migrating a multi-terabyte schema is still a one-way door.
4. **Accountability is foggier.** AI writes 80% of the PR — so who's liable? **The human who approves and commits carries 100%.** "The AI generated it" is not a defence, legally or in a compliance audit.
5. **Outcomes are probabilistic.** Same prompt, different output. So binary assertions (`assert result == 42`) must be supplemented by **Evals** — scored benchmarks for semantic consistency, hallucination rate, toxicity.

**The Inversion of Engineering Value.** Value migrates away from whatever becomes abundant and free. Writing a FastAPI endpoint now costs ~$0, so value moved **up** (intent, specs, invariants) and **down** (review, verification harnesses). Typing sits at the bottom of the new stack.

The four competencies that replaced typing: **intent articulation & architectural control · systematic verification & QA · multi-agent orchestration · human judgment & accountability.**

**Software economics broke in three places:**

1. **The end of zero marginal cost.** Traditional software: build once, serve 100k users for fractions of a cent, **80–90% margins**. AI software: every transaction burns inference tokens and vector lookups, so **COGS scales with usage**. One unoptimised agent loop on every click can destroy gross margin. **High-volume paths must use deterministic code** — regex, a SQL index, a cached lookup — not an LLM call.
2. **"Build vs Buy" became "Token cost vs Human labour."** The new equation is `inference cost + senior verification cost`, compared against full human execution cost. If juniors generate mountains of code that seniors decipher for hours, **total delivery cost exceeds writing it by hand.** (Related: COCOMO and lines-of-code estimation are dead — AI writes 50,000 LOC in an afternoon; what matters is time to verify and safely ship.)
3. **Per-seat pricing collapses into outcome-based pricing.** If agents do the work, you need fewer seats. Pricing moves to **per resolved ticket, per automated deployment**. Architects must track system-level outcomes as telemetry, not logins.

**The story that makes it concrete:** a fintech team replaced an 18-minute, $12/day deterministic Python ETL with an "agentic pipeline". 40,000 records had date-format variations, the agent entered an unconstrained reasoning loop at 8 LLM passes per record, and in 48 hours burned **$41,800 in tokens**. Runtime hit 14 hours; margin went from **+82% to −18%**. *Code is cheap. Inference and unverified logic are not.*

**The risks AI amplifies** — four families, so you can reproduce them:
* **Code quality & security:** plausible-but-insecure code · hallucinated dependencies · missing edge cases in generated tests · architectural drift and "code slop" · code bloat · context blindness.
* **Human factors:** reviewer fatigue · atrophy of fundamental skills (fast answers kill the serendipitous learning you get from reading real docs).
* **Legal/IP/compliance:** licence contamination, algorithmic auditability, accountability in an audit.
* **Economic/operational:** runaway token spend, unbounded loops, unpredictable COGS.

Plus two distinctions worth a mark each:
* **Technical debt vs unfinished backlog.** Unfinished backlog = work deferred to next sprint. Technical debt = *compromised quality* that accrues interest. AI creates **instant technical debt** — code that passes unit tests but violates enterprise patterns and duplicates abstractions.
* **Errors now happen at machine scale.** A human makes mistakes at 100 lines/day. An agent propagates one security misconfiguration across 50 microservices in 3 minutes.

**Slopsquatting** — know this cold, it's a favourite:

1. The LLM needs a library that doesn't exist and **hallucinates a plausible name** (`fast-crypto-auth-jwt`) instead of failing.
2. Attackers prompt public models thousands of times, **catalogue the hallucinated names**, and pre-register them on npm/PyPI with a trojan inside.
3. A developer or agent commits it. CI runs `npm install`.
4. **The malware executes with the full privileges of the CI runner** — AWS keys, DB secrets, backdoored production builds.

Three defences, all **computational**: **private proxy registry** with allow-listing (kill direct public registry access) · **provenance gate** (reject packages younger than ~30 days, or below download/reputation thresholds, or unsigned) · **lockfile integrity plus a HITL gate** (agents computationally barred from editing `package.json`; new dependencies need a security architect's sign-off).

Notice you never ask an LLM *"is this package safe?"* — that would be an inferential control doing a computational control's job.

---

## PART 6 — What's actually inside the model

**AI has four core capabilities** — this is the frame Session 4 opens with:
* **Learning** — improving from data instead of hardcoded rules. Rule-based AI (expert systems, knowledge graphs) is AI with *zero* learning. ML splits into **supervised** (labelled), **unsupervised** (finds clusters), **reinforcement** (rewards/penalties), **deep learning** (many-layered networks).
* **Reasoning** — connecting facts to derive conclusions: symbolic logic (guaranteed deductions), probabilistic inference (Bayesian, incomplete data), chain-of-thought (neural, step-by-step).
* **Perception** — raw sensor data → meaning: computer vision (CNNs, Vision Transformers), speech/audio, multimodal fusion.
* **Problem-solving/action** — goal state + a path to it: search and optimisation (A*, Monte Carlo Tree Search) and **agentic planning** (decompose, call tools, check, re-plan). That last one is the bridge to agents.

*All ML is AI, but not all AI is ML.*

**Four eras of AI:** symbolic logic (1950s–80s: deterministic, explainable, brittle) → classical ML (1990s–2010s: statistical classifiers, hand-engineered features, can classify but not generate) → deep learning and foundation LLMs (2017–2023: transformers, self-supervised, generate code) → **test-time compute and reasoning models** (2024+: hidden chain of thought, verify before answering).

**Self-supervised learning** is why any of this exists. Supervised learning needed humans to label everything — an impossible bottleneck at web scale. The breakthrough: **the data labels itself**. Give the model `def add(a, b): return a + ` and train it to predict the masked next token. Run that over petabytes of code and it learns syntax, API signatures and idioms unsupervised.

**What that means for you, and it's the line examiners want:** the model has **no fact database and no verification engine**. It's a *pattern completion* engine. **If your prompt begins a buggy pattern, it will faithfully complete the buggy pattern.** It doesn't understand Python — it knows the probability distribution of tokens after a Python function header.

**The Transformer (2017)** replaced RNNs because RNNs read token-by-token — unparallelisable and forgetful over distance. Transformers ingest the whole sequence at once. Each token emits three vectors: **Query** ("what am I looking for?"), **Key** ("what do I contain?"), **Value** ("what do I carry?").

```
Attention(Q,K,V) = softmax( Q·Kᵀ / √dₖ ) · V
```
`Q·Kᵀ` scores every token against every other; `÷√dₖ` stops the dot products exploding into tiny-gradient regions; `softmax` normalises to a probability distribution. In code terms: a variable on line 300 can pay direct attention to its declaration on line 5, regardless of distance.

**The catch you must always mention: attention is O(N²) in context length.** Double the prompt, quadruple the compute. This one fact explains why huge contexts are slow and expensive — *and* why character-level tokenization was rejected.

**System 1 vs System 2** (Kahneman, *Thinking, Fast and Slow*):
* **System 1** = standard LLMs. One forward pass, fixed compute per token, no planning. Fast, cheap, and emits what *looks* probable. Good for boilerplate, docstrings, simple CRUD.
* **System 2** = reasoning models. **Test-time compute**: hundreds of hidden scratchpad tokens generating hypotheses, simulating execution, pruning bad branches, verifying — *before* the first answer token. Slow, expensive (you're billed for the thinking), but far safer on edge cases. Use for concurrency, distributed systems, architecture, security review.

**The example that makes it land:** Copilot writes a Redis distributed lock — `client.SetNX(ctx, key, "locked", 0)`. Compiles, passes a simple unit test. But TTL = 0 means **no expiry**. A worker crashes holding the lock, 50 K8s workers queue behind it, the pipeline deadlocks, $1.8M in payments stall. *System 1 outputs what looks probable, not what survives distributed edge cases.*

**S2A (System 2 Attention)** solves a different problem: self-attention attends to *everything*, including banter, stale comments and misleading hints. That dilutes reasoning and causes **sycophancy** (the model agreeing with your wrong premise). S2A has the model **rewrite and denoise your prompt first**, then reason over the clean version. It's an early example of **inference scaling** — add a step between input and response and the output improves.

**Match the engine to the task:** deterministic linters for formatting and secrets (microseconds, free, certain — *never spend tokens checking indentation*) · System 1 for autocomplete and docstrings (latency keeps you in flow) · System 2 for concurrency, architecture and security.

Two lines worth quoting: **"Copilot is a harness, not a model"** (it's an IDE integration; swap the engine underneath). And **"rule-based AI is more important than ever"** — compilers and linters are the deterministic guardrails that catch non-deterministic errors.

---

## PART 7 — Tokens and context, where most things actually break

**A token** is a chunk of text — a character, word, or fragment (`-tion`). **1 token ≈ 4 characters of English ≈ 0.75 words.** Punctuation, spaces and newlines all consume tokens.

**Why tokens and not words or characters?** Three reasons: tokens are *meaningful components* of words · there are far fewer unique tokens than words, so the **vocabulary stays small and the model efficient** · and unknown words can be **composed from familiar fragments**.

**The taxonomy, and why the industry picked what it picked:**
* **Character-level** — tiny vocabulary, but sequences explode **5–10×**. With O(N²) attention that's computationally impossible. ❌
* **Word-level** — short sequences, but the vocabulary hits millions and every unseen identifier or typo becomes `<UNK>`. Useless for code. ❌
* **Subword (BPE / SentencePiece)** — frequent words whole, rare words split into common fragments. Balanced vocabulary (~50k–128k), moderate length. ✅ **The standard.**
* **Code-aware** — subwords *plus* whole indentation blocks, AST-informed. **~50% fewer tokens on code.** ✅ Modern frontier models.

**How the model sees your code.** Humans read semantically; the tokenizer splits statistically by training frequency. So `import` is **1 token** but `fetchUserAccountLedgerBalance` is **5–6**. Cryptic identifiers are expensive.

Three blind spots follow:
1. **Character-level tasks fail.** "How many r's in strawberry", "reverse this string", "slice at offset 17" — the model never sees letters, only integer IDs. **Anti-pattern. Delegate it.**
2. **Custom-identifier bloat** silently eats your budget.
3. **Indentation drift** — old tokenizers encoded four spaces as four tokens, burning **30–40% of context** on whitespace in nested Python. Modern tokenizers chunk indentation, track character offsets alongside token positions, and train on AST-annotated data.

**The context window** is the **hard ceiling on input + output tokens in one call**. Everything counts: the system prompt, the *entire* conversation history (yours and the model's), the current prompt plus attachments, **and the response being generated right now**.

**The four failure modes — this is high-yield:**

1. **Attention dilution, "Lost in the Middle."** Retrieval accuracy is **U-shaped**: strong at the start (primacy) and end (recency), dropping up to **50% in the middle**. Rules buried in the centre are simply ignored. → **Fix: context ordering.** Invariants at the **top**, immediate intent and schema at the **bottom**.
2. **Silent degradation.** No error is thrown — quality just decays, edge cases get skipped. → **Fix: prune context**, sliding windows, targeted RAG instead of dumping the repo.
3. **Inconsistent behaviour.** Add one unrelated file and the whole attention distribution shifts; yesterday's working prompt fails. → **Fix: temperature 0 + seed pinning.**
4. **Cascading failures in agentic loops.** One bad early tool output pollutes history; every later turn reasons over corrupted data. → **Fix: validate each tool output before appending it.**

(Also name **quadratic cost/latency** and **hallucination under saturation** past ~90% capacity.)

**The scenario to quote:** a compliance screener dumps a 150-page manual into the middle of a 128k prompt. On page 78 sits *"any wire over $10,000 to an unverified offshore account needs human 2FA."* A $95,000 offshore wire gets auto-approved, because the model read the header and the user message and never saw the middle. **A big context window is not RAM. Attention is a scarce, decaying resource.**

**System-level guardrails — "prompting is not engineering."** Asking nicely for valid JSON still fails 2–5% of the time, and in an automated pipeline 2% is catastrophic. So you enforce correctness *outside* the network:

* **Tool latching / code interpreters.** Don't let the model *guess* maths, dates or string slicing. Have it **write a script, run it in a sandbox, read back the deterministic answer.** **LLMs are reasoners, not calculators.**
* **Constrained decoding / logit masking.** The model emits **logits** (a probability per vocabulary token). A grammar or JSON Schema intercepts generation **token by token** and forces any syntax-violating token's probability to **zero**. The model is **mathematically prevented** from emitting invalid JSON — not asked nicely, *prevented*.
* **Compilers and AST interceptors on the way out.** Run the output through Tree-sitter and `tsc`/`mypy`, and feed the diagnostics **back into the model** for self-correction before a human ever looks.

**Tokenomics** — the economics of all this: the black box of AI billing · hidden costs beyond the visible token (retries, hidden reasoning tokens, re-sent history) · inability to compute ROI · inefficient model routing and waste.

Four professor's rules worth repeating: **context windows are the new RAM** (never run an agent without tracking token usage) · **never put critical rules in the middle** · **conversational chatter burns budget** (it's re-sent on every turn — write imperative machine instructions) · **never ask an LLM to count characters.**

---

## PART 8 — Agents and the harness

**An AI agent** is an autonomous entity that **perceives** its environment, **decides** using a reasoning model, and **acts** through tools to reach a goal. Unlike static rules or a one-shot LLM, it runs a loop:

```
PERCEIVE → REASON → ACT → EVALUATE → (repeat until goal or budget)
```

Critically: agents operate **with autonomy inside defined boundaries**. The boundaries are the whole point.

**SWE-agent** (Princeton) is the canonical example: a coding agent whose **environment is the computer** — terminal and filesystem — with actions to navigate the repo, search, view and edit files, through an **Agent-Computer Interface (ACI)**.

**The five classical agent types** (Russell & Norvig), easiest remembered as increasing sophistication: **simple reflex** (IF/THEN, ignores history — a linter) → **model-based reflex** (keeps internal state — remembers which files it changed) → **goal-based** (plans a path to a target state — GPS) → **utility-based** (scores trade-offs when goals conflict — speed vs token cost) → **learning** (adapts strategy from outcomes).

**The master equation:**

```
AGENT = MODEL + HARNESS
```

The **model** is raw probabilistic intelligence. On its own it cannot read a file, run a command, check a permission, or judge blast radius. The **harness** is everything else: managing state and history, assembling and pruning context, executing tools in sandboxes, intercepting actions to enforce policy and rate limits, and parsing compiler/test output back into a feedback signal.

**Karpathy's analogy, worth quoting:** if the **LLM is the CPU** and the **context window is the RAM**, the **harness is the operating system kernel** — I/O, device drivers (tools), permissions, scheduling, security sandboxes.

Harnesses come in three layers by who owns them: the **coding harness** (built into the tool, owned by the SDK maker) · the **user harness** (what your team adds — convention files, MCP servers, eval loops) · the **team/org harness** (the platform layer — agent registry, permissions, governance, HITL, measurement).

**The cybernetic governor** — the single cleanest framing in the course:
* **Guides (feedforward)** steer the agent **before** it acts: system prompts, design specs, convention files (`AGENTS.md`, `CLAUDE.md`), API schemas, few-shot examples.
* **Sensors (feedback)** catch deviation **after** it acts: linters, compilers, type checkers, unit/integration tests, ArchUnit structural tests, security scanners.

**Computational vs Inferential controls** — and this decides most guardrail questions:

* **Computational** — deterministic code on CPUs: compilers, AST validation, type checkers, schemas, regex, permission checks, unit tests. Microseconds, free, **100% certain, cannot be hallucinated or prompt-injected**.
* **Inferential** — probabilistic evaluation on GPUs: LLM-as-a-judge, semantic PR review. Seconds, costs tokens, 90–98% accurate, prone to false negatives and sycophancy.

> **The rule: computational controls must be the final gate before production. Inferential controls are advisory only, never sufficient alone.**

**Five layers of AI engineering, and the centre of gravity keeps drifting away from the model:**

1. **Prompt engineering** (2022–23) — *how do we talk to the model?* Words and phrasing.
2. **Context engineering** (2024–25) — *what does the model know?* RAG, token budgeting, structuring.
3. **Harness engineering** (2026) — *how is the model allowed to act?* Tools, permissions, feedback loops.
4. **Loop engineering** (emerging) — *how does one agent self-correct?* Act → test → adjust until the goal is met, with retry caps.
5. **Graph engineering** (frontier) — *how do many agents coordinate?* Nodes (LLM calls, functions, routers, verifiers, human approvals), edges (what runs next), shared state.

**The three-layer operating model:**
* **Spec layer** — *what* must be built. Human-authored intent and architectural constraints.
* **Harness layer** — *what is allowed* to happen. Sandboxes, permission firewalls, test runners.
* **Loop layer** — *how* the work gets done. The agent's act-evaluate-correct cycle until convergence.

**And the three gates of autonomy — match the gate to the blast radius:**
* **HITL (human-in-the-loop)** — approve every action. Production deploys, DB migrations, auth, payments, new dependencies.
* **HOTL (human-on-the-loop)** — agent runs free, humans watch dashboards and intervene on exceptions.
* **Bounded autonomous** — fully independent inside a sandbox. Docstrings, formatting, internal renames, running local tests.

**The cautionary tale:** an agent with unrestricted shell on a CI server hits a permission conflict, tries `sudo rm -rf`, path expansion fails, it escalates to `sudo rm -rf /* --no-preserve-root`, and wipes the host — secrets, worktrees, Docker daemons. **Never give an uncaged agent shell access. Ephemeral non-root containers, always. And always cap the loop** — no timeout and no token ceiling means infinite looping on an unfixable test, burning hundreds of dollars.

---

## PART 9 — Context, prompts, RAG, and MCP

**Context engineering** is deliberately designing, structuring and optimising what the model sees — *filling the context window with just the right information at each step of the agent's trajectory*. It matters because LLMs have **no long-term memory**; they generate **solely** from the context available at inference time.

Its steps: **selection → structuring → prompt design → compression → sequencing → tool and memory integration.**

The hierarchy that clears up a lot of confusion:

```
CONTEXT ENGINEERING  (everything the model sees)
├── Prompt engineering  (just the instruction you write)
└── RAG                 (external documents pulled in)

Engineering a user harness is a specific form of context engineering.
```

**Prompt engineering** is human-to-AI communication — a real skill. *"The problem is when prompt engineering is the only thing people know."* Three techniques: **zero-shot** (no examples) · **few-shot** (a few worked examples showing the task and output format) · **chain-of-thought** (reason step by step before concluding). And **system prompt** (developer's instructions) vs **user prompt** (end user's) — both consume context.

**RAG in four steps:** **ingestion** (chunk documents, store as vectors) → **retrieval** (match your question by *meaning*) → **augmentation** (paste the chunks into the prompt) → **generation** (the LLM answers, grounded). It's the alternative to brute-force context stuffing — retrieve what's relevant instead of dumping 100,000 lines and losing the middle.

**Prompting vs fine-tuning** hinges on one question: **does it update the weights?** Prompting doesn't — zero upfront cost, instant iteration, **model-agnostic** (move your prompts to another provider), but bounded by the context window and paying token cost on every call. Fine-tuning does — high upfront compute and dataset curation, permanently instils domain vocabulary and rigid syntax, cuts per-call tokens and latency, but **locks you to a base model** and risks **catastrophic forgetting** of general reasoning.

**The cleanest table in the course — Prompt vs Context vs Harness:**

| | Prompt | Context | Harness |
|---|---|---|---|
| What it is | the task | the reference material | the testing machinery |
| Audience | the LLM | the LLM | **the AI engineer** |
| Lives in | user input / app logic | system instructions / vector DB | CI/CD pipeline / test suite |
| **Goal** | **right answer now** | **prevent hallucinations** | **prove it works at scale** |

Memorise that last row.

**AI engineering inverted traditional ML engineering.** Classic ML: gather data → train → evaluate offline → build product *last*; focus on loss functions and F1 scores, with model and product development disjointed. Modern AI engineering: **build the product first**, call a foundation-model API, optimise harness and context, and invest in data or fine-tuning **only if the product shows promise**. Focus is UX, guardrails, latency, cost, reliability.

**MCP (Model Context Protocol)** — an open standard connecting AI applications to external systems. **"A USB-C port for AI."** Before it, wiring an agent to Postgres + GitHub + Slack + Jira meant **N × M bespoke integrations**.

Three participants:
* **Host** — the AI application that coordinates and manages one or more clients (Claude Desktop, Cursor, your agent runner).
* **Client** — lives inside the host, maintains a **1:1 connection** to one server, discovers its capabilities.
* **Server** — a lightweight program exposing **Tools** (callable functions), **Resources** (readable data) and **Prompts** (templates).

Messages are **JSON-RPC 2.0**, over two transports:
* **`stdio`** — OS process pipes. Fast, synchronous, process-isolated, **zero network ports**. → **local resources, on-prem databases.**
* **`SSE`** — HTTP streaming. Asynchronous, network-routable, TLS/OAuth2. → **remote cloud services, third-party APIs.**

**The security point that scores:** credentials live in the **server**, not the model. The LLM asks for a capability; the server decides how — and whether — to execute it. That makes MCP a natural **permission firewall**.

**Engineering AI-enabled systems (CMU SEI).** Introducing ML changes the lifecycle mainly through **data centricity** and **probabilistic uncertainty** — but existing software design techniques remain the right starting point. What changes is **which quality attributes you prioritise**: **verifiability** (deterministically prove the artifact meets requirements before release) · **explainability & traceability** (immutable audit log of why the agent chose a tool and what it ingested) · **data centricity & provenance** (lineage, freshness, classification of everything in context) · **change propagation & regression safety** (editing a system prompt must not silently break 20 downstream services).

> **The line to quote: "Invest in systems, not just models."**

---

## PART 10 — Spec-Driven Development, and the two official sample questions

**The problem:** handoffs are a **telephone game**. PM → architect → developer → QA, and intent degrades at every boundary. QA finally discovers the built system isn't what the business asked for — after all the money is spent.

**Vibe coding** is typing loose prompts, accepting blindly, and tweaking until it *looks* like it works. Catastrophic debt, missing edge cases, zero architectural cohesion.

**Spec-Driven Development (SDD)** makes **the specification the single source of truth**. Humans spend their cognitive effort upfront on structured, version-controlled specs; agents generate code strictly against them under deterministic test verification. *This is the natural conclusion of the whole course: if code is cheap and intent is precious, the artifact worth reviewing is the spec.*

**Three canonical files:**
* **`requirements.md`** — **WHAT**: user stories, business motivation, functional and non-functional constraints, EARS-style (Given-When-Then) acceptance criteria.
* **`design.md`** — **HOW**: component topology, data flow, strict API schemas (OpenAPI/Protobuf), DB schemas and indexing, state machines, **ADRs** with trade-offs.
* **`tasks.md`** — **IN WHAT ORDER**: bite-sized independently testable units, explicit dependency graph, verification steps per task.

**Steering files** (`AGENTS.md`, `CLAUDE.md`, `.cursorrules`) put enterprise conventions permanently in the agent's context — *"every endpoint must enforce JWT auth and emit an audit log."* Those are feedforward **guides**.

### Official sample Q1 — "disposable microservices"

*An architect says: "code generation is free, so no more refactoring and no more unit tests. When requirements change we update the spec and regenerate the service from scratch."*

**Part A — evaluate against the Inversion of Engineering Value.** He got the **first half right** (syntax is a commodity, marginal cost ≈ 0) and the **second half exactly wrong**. Value migrated **upstream to specification precision** and **downstream to verification harnesses and invariants** — so "no more unit tests" attacks precisely the half that now carries the value. Because output is probabilistic, it cannot be trusted without a deterministic harness; a spec states *intent* and can't catch low-level edge-case regressions. **Value comes from designing immutable invariants and automated gates, not from throwing code away.**

**Part B — the downstream maintainability risks. Four mechanisms:**
1. **Loss of tacit knowledge.** Years of undocumented fixes — API rate-limit workarounds, socket timeouts, deadlock mitigations, compliance edge cases — never make it back into the spec. Regeneration **wipes them and reintroduces dozens of solved bugs.**
2. **Non-deterministic behavioural drift.** Regeneration produces different algorithms, pooling, concurrency models, subtle schema variations. Neighbouring services depending on stable timing and error semantics **fail unpredictably.**
3. **The validation paradox.** Killing unit tests destroys the harness, leaving **zero automated proof** the new service honours system invariants. Pure **validation debt**, pushed onto manual E2E or production monitoring.
4. **Supply-chain re-ingestion.** Each regeneration re-picks dependencies → **slopsquatting** and fresh CVEs.

### Official sample Q2 — 40% more PRs, lead time unchanged

*200 developers get AI licences. PR throughput +40%. Lead time stays at 4 weeks. Developers say they write faster but wait for QA environments and fight deploy configs.*

**Part A — why.** Name **Goldratt's Theory of Constraints**: lead time is set by the slowest stage, and **coding was never the constraint**, so this is a **local optimisation**. Mechanically: 40% more PRs with unchanged review/test/deploy capacity floods the pipeline with **WIP**; seniors hit **cognitive fatigue** parsing AI PRs; queues, merge conflicts and context switching explode. And they optimised an **activity metric** (PR throughput) while the **DORA Lead Time for Changes** — the only one tied to customer value — never moved.

**Part B — local optimisation → systemic enablers.** Map the value stream and measure **flow efficiency**, not lines or PRs. **Subordinate the pipeline to the bottleneck**: throttle creation to validation capacity and redirect investment from generation tools to downstream enablement. Adopt **balanced DORA metrics** — lead time, change failure rate, MTTR together.

**Part C — the two technical foundations.**
1. **On-demand ephemeral preview environments + declarative CI/CD** (Kubernetes, Docker, Terraform), spun up per PR and torn down. Kills "waiting for QA environments" and staging contention.
2. **Deterministic verification harnesses + automated contract testing** — Pact (consumer-driven contracts), Testcontainers (real disposable containers instead of misleading mocks), AST linters in CI. **AI code is validated against rigid contracts before a human opens the PR** — which de-constrains exactly where the bottleneck sits.

---

## PART 11 — How to actually write the answer

Every 3-mark sub-part is three bullets, one mark each:

```
1. DIAGNOSE — name the exact principle.
   "This is a local optimisation trap under Goldratt's Theory of Constraints."

2. MECHANISM — the chain of cause and effect.
   WIP bloat → reviewer fatigue → queues → lead time unchanged.

3. FIX — a named engineering countermeasure.
   Contract tests in CI, ephemeral per-PR environments, HITL dependency gate.
```

**No introduction. No conclusion.** The first sentence names the principle.

Four things that lose marks: generic openers ("in today's fast-paced world…") score **zero** · word count scores nothing — the professor said explicitly to be short and crisp · vague fixes ("add more testing") score nothing, name the tool · and bleeding points across sub-parts wastes the time you needed elsewhere.

**Budget: 3 minutes per mark.** 3-mark part = 9 minutes. 6-mark question = 18. There's **no choice on this paper**, so an unanswered part is a guaranteed zero — never overrun.

---

## PART 12 — Number hooks

Numbers are cheap marks because they're specific. These are the ones that recur:

* **40 / 60** — coding vs everything else in a developer's day.
* **3 minutes per mark** — 90 minutes ÷ 30 marks.
* **5 / 6** — questions on the paper, each with 2–3 equal sub-parts.
* **4% / 57% / 36%** — AI usage that is extensive / augmentative / at least a quarter of tasks.
* **76% / 69%** — developers avoiding AI for deployment & monitoring / for architecture.
* **19%** — how much *slower* experienced maintainers were with early AI tools (METR).
* **100×** — cost of fixing a requirements defect in production vs at requirements time.
* **1 token ≈ 4 characters ≈ 0.75 words**; 100 tokens ≈ 75 words.
* **~50%** — token reduction from code-aware tokenizers; also the retrieval accuracy drop in the middle of a long context.
* **30–40%** — context burned on indentation by old tokenizers.
* **2–5%** — failure rate when you merely *ask* for valid JSON. Why constrained decoding exists.
* **O(N²)** — attention scaling with context length.
* **~30 days** — minimum package age in an anti-slopsquatting provenance gate.
* **$41,800 / 82% → −18%** — the runaway agentic ETL and its margin collapse.
* **$1.8M** — payments stalled by the TTL=0 Redis lock.
* **2017** — the Transformer. **2022–23 / 2024–25 / 2026** — prompt / context / harness engineering eras.
* **80–90%** — traditional software gross margins, before inference costs arrived.

---

## PART 13 — Confusion traps

Things that look alike and aren't. Each one is a cheap mark if you get it right and a lost mark if you don't.

* **Verification vs validation.** Building it *right* (spec conformance) vs building the *right thing* (customer need).
* **Continuous Delivery vs Continuous Deployment vs Release.** Human click before prod / no human at all / the business switching it on.
* **Deployment vs release.** Technical vs business. Code can be deployed for weeks before it's released.
* **DevOps vs MLOps vs AIOps vs Agentic SDLC.** Code / models / models watching operations / models doing the engineering.
* **Technical debt vs unfinished backlog.** Compromised quality that accrues interest vs work simply deferred.
* **Computational vs inferential controls.** Deterministic CPU checks that must be the *final gate* vs probabilistic LLM judgement that is *advisory only*.
* **Guides vs sensors.** Feedforward, before the action vs feedback, after it.
* **HITL vs HOTL vs bounded autonomous.** Approve everything / watch and intervene / run free inside a sandbox.
* **Prompt vs context vs harness.** Right answer now / prevent hallucinations / prove it works at scale.
* **Prompt engineering vs context engineering.** Prompt engineering is a *subset*. Context engineering covers everything the model sees.
* **RAG vs fine-tuning.** External dynamic data in the prompt vs permanently changed weights.
* **System 1 vs System 2.** Single forward pass vs test-time compute on a hidden scratchpad.
* **Character vs word vs subword tokenization.** Sequence explosion / vocabulary explosion / the balanced winner.
* **`stdio` vs `SSE`.** Local pipes, no network ports vs remote HTTP streaming.
* **Code vs data.** Code is disposable; schemas, ledgers and IAM are one-way doors.
* **Circular validation.** AI writing both the code and its tests is not verification — it's the same assumptions checking themselves.
* **Augmentation vs autonomous replacement.** AI suggests and a human accepts vs AI acts unchecked. Only 4% of real usage is the latter, and it's unacceptable for anything high-risk.

---

## PART 14 — The 3-minute brain dump

Eleven blocks. If you get five minutes before the paper, write them on the rough sheet in this order — each is about 20 seconds of writing, and almost every answer is assembled from them.

### 1. The core tension

- Systems must be **deterministic**. Models are **probabilistic**.
- Therefore: **never verify an LLM with another LLM.**

### 2. Bottleneck inversion

- Generation is cheap, so **verification is now the constraint**.
- **40/60** — only 40% of a developer's day is coding.
- **Goldratt:** throughput is set by the slowest stage. More PRs means more **WIP**, not more value.
- Measure **lead time, change failure rate, MTTR** — never PR throughput.

### 3. Inversion of engineering value

- Syntax became free, so value left the middle of the stack.
- It moved **up** — into intent, specs and invariants.
- It moved **down** — into review and verification harnesses.

### 4. Agent = Model + Harness

- **Guides** are feedforward: specs, system prompts, `AGENTS.md`. They act **before**.
- **Sensors** are feedback: linters, compilers, tests. They act **after**.
- **Computational** controls are the final gate. **Inferential** controls are advisory only.
- Three layers: **Spec → Harness → Loop.**
- Three gates: **HITL, HOTL, bounded autonomous.**
- Karpathy: LLM is the CPU, context is the RAM, **the harness is the kernel**.

### 5. The four context failures

1. **Lost in the middle** — attention is U-shaped, so the centre gets ignored.
2. **Silent degradation** — no error is thrown, the code just gets worse.
3. **Inconsistent behaviour** — one extra file shifts the whole attention distribution.
4. **Cascading agent failures** — one bad tool output poisons the rest of the history.

Fixes: put critical rules **top or bottom**, prune the context, set **temperature 0**, and **checkpoint every tool output** before appending it.

### 6. The three guardrails

- **Tool latching** — a sandbox does the maths and the string work, not the model.
- **Constrained decoding** — any token that breaks the schema gets probability zero.
- **AST plus compiler** — diagnostics are fed back to the model for self-correction.
- Two numbers to carry: attention is **O(N²)**, and **1 token ≈ 4 characters**.

### 7. Inside the model

- Self-supervised next-token training makes it a **pattern completer, not a reasoner**.
- **System 1** is a single forward pass. **System 2** spends test-time compute on a hidden scratchpad.
- **S2A** denoises the prompt before reasoning on it.

### 8. Economics

- Zero marginal cost is dead — **COGS now scales with inference**.
- "Build vs buy" became **token cost plus verification cost, versus human labour**.
- Per-seat pricing is collapsing into **per-outcome pricing**.

### 9. Slopsquatting

- The model hallucinates a package name, an attacker registers it, CI installs it, and **the runner's credentials are stolen**.
- Defend with three computational controls: a **private proxy registry**, a **package age and provenance gate**, and a **human gate on new dependencies**.

### 10. MCP

- **Host** coordinates, **Client** connects 1:1, **Server** exposes Tools, Resources and Prompts.
- Messages are **JSON-RPC 2.0**. Transport is **`stdio` for local**, **`SSE` for remote**.
- Credentials live in the **server**, never in the model — that is what makes it a permission firewall.

### 11. Spec-Driven Development

- **`requirements.md`** is what, **`design.md`** is how (plus ADRs), **`tasks.md`** is the order.
- The disposable-microservice fallacy fails on four things: **lost tacit knowledge**, **behavioural drift**, **the validation paradox**, and **supply-chain re-ingestion**.

---

**And the shape of every answer, written at the top of the sheet:**

> **1. Name the principle. 2. Explain the mechanism. 3. Give the named fix.**
> Three minutes per mark. No preamble. Be crisp.

Good luck. Name the principle in the first sentence and the rest writes itself.
