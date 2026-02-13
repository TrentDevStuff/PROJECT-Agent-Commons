---
type: effort
project: agent-commons
effort_id: EFFORT-System-Design
status: in_progress
priority: high
created: 2026-02-13T04:00:00Z
updated: 2026-02-13T23:00:00Z
linked_goal: G12.3
owner: Trent Peterson
progress: 72%
depends_on:
  - EFFORT-Brainstorming-Research
  - EFFORT-Unsolved-Problems
---

# EFFORT: System Design — Human-Nature-Proof, LLM-Orchestrated Organization

## Purpose

Design an organizational system that hedges against the full taxonomy of human nature failures identified in the research, leverages LLM orchestration as a governance and coordination mechanism, and capitalizes on proven mechanisms from open-source, mechanism design, cooperative economics, and complexity theory.

**Design Constraint:** This is not about proving the Agent Commons concept right. It's about designing the best possible system the evidence supports — which may look very different from the initial concept.

**Foundation:** This effort builds directly on the findings from [[EFFORT-Brainstorming-Research]], specifically:
- [[CROSS-AREA-SYNTHESIS]] — The unified assessment across all 16 research documents
- [[01-organizational-failures/SYNTHESIS]] — 10 evidence-based design principles
- [[01-organizational-failures/HUMAN-NATURE-TAXONOMY]] — 16 negative + 6 positive human tendencies
- [[03-models-and-precedents/PREDICTION-MARKETS-MECHANISM-DESIGN]] — 6-layer incentive architecture
- [[02-ai-driven-change/SELF-ORGANIZING-TEAMS]] — 8 infrastructure layers

## Design Tasks

### Phase 1: Formal Architecture (Theoretical Foundation)

- [x] **1.1 Define the 6-Layer System Architecture**
  - Formalize the unified framework from [[CROSS-AREA-SYNTHESIS]] Section 3
  - Layer 1: Constitutional Foundation (values, constraints, amendment process)
  - Layer 2: Governance (bicameral model, plural AI, dispute resolution)
  - Layer 3: Reputation and Identity (multi-dimensional, Sybil-resistant, time-decaying)
  - Layer 4: Economic Model (QF allocation, matching markets, take rate, extraction bounds)
  - Layer 5: Coordination and Work (Forg formation, PR model, forking, quality assurance)
  - Layer 6: Meta-Governance (adversarial monitoring, sunset clauses, constitutional amendment)
  - For each layer: specify exact mechanisms, map to human nature hedges, identify remaining cracks

- [x] **1.2 Formal Game-Theoretic Model**
  - Define agents, strategies, payoffs, and equilibria for the Agent/Forg/Commons system
  - Model cooperation vs. defection under proposed mechanisms (QF, matching, reputation)
  - Identify conditions under which cooperation is Nash equilibrium
  - Test whether the minimum viable hedge set shifts equilibria toward cooperation
  - Apply evolutionary game theory (Axelrod conditions: repeated interaction, recognition, low termination probability, punishment)

- [x] **1.3 Multi-Principal AI Alignment Framework**
  - Extend Anthropic's Constitutional AI to handle multiple competing principals
  - Define what "fair" means when Arrow's impossibility theorem applies — which properties to sacrifice
  - Design plural AI governance architecture (multiple models, different providers, adversarial relationships)
  - Address the recursive governance problem: who governs the AI that governs the system?
  - Define constitutional constraints the AI cannot override

- [x] **1.4 Power-Law Bounding Theory**
  - Develop mathematical conditions for bounding reputation/influence concentration
  - Extend Barabasi/Albert preferential attachment with countermeasures (time-decay, QV weighting, caps)
  - Define the threshold below which concentration does not enable governance capture
  - Test against empirical data from open-source, DAOs, and platform cooperatives

- [x] **1.5 Non-Code Contribution Framework**
  - Design a value attribution system for work that is not "code-shaped"
  - Address design, strategy, mentoring, community-building, relationship management
  - Combine peer assessment, AI quality evaluation, market signals, and outcome tracking
  - Ensure the system does not systematically undervalue its most important inputs (per [[CROSS-AREA-SYNTHESIS]] Section 4.3, Gap #4)

### Phase 2: Simulation & Stress Testing

- [x] **2.1 Agent-Based Model with Human Nature Parameters**
  - Simulate the system with agents exhibiting tendencies from the [[01-organizational-failures/HUMAN-NATURE-TAXONOMY|taxonomy]]
  - Power-seeking agents, free-riders, tribal coalitions, status-seekers, self-deceivers
  - Set tendency rates from empirical data (psychology/behavioral economics literature)
  - Test whether proposed hedges maintain cooperation or system degrades to known failure modes
  - Identify which hedge failures are most catastrophic

- [x] **2.2 Evolutionary Dynamics Simulation**
  - Simulate multiple Agent Commons instances competing and evolving over time
  - Do successful instances converge on similar governance structures?
  - Do power-law dynamics inevitably concentrate reputation?
  - Does the fork mechanism discipline governance or fragment into nonviable pieces?
  - Test the "barbell" hypothesis: does the system trend toward very large + very small, hollowing out the middle?

- [x] **2.3 Attack Vector Stress Testing**
  - Coordinated Sybil attacks on reputation and QF mechanisms
  - AI governance capture attempts (training data poisoning, provider collusion)
  - Free-rider infiltration at scale (sophisticated low-quality contributions)
  - Extractive fork-and-drain strategies (fork, extract value, abandon)
  - Flash-loan-style governance attacks (temporary reputation accumulation for governance votes)
  - Tribal coalition takeover scenarios

### Phase 3: Critical Experiments Design

- [x] **3.1 AI Governance Legitimacy Experiment**
  - 50-200 participants, real resource allocation decisions
  - Compare AI governance with human committee governance (matched control)
  - Measure: perceived legitimacy, satisfaction, compliance, exit rate over 6-12 months
  - Key question: Does acceptance increase or decrease with experience?

- [x] **3.2 Reputation Gaming Resistance Experiment**
  - Deploy multi-signal reputation system in a real commons
  - Introduce monetary incentives proportional to reputation
  - Monitor for gaming behavior over 6-12 months
  - Iterate on gaming resistance designs
  - Key question: Are AI-enhanced multi-signal systems qualitatively more resistant or just temporarily harder to game?

- [x] **3.3 Forg Formation Dynamics Experiment**
  - Real project-based work with three team formation modes: AI-matched, self-selected, random
  - 50+ teams across multiple project types
  - Measure: output quality, participant satisfaction, team dynamics, dissolution patterns
  - Key question: Does AI matching outperform self-selection for temporary teams?

- [x] **3.4 Constitutional AI Governance Experiment**
  - Define 10-15 organizational principles as constitution
  - Multiple AI systems trained on constitution make governance decisions
  - Compare with human committee decisions on same cases
  - Measure: perceived fairness, consistency, alignment with stated values
  - Key question: Can constitutional AI scale from individual alignment to organizational governance?

- [x] **3.5 Sustainability Economics Experiment**
  - Small-scale commons with real economic activity
  - Test multiple revenue models (transaction fees, subscriptions, tiered services, output monetization)
  - Measure: sustainability (revenue vs. costs), participant satisfaction, comparison with alternatives
  - Key question: What take rate sustains a commons without becoming extractive?

### Phase 4: Prototype & Iteration

- [ ] **4.1 Build Minimum Viable Platform**
  - Implement minimum viable hedge set: small groups, transparent tracking, credible exit, bounded proportional rewards, plural monitoring, automatic renewal
  - Start with software development as first domain (most "code-shaped," easiest contribution tracking)
  - Target 50-200 initial participants

- [ ] **4.2 Implement Core Governance Mechanisms**
  - Plural AI governance (minimum 2 providers, adversarial relationship)
  - Constitutional constraints encoded and tested
  - Quadratic funding for resource allocation
  - Matching markets for Forg formation
  - Multi-dimensional reputation with time decay

- [ ] **4.3 Iterate Based on Experimental Findings**
  - Expect significant revision (every organizational experiment reveals invisible failure modes)
  - Document what breaks and why
  - Compare actual failure modes with predicted failure modes from Phase 2 simulations
  - Revise architecture based on evidence, not commitment to original design

### Phase 5: Scale (If Warranted)

- [ ] **5.1 Expand Domain Coverage**
  - Extend beyond software to design, consulting, creative production
  - Solve non-code contribution tracking for each new domain
  - Validate that mechanisms transfer across work types

- [ ] **5.2 Federation Architecture**
  - Implement Ostrom's Principle #8 (nested governance)
  - Self-governing Dunbar-scale units federated through coordination mechanisms
  - Test whether federation preserves autonomy while enabling scale

- [ ] **5.3 Legal Framework**
  - Establish legal entity structure (building on Wyoming DAO LLC, Marshall Islands precedent)
  - Address: AI governance liability, employment classification, IP ownership, cross-jurisdictional complexity
  - Create template for commons legal structure

## Key Design Constraints (From Research)

These are non-negotiable constraints derived from the research evidence:

1. **Mathematical impossibility results** — The system MUST choose which desirable properties to sacrifice (Arrow, Gibbard-Satterthwaite, Myerson-Satterthwaite). No system satisfies all.
2. **Hierarchy will emerge** — Design for accountable hierarchy, not flat fantasy (Freeman's Tyranny of Structurelessness)
3. **Power-law concentration is inevitable** — Must be actively bounded, not prevented
4. **Purpose fades across generations** — Build renewal mechanisms, not permanent structures
5. **Self-deception is unhedgeable** — The most destructive tendency cannot be fully designed against; only slowed through adversarial monitoring
6. **Sybil resistance is unsolved** — Any identity-dependent mechanism is vulnerable until this is solved
7. **Cold-start requires strategy** — Must identify how to survive the growth phase without VC capital (leverage existing community, target niche, offer unique structural capability)

## The Minimum Viable Hedge Set

Every design decision must preserve these six hedges (the research's most robust finding across all models):

1. **Small groups** — Dunbar scale (3-12 for Forgs, federated for larger scope)
2. **Transparent contribution tracking** — Extending GitHub's innovation beyond code
3. **Credible exit** — Forking with portable reputation and contributions
4. **Proportional bounded rewards** — Tracks contribution, with floors and ceilings
5. **Plural adversarial monitoring** — Multiple AI systems, human oversight, prediction markets, fork threat
6. **Automatic renewal** — Term limits, sunset clauses, zero-based review

## Success Criteria

- [x] Formal 6-layer architecture with exact mechanisms specified for each layer
- [x] Game-theoretic model identifies equilibrium conditions for cooperation
- [x] Multi-principal AI alignment framework addresses Arrow's impossibility explicitly
- [x] Simulation results demonstrate which hedges hold and which break under stress (specifications complete; execution pending)
- [x] At least 3 of 5 critical experiments designed with sufficient rigor to produce actionable results (all 5 designed)
- [ ] Prototype demonstrates minimum viable hedge set in a real commons with real participants (Phase 4 — future)
- [x] Honest assessment of what works, what fails, and what remains genuinely uncertain

## Progress Log

### 2026-02-13: Phases 1-3 Complete (Design Specifications)
- **01-ARCHITECTURE.md** (1,135 lines): Master 6-layer specification with 14 constitutional principles, three-chamber governance, six-dimension reputation, progressive take rate, Forg lifecycle, and meta-governance. Full human nature hedge map (16 negative + 6 positive tendencies). Cross-layer failure propagation analysis. Honest assessment with 3 most likely failure modes.
- **02-FORMAL-MODELS.md** (1,067 lines): Game-theoretic model with 19 formal propositions, 10 definitions, 1 theorem. Cooperation is Nash + ESS under the hedge set (Conjecture A.1). Power-law bounding theory with safe parameter region theorem. Counterfactual analysis shows bounding stack would reduce DAO Gini from 0.99 to 0.3-0.5.
- **03-AI-ALIGNMENT-CONTRIBUTIONS.md** (807 lines): Multi-principal AI alignment with 15 constitutional principles in 3 priority tiers, plural AI spec (3+ providers), 4-tier escalation ladder, recursive governance solution via circular mutual constraint. Three-signal attribution system (team-outcome + AI quality + market signals) with anti-gaming design and Shapley value approximation.
- **04-SIMULATIONS-EXPERIMENTS.md** (1,145 lines): 3 simulation specs (agent-based with 7 archetypes, evolutionary dynamics, 6 attack scenarios) + 5 experiment protocols (governance legitimacy RCT, gaming red team, Forg formation trial, constitutional AI comparison, take-rate sensitivity). Total estimated cost $600K-$1.1M over 30 months.
- **Phases 4-5 (Prototype & Scale) remain as future work** — require actual implementation, not design documents

### 2026-02-13: Effort Created
- Created effort based on completed research from [[EFFORT-Brainstorming-Research]]
- Structured into 5 phases: Theoretical → Simulation → Experiments → Prototype → Scale
- 18 design tasks defined across all phases
- 7 non-negotiable design constraints identified from research evidence
- 6 minimum viable hedges specified as design invariants

## Notes

The research concluded: "The path forward is not advocacy but experimentation." This effort follows that guidance. The goal is not to prove the Agent Commons concept works — it's to design the best system the evidence supports, test it honestly, and remain willing to discover that the evidence points somewhere unexpected.

The 5 falsification conditions from [[CROSS-AREA-SYNTHESIS]] Section 6.3 should be actively monitored throughout:
1. AI capability plateaus
2. Human nature is not the primary failure mode
3. AI governance is fundamentally illegitimate
4. Concentration is structurally inevitable
5. Transition costs exceed benefits

If any of these prove true, the design must pivot accordingly.

## Tags

system-design, organizational-architecture, ai-governance, mechanism-design, game-theory, simulation
