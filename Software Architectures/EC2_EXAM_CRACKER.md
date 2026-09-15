# BITS Pilani WILP — Software Architectures (SEZG651 / SSZG653)
# EC-2 Comprehensive Master Exam Textbook & Cracker

> 🎯 **Your Sole Examination Resource:** This textbook is designed as the single, self-contained reference you need to score top marks (**28–30 / 30**) in the **EC-2 (Mid-Term) Examination**. It combines and explains all 8 lectures (Lectures 1 to 8), presentation decks, transcripts of Prof. Harvinder S. Jabbal, Len Bass's *Software Architecture in Practice* (3rd/4th Edition), and provides complete model answers to past exam papers.

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
  * [2. Deep Dive into the "Big 7" Quality Attributes & Software Engineering Institute (SEI) Tactics](#2-deep-dive-into-the-big-7-quality-attributes--sei-tactics)
    * [Availability](#availability)
    * [Performance](#performance)
    * [Security](#security)
    * [Modifiability](#modifiability)
    * [Usability (The ISO 9241-11 Usability Triad (Effectiveness, Efficiency, Satisfaction) (Three Parts: Effectiveness, Efficiency, Satisfaction): Effectiveness, Efficiency, Satisfaction)](#usability-the-iso-9241-11-triad)
    * [Interoperability](#interoperability)
    * [Testability](#testability)
* [Module 3: Architecturally Significant Requirements (ASRs) & Elicitation (Lectures 4 & 5)](#module-3-architecturally-significant-requirements-asrs--elicitation-lectures-4--5)
  * [1. What is an ASR? The 5% Rule & The 4 Filters](#1-what-is-an-asr-the-5-rule--the-4-filters)
  * [2. Elicitation Frameworks: Quality Attribute Workshop (QAW - 8 Steps) & PALM](#2-elicitation-frameworks-qaw-8-steps--palm)
  * [3. The Utility Tree Masterclass (Notation, Structure & Prioritization)](#3-the-utility-tree-masterclass-notation-structure--prioritization)
  * [4. Attribute-Driven Design (Attribute-Driven Design (ADD 3.0)) 7-Step Method](#4-attribute-driven-design-add-30-7-step-method)
* [Module 4: Software Structures, Views & Kruchten's 4+1 Model (Lecture 6)](#module-4-software-structures-views--kruchtens-41-model-lecture-6)
  * [1. Structures vs. Views (The Fundamental Law)](#1-structures-vs-views-the-fundamental-law)
  * [2. The 3 Software Engineering Institute (SEI) Structure Families (Module, C&C, Allocation)](#2-the-3-sei-structure-families-module-cc-allocation)
  * [3. Philippe Kruchten's 4+1 View Model Deep Dive](#3-philippe-kruchtens-41-view-model-deep-dive)
  * [4. How Quality Attributes Integrate Kruchten's Views](#4-how-quality-attributes-integrate-kruchtens-views)
* [Module 5: Layered Architectures & Architecture Evaluation (ATAM) (Lecture 7)](#module-5-layered-architectures--architecture-evaluation-atam-lecture-7)
  * [1. The Layered Pattern: Strict vs. Relaxed Layering](#1-the-layered-pattern-strict-vs-relaxed-layering)
  * [2. Key Architectural Techniques Across the 4 Layers](#2-key-architectural-techniques-across-the-4-layers)
  * [3. Real-World Case Studies (Aadhaar, Flight Booking, MakeMyTrip, Shipping Façade)](#3-real-world-case-studies)
  * [4. Architecture Tradeoff Analysis Method (ATAM)](#4-architecture-tradeoff-analysis-method-atam)
* [Module 6: Architectural Conformance & Software Architecture Reconstruction (SAR) (Lecture 8)](#module-6-architectural-conformance--software-architecture-reconstruction-sar-lecture-8)
  * [1. Architectural Conformance vs. Architectural Drift & Erosion](#1-architectural-conformance-vs-architectural-drift--erosion)
  * [2. 4 Core Techniques to Ensure Conformance](#2-4-core-techniques-to-ensure-conformance)
  * [3. Architecture & Testing Activities (Utility Tree & Testability Design)](#3-architecture--testing-activities)
  * [4. The 4-Stage Software Architecture Reconstruction (SAR) Pipeline](#4-the-4-stage-software-architecture-reconstruction-sar-pipeline)
  * [5. Real-World Case Study: The 'Vanish' System (ARMIN Tool)](#5-real-world-case-study-the-vanish-system-armin-tool)
  * [6. Vertical vs. Horizontal Conformance Matrix](#6-vertical-vs-horizontal-conformance-matrix)
  * [7. Automated Analysis Tooling & Real-World Violations](#7-automated-analysis-tooling--real-world-violations)
* [Module 7: The Master Architectural Trade-Off Playbook](#module-7-the-master-architectural-trade-off-playbook)
  * [1. Usability: Effectiveness vs. Efficiency vs. Satisfaction](#1-usability-effectiveness-vs-efficiency-vs-satisfaction)
  * [2. Security vs. Performance vs. Reliability](#2-security-vs-performance-vs-reliability)
  * [3. Security vs. Usability](#3-security-vs-usability)
  * [4. Modifiability vs. Performance (The Middle-Layer Slowdown Penalty (Indirection))](#4-modifiability-vs-performance-the-indirection-penalty)
  * [5. Scalability vs. Development Speed / Opportunity Cost](#5-scalability-vs-development-speed--opportunity-cost)
  * [6. General Systems Trade-Offs (Distribution Networks & Additive Manufacturing)](#6-general-systems-trade-offs)
* [Module 8: Fully Solved Past EC-2 Exam Paper (Model Solutions)](#module-8-fully-solved-past-ec-2-exam-paper-model-solutions)
  * [Question 1: Architecture Definition, Scalability/Maintainability & ASRs (8 Marks)](#question-1-model-solution-8-marks)
  * [Question 2: Usability Triad (Effectiveness, Efficiency, Satisfaction), Cross-Cutting Qualities & Kruchten's 4+1 (8 Marks)](#question-2-model-solution-8-marks)
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
Bass et al. identify 13 fundamental drivers why software architecture is paramount:

1. **Inhibits or Enables Quality Attributes:** You cannot achieve high availability or sub-second latency purely through clever coding; the structural topology either facilitates or bottlenecks it.
2. **Reasoning About and Managing Change:** Modular architectures isolate ripple effects. 80% of total lifecycle cost is maintenance; architecture bounds the change impact area (blast-radius).
3. **Predicting System Qualities Early:** Evaluators can inspect documented views (via ATAM) to identify bottlenecks before a single line of code is written.
4. **Enhances Communication Among Stakeholders:** Provides a high-level common shared language uniting non-technical business clients, UX designers, backend coders, and cloud SREs.
5. **Earliest Set of Design Decisions:** Sets the structural mold and commitments that are the hardest and most expensive to alter later.
6. **Defines Implementation Constraints:** Dictates allowed dependency directions (e.g., UI cannot call Database directly) and architectural pattern conformity.
7. **Influences Organizational Structure (Conway’s Law):** *"Organizations which design systems are constrained to produce designs which are copies of the communication structures of these organizations."* Breaking an architecture into microservices drives modular, cross-functional squads.
8. **Enables Evolutionary Prototyping:** Allows constructing an architectural skeleton (an executable walking skeleton) early in the lifecycle to de-risk key unknowns.
9. **Guides Component-Based Development & Commercial Off-The-Shelf (COTS - Ready-Made Software) Integration:** Establishes rigorous interface contracts so off-the-shelf software, open-source libraries, and SaaS APIs can be slotted in seamlessly.
10. **Prevents Cost of Rework:** Detecting an architectural flaw during design costs 1% of what it costs to fix the flaw after production deployment.
11. **Serves as Training Vehicle:** Enables rapid onboarding of new engineering personnel by providing high-level mental models of system components.
12. **Key Artifact for Software Product Lines:** Enables capitalizing on shared architectural assets across multiple related product variations.
13. **Manages Complexity:** Keeps human mental effort (cognitive load) manageable by abstracting away billions of transistors and network packets into structured layers.

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

* **Architectural Erosion (Decay):** Occurs when developers violate intended architectural constraints in source code (e.g., an engineer writes direct database SQL queries inside a React UI component to meet a tight deadline). This introduces illegal dependencies, increases coupling, and destroys modularity.
* **Architectural Drift:** Occurs when the system evolves through new features or bug fixes, but the architectural views and models are never updated. The software reality moves forward while the documentation becomes obsolete fiction.
* **Mitigations:**
  1. *Automated Architecture Unit Testing:* Using tools like **ArchUnit** (Java) or **NetArchTest** (.NET) in CI/CD pipelines to fail builds if unapproved cross-layer dependencies are introduced.
  2. *Scheduled Architecture Audits:* Conducting regular peer reviews and Architecture Tradeoff Analysis Method (ATAM) reviews to compare running system reality with documented views.

---

# Module 2: The Quality Attribute Masterclass & Tactics (Lectures 2 & 3)

### 1. Functional vs. Quality Attribute Requirements
* **Functional Requirements:** Define *what* a system does—the business features, capabilities, and data transformations (e.g., *"System must allow customers to search products, add items to cart, and make credit card payments"*).
* **Quality Attribute Requirements (Non-Functional Requirements):** Define *how well* the system executes those functions—the operational qualifications, constraints, and non-functional behaviors (e.g., *"The checkout transaction must complete in under 1.5 seconds, handle 15,000 concurrent sessions, maintain 99.99% availability, and comply with PCI-DSS encryption standards"*).
* **The Iron Law of Architecture:** *Almost any architectural pattern can satisfy a functional requirement. It is the Quality Attribute Requirements that dictate the exact choice of architectural structures, patterns, and tactics.*

---

### 2. Deep Dive into the "Big 7" Quality Attributes & Software Engineering Institute (SEI) Tactics

```text
                        THE SEI "BIG 7" QUALITY ATTRIBUTES
     ┌───────────────┬───────────────┬───────────────┬────────────────┐
     │ Availability  │  Performance  │   Security    │ Modifiability  │
     ├───────────────┼───────────────┼───────────────┼────────────────┤
     │   Usability   │Interoperabilty│  Testability  │                │
     └───────────────┴───────────────┴───────────────┴────────────────┘
```

---

### Availability
* **Formal Definition:** The degree to which a system is operational and accessible when required for use.
* **Mathematical Formula:**
  $$\text{Availability} (A) = \frac{\text{MTBF}}{\text{MTBF} + \text{MTTR}}$$
  * **MTBF (Mean Time Between Failures):** How long the system runs before a fault occurs.
  * **MTTR (Mean Time To Repair):** Total time taken to detect the fault, isolate it, switch over to backup, and restore service.
* **Industry Targets:** "Four Nines" ($99.99\% \approx 52.6\text{ minutes downtime/year}$); "Five Nines" ($99.999\% \approx 5.26\text{ minutes downtime/year}$).

#### SEI Architectural Tactics for Availability:
1. **Fault Detection:**
   * *Ping/Echo:* A monitor periodically sends an asynchronous ping to a node; absence of echo triggers failover.
   * *Heartbeat:* The node periodically broadcasts an automatic, without waiting for a request *"I am alive"* message. If missing for $N$ intervals, monitor assumes node failure.
   * *Exception Detection / Invariant Checking:* Code asserts runtime data integrity; catches unhandled errors before they propagate.
2. **Fault Recovery:**
   * *Active Redundancy (Hot Standby):* All redundant nodes receive and process requests in parallel. If primary fails, secondary already has state computed; zero downtime switchover.
   * *Passive Redundancy (Warm Standby):* Primary handles requests and streams periodic state updates/checkpoints to standby. If primary fails, standby loads state and takes over in seconds.
   * *Cold Standby:* Backup node is offline/powered down. Must boot OS, start application, and restore from disk; takes minutes.
   * *Checkpoint & Rollback:* Writing consistent operational state to permanent disk storage (SSD/Hard drive) to allow clean recovery after unexpected crash.
3. **Fault Prevention:**
   * *Transactions (ACID):* Atomic rollback ensures hardware crashes do not leave inconsistent, corrupted database states.
   * *Predictive Removal from Service:* Monitoring memory leak trends and rebooting nodes during off-peak windows before an out-of-memory crash occurs.

#### Exam-Ready Software Engineering Institute (SEI) 6-Part Scenario (Availability):
* **Source:** Unscheduled hardware failure (CPU overheating).
* **Stimulus:** Primary database server crashes during peak processing.
* **Artifact:** Core transaction ledger database.
* **Environment:** Normal business operating hours under 5,000 active transactions/sec.
* **Response:** Heartbeat monitor detects outage, triggers automated DNS failover to hot standby read/write replica, and initiates transaction replay.
* **Response Measure:** Failover completes within $\le 3\text{ seconds}$; zero lost transactions ($\text{RPO} = 0$).

---

### Performance
* **Formal Definition:** The timeliness of system response to events, measured by latency, throughput, and deadline satisfaction.
* **Core Metrics:** Latency (milliseconds per request), Throughput (transactions/second), Jitter (standard deviation in latency).

#### SEI Architectural Tactics for Performance:
1. **Control Resource Demand:**
   * *Manage Event Rate / Throttling:* Enforcing token-bucket rate limits on external API clients to avoid server saturation.
   * *Sampling:* Dropping intermediate sensor ticks or logs when ingestion buffers reach 80% capacity.
   * *Limit Response:* Enforcing pagination on search queries (returning 20 items per page instead of 50,000 database records).
2. **Manage Resources (Supply):**
   * *Concurrency / Multi-threading:* Thread pools and event loops (e.g., Node.js libuv, Netty) handling I/O without blocking worker threads.
   * *Data Caching:* Placing in-memory stores (Redis, Memcached) or CDN edge nodes in front of databases to eliminate repeated disk I/O.
   * *Horizontal Scaling:* Replicating stateless application instances behind an Application Load Balancer.

#### Exam-Ready Software Engineering Institute (SEI) 6-Part Scenario (Performance):
* **Source:** 50,000 simultaneous online shoppers.
* **Stimulus:** High-volume product search and checkout requests arriving at peak sale opening.
* **Artifact:** Product Catalog and Inventory Services.
* **Environment:** Peak holiday promotional flash sale.
* **Response:** Requests served from distributed Redis edge caches; database connection pooling buffers spikes; async order queuing absorbs checkout spikes.
* **Response Measure:** 99th percentile (P99) response latency $\le 200\text{ ms}$; sustained throughput $\ge 10,000\text{ transactions/second}$.

---

### Security
* **Formal Definition:** The ability of a system to resist unauthorized access, manipulation, or denial of service, while maintaining full service to legitimate actors.
* **The Security Sextet (CIA + AAA):**
  * *Confidentiality:* Ensuring data is disclosed only to authorized parties (Encryption).
  * *Integrity:* Ensuring data is not altered or tampered with in transit or at rest (HMAC, SHA-256).
  * *Availability:* Ensuring authorized users have uninterrupted access (DDoS mitigation).
  * *Authentication:* Confirming the true identity of users or services (MFA, JWT, OAuth2/OIDC).
  * *Authorization:* Determining whether an authenticated identity has permission to perform an action (RBAC, ABAC).
  * *Non-Repudiation:* Preventing a sender from denying an action they performed (Cryptographically signed audit logs).

#### SEI Architectural Tactics for Security:
1. **Detect Attacks:** Intrusion Detection Systems (IDS), automated anomaly analyzers, honey-pots, and audit log analysis.
2. **Resist Attacks:**
   * *Authenticate Actors:* Multi-Factor Authentication (MFA), biometric authentication, cryptographic mutual TLS (mTLS).
   * *Authorize Actors:* Role-Based Access Control (RBAC) enforced at API gateways.
   * *Encrypt Data:* TLS 1.3 for data in transit; AES-256-GCM for data at rest.
   * *Validate Inputs:* Parameterized queries (blocking SQL Injection); strict JSON schema validators (blocking XSS and remote code execution).
3. **React to Attacks:** Automated session revocation, temporary IP blacklisting, rate-limiting, and alert paging.
4. **Recover from Attacks:** Restoring from clean, read-only and unchangeable backups; cryptographically sealed audit trails to analyze breaches.

#### Exam-Ready Software Engineering Institute (SEI) 6-Part Scenario (Security):
* **Source:** Malicious external attacker.
* **Stimulus:** Distributed denial-of-service (DDoS) flood combined with automated SQL injection injection payloads on login endpoints.
* **Artifact:** Public API Gateway and Authentication Microservice.
* **Environment:** System operating under normal internet-exposed traffic.
* **Response:** Cloud DDoS shield (e.g., AWS Shield/Cloudflare) absorbs large volume network floods; API Gateway validates JSON payloads against strict schemas; input parameterization strips SQL injection vectors; suspicious IPs are throttled.
* **Response Measure:** 100% of malicious SQLi attempts blocked; zero data stealing or leaking data; zero degradation to legitimate user authentication.

---

### Modifiability
* **Formal Definition:** The ease with which a software system can be modified, extended, or refactored with minimal cost, time, and defect risk.
* **Core Principles:** Maximize **Cohesion** (keeping logically related responsibilities together) and minimize **Coupling** (reducing dependencies between components between separate modules).

#### SEI Architectural Tactics for Modifiability:
1. **Reduce Coupling:**
   * *Encapsulation:* Exposing functionality solely through abstract public interfaces while keeping concrete implementation classes private.
   * *Use an Intermediary:* Introducing Brokers, Message Queues, Façades, or API Gateways so clients never talk directly to concrete backend implementations.
   * *Restrict Communication Paths:* Strict layering rules preventing circular dependencies and cross-layer bypassing.
2. **Defer Binding Time:**
   * *Configuration Files:* Externalizing database connection strings, feature flags, and timeouts in YAML/JSON without recompilation.
   * *Dependency Injection (DI):* Binding interface implementations at runtime via inversion-of-control containers (e.g., Spring Boot, Guice).
   * *Plugin / Micro-kernel Architectures:* Dynamically discovering and loading compiled modules at application runtime.

#### Exam-Ready Software Engineering Institute (SEI) 6-Part Scenario (Modifiability):
* **Source:** Product Management / Compliance Officer.
* **Stimulus:** Requirement to integrate a new regional payment provider (e.g., Razorpay/UPI) alongside existing Stripe and PayPal integrations.
* **Artifact:** Payment Processing Subsystem.
* **Environment:** Active production application undergoing regular bi-weekly sprint releases.
* **Response:** Developer implements a new `RazorpayAdapter` conforming to the existing `IPaymentGateway` interface and enables it via configuration file.
* **Response Measure:** Change completed and tested in $\le 2\text{ engineering days}$; zero modifications required to Order, Cart, or Catalog services.

---

### Usability (The ISO 9241-11 Usability Triad (Effectiveness, Efficiency, Satisfaction) (Three Parts: Effectiveness, Efficiency, Satisfaction))

> 💡 **CRITICAL EXAM CONCEPT (Directly Asked in EC-2 Question 2a):**
> ISO 9241-11 defines usability as: *"The extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use."*

```text
                          THE USABILITY TRIAD (ISO 9241-11: THREE CORE PARTS)
      ┌────────────────────┬────────────────────┬────────────────────┐
      │   Effectiveness    │     Efficiency     │    Satisfaction    │
      ├────────────────────┼────────────────────┼────────────────────┤
      │ Accuracy &         │ Speed & minimal    │ Comfort, trust,    │
      │ completeness of    │ mental/physical    │ aesthetic delight, │
      │ goal achievement   │ effort expended    │ and peace of mind  │
      │ (Error-free)       │ (Fewer taps/clicks)│ (Positive emotion) │
      └────────────────────┴────────────────────┴────────────────────┘
```

1. **Effectiveness (Goal Accuracy & Completeness):**
   * Can users successfully finish their objective without making catastrophic errors?
   * *Tactics:* Real-time input masking, inline validation, unambiguous labels, confirmation dialogs for destructive actions, auto-complete.
2. **Efficiency (Speed & Minimal Cognitive/Physical Load):**
   * How much time, physical actions (keystrokes, taps, swipes), and mental calculations must the user expend?
   * *Tactics:* 1-Click checkout, biometric fingerprint authentication (replacing 16-character passwords), auto-filling OTPs from SMS, smart search defaults.
3. **Satisfaction (User Comfort & Subjective Delight):**
   * How pleasant, trustworthy, and non-frustrating is the user experience?
   * *Tactics:* Clear visual feedback (spinners, progress bars), smooth micro-animations, absence of jarring layout shifts, dark mode, friendly humanized error messages.

#### The Trade-Offs in Usability Design (Mobile Application Context):
* **Effectiveness vs. Efficiency Tension:**
  * To maximize *Effectiveness*, designers insert safety checks (confirmation dialogs, two-step verification, review summaries). This protects users from making mistakes, but severely damages *Efficiency* by requiring extra clicks and time.
  * Conversely, an ultra-*Efficient* UI (1-tap instant fund transfer) causes frequent user mistakes (sending money to the wrong contact), completely destroying *Effectiveness*.
* **Modern Mobile Architectural Balancing Strategies:**
  1. *Progressive Disclosure & Risk-Tiered Friction:* For everyday low-risk operations (e.g., merchant payment $<\$20$), maximize efficiency with 1-tap biometric auth. For high-risk operations (e.g., wire transfer $>\$1,000$), insert deliberate defensive friction (full confirmation screen + OTP).
  2. *Forgiving UI (The 5-Second Undo Pattern):* Allow instantaneous 1-tap action (maximizing efficiency and satisfaction), but display a prominent floating *"Undo"* action bar for 5 seconds (safeguarding effectiveness).

---

### Interoperability
* **Formal Definition:** The degree to which two or more systems can usefully exchange information and execute coordinated business processes.
* **The Two Levels of Interoperability:**
  1. *Syntactic Interoperability:* Formatting and protocol compatibility (e.g., both systems agree to communicate using JSON over HTTPS REST).
  2. *Semantic Interoperability:* Common understanding of the *meaning* of the data (e.g., both systems interpret date formats identically and map product categories to a shared industry taxonomy).
* **Tactics:**
  * *Locate:* Dynamic service discovery registries (Consul, Eureka).
  * *Manage Interfaces:* Protocol adapters, data transformation mappers, API Gateways, Enterprise Service Buses (ESB).

---

### Testability
* **Formal Definition:** The ease with which a software system can demonstrate its faults through automated or manual execution.
* **Core Metrics:** Code coverage, defect discovery rate, test execution time.
* **Tactics:**
  * *Manage Interfaces:* Dependency Injection (DI) to allow mocking external payment gateways; exposing specialized test harnesses.
  * *Capture Internal State:* Adding diagnostic actuators (`/health`, `/metrics`), test probes, and state serialization endpoints.

---

# Module 3: Architecturally Significant Requirements (ASRs) & Elicitation (Lectures 4 & 5)

### 1. What is an ASR? The 5% Rule & The 4 Filters
* **The 5% Rule:** In an enterprise software backlog containing 200 user stories, **~95% are routine functional requirements** (e.g., *"User can view profile photo,"* *"Admin can filter transactions by date"*). A developer can implement them in an afternoon; they do not dictate system architecture. **Only ~5% are Architecturally Significant Requirements (ASRs)**.
* **Formal Definition:** An ASR is any requirement that has a profound, shaping effect on a system's high-level structures, requires significant engineering effort to satisfy, and is prohibitively expensive to alter once built.

```text
┌────────────────────────────────────────────────────────┐
│                   ALL REQUIREMENTS                     │
│  ┌──────────────────────────────────────────────────┐  │
│  │ Routine Requirements (95%)                       │  │
│  │ (CRUD endpoints, UI labels, color themes)        │  │
│  │ ┌──────────────────────────────────────────────┐ │  │
│  │ │ ARCHITECTURALLY SIGNIFICANT REQUIREMENTS (5%)│ │  │
│  │ │ (99.999% uptime, 50k req/s, GDPR compliance) │ │  │
│  │ └──────────────────────────────────────────────┘ │  │
│  └──────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────┘
```

#### The 4 Critical Filters to Identify an ASR:
1. **High Business Value & High Technical Risk:** If this requirement fails, the business suffers catastrophic financial ruin, regulatory fines, or severe brand damage (e.g., zero payment transaction loss).
2. **Non-Standard Quality of Service (QoS):** Demands extreme scale, low latency, or continuous uptime beyond standard framework capabilities (e.g., 50,000 requests/sec with P99 < 50ms).
3. **Strict Compliance & Legal Mandates:** Legal regulations dictating system physical topology (e.g., RBI Data Localization requiring Indian financial data to remain physically within India; HIPAA requiring end-to-end data encryption).
4. **Broad Structural / Multi-Subsystem Impact:** A requirement that cannot be contained within a single class or service; it cuts across auth, payment, database, and logging simultaneously (e.g., end-to-end auditability).

---

### 2. Elicitation Frameworks: Quality Attribute Workshop (QAW - 8 Steps) & PALM
Stakeholders rarely state ASRs upfront. They say: *"Make the system fast, secure, and easy to use."* Architects use proven SEI elicitation frameworks to extract concrete ASRs:

#### Pedigreed Attribute Logic Method (PALM)
Connects high-level **Business Goals** to concrete **Quality Attribute Scenarios**.
* *Business Goal:* "Expand our FinTech payments platform into the European Union within 6 months to capture market share."
* *Derived ASR:* "Architecture must enforce GDPR data residency, user right-to-be-forgotten deletion hooks, and localized EU banking gateway connectors."

#### Quality Attribute Workshop (QAW) — The 8 Steps
A collaborative, stakeholder-driven elicitation workshop facilitated by architects:

```text
┌────────────────────────────────────────────────────────────────────────┐
│                     THE 8 STEPS OF THE SEI QAW                         │
├────────────────────────────────────────────────────────────────────────┤
│ Step 1: QAW Presentation & Introductions                               │
│         Facilitator introduces the QAW process and objectives.         │
├────────────────────────────────────────────────────────────────────────┤
│ Step 2: Business / Mission Presentation                                │
│         Project sponsor/manager presents business drivers and context. │
├────────────────────────────────────────────────────────────────────────┤
│ Step 3: Architecture Plan Presentation                                 │
│         Lead architect presents existing or proposed architectural view│
├────────────────────────────────────────────────────────────────────────┤
│ Step 4: Identification of Architectural Drivers                        │
│         Team catalogs key business drivers and quality attributes.     │
├────────────────────────────────────────────────────────────────────────┤
│ Step 5: Scenario Brainstorming                                         │
│         All stakeholders brainstorm raw quality attribute scenarios.   │
├────────────────────────────────────────────────────────────────────────┤
│ Step 6: Scenario Consolidation                                         │
│         Similar and overlapping scenarios are merged together.         │
├────────────────────────────────────────────────────────────────────────┤
│ Step 7: Scenario Prioritization                                        │
│         Stakeholders vote (dot-voting) to identify top-priority items. │
├────────────────────────────────────────────────────────────────────────┤
│ Step 8: Scenario Refinement                                            │
│         Top scenarios are formalized into standard 6-part SEI format. │
└────────────────────────────────────────────────────────────────────────┘
```

---

### 3. The Utility Tree Masterclass (Notation, Structure & Prioritization)

> 💡 **CRITICAL EXAM CONCEPT (Directly Asked in EC-2 Question 3b):**
> The Utility Tree is an Software Engineering Institute (SEI) tool used in Attribute-Driven Design (ADD) and ATAM to translate vague business goals into prioritized, quantifiable quality attribute scenarios.

#### Hierarchical Structure & Notation:
The Utility Tree has four distinct hierarchical levels:
1. **Level 0 (Root Node — `Utility`):** The overall goodness, health, and operational success of the software system.
2. **Level 1 (`Quality Attributes`):** High-level quality categories (e.g., Performance, Availability, Security, Modifiability).
3. **Level 2 (`Attribute Refinements` / Sub-attributes):** Specific aspects of that quality (e.g., Under Performance: *Latency*, *Throughput*; Under Security: *Data Confidentiality*, *User Authentication*).
4. **Level 3 (`Quality Attribute Scenarios`):** Concrete, measurable 6-part operational scenarios.

```text
Level 0 (Root)       Level 1 (QA)       Level 2 (Refinement)       Level 3 (Scenario & Rank)
─────────────────────────────────────────────────────────────────────────────────────────────
                                    ┌─ Flash Sale Latency ──────> Scenario 1: [P99 <200ms] (H, H)
                 ┌── Performance ───┤
                 │                  └─ Batch Ingestion ─────────> Scenario 2: [1M logs/5min] (M, M)
                 │
                 │                  ┌─ Node Crash Failover ─────> Scenario 3: [Failover <3s] (H, H)
UTILITY ─────────┼── Availability ──┤
                 │                  └─ Zero Data Loss ──────────> Scenario 4: [RPO=0 (Recovery Point Objective = zero data loss) on DB] (H, M)
                 │
                 │                  ┌─ SQL Injection Defense ───> Scenario 5: [100% blocked] (H, H)
                 └── Security ──────┤
                                    └─ Audit Logging ───────────> Scenario 6: [Signed logs] (M, L)
```

#### The Prioritization Matrix: $(Importance, Difficulty)$
Every scenario at the leaf of the tree is assigned a 2-dimensional priority coordinate:
* **Dimension 1: Importance to Business / Customer:** High $(H)$, Medium $(M)$, or Low $(L)$.
* **Dimension 2: Difficulty / Technical Risk to Architecture:** High $(H)$, Medium $(M)$, or Low $(L)$.

```text
                      THE (H, M, L) PRIORITIZATION MATRIX
                   ┌───────────────────────┬───────────────────────┐
                   │ (H, M)                │ (H, H)                │
                   │ High Business Value,  │ THE CORE ARCHITECTURE │
                   │ Moderate Risk.        │ Top priority; shapes  │
    IMPORTANCE     │ Must architect early. │ the fundamental design│
    TO BUSINESS    ├───────────────────────┼───────────────────────┤
                   │ (L, L)                │ (M, H)                │
                   │ Low Value, Low Risk.  │ High Risk, Modest Val.│
                   │ Defer / routine coding│ Re-evaluate or find   │
                   │ during sprints.       │ simpler architecture. │
                   └───────────────────────┴───────────────────────┘
                               DIFFICULTY / TECHNICAL RISK
```

> **Exam Rule of Thumb:** Architectures are designed to satisfy the **$(H, H)$** scenarios first. Scenarios marked $(H, H)$ become the primary inputs into Attribute-Driven Design (ADD) and the focal point of Architecture Tradeoff Analysis Method (ATAM) evaluations.

---

### 4. Attribute-Driven Design (Attribute-Driven Design (ADD 3.0)) 7-Step Method
ADD is a systematic, recursive design method developed by the SEI to create software architecture from Architecturally Significant Requirements (ASRs):

```text
 Step 1: Confirm Requirements (Gather ASRs, constraints, and Utility Tree)
    │
 Step 2: Select System Element to Decompose (Start with entire system at Step 1)
    │
 Step 3: Identify Candidate Architectural Drivers (Filter top (H,H) scenarios)
    │
 Step 4: Choose Design Concepts (Patterns, tactics, frameworks satisfying drivers)
    │
 Step 5: Instantiate Architectural Elements & Allocate Responsibilities
    │
 Step 6: Define Interfaces and Structural Relationships
    │
 Step 7: Verify and Refine Architecture Against ASRs (Repeat recursively)
```

---

# Module 4: Software Structures, Views & Kruchten's 4+1 Model (Lecture 6)

### 1. Structures vs. Views (The Fundamental Law)

> **The Fundamental Law:** *Architects design structures; they document views. You change a structure by editing and deploying code; you change a view by updating diagrams and documentation.*

* **Structure:** The objective reality of the system as it physically exists (code files stored in Git repositories, active processes executing in server RAM, network cables connecting server racks).
* **View:** A documented representation or diagram of a specific slice of reality created for a specific stakeholder to address specific concerns.
* **Analogy (Building Architecture):** An architect does not show electrical wiring blueprints to an interior decorator, nor plumbing schematics to a structural foundation engineer. Each blueprint is a *View* of the same underlying physical *Structure*.

---

### 2. The 3 Software Engineering Institute (SEI) Structure Families (Module, C&C, Allocation)
Clements, Bass, et al. (*Documenting Software Architectures: Views and Beyond*) group all software structures into **3 Standard Families**:

```text
┌────────────────────────────────────────────────────────────────────────┐
│                      THE 3 SEI STRUCTURE FAMILIES                      │
├────────────────────┬────────────────────┬──────────────────────────────┤
│ 1. Module Family   │ 2. Component &     │ 3. Allocation Family         │
│                    │    Connector (C&C) │                              │
├────────────────────┼────────────────────┼──────────────────────────────┤
│ What is it?        │ What is it?        │ What is it?                  │
│ Code implementation│ Runtime execution  │ Mapping software to          │
│ units (static).    │ entities (dynamic).│ non-software hardware & org. │
├────────────────────┼────────────────────┼──────────────────────────────┤
│ Elements:          │ Elements:          │ Elements:                    │
│ Classes, packages, │ Processes, threads,│ Servers, VMs, disk volumes,  │
│ layers, modules.   │ databases, caches. │ engineering teams.           │
├────────────────────┼────────────────────┼──────────────────────────────┤
│ Relations:         │ Relations:         │ Relations:                   │
│ "Is-a", "Uses",    │ RPC calls, HTTP,   │ "Allocated to", "Hosted on", │
│ "Part-of".         │ Message queues.    │ "Maintained by".             │
├────────────────────┼────────────────────┼──────────────────────────────┤
│ Primary QA:        │ Primary QA:        │ Primary QA:                  │
│ Modifiability,     │ Performance,       │ Availability, Cost,          │
│ Reusability.       │ Scalability.       │ Infrastructure Security.     │
└────────────────────┴────────────────────┴──────────────────────────────┘
```

---

### 3. Philippe Kruchten's 4+1 View Model Deep Dive

> 💡 **CRITICAL EXAM CONCEPT (Directly Asked in EC-2 Question 2c):**
> Published by Philippe Kruchten in 1995 (IEEE Software), the 4+1 View Model organizes software architecture documentation into four distinct views tailored to specific stakeholders, unified by a central "+1" Scenarios view.

```text
                        KRUCHTEN'S 4+1 VIEW MODEL
                     ┌─────────────────────────────┐
                     │         LOGICAL VIEW        │
                     │  Audience: End-Users / BAs  │
                     │  Focus: Functionality,      │
                     │  Domain Entities, Classes   │
                     └──────────────┬──────────────┘
                                    │
    ┌───────────────────────────┐   │   ┌───────────────────────────┐
    │     DEVELOPMENT VIEW      │   │   │       PROCESS VIEW        │
    │  Audience: Programmers    │   │   │  Audience: Integrators/SRE│
    │  Focus: Packages, Builds, │───┼───│  Focus: Concurrency,      │
    │  Libraries, Code Org      │   │   │  Threads, Scalability, IPC│
    └───────────────────────────┘   │   └───────────────────────────┘
                                    │
                               ┌────┴─────┐
                               │ +1 VIEWS │
                               │ SCENARIOS│
                               └────┬─────┘
                                    │
                     ┌──────────────┴──────────────┐
                     │        PHYSICAL VIEW        │
                     │  Audience: System Engineers │
                     │  Focus: Hardware Nodes,     │
                     │  Cloud VMs, Network Topo    │
                     └─────────────────────────────┘
```

#### Detailed Breakdown of the 5 Elements:
1. **Logical View (The "What"):**
   * *Target Stakeholder:* End-users, business analysts, domain experts.
   * *Architectural Concern:* Functional requirements. What services must the system provide to users?
   * *Structural Elements:* Classes, packages, domain models, interfaces.
   * *Representational Diagrams:* UML Class diagrams, Object diagrams, State Machine diagrams.
2. **Process View (The "How it Runs"):**
   * *Target Stakeholder:* System integrators, performance engineers, SREs.
   * *Architectural Concern:* Non-functional runtime characteristics: concurrency, parallelism, process lifecycles, throughput, latency, thread synchronization, and Inter-Process Communication (IPC).
   * *Structural Elements:* OS processes, worker threads, async queues, task schedulers.
   * *Representational Diagrams:* UML Activity diagrams, Sequence diagrams, Communication diagrams.
3. **Development / Implementation View (The "How it is Built"):**
   * *Target Stakeholder:* Software developers, build release managers.
   * *Architectural Concern:* Software module organization, source code management, build dependencies, libraries, compiler constraints.
   * *Structural Elements:* Source code files, JAR/npm packages, layers, subsystems.
   * *Representational Diagrams:* UML Component diagrams, Package diagrams.
4. **Physical / Deployment View (The "Where it Lives"):**
   * *Target Stakeholder:* Systems engineers, infrastructure architects, cloud DevOps.
   * *Architectural Concern:* Non-functional deployment characteristics: mapping software onto hardware execution environments, server topology, network firewalls, geographic replication.
   * *Structural Elements:* Bare-metal servers, AWS EC2 instances, Kubernetes pods, routers, load balancers.
   * *Representational Diagrams:* UML Deployment diagrams, Network topology architecture maps.
5. **The "+1" Scenarios / Use Cases (The "Unifying Glue"):**
   * *Target Stakeholder:* All stakeholders.
   * *Architectural Concern:* Validation, consistency checking, and driving architectural synthesis.
   * *Structural Elements:* High-priority User Stories, Use Cases, and SEI Quality Attribute Scenarios.
   * *Why it is "+1":* It does not introduce new structural components; instead, it traces an end-to-end user transaction across the other 4 views to verify that the design works holistically.

---

### 4. How Quality Attributes Integrate Kruchten's Views
A common exam question asks: *What role do quality attributes play in integrating Kruchten's views?*

* **The Integration Mechanism:** A single Quality Attribute Requirement cannot exist in isolation within one view; it forces coordinated structural decisions across **all four views**.
* **Concrete Example (Zero Transaction Loss under Peak Load):**
  * *Logical View:* Designs an idempotent `PaymentOrder` class with state transition methods (`PENDING` $\to$ `PROCESSED`).
  * *Process View:* Allocates payment processing to a dedicated asynchronous worker thread pool decoupled via a persistent Kafka message queue to ensure incoming surges don't crash the server (Performance & Availability).
  * *Development View:* Enforces a strict package boundary ensuring `PaymentService` does not directly depend on UI classes, encapsulated in a decoupled `.jar` artifact (Modifiability).
  * *Physical View:* Deploys payment microservices across multi-region AWS Availability Zones with automated cross-zone database replication (Availability & Fault Tolerance).
  * *+1 Scenario:* Traces the execution: *"Customer clicks pay $\to$ Logical entity created $\to$ Process thread enqueues event $\to$ Development jar executes $\to$ Physical node persists state."* Quality attributes act as the architectural thread stitching all four views into a single unified reality.

---

# Module 5: Layered Architectures & Architecture Evaluation (ATAM) (Lecture 7)

### 1. The Layered Pattern: Strict vs. Relaxed Layering
The Layered Pattern is the most widely adopted architectural pattern for enterprise software:

```text
            STRICT LAYERING                       RELAXED (OPEN) LAYERING
        ┌─────────────────────┐                   ┌─────────────────────┐
        │ Presentation Layer  │                   │ Presentation Layer  │
        └──────────┬──────────┘                   └──────────┬──────────┘
                   │ Calls N-1                               │ Calls N-1, N-2, N-3
        ┌──────────▼──────────┐                   ┌──────────▼──────────┐
        │   Business Layer    │                   │   Business Layer    │
        └──────────┬──────────┘                   └──────────┬──────────┘
                   │ Calls N-1                               │
        ┌──────────▼──────────┐                   ┌──────────▼──────────┐
        │   Services Layer    │                   │   Services Layer    │
        └──────────┬──────────┘                   └──────────┬──────────┘
                   │ Calls N-1                               │
        ┌──────────▼──────────┐                   ┌──────────▼──────────┐
        │     Data Layer      │                   │     Data Layer      │
        └─────────────────────┘                   └─────────────────────┘
```

* **Strict Layering:** Layer $N$ can *only* invoke the immediate layer directly below it ($N-1$).
  * *Advantage:* Maximum modifiability and loose coupling. Replacing Layer $N-1$ has zero impact on Layer $N+1$.
  * *Disadvantage:* **The Sinkhole Effect.** Requests simply pass through intermediate layers without adding business logic, creating unnecessary latency and CPU serialization overhead.
* **Relaxed (Open) Layering:** Layer $N$ can invoke any layer below it (e.g., Presentation can directly read from the Data Layer for read-only reports).
  * *Advantage:* Higher performance; avoids intermediate boilerplates for simple queries.
  * *Disadvantage:* Tight coupling; breaks encapsulation; architectural erosion easily spreads.

---

### 2. Key Architectural Techniques Across the 4 Layers

```text
┌────────────────────────────────────────────────────────────────────────┐
│             ARCHITECTURAL TECHNIQUES BY LAYER (LECTURE 7)              │
├────────────────────┬───────────────────────────────────────────────────┤
│ Layer              │ Prominent Architectural Techniques                │
├────────────────────┼───────────────────────────────────────────────────┤
│ Presentation Layer │ • Caching static UI assets                        │
│                    │ • AJAX for asynchronous partial DOM re-rendering  │
│                    │ • Client-side input validation and masking        │
├────────────────────┼───────────────────────────────────────────────────┤
│ Business Layer     │ • Application Façade (simplifying subsystem APIs) │
│                    │ • Session Management (stateless tokens / Redis)   │
│                    │ • Workflow Engines / Rules Engines (Modifiability)│
│                    │ • Aspect-Oriented Design (Aspect-Oriented Programming (AOP) for cross-cutting concerns like logging)  │
├────────────────────┼───────────────────────────────────────────────────┤
│ Data Layer         │ • Database Connection Pooling (resource reuse)    │
│                    │ • Read Replicas / Caching (Performance)           │
│                    │ • Object-Relational Mapping (Object-Relational Mapping (ORM like Hibernate))     │
│                    │ • Parameterized SQL Queries (SQLi Prevention)     │
│                    │ • ACID Database Transactions (Data Integrity)     │
├────────────────────┼───────────────────────────────────────────────────┤
│ Services Layer     │ • API Façades for external partner integrations   │
│                    │ • Idempotency tokens (handling duplicate retries) │
│                    │ • Sequence number ordering for packets            │
│                    │ • Dead-Letter Queues & Circuit Breakers           │
└────────────────────┴───────────────────────────────────────────────────┘
```

#### Detailed Examination of Crucial Techniques:
* **Application Façade:**
  * *Intent:* Provide a unified, simplified, higher-level interface to a complex set of interfaces in a subsystem.
  * *Example:* A client calling a `FlightBookingFacade.bookFlight(details)` instead of having to orchestrate calls to `ScheduleService`, `SeatInventoryService`, `PricingEngine`, and `LoyaltyService` independently.
* **Session Management:**
  * *The Problem:* The HTTP protocol is inherently stateless, but modern web applications require tracking user state across multiple sequential requests.
  * *Stateless Session Beans / Redis Store:* Instead of pinning session state inside server RAM (which breaks horizontal scaling and sticky sessions), session state is stored in a centralized, blazing-fast distributed cache (Redis) or encoded inside cryptographically signed client-side JWT tokens.
* **Aspect-Oriented Design (Aspect-Oriented Programming (AOP - Separating Cross-Cutting Concerns)) for Cross-Cutting Concerns:**
  * *Intent:* Encapsulate logic that cuts across multiple functional layers (e.g., Logging, Instrumentation, Security checks, Transaction clear boundary line) into modular *Aspects*.
  * *Benefit:* Eliminates boilerplate code duplication; ensures that auditing and logging are consistently applied without cluttering core business domain logic.

---

### 3. Real-World Case Studies (From Prof. Jabbal's Lecture 7)

#### Case 1: Aadhaar Citizen Registration Dropdown Optimization
* **The Problem:** The Aadhaar registration portal screen contains nested dropdowns for *"State"*, *"District"*, and *"Town"*. Loading the page experiences terrible latency due to the massive dataset of all Indian administrative zones.
* **Architectural Solution:**
  1. *Presentation Layer:* Implement **AJAX** (Asynchronous JavaScript and XML) for dynamic, cascading loading. The page loads instantly with only States; selecting a State asynchronously fetches only its corresponding Districts.
  2. *Data / Business Layer:* Implement **in-memory caching** (e.g., Redis) for administrative state/district metadata on the backend, since geographic boundaries change very infrequently.

#### Case 2: MakeMyTrip Hotel Reservation Integration
* **The Problem:** A hotel reservation system must allow external aggregator applications (MakeMyTrip, Booking.com) to query room availability and book rooms securely without exposing internal database structures.
* **Architectural Solution:** Build a dedicated **Services Layer**.
  * Exposes standardized, contract-driven REST APIs:
    * `getRoomAvailability(fromDate, toDate, roomType) -> AvailableCount`
    * `reserveRoom(guestDetails, roomType, dates) -> ReservationConfirmation`
  * Implements **Idempotency keys** and **rate limiting** to prevent duplicate bookings if the external aggregator encounters network timeouts and retries requests.

#### Case 3: Complex Logistics Shipping Façade
* **The Problem:** A customer placing a shipping container order requires coordinating: (1) Finding the nearest empty container, (2) Finding an available trucking transporter, and (3) Reserving cargo capacity on an ocean container ship.
* **Architectural Solution:** In the **Business Layer**, construct a unified **Shipping Logistics Façade**. The client makes a single call `requestContainerShipment(origin, destination, date)`. The Façade encapsulates the complexity of orchestrating the three separate legacy backend modules.

---

### 4. Architecture Tradeoff Analysis Method (ATAM)
Developed by the SEI (*Bass, Clements, Kazman*, Chapter 21), ATAM is the premier rigorous methodology for evaluating software architectures before implementation.

```text
                        THE 4 PHASES OF THE SEI ATAM
    ┌───────────────────────┬───────────────────────┬───────────────────────┐
    │ Phase 0: Preparation  │ Phase 1: Evaluation   │ Phase 2: Evaluation   │
    │ Logistics, contracts, │ Architectural core    │ Extended stakeholders,│
    │ team formation        │ team (Steps 1–6)      │ consensus (Steps 7–9) │
    └───────────────────────┴───────────────────────┴───────────────────────┘
                                    │
                            ┌───────▼────────┐
                            │ Phase 3: Audit │
                            │ Final report   │
                            │ & action plan  │
                            └────────────────┘
```

#### Why Evaluate Architecture? (The Philosophy)
* **The "Fail Early" Imperative:** Fixing an architectural defect during design costs **1%** of what it costs to fix the same defect after the system is deployed in production.
* **Trade-Off Discovery:** You cannot maximize all quality attributes simultaneously. ATAM forces architects and business leaders to confront hard trade-offs (e.g., increasing Security often degrades Performance).

#### Key ATAM Roles & Responsibilities:
1. **Team Leader:** Manages evaluation logistics, contracts, schedules, and team assembly.
2. **Evaluation Leader:** Runs the sessions, facilitates scenario generation, and keeps discussions on track.
3. **Scenario Scribe:** Records all brainstormed scenarios verbatim on visible boards/screens.
4. **Proceedings Scribe:** Captures the deep rationale, issues, and resolutions into electronic records.

#### The 9 Steps of the ATAM:

```text
┌────────────────────────────────────────────────────────────────────────┐
│                        THE 9 STEPS OF THE ATAM                         │
├────────────────────────────────────────────────────────────────────────┤
│ PHASE 1: EVALUATION TEAM & ARCHITECTURE DECISION MAKERS                │
├────────────────────────────────────────────────────────────────────────┤
│ Step 1: Present the ATAM                                               │
│         Evaluation leader explains the process, roles, and outputs.    │
├────────────────────────────────────────────────────────────────────────┤
│ Step 2: Present Business Drivers                                       │
│         Project manager or client presents business context and goals. │
├────────────────────────────────────────────────────────────────────────┤
│ Step 3: Present Architecture                                           │
│         Lead architect presents architectural approaches, views, styles│
├────────────────────────────────────────────────────────────────────────┤
│ Step 4: Identify Architectural Approaches                              │
│         Evaluation team catalogs architectural patterns & tactics used.│
├────────────────────────────────────────────────────────────────────────┤
│ Step 5: Generate Quality Attribute Utility Tree                        │
│         Team builds utility tree with prioritized (H,M,L) scenarios.   │
├────────────────────────────────────────────────────────────────────────┤
│ Step 6: Analyze Architectural Approaches                               │
│         Architectural approaches are evaluated against top scenarios.  │
├────────────────────────────────────────────────────────────────────────┤
│ PHASE 2: EXTENDED STAKEHOLDER COMMUNITY INVOLVED                       │
├────────────────────────────────────────────────────────────────────────┤
│ Step 7: Brainstorm and Prioritize Scenarios                            │
│         Wider stakeholders brainstorm and vote on operational scenarios│
├────────────────────────────────────────────────────────────────────────┤
│ Step 8: Analyze Architectural Approaches                               │
│         Evaluate remaining high-priority scenarios against architecture│
├────────────────────────────────────────────────────────────────────────┤
│ Step 9: Present Results                                                │
│         Evaluation team presents findings, risks, and trade-offs.      │
└────────────────────────────────────────────────────────────────────────┘
```

#### The 4 Core Outputs of an Architecture Tradeoff Analysis Method (ATAM) Evaluation:
1. **Utility Tree:** Prioritized catalog of quality attribute requirements.
2. **Sensitivity Point:** An architectural decision or parameter that directly affects a specific quality attribute (e.g., *"Database connection pool size is a sensitivity point for Performance"*).
3. **Tradeoff Point:** An architectural decision that affects multiple quality attributes in opposite directions (e.g., *"Encrypting message payloads is a tradeoff point: it improves Security but degrades Performance"*).
4. **Risk vs. Non-Risk:**
   * *Risk:* An architectural decision that may lead to undesirable consequences (e.g., *"Using single-threaded node processes without clustering creates an Availability risk"*).
   * *Non-Risk:* An architectural decision that has been thoroughly evaluated and found to be safe and robust.

---

# Module 6: Architectural Conformance & Software Architecture Reconstruction (SAR) (Lecture 8)

### 1. Architectural Conformance vs. Architectural Drift & Erosion
* **Architectural Conformance:** The state where the implementation code faithfully follows the architectural rules, constraints, styles, and patterns specified by the architect.
* **Architectural Drift:** The unintended divergence of the implemented software from its intended architecture caused by ad-hoc, undocumented modifications during sprints and maintenance.
* **Architectural Erosion:** The severe, widespread throughout the system degradation of architecture over time due to accumulating, unmanaged technical debt—eventually turning the system into an unmaintainable "Big Ball of Mud."
* **Everyday Examples of Architectural Drift (From Prof. Jabbal's CS08):**
  1. *Violating Layer Discipline:* An object in Layer 1 calling an object located in Layer 3 directly, bypassing Layer 2 to deliver a feature faster.
  2. *Bypassing Data Access Layer:* Writing direct inline SQL inside a UI controller or business service instead of going through designated DAOs or ORM entity beans.
  3. *Point-to-Point Messaging Bypass:* Notifying different modules one-by-one with ad-hoc HTTP calls instead of using the company's designated **Publish-Subscribe** message broker.
  4. *Ad-Hoc Logging:* Creating custom database log tables inside catch blocks rather than routing events through the standardized enterprise logging framework (Log4j).

---

### 2. 4 Core Techniques to Ensure Conformance
To keep code and architecture strictly synchronized, architects employ four concrete techniques:

```text
┌────────────────────────────────────────────────────────────────────────┐
│            4 TECHNIQUES TO KEEP CODE & ARCHITECTURE CONSISTENT         │
├────────────────────┬───────────────────────────────────────────────────┤
│ 1. Architecturally │ • Explicitly indicate architectural roles in code │
│    Evident Coding  │   structure, file names, packages, and interfaces │
│    Style           │ • Layered: packages like com.app.presentation,    │
│                    │   com.app.business, com.app.dataaccess            │
│                    │ • Pub-Sub: explicitly mark classes as Publisher   │
│                    │   or Subscriber                                   │
│                    │ • MQ: indicate Producer (insert) vs Consumer (pull│
├────────────────────┼───────────────────────────────────────────────────┤
│ 2. Standardized    │ • Use enterprise frameworks that enforce patterns │
│    Frameworks      │ • Spring MVC: Model (data), View (UI), Controller │
│                    │ • Hibernate: Object-Relational Mapping (ORM) mapping preventing raw SQL       │
│                    │ • AUTOSAR: Standardized automotive ECU architecture│
│                    │ • JMS / DROOLS / Log4j: Pub-sub, rules, logging   │
├────────────────────┼───────────────────────────────────────────────────┤
│ 3. Code Templates  │ • Rigid structural supporting structureing developers must use│
│                    │ • Example: Fault-tolerant Primary/Backup template │
│                    │   (Primary handles event and syncs state to backup;│
│                    │   Backup updates state and handles switchover)    │
├────────────────────┼───────────────────────────────────────────────────┤
│ 4. Documentation & │ • Synchronize architecture documentation at release│
│    Organizational  │ • "No Longer Applicable" Rule: Mark outdated parts│
│    Discipline      │   to preserve trust in the remaining document     │
│                    │ • Onboard new hires on architecture immediately   │
│                    │ • Architectural folder discipline & code reviews  │
└────────────────────┴───────────────────────────────────────────────────┘
```

---

### 3. Architecture & Testing Activities
Architecture directly guides quality assurance, test planning, and system verification:

1. **Prioritizing Test Cases via the Utility Tree:**
   * *Which architectural work product prioritizes test cases?* The **Utility Tree**!
   * Scenarios classified with **(High Business Value, High Architectural Impact)** directly translate into the highest-priority automated test suites.
2. **Creating the Integration Test Plan:**
   * Architecture specifies which modules interact with each other and which modules depend on other modules (`uses` relationships).
   * This identifies exact module integration test paths, interfaces, and boundary-value test suites required.
3. **Designing Architecture to Support Testability Requirements:**
   * **Data Source Switching:** Ability to hot-swap between test datasets and live production databases without modifying business code.
   * **State Rollback:** Architectural capability to roll back test-induced mutations to restore the system to a clean state for subsequent test runs.
   * **Component Replaceability (Test Simulators):** Providing pluggable adapter interfaces so external systems (payment gateways, sensors, third-party government services like Aadhaar) can be replaced with mock simulators during automated testing.

---

### 4. The 4-Stage Software Architecture Reconstruction (SAR) Pipeline
* **Definition:** The reverse-engineering process of analyzing an existing software system's implementation artifacts (source code, executables, execution traces, build scripts) to extract, reconstruct, and document its high-level architectural views.
* > ⚠️ **The Golden Rule:** *Reconstruction is NOT designing a new architecture, and it is NOT modifying an architecture. Reconstruction is reverse engineering to discover what currently exists. You must reconstruct BEFORE you modify, so you don't put your hand into the pan without knowing what is cooking inside.*
* **Purposes of Software Architecture Reconstruction (SAR):**
  1. *Documenting Undocumented Systems:* Understanding systems running for 10–25 years where original docs are lost and authors are gone.
  2. *Legacy Migration:* Safely planning migrations (e.g., Mainframe to Web, or Monolith to Microservices).
  3. *Identifying Reusable Components:* Isolating shared enterprise services (logging, auth, session management).
  4. *Conformance Checking:* Comparing the reconstructed *as-built* architecture against the *as-designed* specifications to identify violations.

```text
┌────────────────────────────────────────────────────────────────────────┐
│           THE 4-STAGE ARCHITECTURE RECONSTRUCTION PIPELINE             │
├────────────────────┬───────────────────────────────────────────────────┤
│ 1. Raw View        │ Extract low-level facts (ASTs, classes, imports,  │
│    Extraction      │ caller-callee relations, DB tables, global data)  │
│                    │ from source code, debug binaries, and traces.     │
├────────────────────┼───────────────────────────────────────────────────┤
│ 2. Database        │ Structure all extracted entities and relationships│
│    Construction    │ into a standardized repository or graph database. │
├────────────────────┼───────────────────────────────────────────────────┤
│ 3. View Fusion &   │ Combine disparate views into unified architectures│
│    Abstraction     │ • View 1 (Static): Source code & build scripts    │
│                    │ • View 2 (Dynamic): Runtime traces & call graphs  │
│                    │ • View 3 (Expert Guidance): Domain grouping rules │
│                    │ Aggregate low-level elements into high-level tiers│
├────────────────────┼───────────────────────────────────────────────────┤
│ 4. Architecture    │ Validate reconstructed elements against structural│
│    Analysis        │ rules (e.g., layer skipping, unauthorized DB calls│
│                    │ JUnit in production). Iterate as needed.          │
└────────────────────┴───────────────────────────────────────────────────┘
```

---

### 5. Real-World Case Study: The 'Vanish' System (ARMIN Tool)
* **System Context:** An SEI technical investigation reconstructing the architecture of a complex production system named 'Vanish'.
* **Tool Used:** **ARMIN** (ARchitecture Reconstruction and MINing).
* **The "White-Noise" View:** When ARMIN initially extracted all raw source code elements and relationships, the visual output was a completely unreadable, dense tangle termed the *"White-Noise View"*.
* **The Aggregation Step:** The reconstruction engineers consulted with domain experts and technical leads to establish grouping criteria, aggregating low-level classes into high-level abstract subsystems.
* **The Architectural Finding:** Analyzing the reconstructed views revealed that **'Vanish' was NOT strictly layered**—exposing hidden, illegal cross-layer calls that had drifted from the original architecture.

---

### 6. Vertical vs. Horizontal Conformance Matrix

```text
┌────────────────────────────────────────────────────────────────────────┐
│               VERTICAL VS. HORIZONTAL CONFORMANCE MATRIX               │
├────────────────────┬─────────────────────┬─────────────────────────────┤
│ Dimension          │ Vertical Conformance│ Horizontal Conformance      │
├────────────────────┼─────────────────────┼─────────────────────────────┤
│ Scope              │ Cross-Tier          │ Intra-Tier                  │
│                    │ (Top-to-Bottom)     │ (Within a single layer)     │
├────────────────────┼─────────────────────┼─────────────────────────────┤
│ Focus              │ Layer boundary      │ Uniformity of standards     │
│                    │ compliance          │ and shared utilities        │
├────────────────────┼─────────────────────┼─────────────────────────────┤
│ Typical Violation  │ UI controller       │ One module using Log4j while│
│                    │ executing direct SQL│ another uses custom SQL log │
├────────────────────┼─────────────────────┼─────────────────────────────┤
│ Automated Tool     │ Structure101,       │ SonarQube, checkstyle,      │
│                    │ Sonargraph (SonarJ) │ static linters              │
└────────────────────┴─────────────────────┴─────────────────────────────┘
```

---

### 7. Automated Analysis Tooling & Real-World Violations
* **Key Reconstruction & Conformance Tools:**
  * **SonarQube ("Sonar" / Community Edition):** Explores all execution paths, defines layers/slices, and flags rule violations automatically in CI/CD pipelines.
  * **Structure101 & Sonargraph (SonarJ):** Advanced package dependency analyzers that detect circular package dependencies and enforce layer strict rules (invariants).
  * **ARMIN & Dali:** SEI workbenches for workbench relation extraction, querying, and view fusion.
  * **DiscoTect (Dynamic Architecture Monitoring Tool):** Dynamic monitoring tool for capturing active runtime component interactions.
* **Classic / Real-World Violations Detected in Production (from Slides):**
  1. *"No portion of the application should depend upon JUnit":* Detected by Sonar when test harnesses are accidentally packaged into production binaries.
  2. *"All database access is supposed to be managed by entity beans":* Detected by DiscoTect (Dynamic Architecture Monitoring Tool) and Sonar when rogue direct JDBC connections bypass entity beans.
* **Modern AI in SAR:** Leveraging LLMs (such as Claude / Cloud Code) to rapidly inspect unfamiliar codebases—extracting active/passive broker queues, failover strategies, and service discovery topologies for large-scale distributed systems.

---

# Module 7: The Master Architectural Trade-Off Playbook

Exam questions consistently test your ability to explain architectural tensions. Use these pre-baked trade-off analyses:

### 1. Usability: Effectiveness vs. Efficiency vs. Satisfaction
* **The Tension:** Maximum *Effectiveness* requires defensive UI (wizards, confirmations, CAPTCHAs, two-step verification). This creates friction, degrading *Efficiency* (takes more time/clicks). Overly aggressive *Efficiency* (1-tap purchases) causes user errors, destroying *Satisfaction*.
* **Architectural Resolution:** **Context-Aware Adaptive Workflows.** Low-value/routine actions use streamlined efficient pathways; high-value/destructive actions insert intentional confirmation friction with clear undo capabilities.

### 2. Security vs. Performance vs. Reliability
* **The Tension:** 
  * Enhancing **Security** (mutual TLS handshakes, payload decryption, deep packet inspection, token verification) introduces CPU overhead and increases message size.
  * This directly degrades **Performance** (higher latency, lower request throughput).
  * In degraded network conditions, the larger cryptographic payloads and latency can cause connection timeouts and connection retry storms, cascading into system failures that compromise **Reliability**.
* **Architectural Resolution:** Session-level caching of cryptographic keys, hardware-accelerated TLS termination at the API Gateway edge, and decoupled asynchronous security auditing.

```text
       SECURITY TACTIC                  PERFORMANCE IMPACT             RELIABILITY IMPACT
  ┌───────────────────────┐            ┌───────────────────┐          ┌───────────────────┐
  │ Strong Encryption     │ ─────────> │ Increased Latency │ ───────> │ Connection        │
  │ (TLS 1.3 + AES-256)   │            │ & CPU Overhead    │          │ Timeouts under    │
  └───────────────────────┘            └───────────────────┘          │ Network Jitter    │
                                                                      └───────────────────┘
```

### 3. Security vs. Usability
* **The Tension:** Enforcing 16-character alphanumeric passwords, mandatory biometric verification every 5 minutes, and sudden session timeouts maximizes Security but alienates users, destroying Usability.
* **Architectural Resolution:** **Risk-Based Authentication (RBA).** Track user context (IP geolocation, device fingerprint). As long as context remains normal, maintain long-lived session tokens (high usability). Only prompt for step-up MFA if an anomaly is detected (e.g., login attempt from a new country).

### 4. Modifiability vs. Performance (The Middle-Layer Slowdown Penalty (Indirection))
* **The Tension:** Maximizing Modifiability requires layers, design patterns, wrappers, and intermediaries (e.g., Presentation $\to$ Façade $\to$ Business $\to$ ORM $\to$ Database). Every boundary adds function call indirection and serialization overhead, penalizing Performance.
* **Architectural Resolution:** Relaxed Layering for latency-critical paths (e.g., read-heavy query bypass), coupled with asynchronous event buses for background modifications.

### 5. Scalability vs. Development Speed / Opportunity Cost
* **The Tension:** Designing a fully decoupled microservices architecture with Kafka, Kubernetes, and distributed multi-region databases ensures massive long-term scalability. However, it requires 12 months of development time and high infrastructure costs. A simple monolithic MVC architecture can be shipped in 6 weeks.
* **The Concept of Opportunity Cost:** Spending months engineering for scale you don't yet have sacrifices immediate market entry, user feedback, and early revenue.
* **Architectural Resolution:** **Modular Monolith.** Build the system with strict in-process module boundaries. It deploys as a single fast-to-ship unit initially, and can be split into microservices later when scale demands it.

### 6. General Systems Trade-Offs (Operations Management Context)
* **Product Availability vs. Inventory Costs (Distribution Networks):**
  * *High Availability:* Maintaining high buffer stock across local regional distribution hubs guarantees immediate customer delivery, but drives holding costs, warehouse rent, and capital lockup through the roof.
  * *Low Cost:* Lean, Just-In-Time (JIT) centralized inventory minimizes holding costs, but exposes the business to stockouts and shipping delays when supply chain shocks occur.
* **Additive Manufacturing (3D Printing) vs. Traditional Mass Production:**
  * *Additive Manufacturing:* Has near-zero setup tooling costs and can produce infinitely complex, customized (person-specific) geometry on demand. However, unit production time is slow and per-unit material cost remains high.
  * *Traditional Tooling (Injection Molding):* Requires massive upfront capital expenditure for molds/tooling (high initial cost), but once created, the marginal cost per unit drops to pennies with blazing speed.

---

# Module 8: Fully Solved Past EC-2 Exam Paper (Model Solutions)

The following are complete, 100% mark-yielding model answers for the **2025–2026 SEM 2 EC-2 Mid-Term Examination**.

---

### Question 1: Model Solution (8 Marks)

#### Part A [4 Marks]: Architecture Definition, Scalability & Maintainability
> **Question:** *How the concept of software architecture as a structure or set of structures comprising software components, their externally visible properties, and relationships among them, impact the maintainability and scalability of a computer-based system? Provide an example of a system where a well-designed software architecture improves its overall performance and adaptability.*

**Model Answer:**

**1. Architectural Foundation & Definition:**
According to Bass, Clements, and Kazman, software architecture is the set of structures comprising software elements, relations among them, and properties of both. This definition establishes that architecture governs not implementation trivia, but the structural boundaries and interaction contracts of a system.

**2. Impact on Maintainability:**
* **Mechanism:** Maintainability depends on isolating changes to prevent cascading side effects. In this definition, components hide internal implementation details behind **externally visible properties** (explicit API contracts).
* **Structural Effect:** By restricting relationships to well-defined interfaces and adhering to the principle of high cohesion and low coupling (e.g., via SEI Module structures), developers can modify, refactor, or upgrade the internal algorithm of a component without altering or recompiling dependent components.

**3. Impact on Scalability:**
* **Mechanism:** Scalability is the ability of a system to handle growing workloads by adding resources.
* **Structural Effect:** By architecting relationships as asynchronous, loosely coupled connectors (e.g., REST over HTTP or message queues) and specifying statelessness as an externally visible property of components, the architecture enables **horizontal scaling**. Multiple identical component instances can be created as an instance behind a load balancer without data race conditions.

**4. Concrete System Example (E-Commerce Platform — Amazon/Shopify Model):**
* *System Context:* An e-commerce system experiencing massive seasonal traffic surges (e.g., Black Friday).
* *Performance Improvement:* The order-processing architecture separates the frontend `Order Placement Component` from the backend `Payment & Inventory Components` via an asynchronous message queue (Connector). Under sudden load spikes (100,000 orders/minute), the frontend instantly accepts orders and returns an immediate response (sub-200ms latency), buffering the tasks in Kafka. Worker components scale out horizontally to drain the queue at their own sustained throughput, preventing system collapse.
* *Adaptability / Maintainability Improvement:* When integrating a new payment provider (e.g., Apple Pay), only the `Payment Connector Module` is modified. Because the externally visible contract between the `Order Service` and `Payment Service` remains unchanged, zero modifications are required in the catalog, cart, or inventory services.

---

#### Part B [4 Marks]: ASRs, Quality Attributes & System Structure Impact
> **Question:** *How do Architecturally Significant Requirements (ASRs) influence the design of a software system's architecture, and what role do quality attributes play in identifying and prioritizing ASRs, providing an example of a scenario where Architecturally Significant Requirements (ASRs) impact the overall system structure?*

**Model Answer:**

**1. Influence of ASRs on Architecture Design:**
* An Architecturally Significant Requirement (ASR) is any requirement that has a profound, shaping effect on a system's high-level structures.
* While routine functional requirements (e.g., adding a button or generating a report) are handled within existing modules, ASRs dictate the selection of fundamental architectural patterns, partitioning of modules, deployment topologies, and hardware infrastructure.

**2. Role of Quality Attributes in Identifying & Prioritizing ASRs:**
* **Identification:** Functional requirements specify *what* the system does, but Quality Attributes (QAs)—such as Availability, Performance, Security, and Modifiability—specify *how well* it must behave. QAs serve as the primary filter to extract ASRs from general requirements backlogs.
* **Prioritization via the Utility Tree:** QAs provide the criteria to rank requirements along two axes: **Business Importance** and **Architectural Risk/Difficulty**. Requirements ranked **$(High, High)$** are prioritized as primary ASRs that must be addressed during initial architectural design iterations.

**3. Concrete Scenario & System Structure Impact:**
* *Scenario:* A FinTech Core Banking Payment System.
* *Functional Requirement:* "System shall transfer money between accounts." *(Non-architectural on its own)*.
* *The Derived ASR (Availability & Data Integrity):* "During peak hours, if the primary database server suffers a catastrophic hardware crash, the system must fail over to a standby replica within 3 seconds with Zero Transaction Loss ($\text{RPO} = 0$, $\text{RTO} < 3\text{s}$)."
* *Impact on Overall System Structure:*
  1. *Database Topology:* Precludes a simple single-instance relational database; forces the adoption of an **Active-Passive Multi-AZ Hot Standby architecture** with synchronous write replication.
  2. *Connectors:* Requires the introduction of a database connection proxy (e.g., AWS RDS Proxy) to handle seamless TCP failover without dropping in-flight client sessions.
  3. *Business Layer:* Forces the implementation of the **Two-Phase Commit (2PC)** or **Saga Pattern** across distributed ledgers to guarantee absolute atomic consistency.

---

### Question 2: Model Solution (8 Marks)

#### Part A [2 Marks]: Usability Triad (Effectiveness, Efficiency, Satisfaction) Trade-Offs in Mobile Applications
> **Question:** *What are the key trade-offs between effectiveness, efficiency, and satisfaction in usability design, and how can designers balance these competing factors to create an optimal user experience in a mobile application?*

**Model Answer:**

**1. The Key Trade-Offs:**
* *Effectiveness vs. Efficiency:* Effectiveness requires ensuring the user completes tasks accurately without errors (demanding multi-step input validation, confirmation modals, and review screens). Efficiency requires completing tasks with minimal time and interactions (demanding 1-tap shortcuts and minimal clicks). Introducing confirmation dialogs increases effectiveness but degrades efficiency.
* *Efficiency vs. Satisfaction:* An interface hyper-optimized for raw efficiency (e.g., dense data tables, keyboard shortcuts) can overwhelm casual users, causing confusion and degrading satisfaction. Conversely, overly simplistic, slow animations increase aesthetic satisfaction initially but frustrate power users seeking efficiency.

**2. Balancing Mechanism in a Mobile Application (e.g., Mobile Banking / UPI App):**
* **Progressive Disclosure & Risk-Tiered Workflows:**
  * For low-risk micro-actions (e.g., paying a daily merchant < $10), prioritize **Efficiency**: 1-tap biometric fingerprint scan with instant dispatch.
  * For high-risk actions (e.g., transferring > $10,000 to an unknown beneficiary), deliberately introduce friction to guarantee **Effectiveness**: mandate full account number re-entry, display a detailed review modal, and require an SMS OTP.
* **Forgiving UI (Undo Patterns):** Provide instantaneous 1-tap execution (maximizing efficiency and satisfaction), but display a prominent 5-second *"Undo"* floating bar (safeguarding effectiveness against accidental taps).

---

#### Part B [2 Marks]: Intersection & Compromise of Security, Communication & Reliability
> **Question:** *How do the Security, Communication, and Reliability views of quality attributes intersect and impact the design of a software system, and provide an example of a scenario where optimizing one view may compromise another.*

**Model Answer:**

**1. Intersection of the Three Views:**
* **Security** governs the protection of data confidentiality, integrity, and authenticity.
* **Communication** governs the bandwidth, protocol latency, and payload throughput between distributed nodes.
* **Reliability** governs the system's ability to maintain continuous operation and fault tolerance under adverse conditions.

**2. Conflict / Compromise Scenario (Connected IoT Automotive Fleet):**
* *The System:* Real-time vehicle telemetry reporting collision alerts to a central traffic controller.
* *Optimizing Security:* The architect enforces end-to-end payload encryption using RSA-4096 and mutual TLS (mTLS) with frequent handshake re-negotiations to prevent spoofing and eavesdropping.
* *The Compromise on Communication & Reliability:*
  * The massive cryptographic handshake and certificate chain drastically increase communication packet size and CPU serialization latency.
  * When vehicles pass through spotty cellular dead-zones (high jitter and packet loss), the heavy mTLS handshake repeatedly times out.
  * The communication channel becomes saturated with connection retry storms, causing telemetry heartbeat packets to drop. The system falsely diagnoses vehicles as crashed, directly degrading **Reliability** and real-time safety response.

---

#### Part C [4 Marks]: Kruchten's 4+1 View Model & Quality Attributes Integration
> **Question:** *How do the different views in Philippe Kruchten's 4+1 architectural model support the identification and analysis of Architecturally Significant Requirements (ASRs) in a software system, and what role do quality attributes play in integrating these views to ensure a comprehensive architecture?*

**Model Answer:**

**1. How Kruchten's 4+1 Views Support ASR Identification & Analysis:**
Kruchten's 4+1 model distributes architectural reasoning across four specialized structural perspectives, driven by a central scenario view:
1. **Logical View (Functionality & Domain Structure):** Analyzes ASRs related to core business abstractions, domain logic, and data structures. It identifies requirements for reusability and semantic integrity.
2. **Process View (Concurrency & Runtime Performance):** Analyzes ASRs concerning execution threads, process boundaries, responsiveness, throughput, and deadlock avoidance. It directly evaluates **Performance** and **Concurrency** ASRs.
3. **Development View (Codebase & Modularity):** Analyzes ASRs concerning package decomposition, third-party library dependencies, build pipelines, and language constraints. It directly evaluates **Modifiability** and **Portability** ASRs.
4. **Physical / Deployment View (Infrastructure & Topology):** Analyzes ASRs concerning server hardware allocation, virtualization, cloud networks, geographic distribution, and failover topologies. It directly evaluates **Availability**, **Disaster Recovery**, and **Security (Firewalls)** ASRs.
5. **+1 Scenarios (Use Cases / ASR Instances):** Serves as the validation engine. Concrete ASR scenarios are traced across the other four views to verify that the collective design satisfies the operational requirements.

**2. Integrating Role of Quality Attributes:**
* Quality attributes serve as the **unifying cross-cutting force** that links the separate views together into a cohesive system.
* *Example of Multi-View Synthesis for an Availability ASR:*
  * A business ASR mandates: *"System must survive cloud zone outage with zero downtime."*
  * *Logical View:* Defines stateless service entities and separates persistent entity state into a distinct repository interface.
  * *Process View:* Implements non-blocking, asynchronous message dispatch to prevent client threads from hanging during failover.
  * *Development View:* Packages services into self-contained, containerizable deployment units (e.g., Docker images) with strict boundary separation.
  * *Physical View:* Deploys these container units across multiple redundant Availability Zones behind an automated health-checking Application Load Balancer.
  * *Conclusion:* Without Quality Attributes, the four views would remain disconnected diagrams; QAs enforce the structural constraints that ensure all views work in harmony.

---

### Question 3: Model Solution (7 Marks)

#### Part A [3 Marks]: Software Architecture Documentation & Quality Attributes
> **Question:** *How does the documentation of software architecture influence the identification and prioritization of Architecturally Significant Requirements (ASRs), and what role does it play in ensuring that the designed system meets the required quality attributes, such as scalability, security, and usability?*

**Model Answer:**

**1. Influence on Identification and Prioritization of ASRs:**
* Architecture documentation records not just structural diagrams, but the underlying **Architectural Rationale** and **Context**.
* It captures the system's business drivers, constraints, and stakeholder concerns (via frameworks like SEI Views and Beyond).
* By formally documenting requirements using standardized structures (such as Quality Attribute Utility Trees and 6-Part Scenarios), documentation forces stakeholders to resolve vague desires (*"make it scalable"*) into prioritized, quantifiable metrics (*"handle 10,000 req/s at P99 < 100ms"*). This prevents the team from misallocating architectural effort on non-critical requirements.

**2. Role in Ensuring the System Meets Quality Attributes:**
1. **Prevents Architectural Drift & Erosion:** As developers write code, documentation acts as the binding contract governing allowed layer interactions, interface specifications, and dependency rules.
2. **Enables Objective Architecture Evaluation:** High-rigor evaluation methods (like ATAM) cannot function without clear architectural documentation. Evaluators trace quality scenarios through documented views to spot structural risks and bottlenecks prior to code deployment.
3. **Guarantees Traceability:** Documentation maps specific architectural tactics (e.g., TLS encryption for Security, database read-replicas for Scalability, client-side caching for Usability) directly to the ASRs they were chosen to satisfy.

---

#### Part B [4 Marks]: Utility Tree Notation, Structure & Design Decisions
> **Question:** *How does the Utility Tree notation facilitate the identification and prioritization of Architecturally Significant Requirements (ASRs) in software architecture, and provide an example of a scenario where the Utility Tree helps to refine quality attributes and drive design decisions.*

**Model Answer:**

**1. The Utility Tree Notation & Structure:**
The Utility Tree is a top-down hierarchical structuring tool used in Attribute-Driven Design (ADD) and ATAM:
* **Level 0 (Root):** **Utility** (The overall goodness and fitness-for-purpose of the software).
* **Level 1 (Quality Attributes):** Broad architectural qualities (e.g., Availability, Security, Performance).
* **Level 2 (Attribute Refinements):** Sub-qualities narrowing the scope (e.g., Under Performance: *Latency*, *Throughput*).
* **Level 3 (ASR Scenarios):** Concrete, measurable 6-part scenarios.
* **Prioritization Coordinates $(B, A)$:** Each leaf scenario is prioritized along two dimensions using High $(H)$, Medium $(M)$, and Low $(L)$:
  * $B$: Importance to the Business / Stakeholder.
  * $A$: Technical Difficulty / Risk to the Architecture.

```text
UTILITY TREE HIERARCHY:
Utility ──┬── Performance ──┬── Query Latency ──────> [P99 <100ms for Catalog Search] (H, M)
          │                 └── Checkout Throughput ─> [10,000 orders/sec without drop] (H, H)
          │
          └── Security ─────┬── Data Protection ────> [AES-256 encryption at rest] (H, L)
                            └── Threat Detection ───> [Detect brute-force in 5 attempts] (M, M)
```

**2. Example Scenario: Driving Architectural Design Decisions:**
* *Context:* A Healthcare Telemedicine Platform.
* *Unrefined Requirement:* "The platform must be secure and fast during video consultations."
* *Refinement via Utility Tree:*
  * *Root:* Utility
  * *QA:* **Performance** $\to$ *Refinement:* **Media Streaming Latency** $\to$ *Scenario:* *"During peak hours (1,000 concurrent patient-doctor calls), video stream latency must remain below 150ms over 4G connections."* $\rightarrow$ **Priority: $(H, H)$**.
  * *QA:* **Security** $\to$ *Refinement:* **HIPAA Patient Privacy** $\to$ *Scenario:* *"All video and audio streams must be end-to-end encrypted; neither ISP nor intermediary servers can decrypt media packets."* $\rightarrow$ **Priority: $(H, H)$**.
* *Design Decisions Driven by the Tree:*
  * Because both scenarios are rated **$(H, H)$**, the architect cannot use standard centralized HTTP/TCP media proxying (which introduces high latency and server-side decryption).
  * *Architectural Decision:* The architect adopts **WebRTC with SRTP (Secure Real-Time Transport Protocol)** utilizing direct peer-to-peer media mesh connections with DTLS encryption. Intermediary STUN/TURN servers are architected strictly for NAT traversal without media decryption, simultaneously satisfying the 150ms latency target and HIPAA compliance.

---

### Question 4: Model Solution (7 Marks)

#### Part A [3 Marks]: Product Availability vs. Inventory Costs in Distribution Networks
> **Question:** *What are the trade-offs between achieving high product availability and minimizing inventory costs in a distribution network, and how might a firm balance these competing objectives to maximize profitability?*

**Model Answer:**

**1. The Fundamental Trade-Off:**
* *High Product Availability:* Requires holding extensive safety stock across multiple decentralized distribution centers located near customer population hubs. This ensures immediate order fulfillment, reduces stockouts, and maximizes customer satisfaction and revenue. However, it exponentially increases **Inventory Holding Costs** (capital lockup, warehousing rent, insurance, handling labor, and obsolescence risk).
* *Minimizing Inventory Costs:* Adopting Lean, Just-In-Time (JIT) principles and centralizing inventory in a single hub minimizes holding costs and eliminates safety stock overhead. However, it increases replenishment lead times, exposes the firm to stockouts during supply chain disruptions, and incurs high expedited shipping costs, risking lost sales and customer churn.

**2. Balancing Strategy to Maximize Profitability:**
* **ABC Product Segmentation & Risk-Pooling:**
  * *Class A Items (High-Velocity / High-Margin):* Decentralize stock across regional distribution centers close to buyers to guarantee high availability ($>98\%$) where margins justify the storage cost.
  * *Class B/C Items (Slow-Moving / Low-Margin / Long-Tail):* Pool inventory in a single centralized national fulfillment warehouse. Ship via reliable express logistics on demand, avoiding wasteful decentralized stock buildup.
* **Predictive Demand Forecasting & Dynamic Safety Stock:** Utilize machine learning models analyzing historical trends, seasonality, and lead times to dynamically adjust safety stock levels, preventing overstocking while buffering against demand spikes.

---

#### Part B [4 Marks]: Manufacturing Complexity vs. Production Costs in Additive Manufacturing
> **Question:** *What are the potential trade-offs between manufacturing complexity and production costs when utilizing additive manufacturing technologies, and how might these trade-offs impact the design and production of person-specific or location-specific products?*

**Model Answer:**

**1. The Trade-Offs (Additive Manufacturing vs. Subtractive/Forming Methods):**
* *Traditional Manufacturing (CNC Machining, Injection Molding):*
  * High upfront fixed tooling and mold costs, but extremely low variable cost per unit at high volumes.
  * **Complexity Penalty:** As geometric complexity increases (e.g., internal lattices, organic curves), tooling and machining costs rise exponentially.
* *Additive Manufacturing (3D Printing):*
  * **"Complexity is Free":** Printing a complex lattice structure costs the exact same in machine time and material as printing a solid block of the same volume. There are zero expensive tooling or mold changeover costs.
  * **The Production Cost Penalty:** High raw material costs (specialized powders/resins), slow build cycle times, and post-processing labor mean that the **marginal unit cost remains relatively flat**. It does not benefit from the massive economies of scale seen in mass production.

**2. Impact on Person-Specific or Location-Specific Products:**
* **Person-Specific Products (e.g., Custom Medical Implants, Dental Aligners, Prosthetics):**
  * *Design Impact:* Eliminates the need for standardized, one-size-fits-all sizing. Patient CT scans are converted directly into custom CAD models with complex organic geometries that integrate seamlessly with human bone tissue.
  * *Production Impact:* Eliminates multi-million-dollar custom tooling. Production is economically viable at a batch size of one ($N = 1$). The high unit printing cost is easily absorbed by the high medical value and personalized clinical outcome.
* **Location-Specific Products (e.g., Remote Military Outposts, Space Stations, Offshore Oil Rigs):**
  * *Design & Supply Chain Impact:* Eliminates the need to maintain massive, expensive inventories of obscure spare parts at remote sites.
  * *Production Impact:* Replaces physical part supply chains with digital blueprint transmission. Technicians download the 3D model and manufacture the exact required component on-site on demand, trading higher per-unit print energy/time for the total elimination of international freight lead times and warehousing costs.

---

# Module 9: High-Yield Flashcard Cheat Sheet & Glossary

### 38 One-Line Exam Definitions (Software Engineering Institute (SEI) Terminology)

1. **Software Architecture:** The set of software structures needed to reason about the system, comprising software elements, relations among them, and properties of both.
2. **Externally Visible Properties:** Assumptions other components can make about an element (contracts, QoS, latency, interfaces), excluding internal implementation details.
3. **Architecturally Significant Requirement (ASR):** A requirement that has a profound, shaping effect on a system’s high-level structures and is expensive to change later.
4. **Quality Attribute (QA):** A measurable, testable property of a system indicating how well it satisfies stakeholder needs beyond raw functionality.
5. **Quality Attribute Scenario:** A 6-part standardized specification: *Source, Stimulus, Artifact, Environment, Response, Response Measure*.
6. **Availability:** The proportion of time a system is fully operational and capable of delivering required services ($\frac{\text{MTBF}}{\text{MTBF} + \text{MTTR}}$).
7. **MTTR (Mean Time to Repair):** The total time required to detect a failure, execute failover, and restore full operational capacity.
8. **Active Redundancy (Hot Standby):** A tactic where redundant nodes process requests concurrently with zero failover delay.
9. **Passive Redundancy (Warm Standby):** A tactic where a primary node periodically checkpoints state to a secondary node that boots upon failure.
10. **Performance:** Timeliness of system response, measured in latency, throughput, and deadline fulfillment.
11. **Security:** The ability of a system to resist unauthorized usage while maintaining service delivery to authorized actors.
12. **Non-Repudiation:** The structural inability of a sender to deny having initiated an action or message.
13. **Modifiability:** The cost and time required to execute changes to software throughout its operational life.
14. **Usability (ISO 9241-11):** The extent to which a system provides *Effectiveness*, *Efficiency*, and *Satisfaction* in a specified context of use.
15. **Effectiveness (Usability):** The accuracy and completeness with which users achieve their goals without catastrophic errors.
16. **Efficiency (Usability):** The resources (time, physical taps, mental effort) expended relative to the completeness of goals.
17. **Satisfaction (Usability):** The subjective comfort, perceived delight, and positive attitude experienced by the user.
18. **Interoperability:** The degree to which two independent systems can syntactically and semantically exchange actionable data.
19. **Testability:** The ease with which a system can demonstrate its faults through automated or manual test execution.
20. **Utility Tree:** A hierarchical tree notation (Utility $\to$ QA $\to$ Refinement $\to$ Scenario) used to prioritize ASRs via $(H,M,L)$ coordinates.
21. **Attribute-Driven Design (ADD):** A 7-step recursive design process decomposing systems based on prioritized quality attribute drivers.
22. **Structure:** The objective, physical reality of code, runtime processes, or hardware nodes as they exist.
23. **View:** A documented representation or model of a specific structural perspective created for a specific stakeholder.
24. **Kruchten’s 4+1 Model:** Architectural documentation organizing views into *Logical*, *Process*, *Development*, and *Physical*, unified by *+1 Scenarios*.
25. **Strict Layering:** An architectural pattern rule where Layer $N$ can only invoke Layer $N-1$, maximizing modifiability at the cost of sinkhole overhead.
26. **Application Façade:** A design technique providing a unified, simplified interface to a complex underlying cluster of subsystem modules.
27. **Aspect-Oriented Design (AOD):** Encapsulating cross-cutting concerns (logging, security, auditing) into modular aspects that cut across functional layers.
28. **ATAM (Architecture Tradeoff Analysis Method):** A 9-step SEI evaluation method evaluating architectures against quality scenarios to discover risks and trade-offs.
29. **Sensitivity Point:** An architectural parameter or decision that directly controls or impacts a specific quality attribute response.
30. **Tradeoff Point:** An architectural decision that impacts multiple quality attributes in opposing directions (e.g., encryption improving security while degrading performance).
31. **Architectural Conformance:** The state where implementation code strictly follows architectural rules, constraints, and layer boundaries.
32. **Architectural Drift:** Unplanned divergence of implementation from architecture caused by ad-hoc, undocumented shortcuts during sprints.
33. **Software Architecture Reconstruction (SAR):** Reverse-engineering architectural views from source code, binaries, and runtime traces of an undocumented or legacy system.
34. **Raw View Extraction:** The initial phase of SAR mining low-level static/dynamic entities (ASTs, files, calls, DB tables) from artifacts.
35. **View Fusion:** Synthesizing disparate static, dynamic, and expert domain views into cohesive, aggregated architectural subsystems.
36. **White-Noise View:** The dense, unreadable initial web of all extracted raw relations before abstraction/aggregation (from the SEI 'Vanish' case study).
37. **Vertical Conformance:** Verifying that communication across top-to-bottom layers strictly respects layer boundaries without illegal skips.
38. **Horizontal Conformance:** Verifying that all components within a single layer adhere to designated conventions, patterns, and shared frameworks.

---

### "Don't Say X, Say Y" Exam Vocabulary Upgrade

| Don't Say (Casual Dev) | Say (Architectural Scholar (Using SEI Terms)) |
| :--- | :--- |
| "Writing good code so it doesn't break" | "Employing fault prevention and fault detection tactics to maximize MTBF" |
| "Making the UI simple" | "Optimizing the ISO 9241-11 Usability Triad (Effectiveness, Efficiency, Satisfaction)" |
| "Putting it into a microservice" | "Decomposing into Component-and-Connector (C&C) runtime structures with asynchronous connectors" |
| "Encrypting passwords" | "Applying Security tactics to preserve confidentiality and authenticate actors" |
| "The diagram of the app" | "A documented Architectural View addressing specific stakeholder concerns" |
| "Listing our requirements" | "Constructing a Quality Attribute Utility Tree prioritized by business value and architectural risk" |
| "Checking if the design is good" | "Conducting an Architecture Tradeoff Analysis Method (ATAM) to identify risks and sensitivity points" |
| "Code getting messy over time" | "Architectural Erosion and Architectural Drift violating documented structural rules" |
| "Rewriting an old app because there's no docs" | "Conducting Software Architecture Reconstruction (SAR) to recover the as-built architecture before modifying" |
| "Checking if devs followed the rules" | "Validating Horizontal and Vertical Architectural Conformance to detect architectural drift" |

---

### The Last 60-Minutes Exam Survival Checklist

1. **Read Every Question Word Carefully:** Look for explicit keywords: *"Trade-off"*, *"Structure"*, *"Kruchten 4+1"*, *"Utility Tree"*, *"Scenario"*.
2. **Budget Your Time Strictly:** **3 minutes per mark.** Never spend 25 minutes on a 3-mark question.
3. **Always Include a Concrete System Example:** Never leave an answer abstract. Always mention an E-Commerce checkout, FinTech payment gateway, Aadhaar citizen portal, or hospital management system.
4. **Draw Clear Visuals:** When asked about Utility Trees or Kruchten 4+1, draw the hierarchical tree or the 5-box quadrant diagram. Evaluators award marks for visual clarity.
5. **State Trade-Offs Explicitly:** Whenever a tactic is proposed, write: *"This improves [Quality Attribute A] by [Mechanism], but incurs a trade-off penalty on [Quality Attribute B] due to [Cause]."*
6. **Use the 6-Part Scenario Template:** If asked to illustrate an ASR or QA, explicitly label: *Source, Stimulus, Artifact, Environment, Response, Response Measure*.
