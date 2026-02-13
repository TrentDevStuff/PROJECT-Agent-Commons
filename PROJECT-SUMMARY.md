---
created: 2026-02-13T23:45:00Z
updated: 2026-02-13T23:45:00Z
type: summary
backlinks:
  - [[EFFORT-Brainstorming-Research/EFFORT]]
  - [[EFFORT-Brainstorming-Research/CROSS-AREA-SYNTHESIS]]
  - [[EFFORT-Unsolved-Problems/EFFORT]]
  - [[EFFORT-Unsolved-Problems/SYNTHESIS]]
  - [[EFFORT-System-Design/EFFORT]]
  - [[EFFORT-System-Design/01-ARCHITECTURE]]
  - [[EFFORT-System-Design/02-FORMAL-MODELS]]
---

# Agent Commons -- Full Project Summary

## The Question

> Everything will change with the introduction of AI. How can we steer that change to make a better world?

Starting from that single question on February 12, 2026, this project has grown into a comprehensive research and design effort: **33 documents, 21,576 lines, 500+ academic sources** -- progressing from broad exploration through hard problem resolution to formal system architecture in two days.

---

## Effort 1: Brainstorming Research

**17 documents | 13,165 lines | 300+ sources | Completed**

The research began with a fundamental observation: every organizational model in history builds **hedges** against human nature -- and every model eventually fails when human nature finds the **cracks**.

### What We Studied

**Area 1 -- Why Organizations Fail (7 docs):** Built a taxonomy of 22 human tendencies (16 negative, 6 positive, 3 root drives). Then applied the hedge-and-crack framework to democracy (majority tyranny, rational ignorance), socialism (calculation problem, power concentration), corporatism (principal-agent, C-suite extraction), capitalism (monopoly, financialization, externalities), and 5 alternative models (kibbutzim, Mondragon, Buurtzorg, Haier, platform cooperatives).

**Area 2 -- How AI Changes Everything (4 docs):** AI reduces coordination costs 30-90% (attacking Coase's rationale for the firm), democratizes knowledge across 7 professions, and enables organizational forms that were previously impossible. But it also creates new capture risks -- whoever controls the AI controls the organization.

**Area 3 -- What's Been Tried (6 docs):** Open-source governance (6 models), GitHub as organizational infrastructure, DAOs (governance innovations but Gini coefficients of 0.97-0.99), platform cooperatives (7 case studies, none at VC scale), mechanism design (QF, matching markets, prediction markets), and academic frameworks (game theory, complexity, AI alignment).

### The Key Finding -- The Minimum Viable Hedge Set

Six hedges that appear across every successful model studied:

1. Small groups (Dunbar scale)
2. Transparent contribution tracking
3. Credible exit (forking with portable reputation)
4. Proportional bounded rewards (floors and ceilings)
5. Plural adversarial monitoring
6. Automatic renewal (sunset clauses, term limits)

### Capitalism's Unique Lesson

Adam Smith's insight -- don't fight the river of human nature, build a waterwheel. Harness self-interest rather than suppress it. The system design takes this seriously.

---

## Effort 2: Unsolved Problems

**5 documents | 4,026 lines | 340+ sources | Completed**

The research identified 12 hard problems where the literature said "no known solution exists." We couldn't design around them -- we had to confront them.

### The 12 Problems, Organized Into 4 Threads

| Thread | Problems | Verdict |
|--------|----------|---------|
| AI Governance | P1: Recursive governance, P7: Legitimacy, P10: Impossibility trade-offs | All manageable. Three-chamber architecture with circular mutual constraint. |
| Identity & Reputation | P2: Sybil resistance, P4: Non-code valuation, P5: Price signals, P6: Concentration | P5 and P6 are the weakest links. Concentration bounding requires continuous active intervention. |
| Economics | P3: Cold-start, P12: Internal competition | Viable but narrow margin. 8% take rate, "come for the AI tool, stay for the commons." |
| Legal & Social | P8: Legal framework, P9: Meaning of work, P11: Purpose decay | Colorado LCA solves legal. Purpose has a ~40-60 year realistic ceiling. |

### The Synthesis Verdict

No dealbreakers. Proceed to system design. But two problems -- price-signal equivalence (P5) and concentration bounding (P6) -- have **invisible failure modes** that could kill the project slowly without anyone noticing. These require continuous monitoring.

**Falsification condition #4** (concentration is structurally inevitable) was **partially triggered** -- every empirical system studied developed extreme concentration. Mathematical countermeasures can change the distribution, but whether they survive governance capture is the recursive question.

---

## Effort 3: System Design

**4 documents | 4,154 lines | Phases 1-3 Complete**

The formal architecture specification, grounded in everything the research found.

### 01-ARCHITECTURE (1,135 lines)

The master specification. Six layers, each with exact mechanisms:

| Layer | What It Does | Key Mechanisms |
|-------|-------------|----------------|
| Constitutional Foundation | Rules that constrain everything else | 14 principles in 3 priority tiers, supermajority amendments, 5-year sunset clauses |
| Governance | Decision-making | Three chambers: AI Engine (~90%), Sortition Assembly (~8%), Community Referendum (~2%). Four-tier escalation ladder. |
| Reputation & Identity | Know who people are and what they've done | Layered Sybil resistance, 6-dimension reputation with time decay, five-mechanism concentration bounding |
| Economic Model | How value flows | 8% take rate floor, quadratic funding, progressive pricing, 24-month pilot budget |
| Coordination & Work | How work gets done | Forg lifecycle (form -> deliver -> dissolve/fork), AI matching, PR model beyond code |
| Meta-Governance | System governing itself | Adversarial monitoring, 7 early warning signals, 6 purpose-renewal mechanisms |

Every mechanism maps to specific human nature hedges. Every hedge has a documented remaining crack. Every crack has monitoring.

### 02-FORMAL-MODELS (1,067 lines)

The math. 19 formal propositions + 1 theorem.

- Cooperation is Nash equilibrium AND evolutionarily stable under the hedge set
- Safe parameter region for concentration bounding: time-decay lambda in [0.015, 0.025]/month, caps at 10x median, UBR at 10% of peak
- Counterfactual: the bounding stack would compress real-world DAO Gini from 0.99 to an estimated 0.3-0.5

### 03-AI-ALIGNMENT-CONTRIBUTIONS (807 lines)

Two interrelated frameworks.

- **Multi-principal AI alignment** extending Constitutional AI to organizational governance. 3+ independent AI providers in adversarial relationship. Recursive governance solved through circular mutual constraint (no final authority -- same answer as constitutional democracy).
- **Three-signal contribution attribution:** team-outcome + AI quality assessment + market signals. Anti-gaming design with Goodhart Cascade defense.

### 04-SIMULATIONS-EXPERIMENTS (1,145 lines)

How to test all of this.

- **3 simulation specs:** Agent-based model with 7 human-nature archetypes, evolutionary dynamics across competing commons, and 6 attack scenarios (Sybil, governance capture, free-rider infiltration, fork-and-drain, flash governance, tribal takeover)
- **5 experiment protocols:** Governance legitimacy RCT (120-160 participants, crossover design), reputation gaming red team, Forg formation trial, constitutional AI comparison, take-rate sensitivity
- **Estimated cost:** $600K-$1.1M over 30 months for a 200-person pilot

---

## The Honest Assessment

### What the Design Gets Right

- Grounded in 500+ sources, not wishful thinking
- Every mechanism has empirical precedent (pieces work; the combination is untested)
- Mathematical foundations prove cooperation is sustainable under specific conditions
- Built-in falsification -- designed to discover failure, not confirm success

### What Remains Uncertain

- Whether the price-signal hybrid produces information density comparable to market prices (P5 -- weakest link)
- Whether concentration bounding survives governance capture attempts over 5-10 years (P6 -- strongest falsification evidence)
- Whether the economics actually work at the narrow margins identified (P3 -- 8% take rate with thin surplus)
- Whether any of this scales beyond 200 people

### The Recursive Questions No Thread Solved

- **Who governs the governors?** (Circle, not line)
- **Who bounds the bounders?** (Constitutional protection -- but constitutions can be amended)
- **Who renews the renewers?** (Convention -- but conventions require motivated participants)
- **Who prices the price signals?** (Governance -- but governance needs price signals)

The honest conclusion: these recursions don't have terminal answers. They have dynamic equilibrium answers -- the system works as long as the circles keep spinning. This is the same answer constitutional democracy gives. It has worked imperfectly for 237 years.

---

## Falsification Conditions

5 conditions under which the project should be abandoned or pivoted:

1. AI capability plateaus (undermines the transaction-cost argument)
2. Human nature is not the primary failure mode (wrong design focus)
3. AI governance is fundamentally illegitimate (premise fails)
4. **Concentration is structurally inevitable** -- partially triggered; requires monitoring
5. Transition costs exceed benefits (not worth building)

---

## What's Next

**Phase 4: Build the prototype.** The design is specific enough to implement. The 200-person pilot exists to test empirically what the theory can only conjecture. Six minimum viable requirements must be demonstrated before scaling.

**Phase 5: Scale if warranted.** Federation architecture, domain expansion beyond software, legal entity establishment.

The research concluded: *"The path forward is not advocacy but experimentation."*
