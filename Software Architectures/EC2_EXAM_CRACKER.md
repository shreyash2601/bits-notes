# BITS Pilani WILP — Software Architectures (SEZG651 / SSZG653)
# EC-2 Comprehensive Master Exam Textbook & Cracker

> 🎯 **Your Sole Examination Resource:** This textbook is designed as the single, self-contained reference you need to score top marks (**28–30 / 30**) in the **EC-2 (Mid-Term) Examination**. It combines and explains all 8 lectures (Lectures 1 to 8), presentation decks, transcripts of Prof. Harvinder S. Jabbal, Len Bass's *Software Architecture in Practice* (3rd/4th Edition), and provides complete model answers to past exam papers.

> 🔁 **Revising, not learning?** Once you have read this file through, switch to **`EC2_RAPID_REVISION.md`** in this folder — the whole course as one connected story, number hooks, confusion traps, and a 3-minute exam brain dump. Read that one repeatedly; read this one for depth.

---

## 📑 Master Table of Contents

* [Module 0: The Professor's Exam Blueprint & Answer Engineering Engine](#module-0-the-professors-exam-blueprint--answer-engineering-engine)
  * [1. Exam Format & The "3 Minutes per Mark" Time Budget](#1-exam-format--the-3-minutes-per-mark-time-budget)
  * [2. The 4-Part Architectural Answer Anatomy (Scoring Rubric)](#2-the-4-part-architectural-answer-anatomy-scoring-rubric)
  * [3. The Canonical Software Engineering Institute (SEI) 6-Part Quality Attribute Scenario Template](#3-the-canonical-sei-6-part-quality-attribute-scenario-template)
* [Module 1: Foundations of Software Architecture (Lecture 1)](#module-1-foundations-of-software-architecture-lecture-1)
  * [1. The Standard Textbook Definition by Bass, Clements, and Kazman](#1-the-canonical-bassclementskazman-definition)
  * [2. Architectural vs. Non-Architectural Decisions](#2-architectural-vs-non-architectural-decisions)
  * [3. Why Architecture Matters: The 13 Business & Technical Drivers](#3-why-architecture-matters-the-13-business--technical-drivers)
  * [4. Architectural Drift vs. Architectural Erosion](#4-architectural-drift-vs-architectural-erosion)
* [Module 2: The Quality Attribute Masterclass & Tactics (Lectures 2 & 3)](#module-2-the-quality-attribute-masterclass--tactics-lectures-2--3)
  * [1. Functional vs. Quality Attribute Requirements](#1-functional-vs-quality-attribute-requirements)
  * [2. Deep Dive into the "Big 7" Quality Attributes & SEI Tactics](#2-deep-dive-into-the-big-7-quality-attributes--software-engineering-institute-sei-tactics)
    * [Availability](#availability)
    * [Performance](#performance)
    * [Security](#security)
    * [Modifiability](#modifiability)
    * [Usability (ISO 9241-11: Effectiveness, Efficiency, Satisfaction)](#usability)
    * [Interoperability](#interoperability)
    * [Testability](#testability)
* [Module 3: Architecturally Significant Requirements (ASRs) & Elicitation (Lectures 4 & 5)](#module-3-architecturally-significant-requirements-asrs--elicitation-lectures-4--5)
  * [1. What is an ASR? The 5% Rule & The 4 Filters](#1-what-is-an-asr-the-5-rule--the-4-filters)
  * [2. Elicitation Frameworks: Quality Attribute Workshop (QAW - 8 Steps) & PALM](#2-elicitation-frameworks-qaw-8-steps--palm)
  * [3. The Utility Tree Masterclass (Notation, Structure & Prioritization)](#3-the-utility-tree-masterclass-notation-structure--prioritization)
  * [4. Attribute-Driven Design (ADD 3.0) – 7-Step Method](#4-attribute-driven-design-add-30--7-step-method)
* [Module 4: Software Structures, Views & Kruchten's 4+1 Model (Lecture 6)](#module-4-software-structures-views--kruchtens-41-model-lecture-6)
  * [1. Structures vs. Views (The Fundamental Law)](#1-structures-vs-views-the-fundamental-law)
  * [2. The 3 SEI Structure Families (Module, C&C, Allocation)](#2-the-3-software-engineering-institute-sei-structure-families)
  * [3. Philippe Kruchten's 4+1 View Model](#3-philippe-kruchtens-41-view-model)
  * [4. All Five Views Drawn for One System (E-Commerce Checkout)](#4-all-five-views-drawn-for-one-system-e-commerce-checkout)
  * [5. How Quality Attributes Integrate Kruchten's Views](#5-how-quality-attributes-integrate-kruchtens-views)
* [Module 5: Layered Architectures & Architecture Evaluation (ATAM) (Lecture 7)](#module-5-layered-architectures--architecture-evaluation-atam-lecture-7)
  * [1. The Layered Pattern: Strict vs. Relaxed Layering](#1-the-layered-pattern-strict-vs-relaxed-layering)
  * [2. Key Architectural Techniques Across the 4 Layers](#2-key-architectural-techniques-across-the-4-layers)
  * [3. Real-World Case Studies (Aadhaar, MakeMyTrip, Shipping Façade)](#3-real-world-case-studies-prof-jabbal-lecture-7)
  * [4. Architecture Tradeoff Analysis Method (ATAM)](#4-architecture-tradeoff-analysis-method-atam)
* [Module 6: Architectural Conformance & Software Architecture Reconstruction (SAR) (Lecture 8)](#module-6-architectural-conformance--software-architecture-reconstruction-sar-lecture-8)
  * [1. Conformance vs. Drift vs. Erosion](#1-conformance-vs-drift-vs-erosion)
  * [2. The 4 Core Techniques to Ensure Conformance](#2-the-4-core-techniques-to-ensure-conformance)
  * [3. Architecture and Testing Activities](#3-architecture-and-testing-activities)
  * [4. Software Architecture Reconstruction (SAR): the 4-Stage Pipeline](#4-software-architecture-reconstruction-sar-the-4-stage-pipeline)
  * [5. Case Study: The 'Vanish' System (ARMIN Tool)](#5-case-study-the-vanish-system-armin-tool)
  * [6. Vertical vs. Horizontal Conformance](#6-vertical-vs-horizontal-conformance)
  * [7. Automated Tooling and Real-World Violations](#7-automated-tooling-and-real-world-violations)
* [Module 7: The Master Architectural Trade-Off Playbook](#module-7-the-master-architectural-trade-off-playbook)
  * [1. Usability: Effectiveness vs. Efficiency vs. Satisfaction](#1-usability-effectiveness-vs-efficiency-vs-satisfaction)
  * [2. Security vs. Performance vs. Reliability](#2-security-vs-performance-vs-reliability)
  * [3. Security vs. Usability](#3-security-vs-usability)
  * [4. Modifiability vs. Performance (The Indirection Penalty)](#4-modifiability-vs-performance-the-indirection-penalty)
  * [5. Scalability vs. Development Speed (Opportunity Cost)](#5-scalability-vs-development-speed-opportunity-cost)
  * [6. General Systems Trade-Offs (Distribution Networks & Additive Manufacturing)](#6-general-systems-trade-offs-operations-management-context)
* [Module 8: Fully Solved Past EC-2 Exam Paper (Model Solutions)](#module-8-fully-solved-past-ec-2-exam-paper-model-solutions)
  * [Question 1: Architecture Definition, Scalability/Maintainability & ASRs (8 Marks)](#question-1-model-solution-8-marks)
  * [Question 2: Usability Triad, Cross-Cutting Qualities & Kruchten's 4+1 (8 Marks)](#question-2-model-solution-8-marks)
  * [Question 3: Documentation & The Utility Tree Notation (7 Marks)](#question-3-model-solution-7-marks)
  * [Question 4: Operations Trade-offs — Availability vs. Cost & Additive Manufacturing (7 Marks)](#question-4-model-solution-7-marks)
* [Module 9: High-Yield Flashcard Cheat Sheet & Glossary](#module-9-high-yield-flashcard-cheat-sheet--glossary)

---

## 📖 Quick Decoder for Engineers: Acronyms & Hard Words at a Glance
*(If you haven't attended lectures or get confused by academic short forms, use this quick reference table!)*

| Short Form / Term | Full Name | Plain English Meaning (For a 2–3 YOE Engineer) |
| :--- | :--- | :--- |
| **ASR** | **Architecturally Significant Requirement** | A critical requirement (usually non-functional) that strongly shapes how you design the whole system (e.g., "Must handle 100,000 users per second"). |
| **QA** | **Quality Attribute** | A non-functional property of a system—how fast, secure, available, or easy to change it is (not just business features). |
| **SEI** | **Software Engineering Institute** | A famous software research institute at Carnegie Mellon University that created industry-standard architecture methods like ATAM and ADD. |
| **ATAM** | **Architecture Tradeoff Analysis Method** | A structured 9-step team review to test and evaluate an architecture on paper before writing code, finding risks and trade-offs. |
| **QAW** | **Quality Attribute Workshop** | A kickoff meeting with stakeholders early in a project to brainstorm and write down all system quality requirements. |
| **ADD** | **Attribute-Driven Design** | A 7-step design method where you break down your system step-by-step based on your top quality attribute requirements. |
| **SAR** | **Software Architecture Reconstruction** | Reverse engineering an old or undocumented system from its code and runtime logs to see what the architecture actually looks like. |
| **C&C** | **Component-and-Connector** | Runtime view of architecture: *Components* are running processes/containers; *Connectors* are network calls, APIs, or queues connecting them. |
| **MTBF** | **Mean Time Between Failures** | How long a system runs on average before a crash happens (e.g., runs for 1,000 hours before failing). Higher is better. |
| **MTTR** | **Mean Time To Repair** | How fast your system or team can recover and get back online after a crash (e.g., recovers in 3 seconds). Lower is better. |
| **RPO** | **Recovery Point Objective** | Maximum acceptable data loss when disaster strikes (e.g., "RPO = 0" means zero lost database transactions). |
| **RTO** | **Recovery Time Objective** | Maximum acceptable downtime before the system must be working again (e.g., "RTO = 1 minute"). |
| **AOP / AOD** | **Aspect-Oriented Programming / Design** | Pulling out repetitive cross-cutting tasks (like logging, security checks, or transaction rollback) into separate modules called "aspects". |
| **ORM** | **Object-Relational Mapping** | Tools like Hibernate or Entity Framework that automatically turn database rows into code objects so you don't write raw SQL. |
| **DAO** | **Data Access Object** | A dedicated class or module that handles all SQL queries and database operations for a specific entity. |
| **MQ** | **Message Queue** | An asynchronous buffer (like Kafka, RabbitMQ, or AWS SQS) where services send messages to each other without blocking. |
| **PO** | **Product Owner** | In Agile/Scrum, the person responsible for defining business requirements, talking to stakeholders, and prioritizing the sprint backlog. |
| **SRE** | **Site Reliability Engineering** | Engineers whose primary job is keeping production servers, cloud infrastructure, and databases reliable, fast, and online. |
| **COTS** | **Commercial Off-The-Shelf** | Ready-made software or tools that you buy and integrate instead of building them yourself from scratch. |
| **SLA** | **Service Level Agreement** | The promised contract of uptime and response speed given to customers (e.g., "99.9% uptime and response time under 200ms"). |
| **ACID** | **Atomicity, Consistency, Isolation, Durability** | The 4 core database rules that guarantee transactions complete safely without corrupting data. |
| **AJAX** | **Asynchronous JavaScript and XML** | A browser technique to fetch data in the background and update parts of a webpage without doing a full page refresh. |
| **DOM** | **Document Object Model** | The tree structure of HTML elements inside browser memory that JavaScript reads and modifies. |
| **SQLi** | **SQL Injection** | A common cyberattack where an attacker types malicious SQL into an input box to steal or delete database tables. |
| **MFA** | **Multi-Factor Authentication** | Logging in using a password PLUS an extra security step like an SMS OTP or authenticator app. |
| **JWT** | **JSON Web Token** | A cryptographically signed digital security badge that proves who you are on every API request. |
| **TLS** | **Transport Layer Security** | The standard encryption protocol (HTTPS) that protects data as it travels across the internet. |
| **AES** | **Advanced Encryption Standard** | The industry-standard encryption algorithm used to lock up sensitive data at rest on disk. |
| **XSS** | **Cross-Site Scripting** | A security bug where an attacker injects malicious JavaScript into another user's browser. |
| **WCF** | **Windows Communication Foundation** | A Microsoft framework for building service-oriented applications and APIs. |
| **AUTOSAR** | **AUTomotive Open System Architecture** | The global standard architecture used for software inside car computer chips (ECUs). |
| **ECU** | **Electronic Control Unit** | The embedded computer chip inside modern vehicles controlling brakes, engines, or sensors. |
| **ARMIN** | **Architecture Reconstruction and Mining** | An SEI tool used to reverse-engineer software architectures from source code. |
| **DSM** | **Dependency Structure Matrix** | A square grid table showing which modules depend on which other modules to spot circular dependencies. |
| **Canonical** | *(Hard Word)* | Standard textbook / official definition or way of doing things. |
| **Invariants** | *(Hard Word)* | Strict rules that must never be broken in the software. |
| **Indirection Penalty** | *(Hard Word)* | Performance slowdown caused by adding extra middle layers (like Façades, proxies, or gateways). |
| **Pervasive** | *(Hard Word)* | Widespread throughout the entire codebase. |
| **Triad** | *(Hard Word)* | A group of three related items (e.g., the Usability Triad: Effectiveness, Efficiency, Satisfaction). |
| **Concurrency** | *(Hard Word)* | Handling multiple user requests or tasks at the exact same time. |

---

# Module 0: The Professor's Exam Blueprint & Answer Engineering Engine

### 1. Exam Format & The "3 Minutes per Mark" Time Budget
* **Nature of Exam:** **CLOSED BOOK**, Written/Online Examination.
* **Duration:** **90 Minutes** (1.5 Hours).
* **Total Marks:** **30 Marks**.
* **Marks Distribution:** Fairly distributed across all 8 lectures: **7 to 8 marks** from every set of contact sessions (CS 1–2, CS 3–4, CS 5–6, CS 7–8).
* **Question Paper Pattern (Prof. Harvinder S. Jabbal - Lecture 8 Update):**
  * Expect **3 to 4 major questions**, each broken into sub-parts (A, B, C).
  * Sub-parts may test disjointed or related syllabus topics across different course modules.
  * **Answering Mode:** Text answers can be typed directly into the exam portal. Diagrams can be sketched quickly on paper, scanned, and uploaded. Focus on architectural precision rather than artistic beauty.
  * **The Ultimate Scoring Differentiator:** Prof. Jabbal emphasized: *"Understand all the tactics that have been mentioned in the slides. Other things you will remember, but tactics are something you need to review and master."*
* **The Golden Time Formula (Prof. Harvinder S. Jabbal):**
  $$\text{Time per Mark} = \frac{90\text{ minutes}}{30\text{ marks}} = \mathbf{3\text{ minutes per mark}}$$
  * For a **2-mark question:** Allocate **6 minutes** (2 mins thinking/structuring, 4 mins writing).
  * For a **3-mark question:** Allocate **9 minutes** (3 mins thinking, 6 mins writing).
  * For a **4-mark question:** Allocate **12 minutes** (4 mins thinking, 8 mins writing).

> ⚠️ **Professor's Warning:** *"Teachers avoid asking trivial one-liner questions like 'What is architecture?'. They wrap foundational principles into scenario-based, trade-off questions. Read every single word of the question carefully before writing."*

---

### 2. The 4-Part Architectural Answer Anatomy (Scoring Rubric)
BITS Pilani evaluators look for architectural rigor. An informal, conversational paragraph will receive 40–50% marks. To guarantee **100% marks**, structure every 3-mark or 4-mark response using this exact 4-part anatomy:

```text
┌────────────────────────────────────────────────────────────────────────┐
│               THE 4-PART ARCHITECTURAL ANSWER ANATOMY                  │
├────────────────────────────────────────────────────────────────────────┤
│ 1. SEI Academic Anchor & Formal Definition                             │
│    Quote the standard textbook definition (Bass/Clements/Kazman or ISO).       │
│    Establish the structural elements and contracts.                    │
├────────────────────────────────────────────────────────────────────────┤
│ 2. Architectural Mechanism & Structural Dynamics                       │
│    Explain HOW it works technically (components, connectors, tactics). │
│    Describe data flows, decoupling points, or state boundaries.        │
├────────────────────────────────────────────────────────────────────────┤
│ 3. Concrete Real-World System Example                                  │
│    Ground the concept in a concrete engineering system (E-Commerce,    │
│    Aadhaar, FinTech Payment Gateway, or Healthcare).                   │
├────────────────────────────────────────────────────────────────────────┤
│ 4. Structured Trade-Off Matrix / Tensions                              │
│    State explicitly what improves, what degrades, and the architectural│
│    mitigation employed to balance the tension.                         │
└────────────────────────────────────────────────────────────────────────┘
```

---

### 3. The Canonical Software Engineering Institute (SEI) 6-Part Quality Attribute Scenario Template
When asked to provide a scenario, define a quality attribute requirement, or illustrate an ASR, use the **Software Engineering Institute (SEI) 6-Part Scenario Template**. Evaluators assign specific sub-marks to each element:

```text
┌────────────────────────────────────────────────────────────────────────┐
│                 SEI 6-PART QUALITY ATTRIBUTE SCENARIO                  │
├────────────────────┬───────────────────────────────────────────────────┤
│ 1. Source          │ Where the stimulus originates (e.g., end-user,    │
│                    │ internal process, malicious attacker, third-party)│
├────────────────────┼───────────────────────────────────────────────────┤
│ 2. Stimulus        │ The event arriving at the system (e.g., peak load,│
│                    │ server crash, unauthorized login attempt, API call│
├────────────────────┼───────────────────────────────────────────────────┤
│ 3. Artifact        │ The specific subsystem or component targeted      │
│                    │ (e.g., payment gateway, auth service, database)   │
├────────────────────┼───────────────────────────────────────────────────┤
│ 4. Environment     │ The system state under which the stimulus occurs  │
│                    │ (e.g., normal operation, peak hours, degraded mode│
├────────────────────┼───────────────────────────────────────────────────┤
│ 5. Response        │ What the architecture does when stimulus arrives  │
│                    │ (e.g., failover to replica, log error, rate limit)│
├────────────────────┼───────────────────────────────────────────────────┤
│ 6. Response Measure│ Quantifiable, testable metric of the response     │
│                    │ (e.g., recovery within 3 sec, 99.99% latency <50ms│
└────────────────────┴───────────────────────────────────────────────────┘
```

---

# Module 1: Foundations of Software Architecture (Lecture 1)

### 1. The Standard Textbook Definition by Bass, Clements, and Kazman
According to Len Bass, Paul Clements, and Rick Kazman (*Software Architecture in Practice*, Software Engineering Institute (SEI) Series in Software Engineering, Addison-Wesley):

> **Definition:** *"The software architecture of a system is the set of software structures needed to reason about the system, which comprise software elements, relations among them, and properties of both."*

#### Deconstructing the 4 Critical Clauses:
1. **"Set of Software Structures":** There is no single architecture diagram that captures a whole software system. Architecture is multidimensional. Reasoning about deployment requires a different structure (hardware topology) than reasoning about code maintenance (package hierarchy) or runtime throughput (process threads).
2. **"Software Elements":** The architectural building blocks—such as software modules, classes, microservices, databases, or runtime processes.
3. **"Relations Among Them":** How components connect and interact—via synchronous RPC, REST over HTTPS, asynchronous message brokers (Kafka/RabbitMQ), foreign keys, or operating system pipes.
4. **"Properties of Both" (Externally Visible Properties):** Architecture is concerned strictly with the **public contracts and externally visible characteristics** of components—such as their provided and required interfaces, throughput limits, response latency, authentication requirements, and failure modes. The private implementation details (e.g., whether an algorithm uses Bubble Sort or Quick Sort inside a private function) are **not** architectural unless they alter an externally visible quality attribute.

```text
       ┌────────────────────────────────────────────────────────┐
       │                 SOFTWARE ARCHITECTURE                  │
       ├─────────────────┬───────────────────┬──────────────────┤
       │ Elements        │ Relations         │ Externally       │
       │                 │ (Connectors)      │ Visible Props    │
       ├─────────────────┼───────────────────┼──────────────────┤
       │ Services,       │ REST, gRPC,       │ Latency SLA,     │
       │ DB Shards,      │ Kafka Topics,     │ Error Codes,     │
       │ Web Frontends   │ SQL Connections   │ Auth Contracts   │
       └─────────────────┴───────────────────┴──────────────────┘
```

---

### 2. Architectural vs. Non-Architectural Decisions

```text
┌─────────────────────────┬─────────────────────────┬─────────────────────────┐
│ Decision Characteristic │ Architectural Decision  │ Detailed Design Decision│
├─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Scope of Impact         │ System-wide; affects    │ Localized within a      │
│                         │ multiple subsystems.    │ single class or method. │
├─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Cost of Reversal        │ Extremely expensive;    │ Inexpensive; can be     │
│ (Cost of Change)        │ requires major data     │ refactored in a single  │
│                         │ migration or redesign.  │ sprint pull request.    │
├─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Externally Visible?     │ YES; impacts system-    │ NO; encapsulated        │
│                         │ wide quality attributes.│ within private bounds.  │
├─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Concrete Example        │ Choosing an Event-Driven│ Choosing whether to use │
│                         │ Publish-Subscribe model │ an ArrayList vs. a      │
│                         │ over Monolithic SQL.    │ LinkedList inside a svc.│
└─────────────────────────┴─────────────────────────┴─────────────────────────┘
```

---

### 3. Why Architecture Matters: The 13 Business & Technical Drivers

Architecture matters because every decision made while building a real system already demonstrates its value. The stages below follow the lifecycle of a single example — a food delivery app — with each stage illustrating one driver.

---

**1. Earliest and Most Expensive Decision to Change**
*Stage: Choosing the structure (microservices vs. monolith) on Day 1.*
This is the first major decision made, and the hardest one to reverse later. Early structural choices set constraints that persist for the life of the system.

**2. Defines Implementation Constraints**
*Stage: Setting rules such as "the Order Service cannot access the database directly."*
Architecture establishes which components are allowed to interact with which others, and how.

**3. Enables or Inhibits Quality Attributes**
*Stage: Realizing that speed and uptime depend on the chosen structure, not just the code.*
Performance, reliability, and security are shaped by the architecture itself — good code cannot compensate for a weak structural design.

**4. Enables Prediction of Problems Early**
*Stage: An architect reviews the design before any code is written and flags a potential bottleneck.*
Structural weaknesses can be identified and corrected at the design stage, before implementation begins.

**5. Prevents Costly Rework**
*Stage: Fixing an issue during design takes an hour; fixing it after launch takes a month.*
Flaws caught early are inexpensive to resolve. The same flaw discovered after deployment is far more costly.

**6. Enables Early Prototyping**
*Stage: Building a basic working skeleton — order, payment, and notification — to validate the approach.*
A minimal, functioning version of the system allows key risks to be tested before full-scale development.

**7. Supports Integration of Ready-Made Components**
*Stage: Integrating Google Maps instead of building a mapping feature from scratch.*
Clear interfaces make it possible to incorporate external libraries, APIs, or SaaS tools without disrupting the rest of the system.

**8. Shapes Organizational Structure (Conway's Law)**
*Stage: The team reorganizes into separate Order, Delivery, and Payment squads.*
System structure and team structure tend to mirror each other — a modular architecture often produces modular, focused teams.

**9. Serves as a Shared Language Across Stakeholders**
*Stage: Business leaders, designers, and engineers all reference the same architecture diagram in a meeting.*
Architecture provides a common reference point that technical and non-technical stakeholders can both understand.

**10. Serves as an Onboarding Tool**
*Stage: A new engineer understands the system in a day by studying the architecture rather than the full codebase.*
A clear architectural view accelerates the learning curve for new team members.

**11. Makes Reasoning About Change Manageable**
*Stage: A request to add a tipping feature only requires changes to the Payment module.*
Well-defined boundaries contain the impact of a change, making updates safer and faster to implement.

**12. Enables Reuse Across a Product Line**
*Stage: A second product, grocery delivery, reuses most of the existing architecture.*
A well-designed architecture can be shared across multiple related products, reducing duplicate effort.

**13. Manages Overall Complexity**
*Stage: The system scales to millions of users, and the team continues to reason about it in terms of services and layers rather than low-level infrastructure.*
Architecture abstracts away underlying complexity, keeping the system comprehensible as it grows.

**Summary sequence:**
Decide → Constrain → Assess quality → Predict issues → Reduce rework cost → Prototype → Integrate → Shape teams → Communicate → Onboard → Manage change → Reuse → Contain complexity.

---

### 4. Architectural Drift vs. Architectural Erosion

```text
       DOCUMENTED INTENDED ARCHITECTURE          ACTUAL CODEBASE REALITY
            ┌───────────────────┐                 ┌───────────────────┐
            │Presentation Layer │                 │Presentation Layer │
            └─────────┬─────────┘                 └─────────┬─────────┘
                      │                                     │ ──┐ (Illegal Backdoor)
            ┌─────────▼─────────┐                 ┌─────────▼───┴─────┐
            │  Business Layer   │                 │  Business Layer   │
            └─────────┬─────────┘                 └─────────┬─────────┘
                      │                                     │
            ┌─────────▼─────────┐                 ┌─────────▼─────────┐
            │   Database Layer  │                 │   Database Layer  │
            └───────────────────┘                 └───────────────────┘
                Clean Layers                         EROSION & DRIFT
```

**Architectural Erosion (Decay)**
Erosion occurs when developers violate the architecture's intended rules while writing code, often to meet a deadline or take a shortcut.

*Example:* The architecture specifies that only a dedicated data-access layer should query the database. Under time pressure, a developer writes a direct database query inside a UI component instead of going through that layer.

*Effect:* This introduces dependencies that were never intended, increases coupling between components, and gradually breaks down the system's modularity.

**Architectural Drift**
Drift occurs when the system continues to evolve through new features and bug fixes, but the architectural documentation and diagrams are never updated to reflect those changes.

*Example:* A diagram created at the start of a project shows three core services. Over time, the system grows to seven services, but the diagram is never revised.

*Effect:* The documentation no longer reflects how the system actually works, and decisions based on it may be based on outdated assumptions.

---

### Mitigations

1. **Automated Architecture Testing**
   Tools such as ArchUnit (Java) or NetArchTest (.NET) can be integrated into CI/CD pipelines to automatically check for unapproved dependencies between layers. If a violation is detected, the build fails, preventing the issue from reaching production.

2. **Scheduled Architecture Audits**
   Regular reviews — including peer reviews and structured evaluations such as the Architecture Tradeoff Analysis Method (ATAM) — compare the system as it actually runs against its documented design, allowing both code and documentation to be corrected when they diverge.

---

**Summary:**
Erosion is a violation of architectural rules within the code itself. Drift is a mismatch between the documentation and the system's actual state. Automated testing addresses erosion by catching rule violations early; scheduled audits address drift by keeping documentation aligned with reality.

---

# Module 2: The Quality Attribute Masterclass & Tactics (Lectures 2 & 3)

**Running example used throughout:** An e-commerce checkout system (the same one used in class scenarios) — users search products, add to cart, and pay. This example is used to explain each attribute below.

---

### 1. Functional vs. Quality Attribute Requirements

* **Functional Requirements** describe *what* the system does.
  Example: "Users can search products, add items to cart, and pay by card."

* **Quality Attribute Requirements (Non-Functional Requirements)** describe *how well* the system does it.
  Example: "Checkout must complete in under 1.5 seconds, support 15,000 users at once, stay available 99.99% of the time, and follow PCI-DSS security rules."

* **Key idea:** Almost any design can satisfy a functional requirement. It is the quality requirements (speed, security, reliability, etc.) that actually decide which architecture, patterns, and techniques you need.

---

### 2. Deep Dive into the "Big 7" Quality Attributes & Software Engineering Institute (SEI) Tactics

The seven attributes covered are: Availability, Performance, Security, Modifiability, Usability, Interoperability, and Testability.

---

### Availability

**What it means:** Whether the system is up and working when someone needs it.

**How it's measured:**
Availability = MTBF / (MTBF + MTTR)
- **MTBF** = average time the system runs before something breaks.
- **MTTR** = average time taken to detect, fix, and recover from that break.

**Common targets:** "Four nines" (99.99% uptime, about 53 minutes of downtime a year) and "Five nines" (99.999%, about 5 minutes a year).

**How systems stay available:**
1. **Detecting a failure**
   - *Ping/Echo:* A monitor pings a server; if there's no reply, it assumes the server is down.
   - *Heartbeat:* The server itself regularly announces "I'm alive"; if it stops, it's assumed to be down.
   - *Exception/Invariant checks:* The code checks its own data for consistency and catches errors before they spread.
2. **Recovering from a failure**
   - *Active (hot) standby:* A backup server is already running and processing the same requests, so it can take over instantly.
   - *Passive (warm) standby:* A backup gets periodic updates and can take over in a few seconds.
   - *Cold standby:* A backup is switched off and needs to boot up first, taking minutes.
   - *Checkpoint & rollback:* Save progress regularly to disk so the system can restart cleanly after a crash.
3. **Preventing a failure**
   - *Transactions (ACID):* If something goes wrong midway, the system rolls back instead of leaving bad data.
   - *Predictive maintenance:* Restarting servers before they run out of memory, based on observed trends.

**Example:** During a flash sale, the payment database server overheats and crashes. A heartbeat monitor notices within seconds, automatically switches traffic to a backup database, and no in-progress orders are lost.

---

### Performance

**What it means:** How quickly and how much the system can handle.

**Key measurements:** Latency (time per request), throughput (requests handled per second), jitter (how much latency varies).

**How systems improve performance:**
1. **Controlling demand**
   - *Rate limiting:* Capping how many requests a client can send per second.
   - *Sampling:* Dropping some non-critical data (like logs) when the system is overloaded.
   - *Limiting response size:* Showing 20 search results per page instead of returning 50,000 records at once.
2. **Managing resources better**
   - *Concurrency:* Using thread pools or event loops so one slow task doesn't block everything else.
   - *Caching:* Storing frequently used data in fast memory (like Redis) so the database isn't hit every time.
   - *Horizontal scaling:* Running multiple copies of the app behind a load balancer to share the traffic.

**Example:** On the day of a big sale, 50,000 users search for products at once. Because product data is cached and traffic is spread across multiple servers, most searches still respond in under 200 milliseconds.

---

### Security

**What it means:** Keeping the system safe from unauthorized access or misuse, while still working normally for legitimate users.

**The six things security must guarantee:**
- **Confidentiality:** Only the right people can see the data (encryption).
- **Integrity:** Data isn't secretly changed (checksums, signatures).
- **Availability:** The system stays usable even under attack (e.g., DDoS protection).
- **Authentication:** Confirming who someone is (passwords, MFA, OAuth).
- **Authorization:** Confirming what they're allowed to do (role-based permissions).
- **Non-repudiation:** Someone can't deny an action they actually performed (signed audit logs).

**How systems defend themselves:**
1. **Detect attacks:** Monitoring tools and logs that flag unusual activity.
2. **Resist attacks:** Strong login checks (MFA), permission checks (role-based access), encrypting data, and validating all inputs (to block attacks like SQL injection).
3. **React to attacks:** Automatically logging out suspicious sessions, blocking suspicious IP addresses, and alerting the team.
4. **Recover from attacks:** Restoring from clean backups and reviewing audit logs to understand what happened.

**Example:** An attacker floods the login page with traffic and tries SQL injection at the same time. A DDoS filter absorbs the traffic surge, and the login form rejects the malicious input because it's checked against a strict format before reaching the database.

---

### Modifiability

**What it means:** How easily the system can be changed or extended without breaking things.

**Core idea:** Keep related things together (**cohesion**) and reduce dependencies between unrelated things (**coupling**).

**How systems stay easy to modify:**
1. **Reducing dependencies between parts**
   - *Encapsulation:* Only expose what's necessary through a clean interface; hide the internal details.
   - *Using a middleman:* Instead of one part calling another directly, route it through something like a message queue, gateway, or facade.
   - *Restricting communication paths:* Enforce clear layers so components don't call each other in messy, circular ways.
2. **Delaying decisions until as late as possible**
   - *Config files:* Store settings like database URLs or feature toggles outside the code, so they can change without a redeploy.
   - *Dependency Injection:* Decide which specific implementation to use at runtime rather than hardcoding it.
   - *Plugins:* Let new modules be added while the system is running, without changing the core.

**Example:** The team needs to add a new local payment provider alongside Stripe and PayPal. Because payments are built behind a common interface, a developer just adds a new adapter for the new provider and switches it on via configuration — no other part of the system needs to change.

---

### Usability

**What it means (ISO 9241-11):** How well specified users can achieve their goals, with accuracy, speed, and satisfaction, in a given context.

**The three parts of usability:**
1. **Effectiveness — Did the user complete the task correctly?**
   Tactics: input validation, clear labels, confirmation prompts before risky actions.
2. **Efficiency — How much effort did it take?**
   Tactics: one-click checkout, fingerprint login instead of typing passwords, auto-filled OTPs.
3. **Satisfaction — Did it feel pleasant and trustworthy?**
   Tactics: loading indicators, smooth animations, friendly error messages.

**A common trade-off:** Adding safety steps (like confirmation screens) improves effectiveness but slows the user down. Making things faster (like one-tap payments) can lead to more mistakes.

**How this is balanced in practice:**
- *Risk-based friction:* Small, low-risk actions (like a $10 payment) get one-tap ease. Larger, riskier actions (like a $1,000 transfer) get extra confirmation steps.
- *Forgiving UI:* Let the action happen instantly, but show an "Undo" option for a few seconds afterward.

**Example:** A payment app lets you pay a small amount instantly with a fingerprint, but for a large transfer, it asks for an OTP and shows a summary screen before confirming — balancing speed with safety.

---

### Interoperability

**What it means:** How well two different systems can exchange information and work together.

**Two levels:**
1. **Syntactic:** Both systems agree on the format (e.g., both use JSON over HTTPS).
2. **Semantic:** Both systems understand the data the same way (e.g., both agree that "2024-01-05" means January 5th, and both use the same product category names).

**How systems achieve this:**
- *Service discovery:* Tools that help systems find each other automatically (e.g., Consul, Eureka).
- *Interface management:* Adapters, data converters, API gateways, or a shared messaging layer that translates between systems.

**Example:** The checkout system needs to talk to a third-party shipping provider. An adapter converts the shipping provider's data format into the format your system expects, so both sides can "speak the same language" without either one changing internally.

---

### Testability

**What it means:** How easily the system's faults can be found through testing.

**Common measurements:** Code coverage, how many bugs are found, how long tests take to run.

**How systems are made easier to test:**
- *Dependency Injection:* Swap in a fake/mock payment gateway during tests instead of calling the real one.
- *Exposing internal state:* Adding endpoints like `/health` or `/metrics` so tests (and monitoring tools) can check what's happening inside the system.

**Example:** Instead of testing checkout against the real payment provider (which costs money and is slow), the team injects a mock payment gateway during testing, so they can simulate both successful and failed payments instantly.

---

# Module 3: Architecturally Significant Requirements (ASRs) & Elicitation (Lectures 4 & 5)

**Running example used throughout:** The same e-commerce checkout system from Module 2 — used to show how a business need eventually becomes a concrete, testable requirement that shapes the architecture.

---

### 1. What is an ASR? The 5% Rule & The 4 Filters

**The 5% Rule:**
In a typical project backlog of 200 user stories, most of them are routine. For example: "user can view their profile photo" or "admin can filter orders by date." These are simple to build in a day and don't affect the overall system design.

Only a small fraction — roughly 5% — actually shape how the system is built. These are called **Architecturally Significant Requirements (ASRs)**.

**Definition:** An ASR is a requirement that:
- Has a major effect on the system's core structure,
- Takes real engineering effort to satisfy, and
- Would be very expensive to change once the system is built.

**Example:** "Users can add a delivery address" is routine — any reasonable design handles it. But "the system must process 50,000 checkout transactions per second with 99.99% uptime" is an ASR — it forces specific decisions about caching, database replication, and failover, all made upfront.

**The 4 Filters — How to Recognize an ASR:**

1. **High business value, high technical risk.**
   If this requirement fails, the business faces serious financial loss, legal penalties, or reputational damage.
   *Example: Zero tolerance for lost payment transactions.*

2. **Demanding, non-standard performance needs.**
   The requirement asks for scale, speed, or uptime beyond what a standard setup provides out of the box.
   *Example: 50,000 requests/second with 99th percentile latency under 50 milliseconds.*

3. **Legal or compliance obligations.**
   Regulations that dictate how or where the system must operate.
   *Example: RBI rules requiring Indian financial data to stay within India; HIPAA requiring encrypted health data.*

4. **Impact across multiple parts of the system.**
   The requirement cannot be handled inside a single module — it touches authentication, payments, database, and logging all at once.
   *Example: Being able to trace every action a user takes, end to end, for auditing purposes.*

---

### 2. Elicitation Frameworks: Quality Attribute Workshop (QAW – 8 Steps) & PALM

Stakeholders rarely state ASRs directly. They usually say things like "make it fast, secure, and easy to use." Architects use structured methods to turn these vague statements into specific, testable requirements.

**Pedigreed Attribute Logic Method (PALM)**
This method traces a **business goal** down to a specific **quality requirement**.

*Example:*
- Business goal: "Expand our payments platform into the European Union within 6 months."
- Resulting ASR: "The system must keep EU user data within EU servers, support user data deletion on request, and connect to local European banking systems."

**Quality Attribute Workshop (QAW) — The 8 Steps**
A structured workshop where architects and stakeholders work together to surface the real requirements.

1. **Introduction** — The facilitator explains the workshop's goals and process.
2. **Business context** — The project sponsor explains the business goals and background.
3. **Architecture overview** — The lead architect presents the current or proposed design.
4. **Identify drivers** — The group lists the key business goals and quality attributes involved.
5. **Brainstorm scenarios** — Everyone proposes specific situations the system must handle well.
6. **Consolidate scenarios** — Similar or overlapping scenarios are merged.
7. **Prioritize scenarios** — Stakeholders vote to identify which scenarios matter most.
8. **Refine scenarios** — The top scenarios are written up in a precise, standard format.

*Example:* In a QAW for the checkout system, stakeholders might brainstorm ideas like "the system should survive a server crash during a sale" and "checkout should never take more than 2 seconds." These get merged, voted on, and refined into precise, testable requirements.

---

### 3. The Utility Tree Masterclass (Notation, Structure & Prioritization)

The Utility Tree is a tool used to turn broad business goals into specific, ranked, testable requirements. It is used in both Attribute-Driven Design and the Architecture Tradeoff Analysis Method.

**The four levels of the tree:**

1. **Root — "Utility":** The overall success and health of the system.
2. **Quality Attributes:** Broad categories, such as Performance, Availability, or Security.
3. **Refinements:** More specific aspects of each attribute — for example, under Performance: *Latency* and *Throughput*; under Security: *Data Confidentiality* and *User Authentication*.
4. **Scenarios:** Concrete, measurable situations written in the standard six-part format (from Module 2).

**Example, using the checkout system:**

- Performance
  - Checkout latency during a flash sale → "P99 latency under 200ms" (High importance, High difficulty)
  - Log processing → "Process 1 million logs in 5 minutes" (Medium importance, Medium difficulty)
- Availability
  - Server crash recovery → "Failover in under 3 seconds" (High importance, High difficulty)
  - Data loss prevention → "Zero data loss on database failure" (High importance, Medium difficulty)
- Security
  - SQL injection defense → "100% of attempts blocked" (High importance, High difficulty)
  - Audit logging → "All logs cryptographically signed" (Medium importance, Low difficulty)

**Prioritizing the scenarios: Importance vs. Difficulty**

Each scenario is rated on two dimensions — how important it is to the business, and how difficult or risky it is to build:

| | Low/Medium Difficulty | High Difficulty |
|---|---|---|
| **High Importance** | High value, moderate risk — plan for this early | **Core architecture — top priority, shapes the whole design** |
| **Low Importance** | Low value, low risk — handle during normal development | High risk, low value — reconsider the approach or simplify |

**Rule of thumb:** Requirements rated **High importance, High difficulty** are addressed first. These become the main input for Attribute-Driven Design and the focus of Architecture Tradeoff Analysis Method reviews.

---

### 4. Attribute-Driven Design (ADD 3.0) – 7-Step Method

Attribute-Driven Design is a step-by-step method for turning ASRs into an actual architecture. It is applied repeatedly — first to the whole system, then to each major part of it.

1. **Confirm the requirements.** Gather the ASRs, constraints, and the Utility Tree built in step 3.
2. **Choose what to design next.** Start with the system as a whole; in later passes, pick a specific module or service to break down further.
3. **Identify the key drivers.** Focus on the top "High importance, High difficulty" scenarios from the Utility Tree.
4. **Choose design approaches.** Select the architectural patterns and tactics (from Module 2) that satisfy those drivers.
5. **Define the components.** Decide on the actual services or modules, and assign responsibilities to each.
6. **Define how components connect.** Specify the interfaces and relationships between components.
7. **Check the design against the requirements.** Verify it satisfies the ASRs, then repeat the process for the next level of detail.

**Example:** For the checkout system, Step 3 might identify "checkout latency under 200ms during flash sales" as the key driver. Step 4 selects caching and horizontal scaling as the approach. Step 5 defines a separate Checkout Service and Cache Layer. Step 6 defines how they communicate (e.g., via a message queue). Step 7 confirms the design meets the 200ms target, then the same process is repeated for the Cache Layer itself in the next design pass.

---

# Module 4: Software Structures, Views & Kruchten's 4+1 Model (Lecture 6)

**Running example used throughout:** the same e-commerce checkout system from Modules 2 and 3.

---

### 1. Structures vs. Views (The Fundamental Law)

* **Structure** = what actually exists. Real code files in Git, real processes running in server memory, real servers in a data centre. This is physical reality.
* **View** = a document or diagram showing *one slice* of that reality, drawn for *one audience* and the specific concerns they care about.

> **The Fundamental Law:** *Architects design structures; they document views.* You change a structure by editing and deploying code. You change a view by updating a diagram.

**Analogy:** A building has one physical structure. But the electrician gets a wiring blueprint, the plumber gets a piping blueprint, and the interior designer gets a furniture layout. Three different views, one building. Nobody hands the plumber the wiring diagram.

**Why views exist at all:** No single diagram can capture a whole system. The diagram that helps you reason about deployment ("which server runs what?") is useless for reasoning about code maintenance ("which package depends on what?"). So architecture is deliberately documented as *multiple* views.

---

### 2. The 3 Software Engineering Institute (SEI) Structure Families

Clements, Bass and colleagues (*Documenting Software Architectures: Views and Beyond*) group every possible structure into three families. Almost any exam question about "structures" expects these three.

| | **1. Module Family** | **2. Component & Connector (C&C) Family** | **3. Allocation Family** |
| :--- | :--- | :--- | :--- |
| **Question it answers** | How is the *code* organised? | What is *running*, and what is talking to what? | *Where* does it live, and *who* owns it? |
| **When it exists** | At rest — design and compile time (static) | Only while the system is running (dynamic) | At deployment, and in the organisation |
| **Elements** | Classes, packages, layers, modules | Processes, threads, services, databases, caches | Servers, VMs, disks, networks, engineering teams |
| **Relations** | "is-a", "uses", "is-part-of" | Calls over REST/gRPC, message queues, shared memory | "deployed on", "hosted at", "maintained by" |
| **Main quality attributes served** | Modifiability, Reusability | Performance, Scalability, Availability | Availability, Cost, Infrastructure Security |
| **Checkout example** | The `payment` package uses the `order` package | The Checkout Service publishes to a Kafka topic that the Payment Worker consumes | The Payment Worker runs on 3 AWS instances across 2 zones, owned by the Payments team |

**Memory hook:** **Code** (Module) → **Running** (C&C) → **Placed** (Allocation).

---

### 3. Philippe Kruchten's 4+1 View Model

> 💡 **Critical exam concept — directly asked in EC-2 Question 2(c).**

**The problem it solves.** If you try to describe a whole system in one diagram, exactly one of two things happens: either you cram everything in and it becomes an unreadable mess, or you keep it clean and it fails to answer half the stakeholders' questions. Philippe Kruchten's answer (1995, IEEE Software) is to stop trying. Describe the system as **multiple, concurrent views** — four views, each one answering the concerns of one specific group — and then use **scenarios** (the "+1") to prove the four views describe the same system.

**A useful line to open an answer with:** *architecture is the high-level, abstract, logical design; detailed design is the low-level, concrete, physical one.* The 4+1 model is a way of documenting the former.

```text
                        KRUCHTEN'S 4+1 VIEW MODEL
                     ┌─────────────────────────────┐
                     │        LOGICAL VIEW         │
                     │   "WHAT the system does"    │
                     │   Serves: end users         │
                     └──────────────┬──────────────┘
                                    │
    ┌───────────────────────────┐   │   ┌───────────────────────────┐
    │     DEVELOPMENT VIEW      │   │   │       PROCESS VIEW        │
    │  "HOW IT IS BUILT"        │───┼───│  "HOW IT RUNS"            │
    │  Serves: developers       │   │   │  Serves: integrators/SRE  │
    └───────────────────────────┘   │   └───────────────────────────┘
                                    │
                           ┌────────┴────────┐
                           │  +1 SCENARIOS   │
                           │ "PROOF IT WORKS"│
                           └────────┬────────┘
                                    │
                     ┌──────────────┴──────────────┐
                     │       PHYSICAL VIEW         │
                     │     "WHERE IT LIVES"        │
                     │  Serves: infra / DevOps     │
                     └─────────────────────────────┘
```

| View | Question it answers | Whose concerns it serves (Kruchten's stakeholder) | What is inside it | Usual diagrams | Quality attributes it tests |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Logical** | What does the system *do*? | **End users**, product managers — reviewed with business analysts and domain experts | Classes, their attributes and operations, domain objects, interfaces | **Class** or **component** diagrams | Functionality, Data integrity, Reusable domain abstractions |
| **Process** | How does it *run*? | System integrators, performance engineers, SREs | Processes, threads, queues, schedulers | **Sequence** or **activity** diagrams | Performance, Availability, Concurrency, Fault tolerance |
| **Development** | How is it *built*? | Developers, development and release managers | Source files, packages, JAR/npm libraries, layers | **Component** or **package** diagrams | Modifiability, Portability, Reusability |
| **Physical (Deployment)** | Where does it *live*? | System administrators, DevOps and infrastructure engineers | Servers, VMs, Kubernetes pods, load balancers, network links | **Deployment** diagrams | Availability, Disaster recovery, Security |
| **+1 Scenarios** | Does it all actually *work together*? | Everyone (this is the binding element) | Key use cases and quality attribute scenarios | **Use case** diagrams and walkthroughs | Validates all of the above |

> ⚠️ **Read that third column carefully — it is the most misread part of the 4+1 model.**
> It lists **whose concerns the view exists to answer**, *not* who literally opens the diagram. Kruchten's own 1995 table pairs the Logical view with the stakeholder *"end-user"* and the concern *"functionality"* — meaning the logical view is the one that answers the end user's question *"what does this system actually do for me?"*
> * The **diagram itself** is drawn by designers and developers, in UML.
> * At the **conceptual level** — boxes named `Customer`, `Order`, `Payment` with lines between them — a business analyst or domain expert genuinely does review it, and will catch domain errors such as *"an order can have more than one delivery address"*.
> * At the **detailed design level** — methods, visibility, data types — it is for developers only. No end user ever reads this.
>
> **In the exam:** if asked *"which stakeholder does the Logical view serve?"*, answer **end users, whose concern is functionality** — that is Kruchten's own answer. Then add the one-line nuance: *"the view captures end-user functional concerns, expressed in designer notation."* That sentence shows you understand the model rather than having memorised a table.

**Detail on each view:**

1. **Logical View — the "what".** The functional picture, described from the end user's point of view. It shows the system's classes, their attributes and operations, and the relationships between them. For checkout, it defines entities such as `Cart`, `Order` and `Payment`, and the rules connecting them ("an Order must have at least one line item"). It says nothing about servers or threads.
2. **Process View — the "how it runs".** Everything that only exists while the system is running: how many processes and threads, what runs in parallel, what waits for what, how processes talk to each other. This is the view that addresses the non-functional runtime concerns — **performance, availability, concurrency and fault tolerance**. Drawn as sequence diagrams (which show the *order* of interactions — note that a sequence diagram shows ordering, not duration) or activity diagrams (which show how components collaborate to carry out one use case).
3. **Development View — the "how it is built".** The developer's world: which package depends on which, which third-party libraries are allowed, how the build is organised, what compiles into which artifact. The guiding principle is that **each component has one clear responsibility in the system**. This is where you enforce a rule such as "the payment package must not import UI code".
4. **Physical / Deployment View — the "where it lives".** Maps the software onto real hardware: which service runs on which machine, in which region, behind which firewall and load balancer, with which database replicas. A deployment diagram models the physical hardware elements **and the communication paths between them**.
5. **The "+1" Scenarios — the "glue".** This view adds **no new building blocks**. It takes an important use case (or a 6-part quality attribute scenario) and traces it end-to-end through the other four views, to *illustrate and validate* the requirements. If a scenario cannot be traced cleanly, one of the four views is wrong.

> 🔑 **The point most people miss: scenarios are written FIRST, and used again LAST.**
> The "+1" is numbered last but built first. You begin with the important use cases, and they drive what goes into the other four views. When the four views are drawn, you come back and walk the same scenarios through them to check the design actually works. So scenarios are both the **input** that shapes the architecture and the **test** that validates it — which is exactly why they are drawn in the middle of the diagram, touching all four.
>
> *(Small limitation worth knowing: a use case diagram shows which actors do what, but it does not show the order in which the steps happen — that is what the sequence diagram in the Process view is for.)*

**The 6 UML diagrams you need.** UML has 14 diagram types; the 4+1 model only really uses six of them, so memorise this mapping:

| View | Diagram |
| :--- | :--- |
| Logical | Class, Component |
| Process | Sequence, Activity |
| Development | Component, Package |
| Physical | Deployment |
| Scenarios (+1) | Use case |

**Why the model works (three reasons you can quote):**
1. Putting ideas on paper before coding catches structural mistakes while they are still cheap to fix.
2. A picture communicates faster than pages of prose documentation.
3. Modelling is easier when you draw one perspective at a time instead of trying to express everything at once.

**Other models exist** — C4, TOGAF, 5+2, SysML, ArchiMate, and various architecture description languages — but 4+1 remains the default because it is good enough and simple enough for most systems. *(Worth one sentence in an exam answer to show breadth; do not spend more than that on it.)*

**Memory hook (one sentence):** *What it does (Logical) → how it runs (Process) → how it is built (Development) → where it lives (Physical) → proof it works (Scenarios).*

---

### 4. All Five Views Drawn for One System (E-Commerce Checkout)

One system, five diagrams. Read them in order and you are watching the same checkout described from five different angles. **Draw these in the exam** — a labelled diagram earns marks that a paragraph does not.

---

#### View 1 — LOGICAL: UML Class Diagram
*What the system does, in domain terms. Audience: end users' functional concerns.*

```text
                      ┌───────────────────────┐
                      │       Customer        │
                      ├───────────────────────┤
                      │ -customerId : UUID    │
                      │ -name       : String  │
                      ├───────────────────────┤
                      │ +login()              │
                      │ +viewOrderHistory()   │
                      └───┬───────────────┬───┘
                        1 │               │ 1
                     owns │               │ places
                     0..1 │               │ 0..*
        ┌─────────────────▼─────┐   ┌─────▼─────────────────┐
        │         Cart          │   │        Order          │
        ├───────────────────────┤   ├───────────────────────┤
        │ -cartId : UUID        │   │ -orderId  : UUID      │
        │ -total  : Money       │   │ -status   : Status    │
        ├───────────────────────┤   │ -placedAt : DateTime  │
        │ +addItem()            │   ├───────────────────────┤
        │ +removeItem()         │   │ +confirm()            │
        │ +checkout()           │──►│ +cancel()             │
        └───────────┬───────────┘   └───────────┬───────────┘
     contains 1..*  │                 paid by 1 │
        ┌───────────▼───────────┐   ┌───────────▼───────────┐
        │       CartItem        │   │        Payment        │
        ├───────────────────────┤   ├───────────────────────┤
        │ -quantity  : int      │   │ -paymentId : UUID     │
        │ -unitPrice : Money    │   │ -amount    : Money    │
        ├───────────────────────┤   │ -method    : Method   │
        │ +lineTotal()          │   │ -state : PENDING /    │
        └───────────┬───────────┘   │          PROCESSED    │
    refers to *..1  │               ├───────────────────────┤
                    │               │ +authorize()          │
                    │               │ +capture()            │
        ┌───────────▼───────────┐   └───────────────────────┘
        │        Product        │
        ├───────────────────────┤
        │ -sku   : String       │
        │ -name  : String       │
        │ -price : Money        │
        ├───────────────────────┤
        │ +isInStock()          │
        └───────────────────────┘
```

*Reading it:* a Customer owns one Cart and places many Orders. A Cart contains many CartItems, each pointing at a Product. `checkout()` creates an Order, which has exactly one Payment. **No servers, no threads, no packages appear here** — that is the whole point of this view.

---

#### View 2 — PROCESS: UML Sequence Diagram
*How it runs at runtime. Audience: integrators, performance engineers, SREs.*

```text
Customer       Checkout Svc        Order Queue      Payment Worker      Payment GW
    │                │                  │                 │                   │
    ├─checkout()────►│                  │                 │                   │
    │                ├──┐ reserve stock │                 │                   │
    │                │◄─┘ (self-call)   │                 │                   │
    │                ├──publish(Order)─►│                 │                   │
    ◄──202 Accepted──┤                  │                 │                   │
    │  "order received, payment pending"│                 │                   │
    │                │                  ├──consume event─►│                   │
    │                │                  │                 ├───charge card────►│
    │                │                  │                 │◄────approved──────┤
    ◄──payment confirmed (push notification)──────────────┤                   │
    │                │                  │                 │                   │
```

*Reading it:* the customer is answered in under 200 ms (`202 Accepted`) **before** the card is charged; the actual charge happens asynchronously in a background worker. That single decision is what lets the system absorb a flash sale — and it is only visible in this view.

> Remember: a sequence diagram shows the **order** of interactions, not how long each one takes.

**Optional companion — UML Activity Diagram** (same view, shows concurrency and decisions):

```text
                    ( start )
                        │
                 [ Validate cart ]
                        │
              ══════ FORK ══════
                 │            │
        [ Reserve stock ]  [ Fraud check ]        ← run in parallel
                 │            │
              ══════ JOIN ══════
                        │
                 < payment OK? > ──── no ───► [ Release stock ] ──► ( end )
                        │ yes
                [ Confirm order ]
                        │
                     ( end )
```

---

#### View 3 — DEVELOPMENT: UML Package / Component Diagram
*How the code is organised. Audience: developers, build and release managers.*

```text
┌────────────────────────────────────────────────────────────┐
│ «package» com.shop.presentation          →  web-ui.jar     │
│  CheckoutController · CartController · ProductController   │
└───────────────────────────┬────────────────────────────────┘
                            │ «uses»
┌───────────────────────────▼────────────────────────────────┐
│ «package» com.shop.business              →  business.jar   │
│  CheckoutFacade · OrderService · PaymentService            │
└───────────────────────────┬────────────────────────────────┘
                            │ «uses»
┌───────────────────────────▼────────────────────────────────┐
│ «package» com.shop.dataaccess            →  data.jar       │
│  OrderDAO · ProductDAO · PaymentDAO                        │
└───────────────────────────┬────────────────────────────────┘
                            │ «uses»
┌───────────────────────────▼────────────────────────────────┐
│ «external» Hibernate · Kafka client · Redis client         │
└────────────────────────────────────────────────────────────┘

   ✗ FORBIDDEN:  presentation ──► dataaccess
                 (layer skip — the build fails if a developer writes this)
```

*Reading it:* dependencies point **downward only**. The forbidden arrow is the architecture rule made visible — this is exactly the drift from Module 6, caught here by design.

---

#### View 4 — PHYSICAL: UML Deployment Diagram
*Where it runs. Audience: system administrators, DevOps, infrastructure.*

```text
                        ┌────────────────────┐
                        │ «device» Browser   │
                        │        / Mobile    │
                        └─────────┬──────────┘
                                  │ HTTPS
                        ┌─────────▼──────────┐
                        │ «device» CDN + WAF │
                        └─────────┬──────────┘
                                  │
                        ┌─────────▼──────────┐
                        │ «device»           │
                        │ Load Balancer      │
                        └──┬────────────┬────┘
              ZONE A       │            │          ZONE B
        ┌──────────────────▼─┐        ┌─▼──────────────────┐
        │ «node» App Server 1│        │ «node» App Server 2│
        │  web-ui.jar        │        │  web-ui.jar        │
        │  business.jar      │        │  business.jar      │
        └────┬───────────┬───┘        └───┬───────────┬────┘
             │           │                │           │
             │      ┌────▼────────────────▼────┐      │
             │      │ «node» Redis             │      │
             │      │ cache + session store    │      │
             │      └──────────────────────────┘      │
             │                                        │
        ┌────▼────────────────────────────────────────▼────┐
        │ «node» Kafka cluster   (topic: order-placed)     │
        └───────────────────────┬──────────────────────────┘
                                │
                   ┌────────────▼────────────┐        ┌──────────────────┐
                   │ «node» Payment Worker   ├─HTTPS─►│ «external»       │
                   └────────────┬────────────┘        │ Payment Gateway  │
                                │                     └──────────────────┘
   ┌────────────────────────────▼───┐              ┌────────────────────────────┐
   │ «node» PostgreSQL PRIMARY      │◄────sync────►│ «node» PostgreSQL STANDBY  │
   │  Zone A                        │  replication │  Zone B                    │
   └────────────────────────────────┘              └────────────────────────────┘
```

*Reading it:* every box is a machine and every line is a network link. Two zones, a hot standby database and synchronous replication are what deliver the availability requirement — a concern completely invisible in the other three views.

---

#### View 5 — THE "+1" SCENARIOS: UML Use Case Diagram
*Drawn FIRST, used again LAST. Audience: everyone.*

```text
                 ┌───────── E-COMMERCE CHECKOUT SYSTEM ─────────┐
                 │                                              │
    O            │    (  Browse catalogue  )                    │
   /|\  ─────────┼───► (  Manage cart      )                    │
   / \           │                                              │
 Customer ───────┼───► ( Place order & pay )                    │
                 │            │            │                    │
                 │  «include» │            │ «include»          │
                 │            ▼            ▼                    │            O
                 │   ( Reserve stock )  ( Authorise payment )───┼──────────►/|\
                 │                                              │           / \
   Customer ─────┼───► (  Track order status  )                 │         Payment
                 │                                              │         Gateway
                 └──────────────────────────────────────────────┘        (external)
```

**Then the scenario is walked through all four views to validate the design:**

```text
  SCENARIO: "Customer places an order during a flash sale — payment must never be lost"

   LOGICAL  ──► Order + Payment entities created, Payment state = PENDING
      │
   PROCESS  ──► Checkout Svc publishes to queue, replies 202 in <200 ms
      │
   DEVELOP  ──► business.jar handles it; presentation.jar never touches the DB
      │
   PHYSICAL ──► Kafka + Payment Worker in Zone A, DB replicated to Zone B
      │
      ▼
   ✓ VALIDATED — the payment survives an app-server crash and a zone outage
```

> ✍️ **If you draw only one thing in the exam, draw this last trace.** It is the direct answer to *"how do scenarios integrate the four views?"* — and it leads straight into the next section.

---

### 5. How Quality Attributes Integrate Kruchten's Views

A frequent exam question: *What role do quality attributes play in integrating Kruchten's views?*

**The short answer:** A quality attribute requirement cannot be satisfied inside a single view. It forces a matching decision in *every* view, so quality attributes are the thread that stitches four separate diagrams into one coherent system.

**Worked example — the requirement "no payment may ever be lost, even at peak load":**

* **Logical View:** Define a `PaymentOrder` entity that is *idempotent* (processing the same payment twice has no extra effect), with clear states: `PENDING → PROCESSED`.
* **Process View:** Payments are handled by a separate pool of background workers reading from a durable message queue (e.g. Kafka), so a traffic spike queues up instead of crashing the server.
* **Development View:** `PaymentService` is packaged as its own separately built artifact and is forbidden from depending on UI classes — so it can be changed or redeployed on its own.
* **Physical View:** The payment service is deployed across multiple availability zones, with the database replicated across zones so a zone outage does not lose data.
* **+1 Scenario:** Traces the whole path — *customer taps Pay → a PaymentOrder entity is created (Logical) → the event is queued (Process) → the payment worker artifact consumes it (Development) → the replicated database stores it (Physical)* — and confirms that no step can silently lose the payment.

**Exam-ready closing line:** *Without quality attributes, the four views are four unrelated drawings. Quality attributes impose the constraints that force the four views to agree, turning them into one architecture.*

---

# Module 5: Layered Architectures & Architecture Evaluation (ATAM) (Lecture 7)

---

### 1. The Layered Pattern: Strict vs. Relaxed Layering

The layered pattern is the most widely used pattern in enterprise software. The system is stacked into layers, and a layer is only allowed to call *downwards*, never upwards.

```text
            STRICT LAYERING                       RELAXED (OPEN) LAYERING
        ┌─────────────────────┐                   ┌─────────────────────┐
        │ Presentation Layer  │                   │ Presentation Layer  │
        └──────────┬──────────┘                   └──────────┬──────────┘
                   │ only the next layer down                │ may skip to any layer below
        ┌──────────▼──────────┐                   ┌──────────▼──────────┐
        │   Business Layer    │                   │   Business Layer    │
        └──────────┬──────────┘                   └──────────┬──────────┘
                   │                                         │
        ┌──────────▼──────────┐                   ┌──────────▼──────────┐
        │   Services Layer    │                   │   Services Layer    │
        └──────────┬──────────┘                   └──────────┬──────────┘
                   │                                         │
        ┌──────────▼──────────┐                   ┌──────────▼──────────┐
        │     Data Layer      │                   │     Data Layer      │◄── direct read
        └─────────────────────┘                   └─────────────────────┘    allowed
```

**Strict layering — a layer may call only the layer immediately below it.**
* *Advantage:* Maximum modifiability and loose coupling. You can replace an entire layer and only its immediate neighbour notices.
* *Disadvantage:* **The sinkhole effect** — a request passes through a middle layer that adds nothing at all and simply forwards the call. That extra hop costs time and CPU for zero benefit.

**Relaxed (open) layering — a layer may call any layer below it.**
* *Advantage:* Faster. A simple read-only report can go straight from the UI to the data layer instead of writing pass-through code in two intermediate layers.
* *Disadvantage:* Tighter coupling, broken encapsulation, and an easy slide into architectural erosion — once skipping is allowed, developers skip everywhere.

**Practical rule for the exam:** default to strict layering; relax it *deliberately and in writing* for specific latency-critical read paths. An undocumented shortcut is erosion; a documented, justified shortcut is an architectural decision.

---

### 2. Key Architectural Techniques Across the 4 Layers

| Layer | Techniques used there | Why they are used |
| :--- | :--- | :--- |
| **Presentation** | Caching static assets (images, CSS, JS); AJAX partial page updates; client-side validation and input masking | Make the screen feel fast, and stop bad input before it ever reaches the server |
| **Business** | Application façade; session management; workflow and rules engines; aspect-oriented design | Hide complexity, remember user state, and keep frequently changing business rules out of hard-coded logic |
| **Services** | API façades for external partners; idempotency keys; sequence numbering; dead-letter queues; circuit breakers | Talk safely to the outside world, where calls get retried, duplicated, reordered, or simply fail |
| **Data** | Database connection pooling; read replicas and caching; Object-Relational Mapping (ORM); parameterised SQL queries; ACID transactions | Protect the database from overload, from injection attacks, and from half-finished writes |

**Quick meanings of the less obvious ones:**
* **Connection pooling:** Opening a database connection is slow, so keep a pool of ready-made connections and lend them out instead of creating a new one per request.
* **Workflow / rules engine:** Business rules (discount policies, approval chains) live in a configurable engine instead of in code, so they can be changed without a redeployment.
* **Idempotency key:** A unique ID sent with a request so that if the client retries after a timeout, the server recognises the duplicate and does not charge the customer twice.
* **Sequence numbers:** Numbering messages so the receiver can restore the correct order (or detect a missing one) when the network delivers them out of order.
* **Dead-letter queue:** A side queue where messages that repeatedly fail to process are parked, so one bad message does not block the whole queue.
* **Circuit breaker:** After a downstream service fails repeatedly, stop calling it for a while and fail fast — this prevents one slow service from freezing every thread in your system.
* **Parameterised queries:** Sending SQL with placeholders instead of pasting user text into the query string. This is the standard defence against SQL injection.

#### The three techniques worth knowing in depth

**Application Façade**
* *What it is:* One simple entry point that hides a complicated set of subsystems behind it.
* *Example:* The client makes a single call, `FlightBookingFacade.bookFlight(details)`. Behind that call, the façade coordinates the schedule service, the seat inventory service, the pricing engine, and the loyalty points service.
* *Benefit:* The client does not need to know the internal call order, and internal services can be rearranged without breaking any client.
* *Cost:* One extra hop (a small indirection penalty), and the façade itself can become a bottleneck if it grows too large.

**Session Management**
* *The problem:* HTTP is stateless — the server forgets you between requests — but applications need to remember who you are across many requests.
* *The naive approach:* Keep session data in the memory of one server. This breaks horizontal scaling, because the user must then always be routed back to that same server ("sticky sessions"), and everything is lost if that server dies.
* *The architectural approach:* Either store session state in a fast shared cache such as Redis that every server can read, or store it on the client inside a cryptographically signed token (JWT) that any server can verify. Both let you add or remove servers freely.

**Aspect-Oriented Design (AOD) / Aspect-Oriented Programming (AOP)**
* *The problem:* Logging, security checks, auditing, and transaction handling are needed in *every* module. Copying that code everywhere clutters the business logic and guarantees that someone will eventually forget it.
* *The technique:* Pull each of those concerns out into a separate module called an **aspect**, which is then applied automatically wherever it is needed. These are called **cross-cutting concerns** because they cut across all the functional layers.
* *Benefit:* No duplicated boilerplate, and auditing and logging are applied consistently because it is no longer up to each developer to remember.

---

### 3. Real-World Case Studies (Prof. Jabbal, Lecture 7)

**Case 1 — Aadhaar citizen registration dropdowns**
* *Problem:* The registration page has linked dropdowns for State → District → Town. Loading every Indian administrative region at once makes the page painfully slow.
* *Solution:*
  1. *Presentation layer:* Use **AJAX** cascading loads. The page loads instantly with only the list of States; picking a State then fetches only that State's districts in the background.
  2. *Business / Data layer:* Keep the state and district lists in an **in-memory cache** (e.g. Redis) on the server, since geographic boundaries almost never change.
* *Why it works:* It attacks the same latency problem from two layers at once — fetch less data per request, and never re-query the database for data that never changes.

**Case 2 — MakeMyTrip hotel reservation integration**
* *Problem:* External travel aggregators (MakeMyTrip, Booking.com) must be able to check room availability and book rooms — without ever seeing the hotel's internal database structure.
* *Solution:* Build a dedicated **Services Layer** exposing a stable contract:
  * `getRoomAvailability(fromDate, toDate, roomType) → available count`
  * `reserveRoom(guestDetails, roomType, dates) → reservation confirmation`
  * Protected with **idempotency keys** (so a network timeout and retry cannot create two bookings) and **rate limiting** (so one aggregator cannot swamp the system).
* *Why it works:* The internal database schema can be redesigned freely as long as the published API contract stays the same.

**Case 3 — Logistics shipping façade**
* *Problem:* Booking one container shipment actually requires three separate legacy systems: find the nearest empty container, find an available trucking transporter, and reserve cargo space on an ocean-going ship.
* *Solution:* In the **Business Layer**, build a **Shipping Logistics Façade**. The client makes one call — `requestContainerShipment(origin, destination, date)` — and the façade coordinates all three legacy modules behind the scenes.
* *Why it works:* The customer-facing application stays simple, and any of the three legacy systems can later be replaced without the client noticing.

---

### 4. Architecture Tradeoff Analysis Method (ATAM)

ATAM is the SEI's standard method for **evaluating an architecture on paper, before it is built** (Bass, Clements & Kazman, Ch. 21).

#### Why evaluate at all?

1. **Fail early, fail cheap.** Fixing a structural defect during design costs roughly **1%** of what the same defect costs once the system is live in production.
2. **Trade-offs must be made consciously.** You cannot maximise every quality attribute at once. ATAM forces architects *and* business stakeholders into the same room to decide, on the record, which attribute wins when two of them collide.

#### The 4 phases

| Phase | Who is involved | What happens |
| :--- | :--- | :--- |
| **Phase 0 — Preparation** | Evaluation team leadership | Logistics, agreement on scope, forming the team |
| **Phase 1 — Core evaluation** | Evaluation team + architect + key decision makers | Steps 1–6: present, catalogue, build the utility tree, analyse |
| **Phase 2 — Wider evaluation** | Plus the broader stakeholder community | Steps 7–9: brainstorm, re-analyse, report |
| **Phase 3 — Follow-up** | Evaluation team | Final written report and action plan |

#### The 4 roles

1. **Team Leader** — handles logistics, scheduling, contracts, and assembling the team.
2. **Evaluation Leader** — runs the sessions, facilitates scenario generation, and keeps discussion on track.
3. **Scenario Scribe** — writes every brainstormed scenario down visibly, word for word.
4. **Proceedings Scribe** — records the deeper reasoning, the issues raised, and the decisions taken.

#### The 9 steps

**Phase 1 — core team:**
1. **Present the ATAM.** The evaluation leader explains the process, the roles, and what outputs to expect.
2. **Present business drivers.** The project manager or client explains the business goals and what "success" means.
3. **Present the architecture.** The lead architect walks through the design, the patterns used, and the views.
4. **Identify architectural approaches.** The team catalogues which patterns and tactics have actually been used (layering, replication, caching, and so on).
5. **Generate the quality attribute utility tree.** Build the tree from Module 3, and rate every scenario High / Medium / Low on business importance and on technical difficulty.
6. **Analyse architectural approaches.** Take the top-rated scenarios and check, one at a time, whether the architecture really delivers them. Risks, sensitivity points, and trade-off points start appearing here.

**Phase 2 — wider stakeholder group:**
7. **Brainstorm and prioritise scenarios.** A much larger stakeholder group proposes real operating scenarios and votes on them. This surfaces concerns the core team never thought of.
8. **Analyse architectural approaches (again).** Repeat step 6, this time against the newly prioritised scenarios from step 7.
9. **Present results.** Report the risks, non-risks, sensitivity points and trade-off points back to all stakeholders.

> **Why steps 6 and 8 look identical:** they are the same activity done twice — first against the architect's own utility tree with a small expert group (step 6), then against the wider community's voted scenarios (step 8). If the two agree, confidence is high. If step 8 raises new risks, the architecture has a blind spot.

#### The 4 core outputs

1. **Utility Tree** — the prioritised catalogue of quality attribute requirements.
2. **Sensitivity Point** — one decision or parameter that strongly controls **one** quality attribute.
   *Example: "The database connection pool size is a sensitivity point for performance."*
3. **Trade-off Point** — one decision that affects **two or more** quality attributes in **opposite** directions.
   *Example: "Encrypting every message payload is a trade-off point: security improves, performance degrades."*
4. **Risks and Non-Risks**
   * *Risk:* a decision likely to cause trouble. *Example: "Running single-threaded Node processes without clustering is an availability risk."*
   * *Non-Risk:* a decision that was examined and found to be sound and well justified.

> ✍️ **Exam tip:** The most common ATAM mistake is confusing the two "points". **Sensitivity = one attribute moves. Trade-off = two attributes move in opposite directions.** Every trade-off point is also a sensitivity point, but not the other way round.

---
# Module 6: Architectural Conformance & Software Architecture Reconstruction (SAR) (Lecture 8)

---

### 1. Conformance vs. Drift vs. Erosion

* **Architectural Conformance** — the healthy state. The code actually obeys the rules, layer boundaries, and patterns the architect specified.
* **Architectural Drift** — the code has quietly moved away from the intended architecture through small, undocumented, ad-hoc changes made during sprints and maintenance. Nobody decided this; it just happened.
* **Architectural Erosion** — the advanced stage. Those violations have accumulated everywhere, unmanaged, until the structure has genuinely broken down and the system becomes a "Big Ball of Mud" that nobody can safely change.

> **Reconciling the two framings used in the course:** Lecture 1 described **erosion** as *code breaking the architecture's rules* and **drift** as *documentation falling out of step with reality*. Lecture 8 describes **drift** as *small unintended divergences* and **erosion** as *the widespread decay they accumulate into*. Both are consistent if you remember the sequence: **drift is the early, quiet stage; erosion is the advanced, damaging stage.** In an exam answer, define both, then state that drift left unchecked becomes erosion.

**Four everyday examples of drift (from Prof. Jabbal's Contact Session 8):**

1. **Violating layer discipline.** An object in Layer 1 calls an object in Layer 3 directly, skipping Layer 2, because it delivers the feature faster.
2. **Bypassing the data access layer.** A developer writes raw inline SQL inside a UI controller or a business service instead of going through the designated Data Access Objects (DAOs) or ORM entities.
3. **Point-to-point messaging bypass.** A module notifies three other modules with ad-hoc direct HTTP calls, instead of publishing one event to the company's designated publish-subscribe message broker.
4. **Ad-hoc logging.** A developer writes errors into a custom database log table inside a catch block, instead of routing them through the standard enterprise logging framework (e.g. Log4j).

**Why each one hurts:** every example creates a dependency nobody documented, so the next person who changes that area has no way to predict what will break.

---

### 2. The 4 Core Techniques to Ensure Conformance

| Technique | What it means | Concrete examples |
| :--- | :--- | :--- |
| **1. Architecturally evident coding style** | Make the architecture *visible in the code itself* — in package names, file names, class names and interfaces — so a developer cannot miss which architectural role a class plays | Layered system: packages named `com.app.presentation`, `com.app.business`, `com.app.dataaccess`. Publish-subscribe: classes explicitly named or marked as `Publisher` / `Subscriber`. Message queues: clearly separate `Producer` (inserts) from `Consumer` (pulls) |
| **2. Standardised frameworks** | Use a framework that *enforces* the pattern, so the rule is obeyed by construction rather than by discipline | Spring MVC forces the Model / View / Controller split. Hibernate (ORM) maps objects to tables and discourages raw SQL. AUTOSAR standardises automotive ECU software. JMS (publish-subscribe), Drools (rules engine), Log4j (logging) |
| **3. Code templates** | Give developers a fixed skeleton they must fill in, so the structural part of the pattern is already correct before they write a line of business logic | A fault-tolerant primary/backup template: the Primary handles the event and pushes state to the Backup; the Backup applies the state update and handles switchover. Developers only fill in the event-handling body |
| **4. Documentation and organisational discipline** | Keep the written architecture trustworthy and keep people trained on it | Re-sync the architecture documents at every release. Apply the **"No Longer Applicable" rule** — clearly mark outdated sections rather than deleting or ignoring them, so readers keep trusting the rest of the document. Brief every new hire on the architecture on day one. Enforce folder structure and architecture-aware code reviews |

**The underlying idea:** techniques 1–3 make the *right* thing the *easy* thing, so drift never starts. Technique 4 catches what still slips through.

---

### 3. Architecture and Testing Activities

Architecture directly drives how a system is tested.

1. **Prioritising test cases — via the Utility Tree.**
   *Exam question: which architectural work product tells you which tests matter most?* **The Utility Tree.** Scenarios rated **(High business importance, High architectural difficulty)** become the highest-priority automated test suites, because those are exactly the ones where failure is both likely and expensive.
2. **Building the integration test plan — via the "uses" relations.**
   The architecture already records which modules call which others. That dependency map *is* the list of integration points, so it tells you precisely which interfaces, call paths, and boundary values need integration tests.
3. **Designing the architecture so it can be tested at all.** Three architectural capabilities to name in an answer:
   * **Data source switching:** the ability to point the system at a test dataset instead of the live production database, without changing business code.
   * **State rollback:** the ability to undo whatever a test changed, so the system returns to a clean state for the next test run.
   * **Component replaceability (test simulators):** pluggable adapter interfaces, so external systems (payment gateways, hardware sensors, government services such as Aadhaar) can be swapped for mock simulators during automated testing.

---

### 4. Software Architecture Reconstruction (SAR): the 4-Stage Pipeline

**Definition:** Reconstruction is reverse-engineering. You analyse an existing system's artifacts — source code, executables, runtime traces, build scripts — to extract and document the architecture it *actually* has.

> ⚠️ **The golden rule:** *Reconstruction is not designing a new architecture, and it is not modifying one. It is discovering what already exists. You must reconstruct before you modify — do not put your hand in the pan without knowing what is cooking inside.*

**Why it is done — the four purposes:**
1. **Documenting undocumented systems.** Systems that have been running for 10–25 years, where the documents are lost and the original authors have left.
2. **Legacy migration.** Safely planning a move — mainframe to web, or monolith to microservices — which is impossible if you do not know the current structure.
3. **Identifying reusable components.** Spotting shared enterprise services (logging, authentication, session management) buried inside the old system.
4. **Conformance checking.** Comparing the reconstructed *as-built* architecture against the *as-designed* specification, to find exactly where the code has violated the design.

**The 4 stages:**

| Stage | What happens | Output |
| :--- | :--- | :--- |
| **1. Raw view extraction** | Mine low-level facts automatically from source code, binaries and execution traces: classes, files, imports, who-calls-whom, database tables, global data | A huge pile of raw, low-level facts |
| **2. Database construction** | Load all those entities and relationships into a structured repository or graph database so they can be queried | A queryable fact base |
| **3. View fusion and abstraction** | Combine different kinds of evidence and then group low-level elements into meaningful high-level subsystems: **(a) static view** from source code and build scripts, **(b) dynamic view** from runtime traces and call graphs, **(c) expert guidance** from domain experts who say which classes belong together | Readable, high-level architectural views |
| **4. Architecture analysis** | Check the reconstructed views against the intended structural rules — layer skipping, unauthorised database calls, test libraries shipped into production — then iterate if the result is still unclear | A list of real, evidence-backed violations |

**Why stage 3 is the hard one:** stages 1 and 2 are fully automatic, but a machine cannot know that fifteen classes together form "the Billing subsystem". That judgement needs a human domain expert — which is exactly what the case study below demonstrates.

---

### 5. Case Study: The 'Vanish' System (ARMIN Tool)

* **Context:** An SEI investigation reconstructing the architecture of a complex production system code-named **'Vanish'**.
* **Tool:** **ARMIN** — Architecture Reconstruction and Mining.
* **The "white-noise view":** When ARMIN first extracted *every* raw element and relationship and drew them, the result was a completely unreadable tangle of lines. This is the classic failure mode of automatic extraction — technically complete, humanly useless.
* **The aggregation step:** Engineers sat with domain experts and technical leads to agree on grouping rules, and rolled the low-level classes up into a small number of high-level subsystems. Only then did the picture become readable.
* **The finding:** The reconstructed views showed that **'Vanish' was not strictly layered at all.** There were hidden, illegal cross-layer calls — proof of drift from the original intended architecture.
* **The lesson for the exam:** raw extraction alone produces noise; *abstraction guided by human expertise* is what turns extraction into architecture.

---

### 6. Vertical vs. Horizontal Conformance

| | **Vertical Conformance** | **Horizontal Conformance** |
| :--- | :--- | :--- |
| **Scope** | Across layers, top to bottom | Within a single layer |
| **Question it asks** | "Is anyone skipping or bypassing a layer?" | "Is everyone inside this layer following the same conventions?" |
| **Focus** | Layer boundary compliance | Uniform use of standards and shared utilities |
| **Typical violation** | A UI controller executing SQL directly against the database | One module logs via Log4j while another writes its own custom SQL log table |
| **Typical tooling** | Structure101, Sonargraph (SonarJ) | SonarQube, Checkstyle, static linters |

**One-line memory hook:** *Vertical = are we crossing layers legally? Horizontal = are we consistent within a layer?*

---

### 7. Automated Tooling and Real-World Violations

**The main tools:**
* **SonarQube** — explores code paths, lets you define layers and slices, and automatically flags rule violations inside the CI/CD pipeline so a bad build fails before merge.
* **Structure101 and Sonargraph (SonarJ)** — package dependency analysers that detect circular dependencies and enforce strict layering rules (invariants).
* **ARMIN and Dali** — SEI workbenches for extracting relationships, querying them, and fusing views (used in the 'Vanish' study).
* **DiscoTect** — a *dynamic* monitoring tool that captures which components actually talk to each other while the system is running, catching things static analysis cannot see.

**Two classic real violations from the slides:**
1. *"No part of the application should depend on JUnit."* Caught by SonarQube when test harness code is accidentally packaged into the production binary.
2. *"All database access must go through entity beans."* Caught by DiscoTect and SonarQube when rogue direct JDBC connections bypass the entity beans at runtime.

**Modern angle — AI in reconstruction:** Large language models (such as Claude / Claude Code) are now used to rapidly read unfamiliar codebases and extract architectural facts — message broker topics, active/passive failover strategies, service discovery topology — that would previously have taken weeks of manual reading. This is a fast path through stages 1 and 3 of the SAR pipeline, though the expert validation in stage 4 still matters.

---

# Module 7: The Master Architectural Trade-Off Playbook

Exam questions repeatedly ask you to explain an architectural tension. Every answer follows the same shape:
**what pulls against what → why it happens mechanically → how an architect resolves it.** Memorise the six below.

---

### 1. Usability: Effectiveness vs. Efficiency vs. Satisfaction

* **The tension:** Maximum *effectiveness* (no user errors) demands defensive design — wizards, confirmation screens, CAPTCHAs, two-step verification. All of that is friction, which destroys *efficiency*. Pushing *efficiency* to the extreme (one-tap purchase) causes accidental actions, which destroys *satisfaction*.
* **Resolution — context-aware adaptive workflows.** Match the friction to the risk. Low-value, routine actions get the fast path. High-value or destructive actions get deliberate confirmation friction, plus a clear undo.
* **One-line answer:** *Effectiveness buys accuracy with the user's time; efficiency buys speed with the user's risk. Resolve it by making the amount of friction a function of the transaction's risk.*

---

### 2. Security vs. Performance vs. Reliability

* **The tension, step by step:**
  1. Strengthening **security** — mutual TLS handshakes, payload encryption and decryption, deep packet inspection, token verification — costs CPU and makes every message bigger.
  2. That directly degrades **performance**: higher latency, lower throughput.
  3. On a poor network, those bigger payloads and slower handshakes cause timeouts, which cause retries, which cause retry storms — and now **reliability** collapses too.
* **Resolution:** Cache cryptographic session keys instead of re-negotiating; terminate TLS at the API gateway edge using hardware acceleration; move security auditing off the request path and make it asynchronous.

```text
       SECURITY TACTIC                  PERFORMANCE IMPACT             RELIABILITY IMPACT
  ┌───────────────────────┐            ┌───────────────────┐          ┌───────────────────┐
  │ Strong Encryption     │ ─────────> │ Increased Latency │ ───────> │ Connection        │
  │ (TLS 1.3 + AES-256)   │            │ & CPU Overhead    │          │ Timeouts under    │
  └───────────────────────┘            └───────────────────┘          │ Network Jitter    │
                                                                      └───────────────────┘
```

---

### 3. Security vs. Usability

* **The tension:** Sixteen-character passwords, biometric re-verification every five minutes, and aggressive session timeouts maximise security — and drive users away.
* **Resolution — risk-based authentication.** Continuously check context: IP geolocation, device fingerprint, typical behaviour. While the context looks normal, keep the user logged in with a long-lived session (high usability). Only demand step-up multi-factor authentication when something looks anomalous, such as a login from a new country.
* **The key idea:** security effort is applied *per situation*, not uniformly to everyone all the time.

---

### 4. Modifiability vs. Performance (the indirection penalty)

* **The tension:** Modifiability comes from layers, interfaces, wrappers and intermediaries — Presentation → Façade → Business → ORM → Database. Every one of those boundaries costs a function call, an object mapping, and often a serialisation step. That is the **indirection penalty**: each layer you add for flexibility slows the request down.
* **Resolution:** Keep the layered structure for the parts that change often, but use relaxed layering on a small number of documented, latency-critical read paths; and push slow, non-urgent work onto an asynchronous event bus so the user is not waiting for it.
* **One-line answer:** *Indirection buys changeability with latency. Pay it where change is likely; skip it, deliberately and in writing, where latency is critical.*

---

### 5. Scalability vs. Development Speed (Opportunity Cost)

* **The tension:** A fully decoupled microservices architecture with Kafka, Kubernetes and multi-region databases will scale for years — but takes roughly 12 months and heavy infrastructure spend. A simple monolith ships in 6 weeks.
* **Opportunity cost:** Those extra months are not just cost, they are lost market entry, lost user feedback, and lost early revenue — spent engineering for scale the product does not yet have and may never need.
* **Resolution — the modular monolith.** Build one deployable application, but enforce strict module boundaries inside it. It ships fast now, and because the boundaries are already clean, individual modules can be split out into services later when real scale demands it.

---

### 6. General Systems Trade-Offs (Operations Management Context)

These appear in the exam as non-software questions, but the reasoning is identical.

**Product availability vs. inventory cost (distribution networks)**
* *High availability:* Hold buffer stock in many regional warehouses close to customers. Orders ship immediately, but capital is locked up in stock, and you pay warehouse rent, insurance, handling and obsolescence.
* *Low cost:* Lean, just-in-time, centralised inventory. Holding costs collapse, but lead times grow and any supply shock causes stockouts and lost sales.

**Additive manufacturing (3D printing) vs. traditional mass production**
* *Additive manufacturing:* Almost no setup or tooling cost, and **complexity is effectively free** — an intricate lattice costs the same to print as a plain block of the same volume. But material is expensive, printing is slow, and the per-unit cost stays roughly flat no matter how many you make.
* *Traditional tooling (injection moulding, CNC):* Huge upfront cost for moulds and tooling, but after that the marginal cost per unit falls to almost nothing and production is very fast. Complexity, however, raises tooling cost steeply.
* *The crossover rule:* additive wins at low volume and high complexity; traditional wins at high volume and stable, simple geometry.

---
# Module 8: Fully Solved Past EC-2 Exam Paper (Model Solutions)

Complete model answers for the **2025–2026 SEM 2 EC-2 Mid-Term Examination**. Each answer follows the 4-part anatomy from Module 0: **definition → mechanism → concrete example → trade-off.**

---

### Question 1: Model Solution (8 Marks)

#### Part A [4 Marks]: Architecture Definition, Scalability & Maintainability

> **Question:** *How does the concept of software architecture as a structure or set of structures comprising software components, their externally visible properties, and relationships among them, impact the maintainability and scalability of a computer-based system? Provide an example of a system where a well-designed software architecture improves its overall performance and adaptability.*

**Model Answer:**

**1. The definition, and what it commits you to.**
Bass, Clements and Kazman define software architecture as *the set of structures needed to reason about the system, comprising software elements, the relations among them, and the properties of both*. The important consequence is that architecture is about **boundaries and contracts between elements**, not about implementation details inside them.

**2. Impact on maintainability.**
* *Mechanism:* Maintainability depends on being able to change one part without a ripple effect through the rest. In this definition, each component hides its internals and exposes only its **externally visible properties** — its published interface and behaviour.
* *Structural effect:* Because dependencies are allowed only through those declared interfaces, and because modules are designed with high cohesion and low coupling, a developer can rewrite the internal algorithm of a component without touching, retesting or recompiling anything that depends on it.

**3. Impact on scalability.**
* *Mechanism:* Scalability is the ability to absorb more load by adding more resources.
* *Structural effect:* If the relations between elements are **loosely coupled and asynchronous** (message queues, REST calls) and if statelessness is declared as an externally visible property of a component, then many identical copies of that component can run behind a load balancer. This is **horizontal scaling**, and it is only possible because the architecture removed shared mutable state from the component contract.

**4. Concrete example — a large e-commerce platform (Amazon / Shopify style).**
* *Context:* Massive seasonal traffic surges, such as Black Friday.
* *Performance:* The `Order Placement` component is separated from the `Payment` and `Inventory` components by an asynchronous message queue (the connector). During a spike of 100,000 orders per minute, the front end accepts the order, writes it to the queue, and replies in under 200 ms. Worker components then drain the queue at whatever rate they can sustain, and scale out horizontally when the backlog grows. The spike is absorbed instead of crashing the system.
* *Adaptability:* Adding a new payment provider such as Apple Pay changes only the `Payment` module. Because the externally visible contract between `Order Service` and `Payment Service` is unchanged, the catalogue, cart and inventory services need no modification at all.

**5. The trade-off to state explicitly.** The asynchronous queue buys throughput and fault tolerance, but costs immediate consistency — the customer is told "order received", not "payment confirmed". The architecture compensates with order status tracking and idempotent retries.

---

#### Part B [4 Marks]: ASRs, Quality Attributes & System Structure Impact

> **Question:** *How do Architecturally Significant Requirements (ASRs) influence the design of a software system's architecture, and what role do quality attributes play in identifying and prioritizing ASRs, providing an example of a scenario where ASRs impact the overall system structure?*

**Model Answer:**

**1. How ASRs influence the design.**
An Architecturally Significant Requirement is one with a deep shaping effect on the system's high-level structures. Ordinary functional requirements — add a button, produce a report — are absorbed inside existing modules and change nothing structurally. ASRs are different: they dictate the choice of architectural pattern, how modules are partitioned, the deployment topology, and even the hardware needed. Roughly 5% of requirements are ASRs, and they consume most of the architectural effort.

**2. The role of quality attributes.**
* *Identification:* Functional requirements say *what* the system does; quality attributes — availability, performance, security, modifiability — say *how well*. Quality attributes are therefore the filter used to pull the architecturally significant requirements out of a large, mostly routine backlog.
* *Prioritisation via the Utility Tree:* Quality attributes give two ranking axes — **business importance** and **technical difficulty / risk**. Scenarios rated **(High, High)** become the primary ASRs and are addressed in the first design iterations, because they are both valuable and dangerous to get wrong.

**3. Concrete scenario and its structural impact — a core banking payment system.**
* *Functional requirement:* "The system shall transfer money between accounts." On its own this is not architectural — almost any design satisfies it.
* *The derived ASR:* "During peak hours, if the primary database server suffers a catastrophic hardware failure, the system must fail over to a standby replica within 3 seconds with zero transaction loss (RPO = 0, RTO < 3 s)."
* *Impact on the overall structure:*
  1. **Database topology:** rules out a single database instance; forces an active-passive hot standby across availability zones with synchronous write replication (synchronous, because RPO = 0 forbids losing even one committed transaction).
  2. **Connectors:** requires a database connection proxy (for example AWS RDS Proxy) so that failover does not drop client connections that are mid-transaction.
  3. **Business layer:** forces a distributed consistency mechanism — two-phase commit or the Saga pattern — so that a transfer spanning two ledgers can never be left half-applied.

**4. The trade-off to state explicitly.** Synchronous replication guarantees zero data loss but adds write latency on every single transaction, and the hot standby doubles infrastructure cost. The bank accepts both because the cost of a lost payment is regulatory, not just financial.

---

### Question 2: Model Solution (8 Marks)

#### Part A [2 Marks]: Usability Trade-Offs in Mobile Applications

> **Question:** *What are the key trade-offs between effectiveness, efficiency, and satisfaction in usability design, and how can designers balance these competing factors to create an optimal user experience in a mobile application?*

**Model Answer:**

**1. The trade-offs.**
* *Effectiveness vs. efficiency:* Effectiveness means the user completes the task correctly, which pushes towards validation steps, confirmation dialogs and review screens. Efficiency means completing the task with minimum time and taps, which pushes towards one-tap shortcuts. Every confirmation screen you add raises effectiveness and lowers efficiency.
* *Efficiency vs. satisfaction:* An interface tuned purely for speed — dense data tables, hidden shortcuts — overwhelms casual users and lowers satisfaction. But an interface tuned purely for comfort, with slow animations and heavy hand-holding, frustrates experienced users who want speed.

**2. How to balance them in a mobile app (mobile banking / UPI).**
* **Risk-tiered workflows:**
  * Low-risk action (paying a merchant under $10): prioritise **efficiency** — one biometric tap, instant dispatch.
  * High-risk action (transferring over $10,000 to a new beneficiary): deliberately add friction to protect **effectiveness** — re-enter the account number, show a full review screen, require an OTP.
* **Forgiving UI (undo):** Execute instantly for speed and satisfaction, but show a prominent 5-second "Undo" bar so an accidental tap is recoverable. This recovers effectiveness without paying the efficiency cost up front.

---

#### Part B [2 Marks]: Security, Communication & Reliability — Intersection and Compromise

> **Question:** *How do the Security, Communication, and Reliability views of quality attributes intersect and impact the design of a software system, and provide an example of a scenario where optimizing one view may compromise another.*

**Model Answer:**

**1. What each one governs, and where they meet.**
* **Security** governs confidentiality, integrity and authenticity of the data.
* **Communication** governs bandwidth, protocol overhead, payload size and latency between distributed nodes.
* **Reliability** governs the system's ability to keep operating correctly under adverse conditions.
They intersect because **every security measure is paid for in the communication channel**, and a saturated or unstable channel is precisely what breaks reliability.

**2. Conflict scenario — a connected vehicle fleet.**
* *The system:* Vehicles stream real-time telemetry and collision alerts to a central traffic controller.
* *Optimising security:* The architect mandates end-to-end payload encryption with RSA-4096 and mutual TLS, with frequent handshake re-negotiation to prevent spoofing.
* *The resulting compromise:*
  * The large certificate chain and handshake sharply increase packet size and CPU time per message (**communication degraded**).
  * When a vehicle passes through a weak-signal area, the heavy handshake repeatedly times out and retries.
  * The channel fills with retry traffic, and genuine telemetry heartbeats are dropped. The controller then wrongly concludes that vehicles have crashed (**reliability degraded**) — a safety failure caused directly by a security decision.
* *Mitigation to mention:* use session resumption and lighter elliptic-curve cryptography, and keep a small unencrypted-but-signed heartbeat channel so liveness detection never depends on the heavy secure channel.

---

#### Part C [4 Marks]: Kruchten's 4+1 View Model & Quality Attribute Integration

> **Question:** *How do the different views in Philippe Kruchten's 4+1 architectural model support the identification and analysis of Architecturally Significant Requirements (ASRs) in a software system, and what role do quality attributes play in integrating these views to ensure a comprehensive architecture?*

**Model Answer:**

**1. How each view helps identify and analyse ASRs.**
Kruchten's model splits architectural reasoning across four specialised perspectives, each of which naturally surfaces a different class of ASR:
1. **Logical view** — core business abstractions, domain entities and data structures. Surfaces ASRs about correctness, reusability and semantic integrity of the domain model.
2. **Process view** — threads, processes, concurrency, throughput and deadlock. Directly surfaces and tests **performance** and **concurrency** ASRs.
3. **Development view** — package structure, library dependencies, build pipeline and language constraints. Directly surfaces **modifiability** and **portability** ASRs.
4. **Physical / deployment view** — servers, cloud zones, network topology and failover. Directly surfaces **availability**, **disaster recovery** and infrastructure **security** ASRs.
5. **+1 Scenarios** — the validation engine. Each ASR is written as a concrete scenario and traced across the other four views; if it cannot be traced end to end, the design does not actually satisfy it.

**2. The integrating role of quality attributes.**
Quality attributes are the **cross-cutting force** that binds the four views together, because one quality requirement forces a coordinated decision in all of them.

*Worked example — the ASR "the system must survive a cloud zone outage with zero downtime":*
* *Logical view:* define stateless service entities and push all persistent state behind a separate repository interface.
* *Process view:* use non-blocking asynchronous messaging, so client threads do not hang while failover happens.
* *Development view:* package each service as a self-contained, containerisable unit (for example a Docker image) with strict boundaries, so it can be redeployed independently.
* *Physical view:* run those containers across multiple availability zones behind a health-checking load balancer.
* *Conclusion:* Without quality attributes the four views are four disconnected diagrams. Quality attributes impose the constraints that force the views into agreement, which is what makes the architecture comprehensive rather than merely well-documented.

---

### Question 3: Model Solution (7 Marks)

#### Part A [3 Marks]: Architecture Documentation & Quality Attributes

> **Question:** *How does the documentation of software architecture influence the identification and prioritization of ASRs, and what role does it play in ensuring that the designed system meets the required quality attributes, such as scalability, security, and usability?*

**Model Answer:**

**1. Influence on identifying and prioritising ASRs.**
Architecture documentation records more than diagrams — it records the **rationale** and the **context**: the business drivers, the constraints, and each stakeholder's concerns (this is the SEI "Views and Beyond" approach). By forcing requirements into standard structures — the Quality Attribute Utility Tree and the 6-part scenario — documentation converts vague wishes such as *"make it scalable"* into quantified, testable statements such as *"handle 10,000 requests per second with 99th-percentile latency under 100 ms"*. Only once a requirement is quantified can it be ranked, and only once it is ranked can architectural effort be spent where it actually matters.

**2. Role in ensuring the system meets its quality attributes.**
1. **It prevents drift and erosion.** While code is being written, the documentation is the binding contract that states which layer may call which, what each interface guarantees, and which dependencies are forbidden.
2. **It makes evaluation possible.** A rigorous evaluation such as ATAM cannot run without documented views — evaluators trace quality scenarios through those views to find risks and bottlenecks *before* deployment.
3. **It guarantees traceability.** Documentation maps each tactic to the ASR that justified it — TLS encryption to a security ASR, read replicas to a scalability ASR, client-side caching to a usability ASR. That traceability is what lets a future team change a tactic without silently violating the requirement behind it.

---

#### Part B [4 Marks]: Utility Tree Notation, Structure & Design Decisions

> **Question:** *How does the Utility Tree notation facilitate the identification and prioritization of ASRs in software architecture, and provide an example of a scenario where the Utility Tree helps to refine quality attributes and drive design decisions.*

**Model Answer:**

**1. The notation and structure.**
The Utility Tree is a top-down hierarchy used in both Attribute-Driven Design (ADD) and ATAM:
* **Level 0 — Root:** *Utility*, meaning the overall fitness of the system for its purpose.
* **Level 1 — Quality attributes:** broad qualities such as Performance, Availability, Security.
* **Level 2 — Refinements:** narrower sub-qualities, for example under Performance: *latency* and *throughput*.
* **Level 3 — Scenarios:** concrete, measurable 6-part scenarios (Source, Stimulus, Artifact, Environment, Response, Response Measure).
* **Priority pair (B, A):** every leaf scenario is tagged with two ratings, each High / Medium / Low —
  * **B** = importance to the business,
  * **A** = technical difficulty or risk to the architecture.
  Scenarios rated **(H, H)** are the true ASRs and are designed first.

```text
UTILITY TREE HIERARCHY:
Utility ──┬── Performance ──┬── Query Latency ──────> [P99 under 100ms for catalog search] (H, M)
          │                 └── Checkout Throughput ─> [10,000 orders/sec with no drops]   (H, H)
          │
          └── Security ─────┬── Data Protection ────> [AES-256 encryption at rest]         (H, L)
                            └── Threat Detection ───> [Detect brute force within 5 tries]  (M, M)
```

**2. Example — how the tree drives real design decisions (telemedicine platform).**
* *Unrefined requirement:* "The platform must be secure and fast during video consultations." This is unbuildable as written.
* *Refinement through the tree:*
  * Performance → *media streaming latency* → scenario: *"During peak hours with 1,000 concurrent patient-doctor calls, video latency must stay under 150 ms over a 4G connection."* → **(H, H)**
  * Security → *patient privacy (HIPAA)* → scenario: *"All audio and video streams must be end-to-end encrypted; neither the ISP nor any intermediary server may be able to decrypt the media."* → **(H, H)**
* *Design decisions forced by those two ratings:*
  * Both are (H, H), so both must be satisfied by the core structure — neither can be bolted on later.
  * A conventional centralised media server is ruled out: relaying and re-encoding every stream adds latency, and decrypting at the server violates the privacy scenario.
  * *Decision:* adopt **WebRTC with SRTP and DTLS**, using direct peer-to-peer media paths. STUN/TURN servers are used only to establish the connection through firewalls, never to decrypt media. This satisfies the 150 ms target and the HIPAA requirement with a single structural decision.
* *Trade-off to state:* peer-to-peer media is harder to record, monitor and debug centrally, and TURN relaying still costs bandwidth for users behind restrictive networks. The team accepts this because both driving scenarios were rated (H, H).

---

### Question 4: Model Solution (7 Marks)

#### Part A [3 Marks]: Product Availability vs. Inventory Costs in Distribution Networks

> **Question:** *What are the trade-offs between achieving high product availability and minimizing inventory costs in a distribution network, and how might a firm balance these competing objectives to maximize profitability?*

**Model Answer:**

**1. The fundamental trade-off.**
* *High product availability:* Keep generous safety stock in several regional distribution centres near customers. Orders ship immediately, stockouts are rare, and customer satisfaction and revenue are protected. The cost is steep: capital locked up in stock, warehouse rent, insurance, handling labour, and the risk of goods becoming obsolete.
* *Minimising inventory cost:* Run lean and just-in-time, with inventory centralised in one hub. Holding costs fall sharply, but replenishment lead times grow, and any supply disruption causes stockouts, expensive expedited shipping, lost sales and customer churn.

**2. How a firm balances the two.**
* **ABC segmentation with risk pooling** — do not treat all products alike:
  * *Class A (fast-moving, high-margin):* decentralise stock into regional centres close to buyers, and target very high availability (above 98%). The margin justifies the holding cost.
  * *Class B and C (slow-moving, low-margin, long tail):* pool all of it in one central warehouse and ship on demand by express logistics. Pooling demand across regions means far less total safety stock is needed for the same service level.
* **Predictive demand forecasting with dynamic safety stock:** use models of historical demand, seasonality and supplier lead times to raise or lower safety stock continuously, instead of holding a fixed buffer that is simultaneously too much in quiet months and too little in peak season.

**3. The underlying principle:** availability and inventory cost cannot both be optimised globally, so the firm optimises them **per product class**, spending stock where the margin and demand justify it and pooling risk everywhere else.

---

#### Part B [4 Marks]: Manufacturing Complexity vs. Production Costs in Additive Manufacturing

> **Question:** *What are the potential trade-offs between manufacturing complexity and production costs when utilizing additive manufacturing technologies, and how might these trade-offs impact the design and production of person-specific or location-specific products?*

**Model Answer:**

**1. The trade-offs.**
* *Traditional manufacturing (CNC machining, injection moulding):*
  * Very high fixed cost up front for moulds and tooling, but an extremely low variable cost per unit at high volume.
  * **Complexity penalty:** as geometry gets more complex — internal channels, lattices, organic curves — tooling and machining cost rises steeply, and some shapes cannot be made at all.
* *Additive manufacturing (3D printing):*
  * **Complexity is essentially free:** printing an intricate internal lattice takes the same machine time and material as printing a solid block of the same volume, and there is no tooling or changeover cost at all.
  * **Unit cost penalty:** specialised powders and resins are expensive, build cycles are slow, and post-processing needs labour. So the cost per unit stays roughly flat — additive gains almost nothing from economies of scale.
* *The crossover rule:* additive wins at **low volume and high complexity**; traditional wins at **high volume and stable, simple geometry**.

**2. Impact on person-specific products (custom implants, dental aligners, prosthetics).**
* *Design impact:* Standard sizing is no longer necessary. A patient's CT scan can be converted directly into a custom model with complex organic geometry that matches their anatomy.
* *Production impact:* There is no custom tooling to pay for, so production is economically viable at a batch size of one. The high per-unit printing cost is easily absorbed because the clinical value of a perfectly fitted implant is far higher than the cost difference.

**3. Impact on location-specific products (remote outposts, ships, space stations, offshore rigs).**
* *Supply chain impact:* The site no longer needs to stock a large inventory of rarely used spare parts on the chance that one fails.
* *Production impact:* The physical spare-parts supply chain is replaced by transmitting a digital blueprint. The technician downloads the model and prints the part on site, on demand. The firm trades a higher per-unit energy and time cost for the complete elimination of freight lead times, customs delays and remote warehousing.

**4. Closing trade-off statement:** additive manufacturing converts a *fixed* cost (tooling) into a *variable* cost (per-unit printing). That is a bad deal at mass-production volumes and an excellent one wherever each unit must be different, or wherever getting the unit to the site is the hard part.

---

# Module 9: High-Yield Flashcard Cheat Sheet & Glossary

### 38 One-Line Exam Definitions

1. **Software Architecture:** The set of structures needed to reason about a system — its elements, the relations among them, and the properties of both.
2. **Externally Visible Properties:** What other components are allowed to assume about an element — its interface, guarantees, latency and failure behaviour — excluding anything about its internals.
3. **Architecturally Significant Requirement (ASR):** A requirement that shapes the system's high-level structure and would be expensive to change later.
4. **Quality Attribute (QA):** A measurable, testable property describing *how well* a system behaves, as opposed to *what* it does.
5. **Quality Attribute Scenario:** A requirement written in six standard parts — Source, Stimulus, Artifact, Environment, Response, Response Measure.
6. **Availability:** The fraction of time the system is operational, calculated as MTBF ÷ (MTBF + MTTR).
7. **MTTR (Mean Time To Repair):** The total time to detect a failure, fail over, and return to full service.
8. **MTBF (Mean Time Between Failures):** The average time the system runs correctly before the next failure.
9. **Active Redundancy (Hot Standby):** A backup that processes the same requests in parallel, so failover is instant.
10. **Passive Redundancy (Warm Standby):** A backup that receives periodic state updates and takes over after a short delay.
11. **Performance:** How quickly and how much the system can handle — measured by latency, throughput and deadline compliance.
12. **Security:** The ability to resist unauthorised use while continuing to serve authorised users.
13. **Non-Repudiation:** The guarantee that someone cannot later deny having performed an action.
14. **Modifiability:** The cost and time required to make changes to the system over its life.
15. **Usability (ISO 9241-11):** How well specified users achieve their goals with effectiveness, efficiency and satisfaction, in a specified context.
16. **Effectiveness (Usability):** Whether users complete their task accurately and completely.
17. **Efficiency (Usability):** How much time, effort and interaction the task costs the user.
18. **Satisfaction (Usability):** How comfortable and positive the experience feels to the user.
19. **Interoperability:** How well two independent systems can exchange data and act on it — syntactically and semantically.
20. **Testability:** How easily the system's faults can be revealed by testing.
21. **Utility Tree:** A four-level hierarchy (Utility → Quality Attribute → Refinement → Scenario) used to prioritise ASRs by (business importance, technical difficulty).
22. **Attribute-Driven Design (ADD):** A repeatable 7-step method that decomposes a system driven by its highest-priority quality attribute requirements.
23. **Quality Attribute Workshop (QAW):** An 8-step stakeholder workshop that turns vague wishes into prioritised, testable quality scenarios.
24. **Structure:** The actual physical reality of the system — code, running processes, hardware nodes.
25. **View:** A documented representation of one structural perspective, created for one stakeholder group.
26. **Kruchten's 4+1 Model:** Documentation organised as Logical, Process, Development and Physical views, unified by the +1 Scenarios view.
27. **Module Structure:** The static organisation of code — classes, packages, layers — serving modifiability.
28. **Component-and-Connector (C&C) Structure:** The runtime organisation — processes, services and the connections between them — serving performance and availability.
29. **Allocation Structure:** The mapping of software onto hardware, environments and teams — serving availability and cost.
30. **Strict Layering:** A rule that layer N may call only layer N−1; maximises modifiability, at the cost of sinkhole overhead.
31. **Sinkhole Effect:** Wasted latency caused by a layer that adds no logic and merely forwards the call downward.
32. **Application Façade:** A single simplified interface placed in front of a complex group of subsystems.
33. **Aspect-Oriented Design (AOD):** Isolating cross-cutting concerns such as logging, security and auditing into reusable aspects applied across all layers.
34. **ATAM (Architecture Tradeoff Analysis Method):** A 9-step SEI method that evaluates an architecture against prioritised quality scenarios to find risks and trade-offs before implementation.
35. **Sensitivity Point:** A decision or parameter that strongly affects one particular quality attribute.
36. **Trade-off Point:** A decision that affects two or more quality attributes in opposite directions.
37. **Architectural Conformance:** The state in which the implemented code genuinely obeys the architecture's rules and boundaries.
38. **Architectural Drift / Erosion:** Drift is unplanned divergence of code from the intended architecture through ad-hoc shortcuts; erosion is the widespread structural decay that accumulated drift eventually produces.

**Bonus terms worth memorising:**
* **Software Architecture Reconstruction (SAR):** Reverse-engineering the as-built architecture of an undocumented or legacy system from its code, binaries and runtime traces.
* **Raw View Extraction:** SAR stage 1 — automatically mining low-level facts (files, classes, calls, tables) from the artifacts.
* **View Fusion:** SAR stage 3 — combining static, dynamic and expert-guided views and abstracting them into high-level subsystems.
* **White-Noise View:** The unreadable tangle produced when every raw extracted relation is drawn without abstraction (from the SEI 'Vanish' case study).
* **Vertical Conformance:** Checking that calls across layers respect layer boundaries without illegal skips.
* **Horizontal Conformance:** Checking that all components within one layer follow the same conventions and shared frameworks.

---

### "Don't Say X, Say Y" — Exam Vocabulary Upgrade

| Don't say (casual developer) | Say (architectural vocabulary) |
| :--- | :--- |
| "Writing good code so it doesn't break" | "Applying fault-prevention and fault-detection tactics to increase MTBF" |
| "Making the UI simple" | "Optimising the ISO 9241-11 usability triad of effectiveness, efficiency and satisfaction" |
| "Putting it into a microservice" | "Decomposing into Component-and-Connector runtime structures with asynchronous connectors" |
| "Encrypting passwords" | "Applying security tactics to preserve confidentiality and authenticate actors" |
| "The diagram of the app" | "A documented architectural view addressing a specific stakeholder's concerns" |
| "Listing our requirements" | "Constructing a Quality Attribute Utility Tree prioritised by business importance and architectural risk" |
| "Checking if the design is good" | "Conducting an ATAM evaluation to identify risks, sensitivity points and trade-off points" |
| "Code getting messy over time" | "Architectural drift and erosion violating the documented structural rules" |
| "Rewriting an old app because there are no docs" | "Performing Software Architecture Reconstruction to recover the as-built architecture before modifying it" |
| "Checking if devs followed the rules" | "Validating vertical and horizontal architectural conformance to detect drift" |
| "It'll be slower but easier to change" | "This is a trade-off point: modifiability improves, performance degrades through added indirection" |

---

### The Last 60-Minutes Exam Survival Checklist

1. **Read every word of the question.** Look for the trigger words: *trade-off, structure, view, Kruchten 4+1, utility tree, scenario, ASR, tactic*. Each one tells you which framework the examiner wants.
2. **Budget strictly: 3 minutes per mark.** A 3-mark question gets 9 minutes, never 25.
3. **Always name a concrete system.** Never leave an answer abstract — anchor it in e-commerce checkout, a FinTech payment gateway, the Aadhaar portal, a hospital or telemedicine system.
4. **Draw the diagram when asked.** For a utility tree or Kruchten 4+1, sketch it. Marks are awarded for the structure being visible, not for it being beautiful.
5. **State the trade-off explicitly, in one sentence.** *"This improves [attribute A] through [mechanism], but degrades [attribute B] because of [cause], mitigated by [tactic]."*
6. **Use the 6-part scenario template** whenever asked to illustrate an ASR or a quality attribute: label Source, Stimulus, Artifact, Environment, Response, Response Measure.
7. **Name the tactics.** Prof. Jabbal's own emphasis: *"Other things you will remember, but tactics are something you need to review and master."* Every quality attribute answer should name at least two specific tactics from Module 2.
8. **Structure every long answer in four parts:** definition → mechanism → concrete example → trade-off. An unstructured paragraph loses half the marks even when the content is right.
