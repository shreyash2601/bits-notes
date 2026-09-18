# EC-2 Exam Cracker — AI-Augmented SDLC (SEZG534)

**Course:** SEZG534, BITS Pilani WILP · **Instructor:** Prof. Akshaya Ganesan
**Scope:** Contact Sessions 1–7 (Modules 1 & 2), plus the transition material from Session 8.

**What this file is:** the whole EC-2 syllabus in plain English, in exam order, with nothing conceptual dropped. Built from the lecture slides (CS1–CS7) and the per-lecture notes.

**How to read it:** don't memorise lists. Understand *why* each thing exists — then you can rebuild any list in the exam. This paper has **no recall questions**, so understanding is the only thing that scores.

---

## Contents

| Part | Topic | Sessions |
|---|---|---|
| 0 | Exam mechanics + the answer formula | — |
| 1 | The one idea the whole course is built on | all |
| 2 | SDLC evolution and what AI changes per phase | CS1, CS2 |
| 3 | The 5 paradigm shifts, economics, and risks | CS3 |
| 4 | AI fundamentals: capabilities, transformers, reasoning | CS4 |
| 5 | Tokens, context windows, guardrails | CS5 |
| 6 | Agents, harness engineering, context engineering | CS6 |
| 7 | Prompt vs fine-tune, MCP, AI-enabled systems | CS7 |
| 8 | AI-native SDLC and Spec-Driven Development | CS8 |
| 9 | The trade-off playbook | all |
| 10 | Solved exam paper — answer skeletons | — |
| 11 | Flashcards, vocabulary, last-hour checklist | — |

---

## Acronym decoder (read once)

| Short form | Means | In plain words |
|---|---|---|
| **SDLC** | Software Development Life Cycle | Plan → requirements → design → code → test → deploy → operate |
| **HITL / HOTL** | Human-in / on-the-Loop | Human approves every action / human watches dashboards and steps in on exceptions |
| **LLM / LRM** | Large Language / Reasoning Model | Next-token predictor / model that thinks on a hidden scratchpad before answering |
| **CoT** | Chain of Thought | Step-by-step intermediate reasoning |
| **S2A** | System 2 Attention | Model rewrites and cleans your prompt before reasoning on it |
| **BPE** | Byte-Pair Encoding | The standard subword tokenizer: merge frequent character pairs into tokens |
| **OOV** | Out-Of-Vocabulary | A word the tokenizer has never seen |
| **AST** | Abstract Syntax Tree | Code as a tree; what compilers and linters check deterministically |
| **RAG** | Retrieval-Augmented Generation | Fetch relevant docs by meaning, paste them into the prompt, then answer |
| **MCP** | Model Context Protocol | Anthropic's open standard — "a USB-C port for AI" connecting agents to tools/data |
| **JSON-RPC** | JSON Remote Procedure Call | The message format MCP uses |
| **stdio / SSE** | Standard I/O / Server-Sent Events | MCP's local transport (OS pipes) / its remote transport (HTTP streaming) |
| **ADR** | Architecture Decision Record | A short doc recording *why* a technical choice was made |
| **SDD** | Specification-Driven Development | Humans write precise specs; AI generates code against them |
| **EARS** | Easy Approach to Requirements Syntax | Given-When-Then style acceptance criteria |
| **WIP** | Work-In-Progress | Unfinished work sitting in the pipeline — open PRs, unreviewed branches |
| **DORA** | DevOps Research & Assessment metrics | Deployment Frequency, Lead Time, Change Failure Rate, MTTR |
| **COGS** | Cost of Goods Sold | What it costs to serve one unit — now includes inference tokens |
| **CapEx / OpEx** | Capital / Operational Expenditure | One-time build cost / recurring running cost |
| **Evals** | Evaluation suites | Scored benchmarks for non-deterministic LLM output |
| **PEFT / LoRA** | Parameter-Efficient Fine-Tuning / Low-Rank Adaptation | Cheap fine-tuning that updates a small slice of weights |
| **Slopsquatting** | — | Attackers register package names that LLMs commonly hallucinate |
| **Code slop** | — | Bloated AI-generated code that compiles but destroys the mental model |
| **Vibe coding** | — | Prompting loosely, accepting blindly, tweaking until it seems to work |

---

# Part 0 — Exam mechanics and the answer formula

### The paper

* **Closed book**, **90 minutes**, **30 marks** (30% of the course grade).
* **5–6 scenario questions**, each with **2–3 equally weighted sub-parts** (3+3 = 6 marks, or 3+3+3 = 9 marks).
* **No choice** — every question is compulsory.
* **Zero recall questions.** No MCQs, no fill-in-the-blanks, no "What is Waterfall?". Every question puts you in a situation and asks **what works, what breaks, and why**.

> **The professor's own words (Session 8):** *"It will all be applied, scenario-based questions where you are put into a situation and you have to justify what works well, what breaks, and why… We are not going to evaluate based on the number of lines or word count. You must be very short, concise, and crisp."*

### Time budget

**90 min ÷ 30 marks = 3 minutes per mark.**
3-mark sub-part → 9 min (≈2.5 min reading the scenario, 5 min writing, 1.5 min checking you used the right terms).
6-mark question → 18 min. 9-mark question → 27 min.

### How the evaluator scores you

1. **Generic fluff scores zero.** "In today's fast-paced world, AI is revolutionising software…" earns nothing. Start with the diagnosis.
2. **Naming the exact principle scores high.** Write *Inversion of Engineering Value*, *Theory of Constraints*, *Cybernetic Governor*, *Computational vs Inferential Controls*, *Loss of Tacit Knowledge*, *Lost in the Middle*, *Local Optimisation vs Systemic Flow*. Each named principle is worth marks by itself.
3. **Marks are split evenly across sub-parts.** Answer each sub-part in its own box; don't let points bleed across.

### The 3-part answer formula (use for every 3-mark sub-part)

```
1. DIAGNOSE + NAME THE PRINCIPLE          (1 mark)
   "This violates the Inversion of Engineering Value."
   "This is a local optimisation trap under Goldratt's Theory of Constraints."

2. EXPLAIN THE MECHANISM — why it breaks  (1 mark)
   The actual chain of cause and effect: tacit knowledge wiped, WIP jam,
   validation debt, non-deterministic drift, attention dilution.

3. GIVE THE CONCRETE FIX                  (1 mark)
   A named engineering countermeasure: contract tests, computational
   sensors, ephemeral environments, private registry, HITL gate.
```

Three crisp bullets, one per mark. That is the whole answer — no introduction, no conclusion.

### The mental model behind most scenario questions: Goldratt's Theory of Constraints

```
 Requirements → Design → CODING → Code review & QA → CI/CD & deploy
  (manual)      (manual)  (AI: 10x)   (BOTTLENECK)      (BOTTLENECK)
                             │              ▲                 ▲
                             └──► huge PR volume (WIP) ───────┘
                                  traffic jam · reviewer fatigue · lead time unchanged
```

**The law:** *the throughput of any pipeline is set by its slowest stage.*
**The trap:** speeding up a stage that was never the bottleneck just piles up inventory (WIP) in front of the real one. Keep this picture in your head — it answers a large share of the paper.

---

# Part 1 — The one idea the whole course is built on

Everything in this syllabus comes from one clash:

> **Production software must be 100% deterministic, secure and reproducible. Generative AI is inherently probabilistic and non-deterministic.**

A bank transfer, an auth check, a compiler build — same input must give the same output, every time. An LLM samples the next token from a probability distribution; the same prompt twice can give code that quietly differs in edge-case handling.

**Three consequences, and they explain the entire syllabus:**

1. **You never trust the model — you build a deterministic cage around it.** Compilers, linters, type checkers, AST parsers, schemas, contract tests, sandboxes. That cage is what Parts 5, 6 and 7 are about.
2. **The bottleneck has inverted.** Writing code used to be the hard part. Now generating code is nearly free, so **reviewing, verifying and governing it** is the bottleneck. Everything about WIP, reviewer fatigue and validation debt follows from this.
3. **Value moved to the two ends.** If the middle (typing code) is free, the money is upstream in **precise intent** and downstream in **verification**. That is the *Inversion of Engineering Value*.

**If a question confuses you, come back to these three.** Almost every answer is somewhere in here.

### The course as one story

1. A business wants something, stated vaguely.
2. You turn vague intent into a **precise, machine-readable spec** — because an agent will execute it literally.
3. AI generates the code in seconds. That part is now cheap.
4. The code floods downstream into review, QA and deploy — which did **not** get faster. **The pipeline jams.**
5. So you mechanise the downstream: deterministic sensors (compilers, linters, tests), ephemeral environments, contract tests.
6. To let agents act at all safely, you wrap the model in a **harness**: tools, permissions, sandboxes, feedback loops.
7. You place **human gates** where the blast radius is large — production, schemas, auth, dependencies.
8. And you watch the **cost**, because every inference call now has a price and software is no longer zero-marginal-cost.

---

# Part 2 — SDLC evolution and what AI changes (CS1, CS2)

### What SDLC is

The process of planning, developing, testing, deploying and maintaining software, so that you ship **high-quality software that meets customer needs, within cost and time**.

**The phases and who owns them:**

| Phase | Primary roles | Key artifacts |
|---|---|---|
| 1. Planning & feasibility | Product Manager, Eng Lead, business stakeholders | Scope, budget, timeline |
| 2. Requirements analysis | Business Analyst, Product Owner | User stories, SRS, acceptance criteria |
| 3. Design & architecture | Architect, UI/UX designer | Architecture diagrams, schemas, ADRs |
| 4. Implementation | Developers | Source code, PRs |
| 5. Testing & QA | QA engineers | Test plans, automated suites |
| 6. Deployment | DevOps / release engineers | Pipelines, manifests |
| 7. Operations & maintenance | SRE / support | Monitoring, incident response |

### The 5 eras — each one killed the previous era's bottleneck

| Era | Core paradigm | Cycle time | Its bottleneck |
|---|---|---|---|
| **1. Waterfall (1970s)** | Sequential, phase-gated, document-heavy. Nothing moves until the previous phase is frozen | Months–years | Rigid handoffs, late integration surprises, zero early feedback. A defect found in production costs ~100× a defect found in requirements |
| **2. V-Model (1980s)** | Same sequence, but every design stage is **paired upfront with a matching test stage** | Months | Still rigidly sequential; changing requirements is still painful |
| **3. Agile / Scrum (2000s)** | Short 2–4 week sprints delivering working increments; customer feedback over documentation *(grew out of the Iterative (1975) and Incremental (1978) models)* | 2–4 weeks | Communication overhead, ceremonies, backlog grooming, manual story writing; deploy still manual |
| **4. DevOps / CI-CD (2010s)** | Dev + Ops merged. Automated pipelines, Infrastructure-as-Code, automated monitoring | Days–hours | Pipeline maintenance, flaky tests, manual release coordination |
| **5. AI-Native / Agentic (2020s+)** | Continuous synthesis of artifacts from human intent; agents across all phases | Real-time / on demand | **Verification debt, reviewer cognitive fatigue, architectural governance** |

**The one-line hook:** *In Waterfall you wrote specs. In Agile you wrote user stories. In DevOps you wrote pipelines. In the Agentic SDLC you write **intent and verification guardrails**.*

**What drove the evolution at every step:** faster delivery and time-to-market · continuous customer feedback · lower risk and cost · higher productivity and collaboration · better quality and security · no-downtime updates to complex infrastructure · more automation · developer/skill shortage · rapid tech change (cloud, containers, low-code, 5G, IoT, AI, big data).

### The V-Model and V&V symmetry

The principle that **testing is not a post-coding afterthought** — every specification stage is planned against a test stage from day one.

```
  DECOMPOSE & DESIGN                              TEST & INTEGRATE
  ┌──────────────────────┐                  ┌──────────────────────┐
  │ Business requirements│◄────────────────►│  Acceptance testing  │  VALIDATION
  └──────────┬───────────┘                  └──────────▲───────────┘
  ┌──────────▼───────────┐                  ┌──────────┴───────────┐
  │ System specification │◄────────────────►│    System testing    │
  └──────────┬───────────┘                  └──────────▲───────────┘
  ┌──────────▼───────────┐                  ┌──────────┴───────────┐
  │ Architecture design  │◄────────────────►│ Integration testing  │  VERIFICATION
  └──────────┬───────────┘                  └──────────▲───────────┘
  ┌──────────▼───────────┐                  ┌──────────┴───────────┐
  │    Module design     │◄────────────────►│     Unit testing     │
  └──────────┬───────────┘                  └──────────▲───────────┘
             └────────────►[ IMPLEMENTATION ]──────────┘
                             (AI-assisted)
```

* **Verification — "are we building the product *right*?"** Does it match the spec, the schema, the types?
* **Validation — "are we building the *right* product?"** Does it actually meet the customer's need?

> ⚠️ **The exam angle.** AI massively accelerates the bottom of the V (implementation and unit tests). But if the **top-left is ambiguous, AI builds the wrong system faster**. The symmetry breaks when verification is automated but human validation is neglected.
>
> *Concrete example:* if an AI writes both the API endpoint and its test mock with no independent schema check, both pass in isolation and both fail under real traffic. That is **circular validation**.

### Delivery vs Deployment vs Release — a favourite distinction

| | **Continuous Integration** | **Continuous Delivery** | **Continuous Deployment** | **Release** |
|---|---|---|---|---|
| **What it is** | Merge daily; builds + unit tests run on every commit | Pipeline keeps the app **always in a deployable state**, staged and tested | **Every** commit that passes CI goes **straight to production** | The **business act** of switching the feature on for users |
| **Human gate?** | — | ✅ Yes — a manual approval click | ❌ None | ✅ Yes — product/marketing |
| **Safety net** | Unit tests | Staging approval gate | Canary analysis + instant auto-rollback | Feature flags, dark launches, ring deployments |
| **Best for** | Everyone | Enterprise, banking, healthcare, **AI-generated code** | Low-risk SaaS, internal tools | — |

**Hook:** *Deployment is technical (code is running on servers). Release is business (users can see it).* A payment feature can be deployed for weeks behind a dead feature flag before it is released.

**Why it matters here:** because AI output is probabilistic, enterprises mandate **Continuous Delivery with a human sign-off**, not blind Continuous Deployment, for anything high-risk.

### DevOps → MLOps → AIOps → Agentic SDLC

Four different things — don't mix them up:

* **DevOps** — automates **deterministic software** delivery: builds, tests, containers, CI/CD.
* **MLOps** — operationalises **ML models**: data pipelines, feature stores, training, hyperparameter tracking, data/model drift monitoring, retraining. (**Data + Code = Model**.)
* **AIOps** — applies AI **to operational telemetry**: ingest logs/metrics/traces, detect anomalies, deduplicate alerts, correlate a spike with a recent commit, automate root-cause analysis.
* **Agentic SDLC** — applies AI **to the engineering process itself**: eliciting requirements, authoring specs, synthesising code, running test-fix loops.

**Hook:** *DevOps manages code · MLOps manages models · AIOps uses models to manage operations · Agentic SDLC uses models to do the engineering.*

### What AI actually changes at each SDLC phase

| Phase | Traditional | AI-augmented | The trade-off to name |
|---|---|---|---|
| **Requirements** | BA writes a PRD over weeks | **Intent-to-Spec:** meeting audio or rough notes → structured OpenAPI specs, JSON schemas, ADRs, Gherkin tests | **Omission risk** — AI misses *negative* requirements (what the system must NOT do). Human review mandatory |
| **Architecture** | Architect draws UML, writes ADRs | AI scaffolds ADR templates, suggests patterns, simulates topology for concurrency bottlenecks before implementation | **Architectural drift** — AI makes locally sensible fixes that violate global boundaries |
| **Coding** | Manual boilerplate, business logic, APIs | **Copilots → multi-file agents** that refactor dozens of interconnected files from one prompt | **Review fatigue** — cheap code floods reviewers with huge PRs |
| **Testing** | QA writes scripts, mocks, boundary checks; brittle Selenium/Cypress locators | **Self-healing tests** (agents fix element locators when the UI changes) + autonomous edge-case generation from code branches | **Circular validation** — AI tests its own code with its own flawed assumptions and gets a false 100% pass |
| **Code review** | Peer review takes 24–72 h, misses subtle flaws through fatigue | **Semantic AI reviewers** flag OWASP issues, schema mismatches, unauthorised dependencies *before* a human is notified | Bots are advisory; they can be fooled and must not be the final gate |
| **Operations** | Engineer wakes at 2 AM, greps Splunk, traces stacks manually | **AIOps autonomous remediation**: correlate errors with recent PRs, draft a fix or rollback, hand the SRE a root-cause summary | **Hallucinated fixes** — a diagnostic bot must never run destructive restart/drop commands |

### The evidence: capability is rising, deployed productivity is not

* **Anthropic Economic Index** — 36% of software roles use AI for at least a quarter of their tasks; only **4% use it extensively**; **57% of usage augments** the developer rather than replacing them.
* **Stack Overflow survey** — 84% use or plan to use AI tools, but **76% actively avoid AI for deployment and monitoring**, and **69% avoid it for system architecture**.
* **METR maintainer study** — experienced open-source maintainers using early AI tools were **19% slower** on complex tasks: prompting and debugging unfamiliar AI code took longer than writing it themselves.
* **Stack drift** — Python overtook JavaScript as the #1 language by project volume on GitHub, driven by generative-AI repos.

**Read it as:** developers trust AI for **low blast radius** work (boilerplate, tests, docstrings) and refuse it for **high blast radius** work (deploys, infra, IAM).

### The 40/60 split — why 10× typing ≠ 10× productivity

```
┌─────────────────────────────────────────────────────────────┐
│ 40%  WRITING CODE                                           │
│      boilerplate · unit tests · CRUD endpoints              │
│      ===> AI accelerates THIS by 50–80%                     │
├─────────────────────────────────────────────────────────────┤
│ 60%  EVERYTHING ELSE  ← the real bottleneck                 │
│      understanding ambiguous requirements                    │
│      cross-team architecture and API contract debates        │
│      deciphering undocumented legacy systems                 │
│      code review, debugging distributed race conditions      │
│      waiting on CI runners, QA environments, security sign-off│
│      ===> AI does NOT automatically solve any of this        │
└─────────────────────────────────────────────────────────────┘
```

**The capability–productivity gap:** raw generation capability is exploding, but *deployed* productivity (features actually earning revenue) stays flat. Halving the 40% saves very little when the 60% is untouched — and if unreviewed AI code doubles review time, **net productivity goes down**.

**The analogy to use in an answer:** *Kafka backpressure.* An unthrottled producer pushing 100,000 events/sec into a consumer that writes 500/sec doesn't speed anything up — lag explodes and the broker stalls. AI code generation is the producer; code review is the consumer.

### Augmentation vs autonomous replacement

* **Augmentation** — AI suggests, the human reviews and accepts. The cognitive amplifier model.
* **Autonomous replacement** — AI decides and acts with no human checkpoint. Unacceptable for mission-critical enterprise systems.

**Why:** an LLM carries **zero legal, operational or financial accountability**. You cannot blame a prompt for an outage. **The human who approves and commits owns 100% of the liability.**

**Analogy:** autopilot manages altitude and heading; the human pilot is fully accountable for takeoff, landing and emergencies.

### Where human gates go (risk tiering)

| Risk | Tasks | Policy |
|---|---|---|
| **Low** | Docstrings, boilerplate DTOs, formatting, log clustering | **Automate with linters** — no human bottleneck |
| **Medium** | Refactoring isolated functions, unit test stubs, drafting ADRs | **AI-assisted + human review** |
| **High** | Production deploys, DB migrations, auth/payment code, IAM policies | **Strict HITL gate** — non-negotiable |

---

# Part 3 — The 5 paradigm shifts, economics, and risks (CS3)

### The 5 shifts in software engineering

| # | The shift | What it used to be | What it is now | What you must do about it |
|---|---|---|---|---|
| **1** | **Dev effort is no longer the bottleneck** | Effort scarcity drove MVP scope-cutting and ruthless prioritisation | Build **three working prototypes in parallel** and test with real users instead of arguing over wireframes. Design docs / RFCs become **machine-executable specifications** for agents | Optimise for review and verification capacity, not typing speed |
| **2** | **Roles are less siloed** | PM writes PRD → Dev codes → QA tests → SRE deploys | The blur: a PM ships a working prototype; a developer generates E2E tests and Kubernetes manifests | Engineers must own end-to-end systems and product intent, not just code |
| **3** | **Decisions are less "hard to change"** | Architecture decisions were one-way doors; refactoring took months | Regenerating code is cheap → "disposable microservices" | **Code logic is disposable. Persistent data is NOT.** You can rewrite a service in an afternoon; migrating a multi-terabyte schema is still a one-way door |
| **4** | **Accountability is foggier** | "You built it, you run it" — git blame pointed at a person | AI authors 80% of a PR; who is at fault for the breach? | **The human who approves and commits carries 100% liability.** "The AI generated it" is not a defence — legally, or in a compliance audit |
| **5** | **Outcomes are probabilistic** | Compilers are deterministic; tests pass or fail reliably | Same prompt, different output, depending on temperature, model version and phrasing | Binary assertions (`assert result == 42`) must be supplemented with **continuous LLM Evals** scoring semantic consistency, hallucination rate and toxicity |

### The Inversion of Engineering Value

```
   TRADITIONAL VALUE STACK              AI-AUGMENTED (INVERTED)
  ┌──────────────────────────┐        ┌──────────────────────────┐
  │ ▲ 1. Writing syntax      │        │ ▲ 1. Architecture &      │ ← highest value
  │ │ 2. Memorising algos    │        │ │    invariants          │
  │ │ 3. Manual unit tests   │        │ │ 2. Precision specs     │
  │ │ 4. Architecture        │        │ │ 3. Rigorous review     │
  │ ▼ 5. Problem formulation │        │ │ 4. Verification harness│
  └──────────────────────────┘        │ ▼ 5. Writing code        │ ← commodity, ~free
                                      └──────────────────────────┘
```

**The premise:** *value migrates away from whatever becomes abundant and free.* Writing a FastAPI endpoint or a quicksort now costs ≈ $0. So value moved **upstream to intent** and **downstream to verification**.

**The 4 new core competencies (name these — they are straight from the slides):**
1. **Intent articulation & architectural control** — unambiguous specs that guide AI without architectural drift.
2. **Systematic verification & quality assurance** — deterministic harnesses, mutation suites, eval rubrics that catch probabilistic errors.
3. **Multi-agent orchestration** — workflows where specialised agents (architect, coder, reviewer) collaborate reliably.
4. **Human judgment & accountability** — being the legal, ethical and operational gatekeeper for production.

**The transition needs four coordinated dimensions:** **Education** (from syntax mastery to systems curation) · **Tooling** (infrastructure for orchestration and verification) · **Processes** (verification-first, human-in-the-loop lifecycles) · **Professional practice** (roles, metrics, governance).

### The 3 shifts in software economics

**Shift 1 — The end of "zero marginal cost" software.**
*Old:* build once, serve 100k users for fractions of a cent each → **80–90% gross margins**.
*New:* every transaction fires inference tokens, vector lookups and API calls. **COGS now scales with usage.**
*Engineering consequence:* design for **cost efficiency per query**. One simple feature that triggers an unoptimised multi-step agent loop on every click can destroy gross margin. **High-volume, high-frequency paths must use deterministic code** (regex, SQL indexes, cached lookups), not LLM calls.

**Shift 2 — From "Build vs Buy" to "Token cost vs Human labour".**
*Old question:* internal developer salary (build) vs vendor subscription (buy).
*New equation:*
```
Cost(AI) = Inference token cost + Senior human verification cost
           ...compared against full human execution cost
```
If juniors generate mountains of AI code that seniors spend hours deciphering, **total delivery cost can exceed writing it by hand**. *(And COCOMO-style estimation by lines of code is dead — an AI writes 50,000 LOC in an afternoon; what matters is time to verify and safely deploy.)*

**Shift 3 — Per-seat licensing collapses → outcome-based pricing.**
*Old:* $30/user/month. *New:* agents do the work humans used to, so seats shrink. Pricing pivots to **per outcome** — $1.50 per resolved ticket, $10 per automated security patch, per automated deployment.
*Engineering consequence:* architects must track **system-level outcomes** (resolutions, completed tasks) as core telemetry, not user logins.

> **The cautionary tale to quote:** a fintech team replaced an 18-minute, $12/day deterministic Python ETL with an "agentic pipeline". 40,000 records had date-format variations, the agent entered an unconstrained reasoning loop running 8 LLM passes per record, and in 48 hours burned **$41,800 in tokens**; runtime went to 14 hours and gross margin fell from **+82% to −18%**. Code is cheap; **inference compute and unverified logic are not**.

### The risks AI amplifies across the SDLC

Group them into four families — then the list is easy to reproduce:

**A. Code quality & security**
* **Plausible but insecure code** — compiles, reads well, quietly wrong.
* **Hallucinated package dependencies** → supply-chain attacks (see slopsquatting below).
* **Missing edge cases in generated tests** — the tests assert the bug is correct.
* **Architectural drift / unchecked tech debt ("code slop")** — different developers prompt differently, so error handling, DB access and logging diverge; in six months the microservice estate is a zoo of incompatible styles.
* **High-volume code bloat** — more code than anyone can hold in their head.
* **Context blindness** — the model can't see the constraint that lives in another team's repo.

**B. Human factors & cognitive risks**
* **Reviewer fatigue** — seniors rubber-stamp or burn out.
* **Atrophy of fundamental skills** — juniors never build debugging intuition. *(Related: fast AI answers remove the serendipitous learning you get from reading real docs and Stack Overflow threads where edge cases are discussed.)*

**C. Legal, IP and compliance exposure** — licence contamination from training data, algorithmic auditability, "who is accountable" in a regulated audit.

**D. Economic & operational risks** — runaway token spend, unbounded agent loops, unpredictable COGS.

**Plus two framing distinctions the exam likes:**
* **Instant technical debt vs unfinished backlog.** *Unfinished backlog* = known work that rolled to next sprint — just deferred. *Technical debt* = compromised quality you must repay with interest. AI creates **instant technical debt**: code that passes unit tests but violates enterprise patterns and duplicates abstractions.
* **Errors at machine scale.** A human makes mistakes at ~100 lines/day. An agent propagates one security misconfiguration across 50 microservices in 3 minutes.

### Slopsquatting — the supply-chain hallucination attack

**The mechanism, in four steps:**
1. An LLM needs a library that doesn't exist and **hallucinates a plausible name** — `fast-crypto-auth-jwt`, `auth-jwt-utils-v2`, `react-dates-helper`.
2. Attackers prompt public models thousands of times, **catalogue the names that get hallucinated**, and register those exact names on npm/PyPI with a trojan inside.
3. A developer or autonomous agent accepts the suggestion and commits it to `package.json`.
4. CI runs `npm install`. **The malware executes with the full privileges of the CI runner** — able to exfiltrate AWS credentials, steal DB secrets, or backdoor customer production builds.

**The three defences (all computational, all deterministic):**
1. **Private proxy registry with allow-listing** — route every package request through an internal Artifactory/Nexus proxy; **disable direct outbound access to public npm/PyPI**.
2. **Package provenance & metadata gate** — auto-reject any package published less than ~30 days ago, or below a minimum download/reputation threshold, or without verified maintainer signatures.
3. **Lockfile integrity + a human dependency gate** — agents are computationally barred from editing `package.json`/`package-lock.json`; adding a new third-party dependency requires a **HITL sign-off** from a security architect.

### Disposable code vs permanent state — the decision matrix

| | **Disposable (two-way door)** | **Permanent (one-way door)** |
|---|---|---|
| **Examples** | Frontend components, batch ETL scripts, mocks, prototypes, single-file lambdas with no state | Database schemas, financial ledgers, IAM permissions, auth services, payment gateways, shared libraries |
| **Approach** | Generate with AI; **rewrite rather than refactor** | Hand-crafted design, strict peer review, formal ADRs |
| **Cost of change** | Low — regenerate in minutes | Catastrophic — data migrations and outages |

**The rule to write:** *Code is disposable; data is permanent.*

---

# Part 4 — AI fundamentals: capabilities, transformers, reasoning (CS4)

### The 4 core capabilities of AI

AI = systems doing tasks that normally need human intelligence. Four capabilities:

**1. Learning** — improving at a task over time by extracting patterns from data instead of following hardcoded rules.
* **Rule-based AI** — explicit if-then-else (expert systems, symbolic AI, knowledge graphs). **All ML is AI, but not all AI is ML** — rule-based AI is AI with zero learning capacity.
* **Machine Learning** — trains on sample data and optimises itself:
  * **Supervised** — needs human-labelled data (images tagged "dog"/"cat").
  * **Unsupervised** — no labels; finds clusters and patterns (recommendation engines).
  * **Reinforcement** — trial and error with rewards/penalties (self-driving, trading).
  * **Deep learning** — many-layered neural networks; the basis of foundation models.

**2. Reasoning** — connecting facts, applying logic, deriving new conclusions.
* **Symbolic / knowledge-graph** — strict logic, guaranteed deductions.
* **Probabilistic / statistical inference** — likelihoods from incomplete data (Bayesian networks).
* **Chain-of-Thought (neural)** — LLMs break a prompt into intermediate logical steps.

**3. Perception** — turning raw sensor data into structured meaning.
* **Computer vision** — CNNs and Vision Transformers on pixel matrices (object detection, segmentation, depth).
* **Speech & audio** — acoustic models converting sound frequencies to text tokens.
* **Multimodal fusion** — frontier models combining text, image, audio and sensor input.

**4. Problem-solving / action** — finding a sequence of actions from the current state to a goal state.
* **Search & optimisation** — state-tree searches like A* and Monte Carlo Tree Search (chess, logistics routing).
* **Agentic planning** — break a high-level task into sub-tasks, call tools, check outputs, re-plan on failure. *(This is the bridge into Part 6.)*

### The evolution of AI — four eras

| Era | What it is | Strength | Fatal weakness |
|---|---|---|---|
| **1. Symbolic logic / expert systems (1950s–1980s)** | Human-coded if-then rules, formal logic | Fully deterministic and explainable | Brittle; cannot generalise or handle ambiguity |
| **2. Classical ML (1990s–2010s)** | Statistical classifiers — SVMs, random forests, regression — on labelled data with hand-engineered features | Great at classification (e.g. which file likely has the bug) | Requires manual feature engineering; cannot generate code or understand language |
| **3. Deep learning & foundation LLMs (2017–2023)** | Transformers pre-trained on internet-scale unlabelled data by self-supervised next-token prediction | Generalises zero-shot / few-shot across tasks; generates code | Single forward pass — no planning, no self-check |
| **4. Test-time compute & reasoning models (2024–present)** | Trained (often with RL) to generate a hidden chain of thought, spending compute **at inference** to test hypotheses and verify | Handles multi-step logic, concurrency, edge cases | Slow; bills for hidden thinking tokens |

### Self-supervised learning and next-token prediction

* **The old bottleneck:** supervised learning needed expensive human annotators for every sample.
* **The breakthrough:** the data labels itself. Give the model `def add(a, b): return a + ` and train it to predict the masked next token (`b`). Run that over petabytes of open-source code and it learns syntax, API signatures and idioms on its own.
* **The objective, if you want to write it:** maximise `P(wₜ | w₁ … wₜ₋₁)` across the corpus.
* **What this means for you:** the model has **no internal fact database and no verification engine**. It is an extraordinary *pattern completion* engine. **If your prompt begins a buggy pattern, it will happily complete the buggy pattern.** It doesn't "understand" Python; it knows the probability distribution of tokens after a Python function header.
* **"Large":** model size is measured in **parameters**; the basic unit it processes is the **token**.

### The Transformer and self-attention (Vaswani et al., 2017)

**Why it beat RNNs/LSTMs:** RNNs read token-by-token — unparallelisable, and they forget across long distances (vanishing gradients). **Transformers ingest the whole sequence in parallel.**

**How self-attention works — three vectors per token:**
* **Query (Q)** — "what am I looking for?"
* **Key (K)** — "what do I contain / offer?"
* **Value (V)** — "what information do I actually carry?"

```
Attention(Q, K, V) = softmax( Q·Kᵀ / √dₖ ) · V
```
* `Q·Kᵀ` — pairwise relevance score between every token and every other token.
* `÷ √dₖ` — stops the dot products from exploding into tiny-gradient regions.
* `softmax` — normalises the scores into a probability distribution.

**What it buys you in code terms:** a variable used on line 300 can pay direct, high-weight attention to its type declaration on line 5, regardless of distance.

> **The catch you must mention: attention scales quadratically, O(N²), with context length.** Doubling the prompt quadruples the attention compute. This is why huge contexts are slow and expensive — and it is the reason character-level tokenization was rejected (Part 5).

### System 1 vs System 2 (Kahneman, *Thinking, Fast and Slow*)

| | **System 1 — fast & intuitive** | **System 2 — slow & deliberate** |
|---|---|---|
| **Models** | Standard LLMs (GPT-4o, Claude Sonnet) | Reasoning models / LRMs (o1, o3, DeepSeek-R1, thinking modes) |
| **Mechanism** | Single forward pass, fixed compute per token | **Test-time compute**: hundreds of hidden reasoning tokens exploring branches |
| **Behaviour** | Emits what *looks* probable, immediately | Generates hypotheses, simulates execution, prunes bad branches, verifies, then answers |
| **Latency** | Sub-second to ~2 s | 10–60 s+ |
| **Cost** | Low–moderate | High — **you are billed for the hidden thinking tokens** |
| **Edge-case safety** | Poor — plausible-looking concurrency bugs | Superior |
| **Use it for** | Boilerplate, docstrings, simple CRUD, syntax translation, inline autocomplete | Concurrency, distributed systems, architecture, security review, complex refactors |

**What "test-time compute" means:** a normal LLM spends a fixed amount of computation per output token. A reasoning model spends **extra compute before the first answer token**, thinking on a private scratchpad.

**The worked example to reuse (automated bug fixing in a microservices codebase):**
* *Classical ML:* classifies which file probably contains the bug from commit history — but cannot write or evaluate a fix.
* *Standard LLM (System 1):* reads the buggy function and writes a plausible patch in one pass — and may miss a race condition or break an API elsewhere.
* *Reasoning model (System 2):* traces the call stack across services on a scratchpad, generates several root-cause hypotheses, simulates crash scenarios, prunes the invalid ones, verifies against API contracts, then emits the patch.

> **The concrete failure to quote:** Copilot writes a Redis distributed lock in Go — `client.SetNX(ctx, key, "locked", 0)`. It compiles and passes a simple unit test. But TTL = 0 means **no expiry**: a worker pod crashes holding the lock, 50 Kubernetes workers queue behind it, the clearing pipeline deadlocks, $1.8M in payments stall. System 1 outputs what looks probable, **not what survives distributed edge cases**.

### System 2 Attention (S2A)

**The problem:** self-attention attends to *everything* in the prompt — conversational banter, stale comments, old stack traces, misleading hints. That dilutes reasoning ("context pollution") and causes **sycophancy** (the model agrees with your flawed premise).

**The technique:** an intermediate step where **the model rewrites your prompt first** — stripping opinions, noise and irrelevant context — and the purified prompt is then reasoned over.

**Result:** less distraction, fewer hallucinated solutions caused by context distractors. It is an early example of **inference scaling**: add a step between input and response and the final output improves.

### Choosing the right engine for the task

| Task | Use | Why |
|---|---|---|
| Formatting, secret scanning, syntax rules | **Deterministic linters** (ESLint, Semgrep, compilers) | Microseconds, free, 100% certain. **Never spend LLM tokens checking indentation** |
| Autocomplete, docstrings, simple CRUD | **System 1 LLM** | Sub-second latency keeps the developer in flow |
| Concurrency, race conditions, architecture, security | **System 2 reasoning model** | Needs multi-step hypothesis testing and execution simulation |

> **Two professor's points worth a sentence each:**
> * **"Copilot is a harness, not a model."** Copilot is an IDE integration; you can swap the engine underneath — fast models for inline typing, reasoning models for repo-wide refactoring.
> * **"Rule-based AI is more important than ever."** Compilers, AST linters and type checkers are not obsolete — they are the **deterministic guardrails** that catch non-deterministic errors.
> * **The "recipe vs chef" line:** deterministic code is a recipe (same steps → same dish, every time). A foundation model is an experienced chef improvising from memory — sometimes brilliant, sometimes it ruins the dish, and you must inspect the ingredients.

---

# Part 5 — Tokens, context windows, and guardrails (CS5)

### Tokens — the model's unit of currency

A **token** is a chunk of text: a character, a word, or a word fragment (`-tion`). Breaking text into tokens is **tokenization**.

**Rule of thumb:** **1 token ≈ 4 characters of English ≈ 0.75 words**, so 100 tokens ≈ 75 words. Short common words ("is", "the") are one token each; rare words split ("Tokenization" → "token" + "ization"). **Punctuation, spaces and line breaks consume tokens too.** In vision models the unit is pixels/patches instead.

**Why tokens, and not words or characters — three reasons:**
1. Compared to characters, tokens are **meaningful components** of words.
2. There are far fewer unique tokens than unique words → **smaller vocabulary, more efficient model**.
3. Tokens let the model **handle unknown words** by composing them from familiar fragments.

### The tokenization taxonomy

| Approach | Unit | Vocabulary | Sequence length | Verdict |
|---|---|---|---|---|
| **Character** | Every letter/symbol | Tiny (~256) | **Explodes 5–10×** | ❌ Rejected — with O(N²) attention, long code contexts become computationally impossible |
| **Word** | Whole words split on whitespace | **Gigantic (millions)** | Short | ❌ Rejected — any unseen identifier or typo becomes `<UNK>` (OOV explosion); can't handle camelCase or syntax |
| **Subword (BPE / SentencePiece)** | Frequent words whole, rare words split into common fragments | Balanced (~50k–128k) | Moderate | ✅ **The industry standard** — best trade-off between vocabulary size and sequence length |
| **Code-aware (AST-informed)** | Subwords + whole indentation blocks | Optimised (~100k+) | Compact | ✅ Modern frontier models; **~50% fewer tokens on code** |
| *(Morphological)* | Splits by linguistic morphemes | — | — | Mentioned as a technique; not the mainstream choice |

**How subword tokenization actually looks:**
```
Raw code:  def calculate_sum(a, b):
Tokens:    ["def", " calculate", "_", "sum", "(a", ",", " b", "):"]
Token IDs: [1314, 17950, 29859, 6271, 11, 287, 3127, 220]
```

### How the model "sees" code — and its blind spots

Humans read code semantically. **The tokenizer splits it statistically, by training-set frequency.** So:
* **Common keyword** (`import`, `def`) = **1 token**.
* **Custom identifier** (`fetchUserAccountLedgerBalance`) = **5–6 tokens**.
* **Cryptic identifiers = high token cost.**

**The blind spots this creates:**
1. **Character-level tasks fail.** "How many 'r's in strawberry?", "reverse this string", "slice at character offset 17" — the model never sees the letters, only integer IDs. **This is an anti-pattern; delegate it.**
2. **Custom-identifier bloat** eats your context budget silently.
3. **Indentation drift.** Old tokenizers (GPT-2/3) encoded four spaces as four separate tokens — **30–40% of a deeply nested Python file's context spent on whitespace**.

**How modern models fixed it:**
* **Code-aware tokenizers** group common indentation levels (2/4/8 spaces) into single tokens.
* **Positional metadata** tracks both token index *and* precise character offsets (older attention only saw "token 1, token 2" and had no idea how many characters were inside).
* **Syntax-guided pre-training** — training data includes ASTs and linted structure.

```
def process_data(item_id):
    if item_id == None:
        return []

Old tokenizer:  ~19 tokens   (every space and fragment separate)
New tokenizer:  ~10 tokens   (identifiers and indentation chunked)
```

### The context window

**Definition:** the hard ceiling on the **total tokens in one inference call — input prompt + generated output combined**.

**Everything counts toward it:**
* the system prompt and custom instructions
* the full conversation history (your past messages *and* the model's past answers)
* the current user prompt plus attached files/images
* **the response currently being generated**

### The 4 context-window failure modes

| # | Failure | What you observe | The fix |
|---|---|---|---|
| **1** | **Attention dilution — "Lost in the Middle"** | Retrieval accuracy follows a **U-shaped curve**: strong at the start (primacy) and end (recency), dropping by up to **50% in the middle**. Rules buried in the centre are simply ignored | **Context ordering** — critical invariants at the **top** (system prompt), immediate intent and schema at the **bottom** (user turn) |
| **2** | **Silent degradation** | No error is thrown. Code quality just decays — edge cases skipped, subtle logic bugs appear | **Context pruning** — truncate old turns, sliding windows, targeted RAG instead of dumping the repo |
| **3** | **Inconsistent behaviour** | Adding one unrelated file or log snippet changes the whole attention distribution; a prompt that worked yesterday fails today | **Temperature = 0 + seed pinning** for deterministic sampling |
| **4** | **Cascading failures in agentic loops** | One bad early tool output pollutes the history; every later turn reasons over corrupted data until the task collapses | **Context checkpoints** — validate each tool output *before* appending it to history |

*(Also worth naming: **quadratic cost and latency** — O(N²) attention means huge contexts blow up time-to-first-token and price; and **hallucination under saturation** — past ~90% capacity, confabulation and dropped constraints rise sharply.)*

> **The scenario to quote:** a fintech compliance screener dumps a 150-page manual into the middle of a 128k prompt. On page 78 (token ~65,000) sits the rule *"any wire over $10,000 to an unverified offshore account needs human 2FA approval."* A $95,000 offshore wire is auto-approved, because the model attended to the header and the user message and never saw the middle. **A large context window is not RAM — attention is a scarce, decaying resource.**

### System-level guardrails — "prompting is not engineering"

**Why asking nicely fails:** *"Please return only valid JSON matching this schema"* still fails in 2–5% of calls. In an automated pipeline, a 2% failure rate is catastrophic. So you enforce correctness **outside the neural network**.

**Guardrail 1 — Tool latching / code interpreters (delegate the task).**
Don't ask the model to *guess* the result of arithmetic, date maths or string slicing. Have it **write a short script, run it in an isolated sandbox (REPL/container), and read back the deterministic result.**
> 💡 This is the direct fix for the character-level blind spot. **LLMs are reasoners, not calculators.**

**Guardrail 2 — Constrained decoding / grammar masking (guard the syntax).**
The model emits **logits** (a probability for every token in the vocabulary). A context-free grammar or JSON Schema intercepts generation **token by token**, and any token that would break the syntax has its probability forced to **zero (−∞)**.
**Result: the model is mathematically prevented from emitting invalid JSON or malformed code.** Not "asked nicely" — *prevented*.

**Guardrail 3 — Compilers and AST interceptors on the way out.**
Pass generated code through an AST parser (Tree-sitter) and a compiler/type checker (`tsc`, `mypy`). Feed the diagnostics **back into the model** for automated self-correction before a human ever sees it.

> 💡 **Tools worth naming:** `tiktoken` (count tokens and cost before you send) · `Pydantic` (runtime schema validation of LLM JSON) · `Outlines` (finite-state-machine guided sampling for guaranteed valid JSON/SQL/regex) · `vLLM` (high-throughput serving with PagedAttention, managing GPU memory like OS paging) · `Tree-sitter` (fast incremental AST parsing).

### Tokenomics — the economics of tokens

The emerging discipline of measuring what AI actually costs. Four problems it names:
1. **The "black box" of AI billing and pricing** — you can't see what you're paying for.
2. **Hidden costs beyond the token** — retries, hidden reasoning tokens, re-sent conversation history.
3. **Inability to calculate AI ROI** — no clean denominator for the value delivered.
4. **Inefficient model routing and waste** — using an expensive reasoning model for trivial string work.

*(The Linux Foundation launched a **Tokenomics Foundation** to define the economics and ROI of AI value.)*

> **Professor's rules for this part:**
> * **Context windows are the new RAM.** You wouldn't run a service without watching memory. Never run an agent without tracking token consumption and context headroom.
> * **Never put critical rules in the middle.** Top or bottom, always.
> * **Conversational chatter burns budget** — "Hey, could you please kindly…" is re-transmitted on *every subsequent turn*. Write concise, imperative machine instructions.
> * **Never ask an LLM to count characters.** Delegate to a code interpreter.

---

# Part 6 — Agents, harness engineering, context engineering (CS6)

### What an AI agent is

**Definition:** an **autonomous software entity** that **perceives** its environment through sensors/data inputs, **decides** using a reasoning mechanism, and **acts** through tools to achieve a goal.

Unlike traditional software (rigid static rules) or a plain LLM (responds once to a prompt), an agent runs a continuous loop:

```
   ┌──────────────────────────────────────────────┐
   │   PERCEIVE → REASON → ACT → EVALUATE         │
   └──────────▲───────────────────────┬───────────┘
              └───────────────────────┘
        (repeat until the goal is met or a budget is hit)
```

**Agents operate with autonomy *inside defined boundaries*.** Each one understands a specific input, decides the next step, and acts **within the constraints of its design**.

> 💡 **SWE-agent** (Yang et al., Princeton, 2024) — a coding agent built on GPT-4 whose **environment is the computer**: the terminal and the file system. Its actions are **navigate repo, search files, view files, edit lines**. The interface it uses is called an **Agent-Computer Interface (ACI)**.

### The 5 classical agent types (Russell & Norvig)

| Type | Core mechanism | How it decides | Example |
|---|---|---|---|
| **Simple reflex** | IF/THEN condition-action rules; **ignores history** | Purely on the current perception | Smart thermostat; a basic linter |
| **Model-based reflex** | Internal state + a model of how the world evolves | Current input **plus** remembered state | Automated braking accounting for wet roads; an agent tracking which files it already modified |
| **Goal-based** | Planning / pathfinding algorithms | Chooses actions that reach a defined target state | GPS navigation; test-suite pathfinding |
| **Utility-based** | Multi-objective trade-off scoring | Maximises a utility function when goals conflict | Balancing execution speed against token cost |
| **Learning** | Feedback-driven adaptation | Improves its strategy over time from outcomes | An agent that learns which fix strategies actually pass CI |

### The master equation

```
                    AGENT  =  MODEL  +  HARNESS
```

* **The model** — raw probabilistic intelligence: reads input, generates output, synthesises candidate code. On its own it **cannot** read a file, run a command, check a permission, or evaluate blast radius.
* **The harness** — everything the model can't do for itself: **tools, state, execution, context, permissions, validation.**

**What the harness is responsible for:**
1. Managing state and conversation history
2. Assembling and pruning the context window
3. Exposing and executing tools inside secure sandboxes
4. Intercepting actions to enforce security policy, permissions and rate limits
5. Parsing compiler/test output back into a feedback signal

> **Karpathy's OS analogy — quote this.** If the **LLM is the CPU** and the **context window is the RAM**, then the **harness is the operating system kernel**: it handles I/O, device drivers (tools), access permissions, scheduling, and security sandboxes.

**The three harness layers — who controls what:**

| Layer | What it is | Controlled by | Components |
|---|---|---|---|
| **Coding harness** | The runtime built into the coding agent | The agent/SDK maker | Tool use, system prompt, sub-agents, orchestration, code search, context management |
| **User harness** | The feedforward and feedback controls your team adds on top | The team deploying the agent | Convention files (`CLAUDE.md`, `AGENTS.md`), MCP servers, eval loops, custom skills |
| **Team / Org / SDLC harness** | The shared platform layer governing agents across teams | The platform team | Context lake, integrations, agent registry, permissions, orchestration, governance, HITL, measurement |

### The cybernetic governor — Guides vs Sensors

The harness works like a **steam-engine governor**: it continuously steers and corrects.

| | **GUIDES — feedforward** | **SENSORS — feedback** |
|---|---|---|
| **When** | **Before** the agent acts | **After** the agent acts |
| **Job** | Set expectations, constrain the space | Detect deviation, enable self-correction |
| **Examples** | System prompts, personas, design specs, convention files (`CLAUDE.md`, `AGENTS.md`), API schemas, tool definitions, few-shot examples, coding standards | Linters (ESLint, Flake8), compilers and type checkers (`tsc`, `mypy`), unit/integration/regression tests, ArchUnit structural tests, security scanners (Semgrep, SonarQube) |

**Worked mapping (straight from the slides):**

| Control | Direction | Type | Implementation |
|---|---|---|---|
| Coding conventions | Feedforward | Inferential | `AGENTS.md`, skills |
| How to bootstrap a project | Feedforward | Both | A skill with instructions **plus** a bootstrap script |
| Code mods | Feedforward | Computational | A tool with OpenRewrite recipes |
| Structural tests | Feedback | Computational | Pre-commit hook running **ArchUnit** module-boundary checks |
| How to review | Feedback | Inferential | Review skills / LLM-as-judge |

### Computational vs Inferential controls — the safety hierarchy

| | **Computational (deterministic)** | **Inferential (probabilistic)** |
|---|---|---|
| **Runs on** | CPUs | GPUs / NPUs / LLM APIs |
| **Mechanism** | Hard algorithmic code — regex, AST validation, type checkers, schema enforcers, permission checks, unit tests | Semantic evaluation by a model — "LLM-as-a-Judge", autonomous code review |
| **Latency** | Microseconds–milliseconds | Seconds–minutes |
| **Cost** | Free (local CPU cycles) | Variable token cost per call |
| **Reliability** | **100% mathematical certainty**; cannot be hallucinated or prompt-injected | ~90–98%; prone to false negatives, drift, sycophancy |
| **Best for** | Compilers, linters, unit tests, secret scanning, schema conformance, permissions | Intent understanding, semantic review, tone, docstring clarity |
| **Governance role** | **Must be the final gate before production** | **Advisory only — never sufficient alone** |

**The golden rule:** *always prefer computational controls. Use inferential controls only for genuinely subjective judgements.*

### Where the harness fits in the SDLC

| Stage | What happens | Where the harness matters |
|---|---|---|
| **Plan** | Work is scoped, context assembled | Context management decides what the agent sees **before** it starts |
| **Build** | The agent generates code / takes action | Tools, orchestration and guardrails govern what it is **allowed** to do |
| **Review** | A human or agent checks the work | **Sensors** — tests and linters — catch problems before they ship |
| **Deploy** | The change goes to production | **Approval gates** decide what runs automatically and what waits for a human |

### Context engineering

**Definition:** deliberately designing, structuring and optimising the context given to an LLM, to get accurate, relevant, reliable output. Karpathy's framing: *filling the context window with **just the right information at each step of the agent's trajectory**.*

**Why it dominates quality:** LLMs have **no long-term memory**. They generate responses **solely** from the context window available at inference time. Well-managed context → good reasoning and tool calls. Poorly managed → hallucination, confusion, irrelevant output.

**The core steps of the process:**
Context **selection** → **structuring** → **prompt design** → **compression** → **sequencing** → **tool and memory integration**.
*(Grouped another way: context retrieval · generation · processing · management.)*

**How it relates to everything else:**
```
        CONTEXT ENGINEERING  (everything the model sees)
        ├── Prompt engineering   (just the instruction you write)
        └── RAG                  (external documents pulled in)

   Engineering a user harness is a specific form of context engineering —
   it is how guides and sensors are made available to the agent.
```

### Prompt engineering

**A prompt** is an instruction given to a model to perform a task. Prompt engineering is **human-to-AI communication** — a real and useful skill.

> **The professor's caveat, worth quoting:** *"The problem is not with prompt engineering. It's a real and useful skill to have. The problem is when prompt engineering is the only thing people know."*

**The three techniques:**
* **Zero-shot** — ask for the task with no examples; relies entirely on pre-trained knowledge.
* **Few-shot** — include a small number of worked examples in the prompt to demonstrate the task and expected output format.
* **Chain-of-Thought (CoT)** — instruct the model to reason step by step, breaking the problem into smaller components before concluding.

**System prompt vs user prompt:** instructions from the **application developer** go in the **system prompt**; instructions from the **end user** go in the **user prompt**. *(Both consume context — see Part 5.)*

### RAG — Retrieval-Augmented Generation

Making the model reference an **authoritative knowledge base outside its training data** before answering. Four steps:

1. **Ingestion** — documents are cut into chunks and stored as **vectors** in a database.
2. **Retrieval** — your question is matched **by meaning** against those vectors; the closest chunks come back.
3. **Augmentation** — those chunks are added to your question to build a new, detailed prompt.
4. **Generation** — the LLM reads that enriched prompt and writes a grounded, fact-based reply.

**Why it matters here:** RAG is the alternative to brute-force context stuffing. Instead of dumping a 100,000-line repo into the window (and losing the middle), you retrieve only what's relevant.

### The 5 layers of AI engineering — the centre of gravity is drifting away from the model

| Layer | Period | Core question | Focus | Primary output |
|---|---|---|---|---|
| **1. Prompt engineering** | 2022–2023 | *How do we talk to the model?* | Syntax and phrasing of instructions | Code snippets, autocomplete |
| **2. Context engineering** | 2024–2025 | *What does the model know?* | Relevance and memory — RAG, token budgeting, structuring | Multi-file, context-aware feature logic |
| **3. Harness engineering** | 2026 | *How is the model allowed to act?* | Tools, permissions, cybernetic feedback | Autonomous repository tasks |
| **4. Loop engineering** | Emerging | *How does one agent self-correct?* | Automated cycles of act → test → adjust until the goal is met, with retry limits and test-driven termination | End-to-end bug fixing |
| **5. Graph engineering** | Frontier | *How do many agents coordinate?* | The graph the system executes: **nodes** (LLM call, deterministic function, router, verifier, human approval), **edges** (what runs next), **shared state** travelling along them | Complete enterprise feature delivery |

*(Organisations climb a parallel adoption ladder: ad-hoc web-chat prompts → in-IDE copilots → repo-grounded RAG → agentic workflows with harnesses → systemic spec-to-deployment platforms.)*

### The three-layer operating model and the three gates

```
1. SPEC LAYER    — WHAT must be built
                   Precise human-authored intent, architectural constraints, AGENTS.md
2. HARNESS LAYER — WHAT IS ALLOWED to happen
                   Sandboxes, permission firewalls, test suites, security gates
3. LOOP LAYER    — HOW the work gets done
                   The agent's act → evaluate → correct cycle, running until convergence
```

**The three gates of agent autonomy — match the gate to the blast radius:**

| Gate | How it works | Use it for |
|---|---|---|
| **Human-in-the-Loop (HITL)** | Explicit human approval for **every** action/PR | High-risk: production deploys, DB migrations, auth, payments, new dependencies |
| **Human-on-the-Loop (HOTL)** | Agent runs continuously; humans monitor dashboards and aggregate telemetry, intervening on exceptions | Medium-risk, well-instrumented work |
| **Autonomous (bounded)** | Fully independent, strictly inside sandboxes and constraints | Low-risk, well-harnessed: docstrings, formatting, internal variable renames, running local tests |

> **Professor's rules for this part:**
> * **The centre of gravity is the harness, not the model.** Don't wait for the next frontier model to solve your problems — the model is commodity intelligence. **Your engineering IP is the harness.**
> * **Beware the "uncaged agent" anti-pattern.** *The cautionary tale:* an agent with unrestricted shell access on a CI server hits a permission conflict, tries `sudo rm -rf`, path expansion fails, it escalates to `sudo rm -rf /* --no-preserve-root` — and wipes the host, its secrets, worktrees and Docker daemons. **Tool execution must be confined to ephemeral, non-root containers.**
> * **Always cap execution loops.** Without a hard timeout and a token budget ceiling, an agent will loop forever on an unfixable test and burn hundreds of dollars.

---

# Part 7 — Prompt vs fine-tune, MCP, and AI-enabled systems (CS7)

### Prompt-based techniques vs fine-tuning

The defining line: **does it update the model weights?**

| | **Prompt-based (prompt engineering, in-context learning)** | **Fine-tuning (full, PEFT, LoRA)** |
|---|---|---|
| **Weights** | **Not updated** | **Updated** via backpropagation on your data |
| **Upfront cost** | Zero — instant iteration, no downtime | High — compute plus dataset curation |
| **Portability** | **Model-agnostic** — move your prompts from one provider to another | **Locked** to a specific base model |
| **What it buys** | Fast experimentation | Permanently instilled domain vocabulary, tone and rigid syntax |
| **Running cost** | Recurring token cost on **every** call; few-shot examples re-sent each time | Lower per-call latency and token count (no prompt bloat) |
| **Limits** | Bounded by the context window | Maintenance burden; risk of **catastrophic forgetting** of general reasoning |

### The unified triangle: Prompt vs Context vs Harness

| | **The Prompt** | **The Context** | **The Harness** |
|---|---|---|---|
| **What it is** | The task or question | The reference material | The testing machinery |
| **Target audience** | The LLM | The LLM | **The AI engineer** |
| **Where it lives** | User input or application logic | System instructions or a vector database | CI/CD pipeline or local test suite |
| **Goal** | **Get the right answer right now** | **Prevent hallucinations** | **Prove the system works at scale** |

**Memorise that last row** — it is the cleanest one-line distinction in the course.

### AI engineering vs traditional ML engineering — an inversion

```
TRADITIONAL ML ENGINEERING  (model-first, disjointed)
  gather & clean data → train model → evaluate offline → build product (LAST)
  Focus: loss functions, hyperparameters, offline F1 scores
  Model development and product development are separate processes

MODERN AI ENGINEERING  (product-first, systems-centric)
  build the product → call a foundation-model API → optimise harness & context
                    → invest in data/fine-tuning ONLY if the product shows promise
  Focus: user experience, deterministic guardrails, latency, cost, reliability
```

**The point:** because capable models are readily available, you can **build the product first** and only invest in data and models once it shows promise. That reverses the classic ML order.

### Model Context Protocol (MCP)

**What it is:** an **open-source standard for connecting AI applications to external systems** — data sources (local files, databases), tools (search engines, calculators) and workflows (specialised prompts).

**The one-line definition to write:** *MCP is a USB-C port for AI applications.* Before it, connecting an agent to Postgres + GitHub + Slack + Jira meant **N × M bespoke integrations**. MCP makes it one standard.

**The three participants (client-server architecture):**

| Role | What it does |
|---|---|
| **MCP Host** | The AI application that **coordinates and manages one or more MCP clients** — e.g. Claude Desktop, Cursor, a custom agent runner. Captures the user query, holds session context, drives the LLM |
| **MCP Client** | Lives inside the host; maintains a **1:1 connection to one MCP server**, discovers its capabilities, and obtains context for the host |
| **MCP Server** | A lightweight program that **provides context to clients**, exposing three things: **Tools** (callable functions like `query_sql()`, `send_email()`), **Resources** (readable data such as file contents or logs), and **Prompts** (pre-packaged templates) |

**The transport layer — messages are JSON-RPC 2.0, over one of two transports:**

| | **`stdio` (standard input/output)** | **`SSE` (Server-Sent Events over HTTP)** |
|---|---|---|
| **Mechanism** | OS-level process pipes | Streaming HTTP |
| **Best for** | **Local resources** — local tools, CLI programs, on-prem databases | **Remote resources** — cloud services, third-party APIs |
| **Characteristics** | Fast, synchronous, process-level isolation, **zero exposed network ports** | Real-time streaming, network-routable, secured by TLS/OAuth2 |

**How a request actually flows** (*"find the latest sales report in our database and email it to my manager"*):
1. **Tool discovery** — the LLM knows it can't query a DB or send mail itself, so via the MCP client it discovers two registered tools: `database_query` and `email_sender`.
2. **Tool invocation** — it generates a structured request for `database_query`; the client routes it to the right server.
3. **External action & return** — the server translates it into a **secure SQL query**, retrieves the report, formats it, and sends the data back.
4. **Second action** — now holding the data, the LLM calls `email_sender` with the manager's address and the content; the server confirms.
5. **Final response** — "I've found the report and emailed it to your manager."

**The security point for exam answers:** the MCP server is where the *translation and the privilege* live. The LLM never holds the DB credentials — it asks for a capability, and the server decides how (and whether) to execute it. That makes MCP a natural **permission firewall**.

### The three layers of the AI stack

1. **Application development (top)** — agent harnesses, context assembly, prompt workflows, UI, MCP host coordination.
2. **Model development (middle)** — foundation models and LRMs, fine-tuned weights, serving engines (vLLM, Ollama).
3. **Infrastructure (bottom)** — GPU/TPU compute, vector databases, networking, distributed storage.

### Engineering AI-enabled systems (CMU SEI)

The software lifecycle changes significantly once ML components are introduced, driven mainly by **data centricity**. AI systems introduce **intense probabilistic uncertainty** — but **existing software design techniques remain the essential starting point**. Security, usability and privacy are already mainstream architectural concerns; **the real difference is which quality attributes you must now prioritise**:

| Quality attribute | What it demands |
|---|---|
| **Verifiability** | Being able to **deterministically prove** an AI-generated artifact meets safety, functional and performance requirements *before* release |
| **Explainability & traceability** | An immutable audit log of **why** an agent chose a tool, what context it ingested, and what intermediate reasoning occurred |
| **Data centricity & provenance** | Tracking lineage, freshness and security classification of every piece of data pulled into the context window |
| **Change propagation & regression safety** | Ensuring that editing a system prompt or upgrading the model version does not silently break 20 downstream services |

> **The SEI line to quote:** *"Invest in systems, not just models."* Shift focus away from the hype curve of raw model capability toward the **software engineering infrastructure that wraps, constrains and safeguards probabilistic components.** *(The **AI Complexity Matrix** comes from the CMU SEI "AI Adoption Maturity Model v1.0".)*

---

# Part 8 — AI-native SDLC and Spec-Driven Development (CS8)

### The problem: handoffs are a telephone game

```
Product Manager (PRD) → Architect (design) → Developer (code) → QA (tests)
        ↓ drift              ↓ drift             ↓ drift
   Every boundary loses intent. QA finally discovers the built system
   isn't what the business asked for — after all the money is spent.
```

Every verbal meeting and informal handoff introduces interpretation error. Intent degrades at each boundary, and the rework lands at the most expensive point.

### Vibe coding vs Specification-Driven Development

* **Vibe coding** — typing loose natural-language prompts, blindly accepting the output, and tweaking until it *appears* to work. Produces catastrophic technical debt, missing edge cases and zero architectural cohesion.
* **Spec-Driven Development (SDD)** — **the specification is the single source of truth.** Humans invest their cognitive effort **upfront**, writing structured, version-controlled markdown specs. Agents then generate code strictly against those contracts, under deterministic test verification.

**Why SDD is the natural conclusion of this whole course:** if code is cheap and intent is precious (Part 3), then the artifact worth version-controlling and reviewing is **the spec**, not the code.

### The 3 canonical spec files

| File | Answers | Contains |
|---|---|---|
| **`requirements.md`** | **WHAT** to build | User stories and business motivation; functional requirements; non-functional constraints (SLAs); **EARS-style acceptance criteria** (Given-When-Then) |
| **`design.md`** | **HOW** to build it | Component topology and data flow; strict API schemas (OpenAPI/Protobuf); database schemas, indexing strategy, state machines; **ADRs** explaining the trade-offs |
| **`tasks.md`** | **IN WHAT ORDER** | Ordered, bite-sized, independently testable units; an explicit dependency graph (task 3 needs 1 and 2); concrete verification steps per task |

**Steering files** — repository-level instruction files (`steering.md`, `.cursorrules`, `AGENTS.md`, `CLAUDE.md`) that put enterprise conventions permanently in the agent's context: *"every API endpoint must enforce JWT auth and emit an audit log."* These are **feedforward guides** from Part 6.

*(Frameworks that implement this: Kiro, SpecKit.)*

### The "disposable microservices" fallacy

**The claim:** *"Code generation is free, so we won't refactor or write unit tests. When requirements change, we update the spec and regenerate the whole service from scratch."*

**Why it fails — four mechanisms. These are the highest-yield points in the syllabus:**

1. **Loss of tacit knowledge.** A production service accumulates hundreds of subtle fixes over years — workarounds for a third-party API's rate limits, socket timeout tweaks, race-condition mitigations, obscure compliance edge cases. **Almost none of it gets back-ported into the high-level spec.** Regenerating from scratch wipes it all and instantly reintroduces dozens of already-solved production bugs.
2. **Non-deterministic behavioural drift.** LLMs are probabilistic. Regeneration yields different internal algorithms, different connection pooling, different concurrency models, subtle schema variations. **Neighbouring services depend on stable timing, caching and error-response behaviour** — so you get unpredictable distributed regressions across service boundaries.
3. **The validation paradox.** Abandoning unit tests destroys the verification harness. High-level specs state *intent*; they cannot catch low-level edge-case regressions. You end up with **zero automated proof** that the new service honours system invariants — pure **validation debt**, pushed onto manual E2E testing or production monitoring.
4. **Supply-chain re-ingestion.** Every scratch generation lets the agent pick fresh third-party dependencies — reopening the door to **slopsquatting**, deprecated libraries and unvetted CVEs.

**The correct synthesis to write:** the architect got the **first half** of the Inversion of Value right (code is cheap) and the **second half** exactly wrong. Value moved **upstream to specification precision** and **downstream to verification harnesses and invariants** — so eliminating tests contradicts the very principle being invoked. **You don't create value by throwing code away; you create it by designing immutable invariants and automated verification gates.**

### Local optimisation vs systemic enablers

```
┌────────────────────┐    ┌────────────────────┐    ┌────────────────────┐
│ Coding throughput  │───►│ Review & QA queue  │───►│ Deployment pipeline│
│   ▲ 40% increase   │    │  MASSIVE BOTTLENECK│    │  STALLED           │
│ (local optimum)    │    │  (WIP accumulates) │    │  lead time: 4 weeks│
└────────────────────┘    └────────────────────┘    └────────────────────┘
```

**The fallacy:** buy AI tools for 200 developers, PR throughput jumps 40%, and lead time doesn't move.

**The diagnosis (Goldratt):** coding was never the constraint. Flooding a constrained downstream with 40% more PRs creates a **WIP traffic jam** — seniors drowning in unvetted PRs (reviewer cognitive fatigue), QA waiting on contended shared staging, deployment configs needing manual firefighting.

**The remedy:** move investment **from local developer tools to systemic flow enablers**:
* Stop measuring raw activity (lines written, PRs opened); measure **flow efficiency** — idea to production.
* **Subordinate the pipeline to the bottleneck** (Lean): throttle or couple code creation to validation and release capacity; invest in automating review, staging and deployment.
* Track **balanced DORA metrics** — **Lead Time for Changes, Change Failure Rate, MTTR** — not PR throughput. *If lead time doesn't shrink and failure rate spikes, AI is destroying value.*

### The two technical foundations that unlock real AI value

1. **Automated ephemeral environments + declarative CI/CD.**
   *Build:* on-demand, isolated preview environments for **every PR** (Kubernetes, Docker, Terraform/IaC), torn down automatically.
   *Impact:* kills "waiting for the QA environment" and staging contention; every AI-generated PR is validated hermetically and in parallel.
2. **Deterministic verification harnesses + automated contract testing.**
   *Build:* consumer-driven contract tests (**Pact**), hermetic integration tests (**Testcontainers**), AST-based linters, all in CI.
   *Impact:* catches hallucinations, behavioural drift and contract violations **before a human opens the PR** — relieving reviewers of basic verification so they can spend attention on architecture. This directly de-constrains the bottleneck.

> 💡 **Tech primers:** `Testcontainers` spins up real disposable Docker containers (Postgres, Redis, Kafka) during tests instead of misleading in-memory mocks. `Pact` verifies that a provider's API still satisfies what each consumer actually relies on. `LaunchDarkly` toggles features at runtime without redeploying.

---

# Part 9 — The trade-off playbook

Every trade-off answer has the same shape: **what pulls against what → why, mechanically → how an engineer resolves it.**

### 1. Generation speed vs reviewer cognitive fatigue
* **Tension:** an agent writes 500 lines in 10 seconds; a human verifies 500 lines in 45 minutes.
* **Failure mode:** reviewers either rubber-stamp (outages) or become the bottleneck (delivery stalls). Both are WIP bloat.
* **Fix:** cap agentic PR size (small atomic commits, ~≤150–300 lines); require **passing automated contract and regression tests before a PR ever reaches a human inbox**.

### 2. Disposable regeneration vs long-lived invariants
* **Tension:** regeneration is cheap, but systems depend on long-lived contracts and accumulated fixes.
* **Use disposable regeneration for:** throwaway prototypes, stateless single-file lambdas, benchmark scripts, UI mockups.
* **Use long-lived maintenance for:** transactional databases, auth/authorisation services, payment gateways, shared enterprise libraries.
* **Rule:** *code is disposable, data and contracts are not.*

### 3. Computational guardrails vs inferential (LLM) evaluators
* **Tension:** validate AI output with deterministic code, or with another model?
* **Computational** (AST, JSON schema, compilers, regex, permission checks) — syntax, schema conformance, parameter types, security checks. 100% deterministic, unhallucinatable, free.
* **Inferential** (LLM-as-judge) — subjective UX review, brand voice, docstring clarity, intent summarisation.
* **Rule:** **computational controls are the final gate; inferential controls are advisory.**

### 4. Prompt engineering vs RAG vs fine-tuning

```
                 Do you need to change the model's WEIGHTS?
                    ┌───────────── no ─────────────┐         yes
                    ▼                              ▼          ▼
        Do you need external / dynamic data?              FINE-TUNING
          ┌──── no ────┐       ┌──── yes ────┐            (PEFT/LoRA/full)
          ▼            ▼       ▼                          • permanent style,
   PROMPT ENGINEERING        RAG                            tone, rigid syntax
   • fast iteration         • vector search / MCP          • lower per-call latency
   • static system prompts  • dynamic enterprise docs      • high upfront cost
                                                           • locked to a base model
```

### 5. Agentic autonomy vs HITL gate placement
* **Tension:** autonomy buys speed; gates buy safety and accountability.
* **Autonomous (no gate):** reading files, planning steps, running local tests, renaming internal variables, generating docs.
* **Mandatory HITL gate:** changing public API contracts, DB schema migrations, **adding third-party dependencies**, promoting to production, IAM/auth changes.
* **Rule:** *place the gate where the blast radius is, not where the uncertainty is.*

### 6. Deterministic code vs LLM calls on the hot path (cost)
* **Tension:** an LLM call is flexible; it also costs money and latency on every single request.
* **Fix:** high-volume, high-frequency paths use deterministic code (regex, SQL index, cached lookup); reserve inference for genuinely ambiguous work. Cache repeated LLM responses (e.g. in Redis). Put a **token budget gate** in CI so a feature can't ship if its projected COGS destroys gross margin.

---

# Part 10 — Solved exam paper (answer skeletons)

Each bullet below is one mark. Expand each into 2–3 crisp sentences in the exam. Structure = **diagnose → mechanism → fix.**

---

### Q1 [6 marks — official sample] "Specification-Driven, Disposable Microservices"

> *An architect declares: "Since code generation is free, we will no longer refactor old code or write comprehensive unit tests. If a microservice needs modification, we update the design spec and have an AI agent regenerate the service from scratch."*

**(a) Evaluate this in light of the Inversion of Engineering Value [3]**
1. **The half he got right.** He correctly recognises the first half of the **Inversion of Engineering Value** — raw syntax has become a commodity with marginal cost ≈ 0.
2. **The half he got wrong.** He misunderstands **where the value went**. It migrated **upstream to specification precision** and **downstream to verification harnesses, boundary constraints and architectural invariants**. Declaring "no more unit tests" attacks exactly the half of the inversion that now carries the value.
3. **The synthesis.** Because generative output is probabilistic, it cannot be trusted without a **deterministic verification harness**. A high-level spec states *intent*; only independent boundary tests catch low-level edge-case regressions. **Value is created by designing immutable invariants and automated gates — not by throwing code away.**

**(b) Analyse the downstream maintainability risks [3]**
1. **Loss of tacit knowledge.** Years of undocumented fixes — third-party rate-limit workarounds, socket timeouts, deadlock mitigations, compliance edge cases — are never back-ported to the spec. Regeneration **wipes them and reintroduces dozens of solved production bugs.**
2. **Non-deterministic behavioural drift + contract brittleness.** Regeneration produces different internal algorithms, pooling behaviour, concurrency models and subtle schema variations. Neighbouring services depending on stable timing and error semantics **fail unpredictably**.
3. **Supply-chain ingestion + validation debt.** Each scratch generation re-picks dependencies → **slopsquatting** and CVE exposure. With no unit tests, bug discovery shifts entirely to manual E2E or production monitoring — **insurmountable validation debt.**

---

### Q2 [9 marks — official sample] PR throughput up 40%, lead time unchanged

> *A director buys AI coding licences for 200 developers. PR throughput rises 40%. Lead time for changes stays at 4 weeks. Developers say they write code faster but spend afternoons in meetings, waiting for QA environments, and fighting deployment configs.*

**(a) Why didn't 40% more PRs shorten time-to-market? [3]**
1. **Principle — Goldratt's Theory of Constraints.** End-to-end lead time is set by the **slowest stage**, not the fastest. **Coding was never the constraint**, so accelerating it is a **local optimisation** that cannot improve global flow.
2. **Mechanism — WIP bloat and reviewer fatigue.** 40% more PRs with unchanged review/test/deploy capacity floods the pipeline with unmerged inventory. Seniors suffer **cognitive fatigue** parsing high-volume AI PRs; queues grow, merge conflicts multiply, context switching explodes.
3. **Metric contrast.** They optimised a **local activity metric** (PR throughput) while the **DORA Lead Time for Changes** — the only one tied to customer value — stayed at 4 weeks. The real constraints (shared staging contention, coordination meetings, brittle deploy configs) received no investment at all.

**(b) How to shift from "local optimisation" to "systemic enablers" [3]**
1. **Map and optimise the value stream.** Stop measuring lines written and PRs opened; measure **flow efficiency** — friction-free transit from idea to production.
2. **Subordinate the pipeline to the bottleneck (Lean).** Throttle or couple code creation to validation and release capacity, and **redirect investment from front-end generation tools to downstream enablement**: automated review, elimination of staging contention, automated deployment.
3. **Adopt balanced lifecycle metrics.** Track **Lead Time for Changes, Change Failure Rate and MTTR** together. **If lead time doesn't fall and CFR rises, AI is destroying value, not creating it.**

**(c) Two technical foundations to prioritise [3]**
1. **On-demand ephemeral preview environments + declarative CI/CD.** Containerised, isolated environments spun up per PR via Kubernetes/Docker/Terraform and torn down after. **Kills "waiting for QA environments"** and staging contention; every AI PR is validated hermetically, in parallel.
2. **Deterministic verification harnesses + automated contract testing.** Consumer-driven contract tests (Pact) and hermetic integration tests (Testcontainers) with AST linters in CI. **AI code is validated against rigid contracts before a human opens the PR** — slashing reviewer fatigue and unclogging the review queue, which is precisely where the constraint sits.

---

### Q3 [6 marks — high-yield] Slopsquatting in autonomous dependency resolution

> *An autonomous agent in a fintech CI/CD pipeline inserts `import { signPayload } from 'fast-crypto-auth-jwt'`. An attacker registered that exact name on npm 48 hours earlier, having predicted it would be hallucinated.*

**(a) Explain the mechanism and how the breach succeeds [3]**
1. **The hallucination vector.** LLMs are probabilistic token predictors. Needing a library that doesn't exist, the model **invents a semantically plausible name** rather than failing.
2. **Reconnaissance and squatting.** Attackers prompt public models across thousands of common tasks, **catalogue the hallucinated names**, and pre-register them on npm/PyPI with trojans embedded.
3. **The enterprise breach.** The agent commits it; the build runner executes `npm install`; **the payload runs with the full privileges of the CI/CD runner** — exfiltrating AWS credentials and DB secrets, or backdooring customer production builds. *(Note the amplification: an autonomous agent does this at machine scale, with no human pausing to wonder whether the package is real.)*

**(b) Design a guardrail using Computational Controls [3]**
1. **Private proxy registry with strict allow-listing.** Route every package request through internal Artifactory/Nexus; **disable direct outbound access to public registries** entirely. Deterministic, unbypassable by prompt injection.
2. **Automated provenance and metadata gate.** A CI check that **rejects any package published < 30 days ago**, or below minimum download/reputation thresholds, or lacking verified maintainer signatures.
3. **Lockfile integrity + HITL dependency gate.** Agents are **computationally barred** from editing `package.json`/`package-lock.json`; any new third-party dependency requires a **human security-architect sign-off**. *(State the principle: this is a computational control, not an inferential one — you never ask an LLM "is this package safe?")*

---

### Q4 [6 marks — high-yield] MCP in enterprise architecture

> *A health-tech firm builds an AI medical assistant that must read patient lab records from an on-premise Oracle DB, search internal clinical guidelines, and send SMS alerts to doctors.*

**(a) How MCP coordinates Host, Client and Server [3]**
1. **MCP Host — the orchestrator.** The AI application (the doctor's portal). Captures the query, holds session context, drives the LLM, and manages the lifecycle of multiple MCP clients.
2. **MCP Client — the protocol adapter.** Lives inside the host; maintains a **1:1 connection** with one server, discovers its tool catalogue over **JSON-RPC 2.0**, and presents the available capabilities (`query_patient_records`, `search_guidelines`, `send_sms`) to the LLM.
3. **MCP Server — the secure tool provider.** Lightweight programs exposing **Tools, Resources and Prompts**: a database server translating requests into **parameterised SQL** against Oracle; a documents server exposing the guidelines repository; an SMS server wrapping the telecom REST API. **Credentials stay in the server — the LLM never holds them**, which makes the server a permission firewall.

**(b) `stdio` vs `SSE` — recommend a transport for each [3]**
1. **Characteristics.** `stdio` runs over OS process pipes — ultra-low latency, synchronous, process-isolated, **zero exposed network ports**. `SSE` streams over HTTP — asynchronous, network-routable, secured with TLS/OAuth2.
2. **On-premise Oracle → `stdio`.** Keeps patient data and DB credentials inside the local secure runtime with **no open HTTP endpoint**, eliminating network eavesdropping — the right call for **HIPAA-grade data**.
3. **External SMS provider → `SSE` over HTTPS.** The telecom API is a remote cloud endpoint, so you need a network-routable transport that streams asynchronously, tolerates remote latency, and integrates with cloud API gateways.

---

### Q5 [6 marks — high-yield] Context saturation and constrained decoding

> *An assistant must extract REST endpoint contracts from a 100,000-line legacy Java monolith into strict OpenAPI JSON. The team pastes the whole codebase into a 1M-token context window. The output has invalid JSON, hallucinated HTTP status codes, and omits endpoints defined in middle files.*

**(a) Analyse the mechanical causes [3]**
1. **"Lost in the Middle" — attention dilution.** Retrieval accuracy is **U-shaped**: strong at the start (primacy) and end (recency), dropping up to 50% in the centre. The **omitted endpoints were buried mid-payload**, so the model never attended to them.
2. **Context pollution and semantic dilution.** 100,000 lines of getters, setters, imports and build scripts dilute the attention distribution; scaled dot-product attention **cannot isolate the endpoint annotations from the boilerplate**. *(And O(N²) attention means this also costs enormously and slows time-to-first-token.)*
3. **Syntax drift under saturation.** With no structural constraint on generation, a single misplaced bracket or trailing comma breaks the JSON — and near context saturation, confabulation (invented status codes) rises sharply.

**(b) Propose a system-level remedy [3]**
1. **Deterministic AST extraction instead of context stuffing.** Use **Tree-sitter** to programmatically extract only the controller route annotations (`@GetMapping`, `@PostMapping`, paths, parameter types) and assemble a clean **~2,000-token** context of endpoint signatures. **Let the computational tool do what it does perfectly, and give the model only what needs judgement.**
2. **Constrained decoding at the logit level.** Enforce the OpenAPI grammar during generation — any token that would violate the schema has its probability masked to zero. This **mathematically guarantees valid JSON**, rather than asking the model nicely.
3. **Automated schema validation in a feedback loop.** Run the output through `swagger-parser`; feed any diagnostics **back into the agent loop** for self-correction before a human sees it. *(Principle: computational sensors gate probabilistic output.)*

---

# Part 11 — Flashcards, vocabulary, checklist

### The 15 anchors — if you remember nothing else

| Anchor | The rule | Question trigger |
|---|---|---|
| **Core Tension** | Systems must be 100% deterministic; GenAI is a probabilistic token sampler | Why prompting alone can't guarantee production safety |
| **Bottleneck Inversion** | Generating code is cheap; reviewing, verifying and governing it is the bottleneck | Any "we got faster but shipped no faster" scenario |
| **Inversion of Engineering Value** | Syntax ≈ free; value moved **upstream to specs** and **downstream to verification** | Disposable code, free generation, changing developer roles |
| **Goldratt / Theory of Constraints** | Optimising a non-bottleneck only bloats WIP; throughput = slowest stage | PR throughput up, lead time flat |
| **40/60 Split** | 40% of dev time is coding; 60% is coordination, review, environments. AI accelerates only the 40% | Why Copilot licences don't double velocity |
| **Agent = Model + Harness** | Model = intelligence; harness = tools, state, permissions, sandboxes, validation | What an agent is; how to make autonomy safe |
| **Cybernetic Governor** | **Guides** (feedforward: prompts, specs, `AGENTS.md`) before; **Sensors** (feedback: linters, tests) after | Designing guardrails and agent feedback loops |
| **Computational > Inferential** | Deterministic CPU checks are the **final gate**; LLM judges are advisory only | Any guardrail, validation or security design |
| **Lost in the Middle** | U-shaped attention: start and end recalled, middle dropped | Long-context failures; why rules go top or bottom |
| **Constrained Decoding** | Mask invalid tokens' logits to zero → **mathematically guaranteed** valid JSON/code | Guaranteeing structured output |
| **Tool Latching** | Delegate maths/string work to a sandboxed interpreter; LLMs are reasoners, not calculators | Character counting, arithmetic, exact slicing |
| **Slopsquatting** | Attackers register hallucinated package names. Defend with private registries, age/provenance gates, HITL dependency approval | Supply-chain security in AI codegen |
| **MCP** | Host coordinates → Client connects 1:1 → Server exposes Tools/Resources/Prompts, over JSON-RPC 2.0 via `stdio` (local) or `SSE` (remote) | Connecting agents to DBs, tools, APIs |
| **The 3 Canonical Specs** | `requirements.md` (what) → `design.md` (how + ADRs) → `tasks.md` (order) | Spec-Driven Development, vibe coding |
| **Code disposable, data permanent** | Rewrite services freely; schemas, ledgers and IAM are one-way doors | Disposable microservices, architecture decisions |

### One-line definitions

* **SDLC** — the process of planning, developing, testing, deploying and maintaining software to meet customer needs within cost and time.
* **V&V** — Verification: "are we building it right?" (spec conformance). Validation: "are we building the right thing?" (customer fitness).
* **Continuous Delivery** — always deployable, but production needs a human click. **Continuous Deployment** — every passing commit ships automatically. **Release** — the business act of switching it on.
* **MLOps / AIOps** — operationalising models (data + code = model) / using AI on operational telemetry to detect, correlate and remediate.
* **Intent-to-Spec** — turning unstructured stakeholder input into structured OpenAPI schemas and ADRs.
* **Self-healing tests** — suites that auto-update element locators when the UI changes.
* **Circular validation** — AI writes both the code and its tests from the same flawed assumptions, producing a false 100% pass.
* **Technical debt vs unfinished backlog** — compromised quality that accrues interest vs work simply deferred to the next sprint.
* **Code slop** — bloated, redundant AI code that compiles but destroys the team's mental model.
* **One-way door** — an irreversible decision (core schema, ledger) with catastrophic rollback cost.
* **Evals** — quantitative scored benchmarks for non-deterministic output (semantic consistency, hallucination rate, toxicity).
* **COGS / outcome-based pricing** — cost to serve one unit, now including inference / charging per resolved outcome instead of per seat.
* **Foundation model** — a large general-purpose model pre-trained on vast multimodal data by self-supervised learning, adaptable to many tasks.
* **Self-supervised learning** — labels generated from the data itself (next-token prediction), removing the human annotation bottleneck.
* **Transformer / self-attention** — architecture processing all tokens in parallel; each token's Query is scored against every Key to weight every Value. **O(N²) in context length.**
* **System 1 / System 2** — fast single-pass pattern matching / slow deliberate reasoning using test-time compute.
* **Test-time compute** — extra compute spent at inference, exploring and verifying before emitting the answer.
* **Reasoning trace** — the hidden scratchpad chain-of-thought an LRM produces.
* **S2A (System 2 Attention)** — the model rewrites and denoises the prompt before reasoning, removing distractors and sycophancy.
* **Token / BPE** — the model's unit (~4 chars of English) / the standard subword algorithm merging frequent character pairs.
* **Context window** — the hard ceiling on input + output tokens in one call; includes system prompt, full history, attachments and the response being generated.
* **Logit masking** — forcing invalid tokens' sampling probability to zero to enforce a grammar.
* **AI agent** — an autonomous entity running Perceive → Reason → Act → Evaluate, with autonomy inside defined boundaries.
* **SWE-agent** — Princeton's coding agent whose environment is the computer (terminal + filesystem) via an Agent-Computer Interface.
* **Harness engineering** — designing the environment, tools, permissions and feedback sensors around a model. *(Karpathy: LLM = CPU, context = RAM, harness = kernel.)*
* **Context engineering** — deliberately selecting, structuring, compressing and sequencing what the model sees. **Prompt engineering and RAG are subsets of it.**
* **Zero-shot / few-shot / CoT** — no examples / a few worked examples / explicit step-by-step reasoning.
* **RAG** — ingestion → retrieval → augmentation → generation.
* **Loop engineering / graph engineering** — one agent self-correcting until a goal is met / many agents coordinated as nodes, edges and shared state.
* **HITL / HOTL / bounded autonomous** — approve every action / monitor and intervene on exceptions / run free inside a sandbox.
* **Fine-tuning** — updating model weights on your data; permanent style, lower per-call cost, locked to a base model, risks catastrophic forgetting.
* **Prompt vs Context vs Harness** — get the right answer now / prevent hallucinations / prove it works at scale.
* **AI-enabled system quality attributes** — verifiability, explainability & traceability, data centricity & provenance, change propagation & regression safety.
* **SDD / steering files** — the spec is the source of truth / repo-level files putting enterprise conventions permanently in the agent's context.

### "Don't say X, say Y"

| Don't say | Say |
|---|---|
| "AI writes code fast but review is slow" | "The bottleneck has inverted: generation is cheap, **verification is the constraint**" |
| "We got faster but nothing shipped sooner" | "A **local optimisation** of a non-bottleneck; under **Goldratt's Theory of Constraints** it only inflated **WIP**" |
| "Coding isn't valuable any more" | "The **Inversion of Engineering Value**: value migrated upstream to **specification precision** and downstream to **verification harnesses**" |
| "The AI made a mistake" | "Probabilistic output entered a deterministic system without a **computational control** gating it" |
| "Ask another AI to check it" | "**Inferential controls** are advisory; the **final gate must be computational**" |
| "The prompt was too long" | "**Attention dilution** — the constraint sat in the **'lost in the middle'** region of the context window" |
| "Tell the model to return JSON" | "Enforce the schema with **constrained decoding** — mask invalid tokens at the logit level" |
| "Let the agent run commands" | "Tool execution is confined to an **ephemeral non-root sandbox** behind a **permission firewall**, with a capped loop budget" |
| "It installed a bad package" | "A **slopsquatting** supply-chain attack via a hallucinated dependency; mitigated by a **private proxy registry** and a **HITL dependency gate**" |
| "We'll just regenerate the service" | "That discards **tacit knowledge** and invites **non-deterministic behavioural drift** across service contracts" |
| "Writing prompts is the skill" | "Prompt engineering is a subset of **context engineering**; the centre of gravity has moved to **harness engineering**" |
| "AI is expensive" | "Software lost its **zero marginal cost**; **COGS now scales with inference**, so design for **cost efficiency per query**" |

### Last-hour checklist

1. **Read the scenario twice.** The trigger words tell you which principle to name: *throughput/lead time* → Goldratt · *free code/disposable* → Inversion of Value · *regenerate* → tacit knowledge + drift · *long prompt* → Lost in the Middle · *autonomous agent* → harness + sandboxes + gates · *package/dependency* → slopsquatting · *guarantee JSON* → constrained decoding · *connect to a DB/tool* → MCP.
2. **3 minutes per mark.** A 3-mark sub-part gets 9 minutes. Don't overrun — there is no choice, so an unanswered part is a guaranteed zero.
3. **Open with the diagnosis, never with a preamble.** First sentence names the principle. Generic introductions score zero.
4. **Three bullets per 3-mark part**: principle → mechanism → fix. One mark each.
5. **Always name the countermeasure concretely** — Pact, Testcontainers, Tree-sitter, private registry, ephemeral environments, HITL gate, constrained decoding, ArchUnit. Vague "add more testing" doesn't score.
6. **Always state the trade-off explicitly** in one sentence: *"This improves X via [mechanism] but degrades Y because of [cause], mitigated by [countermeasure]."*
7. **Anchor every answer in a concrete system** — payment service, CI/CD pipeline, fintech ETL, health-tech assistant, legacy Java monolith.
8. **Be short and crisp.** The professor said explicitly: marks are not for word count. Five tight lines beat two vague paragraphs.
