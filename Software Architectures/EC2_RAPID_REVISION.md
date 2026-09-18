# EC-2 — Last-Minute Notes

**Read this top to bottom. It takes about 25 minutes. If you read nothing else, this is enough to write the paper.**

Nothing here is a list to memorise. Everything is explained, so if you forget the exact words in the exam, you can still work the answer out from scratch.

---

## PART 1 — The one idea the whole subject is built on

Any developer can write software that **works**.

The hard part is writing software that is **fast enough**, **safe enough**, **stays up**, and **can be changed later without breaking**. Those "enough" things have a name: **quality attributes**.

**Architecture is the set of big structural decisions you make to get those qualities.**

Three things follow from this, and they explain most of the syllabus:

1. **Features don't shape architecture — qualities do.** "Users can pay by card" can be built a hundred different ways. "50,000 payments per second, never losing one" forces your hand. So architecture is driven by *how well*, not *what*.
2. **You can't have all the qualities at once.** More security means slower. More flexibility means slower. More reliability means more money. So every architecture answer involves a **trade-off**.
3. **These decisions are made first and are expensive to undo.** You cannot switch from one database design to another the way you rename a variable. So you have to think before you build, and check your thinking before you build.

If a question confuses you, come back to these three. Most answers are somewhere in here.

---

## PART 2 — The whole course as one story

Read this once and the modules stop feeling separate.

1. **A business wants something.** "We want to sell in Europe."
2. **People ask for it vaguely.** "Make it fast, make it secure, make it easy."
3. **You turn vague into measurable.** "Checkout finishes in under 2 seconds for 10,000 users at once." Now it can be tested. *(This is what a **scenario** is.)*
4. **You find the few requirements that really shape the design.** Most requirements are routine. A handful decide everything. *(These are the **ASRs**.)*
5. **You design the system around those few.** *(The method is called **ADD**.)*
6. **You draw the design from a few different angles** so different people can understand it. *(These are **views** — Kruchten's **4+1**.)*
7. **You review the design on paper before writing code,** because fixing it later costs a hundred times more. *(The review method is **ATAM**.)*
8. **Developers write the code, and slowly break the rules** to meet deadlines. *(This is **drift**, and if ignored, **erosion**.)*
9. **You enforce the rules.** And if the system is already a mess with no documents, you reverse-engineer what's actually there. *(That's **SAR** — reconstruction.)*

That's it. That's the subject. Everything below just fills in each step.

---

## PART 3 — What architecture actually is

**The definition to quote (Bass, Clements and Kazman):**
> *"The software architecture of a system is the set of software structures needed to reason about the system, which comprise software elements, relations among them, and properties of both."*

In plain words: architecture is the **parts**, **how they connect**, and **what each part promises to the others**.

The important half is that last bit. Architecture cares about what a component **promises publicly** — its interface, how fast it responds, what happens when it fails. It does **not** care what happens inside it. If you swap a sorting algorithm inside one function, nobody outside notices, so that is not architecture.

**How to tell if a decision is architectural — three questions:**
* Does it affect more than one part of the system?
* Would it be expensive and painful to reverse later?
* Can other components see the effect of it?

All yes → architectural. ("Use an event queue instead of direct calls.")
All no → just detailed design. ("Use an ArrayList instead of a LinkedList.")

---

## PART 4 — The qualities, and what you do about them

There are seven the course cares about. For each one, the "tactics" are just the sensible things you can do. **Don't memorise the lists — understand the logic and the list writes itself.**

### Availability — is it up when I need it?
Things break. There are only three things you can possibly do about breaking:

* **Notice it broke.** Ping the server and see if it answers. Or have the server shout "I'm alive" every second (a *heartbeat*) and worry when it goes quiet.
* **Get back up.** Keep a spare. A **hot** spare is already running and takes over instantly. A **warm** spare gets regular updates and takes seconds. A **cold** spare is switched off and takes minutes. Or save your progress regularly so you can restart from the last save point.
* **Stop it breaking.** Use database transactions so a half-finished operation rolls back instead of corrupting data. Restart servers before they run out of memory.

**Formula:** `Availability = MTBF / (MTBF + MTTR)`.
MTBF = how long it runs before breaking. MTTR = how long it takes to recover. So you improve availability by breaking less often, *or* by recovering faster — and recovering faster is usually cheaper.

### Performance — how fast, how much?
Only two ways to be faster: **do less work**, or **use your resources better**.

* **Do less work:** limit how many requests one user can send; return 20 search results instead of 50,000; drop non-essential logging when overloaded.
* **Use resources better:** cache things you keep asking for (Redis) so you don't hit the database; run many copies behind a load balancer; use threads so one slow job doesn't block everything.

### Security — keep bad actors out, keep working for good ones
Four stages, and they're just common sense in order: **notice the attack → block it → respond → recover.**

* Notice: monitoring and logs that flag strange activity.
* Block: passwords plus a second factor, role-based permissions, encryption, and checking every input (so nobody can type SQL into your form).
* Respond: log the session out, block the IP, alert someone.
* Recover: restore from clean backups, read the audit log to see what happened.

**The six things security must guarantee:** only the right people can read data (confidentiality), nobody secretly changes it (integrity), it stays usable under attack (availability), we know who you are (authentication), we know what you're allowed to do (authorisation), and you can't deny doing it later (non-repudiation).

### Modifiability — how cheap is it to change?
Two ideas only:

* **Reduce dependencies.** Hide the internals behind a clean interface. Put something in the middle (a queue, a gateway, a façade) so two parts don't touch directly. Keep the layers clean so nothing calls in circles.
* **Decide as late as possible.** Put settings in config files instead of code. Choose the implementation at runtime instead of hardcoding it. Allow plugins.

The underlying rule: **keep related things together, keep unrelated things apart.** (High cohesion, low coupling.)

### Usability — three parts
* **Effectiveness** — did they get it right? (validation, confirm screens)
* **Efficiency** — how much effort did it cost? (one tap, fingerprint instead of typing)
* **Satisfaction** — did it feel good? (progress bars, friendly errors, undo)

These fight each other. Adding a confirmation screen makes people accurate but slow. One-tap payment is fast but people make mistakes.

### Interoperability — can two systems talk?
* **Syntactic** = same format (both use JSON).
* **Semantic** = same meaning (both agree what "delivery date" means).
Getting the format right is easy; getting the meaning right is the hard part. You fix mismatches with an **adapter** that translates between them.

### Testability — how easily can I find bugs?
* Swap out the real outside world for fakes during tests (a fake payment gateway instead of charging a real card).
* Expose what's happening inside (a `/health` or `/metrics` endpoint) so tests can look in.

---

## PART 5 — Which requirements actually matter (ASRs)

In a backlog of 200 requirements, maybe 190 are routine — "user can upload a profile photo". Any design handles them.

About **5%** are different. They force decisions that shape the entire system. These are **Architecturally Significant Requirements**.

**A requirement is an ASR if any of these are true:**
* Getting it wrong costs serious money, legal trouble, or reputation.
* It demands scale or speed that normal setups can't give you.
* A law or regulation forces it (data must stay in India; health data must be encrypted).
* It touches everything at once — you can't fix it inside one module.

**The test that makes it obvious:** *if we got this wrong, would we have to redesign, or just fix a file?* Redesign → it's an ASR.

---

## PART 6 — Writing a requirement properly (the 6-part scenario)

A requirement is useless until it's measurable. "Make it reliable" can't be tested. So the course uses a standard six-part format. It's really just **a short story with a number at the end**:

**Who or what causes it (Source) → what happens (Stimulus) → to which part (Artifact) → in what situation (Environment) → what the system does about it (Response) → and how you'd measure that (Response Measure).**

**Learn this one example sentence.** You can reuse it all exam by swapping the nouns:

> *"During a flash sale **(Environment)**, the payment database **(Artifact)** suffers a hardware failure **(Stimulus)** caused by the infrastructure **(Source)**. The system switches to a standby replica **(Response)** within 3 seconds, with zero transactions lost **(Response Measure)**."*

Whenever a question says *"give an example of a requirement"* or *"illustrate an ASR"* — write that, adapted. Label the six parts in brackets so the examiner can see them.

---

## PART 7 — The utility tree (ranking what matters)

This is just a **ranked shopping list of qualities**, drawn as a tree.

```text
Utility  ──┬── Performance ──┬── Checkout speed  →  "under 2 seconds"      (High, High)
           │                 └── Report speed    →  "under 10 seconds"     (Low, Low)
           │
           └── Availability ─┬── Server crash    →  "recover in 3 seconds" (High, High)
                             └── Backups         →  "nightly"              (Med, Low)
```

Four levels: **Utility** at the top (meaning "the system being good"), then the **quality attributes**, then **more specific versions** of each, then the actual **measurable scenarios** at the tips.

Each tip gets two ratings, High / Medium / Low:
* **How much the business cares.**
* **How hard or risky it is to build.**

**The tips rated (High, High) are your ASRs.** They're both important and dangerous, so you design for them first. Everything else waits.

This one tree is used everywhere: it feeds the design method (ADD), it's built during the review method (ATAM), and it even tells you **which tests to write first** — the (High, High) ones.

---

## PART 8 — The three methods (QAW, ADD, ATAM) — don't memorise these

Here is the important part: **these are just meetings.** If you understand what each meeting is trying to do, you can write out its steps from common sense. Nobody needs to memorise them.

### QAW — the meeting where you *collect* requirements
You've got stakeholders in a room and you want to leave with a list of measurable quality requirements.

What would that meeting obviously do?
> Explain why we're here → the business person explains the goals → the architect shows what exists so far → everyone agrees what matters → **everyone throws out ideas** → merge the duplicates → **vote** on what's most important → write the winners up properly.

That's the 8 steps. You just derived them. The core of it is the last four: **brainstorm, merge, vote, write up.**

### ADD — the method where you *design*
You have your ASRs, and now you must produce an actual design.

What would you obviously do?
> Check what the requirements are → pick which piece of the system you're designing right now → pick the few drivers that matter most for that piece → choose an approach (a pattern, some tactics) → decide what the parts are → decide how the parts talk to each other → check it meets the requirement.

Then **you repeat the whole thing** for the next piece, and the piece inside that. That repetition is the only distinctive thing about ADD — it's design applied over and over, at smaller and smaller scale.

### ATAM — the meeting where you *review* the design
The design exists on paper. You want to find problems before anyone writes code, because fixing a flaw now costs about **1% of fixing it after launch**.

What would that review obviously do?
> Explain how the review works → the business people say what they need → the architect presents the design → the reviewers note which patterns were used → everyone builds the utility tree and ranks it → **check the design against the top-ranked items** → then bring in a wider group of stakeholders, who add their own concerns and vote → **check the design again** against their list → present the findings.

That's the 9 steps. Notice it's the **same checking step done twice** — once with a small expert group, once with a wider group. If both agree, you're confident. If the wider group finds new problems, your design had a blind spot.

**What ATAM gives you at the end — this part IS worth knowing properly:**

| Output | What it means | Example |
| :--- | :--- | :--- |
| **Utility tree** | The ranked list of what matters | — |
| **Sensitivity point** | One decision that strongly affects **one** quality | "The size of the database connection pool controls our performance" |
| **Trade-off point** | One decision that affects **two or more** qualities **in opposite directions** | "Encrypting every message improves security but slows the system down" |
| **Risks / non-risks** | Decisions that look dangerous / decisions checked and found fine | "Running a single server with no backup is an availability risk" |

> **The one distinction examiners love:** sensitivity point = **one** thing moves. Trade-off point = **two** things move in **opposite** directions.

---

## PART 9 — Views, and Kruchten's 4+1

**Structure** is the real thing: the actual code, the actual running processes, the actual servers.
**A view** is a *drawing* of one slice of it, made for one audience.

Think of a building. One building, but the electrician gets the wiring plan and the plumber gets the pipe plan. Same building, different drawings, because they care about different things.

**Why not one diagram?** Because it's either cluttered and unreadable, or clean and missing half of what people need. So you draw four, for four different audiences:

| View | Answers | For whom | Drawn as |
| :--- | :--- | :--- | :--- |
| **Logical** | What does it **do**? | End users' concerns (functionality) | Class diagram |
| **Process** | How does it **run**? | Integrators, performance engineers | Sequence diagram |
| **Development** | How is it **built**? | Developers | Package diagram |
| **Physical** | Where does it **live**? | Infrastructure, DevOps | Deployment diagram |
| **+1 Scenarios** | Does it all **work together**? | Everyone | Use case diagram |

**Remember it as five questions:** *what it does · how it runs · how it's built · where it lives · proof it works.*

**Two things to say about the "+1":**
1. It adds **no new parts**. It just takes one important use case and traces it through the other four views to prove the design works.
2. It's **written first and used again last** — the use cases drive what goes into the four views, then you walk them back through to check.

**The classic exam question: "what role do quality attributes play in integrating the views?"**
Answer: one quality requirement forces a matching decision in **every** view. Take *"we must never lose a payment"*:
* **Logical** — design a Payment entity that can't be double-charged.
* **Process** — put payments on a queue handled by background workers.
* **Development** — package the payment code separately so it can't depend on the UI.
* **Physical** — run it in two zones with the database replicated.

So without quality attributes, you have four unrelated drawings. Quality attributes are what force the four drawings to agree. **That sentence is the answer.**

---

## PART 10 — Layers

Most enterprise systems are stacked: **Presentation → Business → Services → Data**. Each layer calls downwards only.

* **Strict layering:** a layer may only call the one directly below it. Very clean and easy to change — but you get the **sinkhole effect**, where a request passes through a middle layer that does nothing except forward it. Wasted time.
* **Relaxed layering:** a layer may call any layer below. Faster for simple read-only queries, but now everything is tangled together, and once skipping is allowed, developers skip everywhere.

**Sensible answer:** default to strict; relax it deliberately and *in writing* for a few speed-critical paths. An undocumented shortcut is decay. A documented one is a decision.

**Three techniques worth naming:**
* **Façade** — one simple door in front of a complicated set of subsystems. The client makes one call, the façade does the five calls behind it.
* **Session management** — HTTP forgets you between requests. Don't keep the session in one server's memory (that breaks scaling and dies with the server). Keep it in a shared cache like Redis, or in a signed token the client carries.
* **Aspect-oriented design** — logging, security and auditing are needed everywhere. Instead of copying that code into every module, pull it out into separate "aspects" applied automatically.

---

## PART 11 — Drift, erosion, conformance, reconstruction

**The story:** the architect writes rules. Developers under deadline pressure break them. Nobody writes it down. Over time the real system stops matching the design.

* **Drift** = the early, quiet stage. Small undocumented shortcuts.
* **Erosion** = the advanced stage. They're everywhere now, and the system becomes an unmaintainable "Big Ball of Mud".

**Typical examples:** a UI class running SQL directly instead of going through the data layer; skipping a layer to save time; calling three services directly instead of publishing one event; writing logs into a custom table instead of the standard logging framework.

**Four ways to stop it:**
1. **Make the architecture visible in the code** — name your packages `presentation`, `business`, `dataaccess`, so nobody can claim they didn't know.
2. **Use frameworks that enforce it** — if you use Spring MVC or Hibernate, the pattern is enforced by the tool, not by willpower.
3. **Give people templates** — a fixed skeleton to fill in, so the structure is already correct before they start.
4. **Keep the documents honest and train people** — update docs each release, and clearly mark outdated sections rather than leaving them to mislead people.

**Checking conformance two ways:**
* **Vertical** — are we crossing layers legally? (A UI class doing SQL is a vertical violation.)
* **Horizontal** — is everyone inside one layer doing things the same way? (One module using the standard logger and another rolling its own is a horizontal violation.)

**SAR — reconstruction.** When a system is 20 years old, has no documents, and the original team has left, you reverse-engineer the architecture from the code and from watching it run.

Four stages, and again it's just common sense: **pull the facts out of the code → store them somewhere you can query → group the thousands of tiny pieces into a few meaningful subsystems → check the result against the rules.**

The third stage is the hard one, because a tool can't know that fifteen classes together are "the billing subsystem" — a human expert has to say so.

> **The golden rule to quote:** *reconstruction is not designing and not modifying — it is discovering what already exists. Reconstruct before you modify.*

**The case study:** a system called **'Vanish'** was reconstructed using a tool called **ARMIN**. When it first drew every relationship, the result was an unreadable tangle called the **"white-noise view"**. Only after experts grouped things into subsystems did it become readable — and it revealed that the system **was not actually layered**, despite its design saying so.

---

## PART 12 — The trade-offs (this is where marks live)

Every trade-off answer has the same three parts: **what fights what → why → what you do about it.**

| The fight | Why it happens | What you do |
| :--- | :--- | :--- |
| **Accuracy vs speed** (usability) | Confirmation screens prevent mistakes but slow people down | Match the friction to the risk. One tap for a ₹100 payment, OTP and review screen for ₹100,000 |
| **Security vs performance** | Encryption costs CPU time and makes messages bigger | Cache the security handshake, do encryption at the edge, move auditing off the main path |
| **Security vs reliability** | On a bad network, bigger encrypted messages time out, retries pile up, and the system looks dead | Lighter encryption, session resumption, a simple separate heartbeat |
| **Security vs usability** | Long passwords and constant re-verification drive users away | Risk-based login: stay logged in while behaviour looks normal, ask for more only when something looks odd |
| **Flexibility vs speed** | Every layer you add for flexibility costs a hop | Keep layers where change is likely; skip them deliberately on speed-critical paths |
| **Scalability vs shipping now** | Microservices take a year; a monolith takes six weeks. Waiting costs you the market | Modular monolith — one deployable app with clean internal boundaries you can split later |
| **Stock availability vs cost** | Warehouses near customers mean fast delivery but expensive stock sitting around | Keep fast-selling items local; pool the slow-moving ones centrally |
| **3D printing vs mass production** | Printing makes complexity free but each unit stays expensive; moulds cost a fortune upfront but then each unit is pennies | Print when volume is low or every unit differs (custom implants, remote spare parts). Mould when volume is high |

---

## PART 13 — How to actually write the answers

**Every 3- or 4-mark answer, in this order:**

1. **Define it** — one or two lines, quoting the textbook where you can.
2. **Explain how it works** — the parts, the connections, the tactics.
3. **Give a real example** — e-commerce checkout, a payment app, Aadhaar, a hospital system. Never leave an answer abstract.
4. **State the trade-off** — always.

**The trade-off sentence. Memorise this shape and use it in every answer:**
> *"This improves ______ by ______, but it costs us ______ because ______, which we reduce by ______."*

That single sentence is the easiest mark in the paper, and most students forget it.

**Spotting what a question wants:**

| The question says | Give them |
| :--- | :--- |
| "trade-off", "competing", "compromise" | The fight → why → resolution |
| "structures", "externally visible properties" | The definition + what counts as architectural |
| "views", "perspectives", "Kruchten" | The 4+1 table, and **draw it** |
| "identify and prioritise requirements" | Utility tree + (High, High) |
| "give an example of a requirement/scenario" | The six-part sentence, labelled |
| "evaluate the architecture", "risks" | ATAM + its four outputs |
| "documentation" | It stops drift, it makes review possible, it links each decision to the requirement behind it |
| "legacy system", "no documentation" | SAR — and "reconstruct before you modify" |
| "maintainability" | Hide internals behind interfaces; low coupling, high cohesion |
| "scalability" | Stateless components, async connectors, many copies behind a load balancer |

---

## PART 14 — Things people mix up

| A | B | The difference in one line |
| :--- | :--- | :--- |
| Drift | Erosion | Drift is the early quiet stage; erosion is when it's everywhere |
| Sensitivity point | Trade-off point | One quality moves vs two qualities move in opposite directions |
| Structure | View | The real thing vs a drawing of one slice of it |
| MTBF | MTTR | How long before it breaks vs how long to recover |
| RPO | RTO | How much **data** you can lose vs how much **time** you can be down |
| Effectiveness | Efficiency | Did they get it right vs how much effort it took |
| Syntactic | Semantic | Same format vs same meaning |
| Strict layering | Relaxed layering | Only the next layer down vs any layer below |
| Vertical conformance | Horizontal conformance | Crossing layers legally vs being consistent within a layer |
| Functional requirement | Quality requirement | What it does vs how well it does it |

---

## PART 15 — In the exam

* **3 minutes per mark.** A 4-mark question gets 12 minutes. Not 25. Watch the clock.
* **Always name a real system.** Abstract answers lose marks even when they're correct.
* **Draw something** whenever views or utility trees come up. Rough is fine — they're marking the structure, not the art.
* **End every answer with the trade-off sentence.**
* **Name specific tactics** — caching, heartbeat, hot standby, dependency injection, façade, rate limiting. The professor said this is what separates a good answer from a full-mark one.

**If you completely blank on a question,** fall back to Part 1. Ask: *which quality is this about? what would you do to get it? what does that cost you?* Write those three things and you will get most of the marks.
