# Agent Commons

**Everything will change with the introduction of AI. How can we steer that change to make a better world?**

This project designs an AI-enabled organizational model that could replace traditional corporate hierarchy. Starting from a simple question, it has grown into a comprehensive research and design effort: 33 documents, 21,000+ lines, 500+ academic sources, covering organizational failure analysis, unsolved problem resolution, and formal system architecture.

The core insight from the research: every organizational model in history builds "hedges" against human nature (greed, tribalism, power-seeking, free-riding) — and every model eventually fails when human nature finds the "cracks." AI offers a new tool for building hedges, but also introduces new cracks. The design must account for both.

## The Agent Commons Model

A three-layer organizational system with AI governance replacing management hierarchy:

### Layer 1: Agent
Autonomous individuals (human or AI). Self-directed, free to come and go. Contribute to Forgs based on skills, interests, and AI matching.

### Layer 2: Forg (Fork + Org, Forge + Org)
Self-organizing teams of 3-12 that form around projects. They form, deliver, dissolve, or fork. AI-matched or self-selected. Dunbar-scale for direct observation; federated for larger scope.

### Layer 3: Agent Commons
The platform/system itself. Six-layer architecture: Constitutional Foundation, Governance (three-chamber: AI Engine + Sortition Assembly + Community Referendum), Reputation & Identity, Economic Model (8% take rate, QF allocation), Coordination & Work, and Meta-Governance (sunset clauses, adversarial monitoring, purpose renewal).

## Key Design Principles

- **Rewards contribution**, not hierarchy or ownership — bounded proportional rewards with floors and ceilings
- **AI governance** via plural AI (3+ independent providers) with constitutional constraints and human override
- **Hedges against human nature** — every mechanism maps to specific tendencies from a 22-tendency taxonomy
- **Honest about cracks** — every hedge has a known remaining vulnerability
- **Forkable** — credible exit with portable reputation provides anti-capture discipline
- **Mathematically grounded** — formal game theory, power-law bounding, impossibility trade-off analysis
- **Designed for impermanence** — 40-60 year realistic lifespan with generational renewal mechanisms

## Project Structure

Three completed efforts, progressing from broad research to formal design:

```
PROJECT-Agent-Commons/
├── EFFORT-Brainstorming-Research/    # Effort 1: Foundation research (completed)
│   ├── EFFORT.md                     # Effort metadata
│   ├── CROSS-AREA-SYNTHESIS.md       # Unified findings across all 17 documents
│   ├── 01-organizational-failures/   # Area 1: Why organizations fail
│   │   ├── HUMAN-NATURE-TAXONOMY.md  #   16 negative + 6 positive human tendencies
│   │   ├── DEMOCRACY.md             #   Hedge-and-crack analysis of democracy
│   │   ├── SOCIALISM.md             #   Hedge-and-crack analysis of socialism
│   │   ├── CORPORATISM.md           #   Hedge-and-crack analysis of corporatism
│   │   ├── CAPITALISM.md            #   Hedge-and-crack analysis of capitalism
│   │   ├── ALTERNATIVE-MODELS.md    #   Kibbutzim, Mondragon, Buurtzorg, etc.
│   │   └── SYNTHESIS.md             #   10 evidence-based design principles
│   ├── 02-ai-driven-change/          # Area 2: How AI changes organizations
│   │   ├── CORPORATE-BREAKDOWN.md   #   Coase + AI = corporate dissolution
│   │   ├── SELF-ORGANIZING-TEAMS.md #   Forg analogies, 8 infrastructure layers
│   │   ├── KNOWLEDGE-DEMOCRATIZATION.md # 7 professions analyzed
│   │   └── ECONOMIC-IMPLICATIONS.md #   Distribution, sustainability, transition
│   └── 03-models-and-precedents/     # Area 3: What's been tried
│       ├── OPEN-SOURCE.md           #   6 governance models
│       ├── GITHUB-INFRASTRUCTURE.md #   GitHub as organizational infrastructure
│       ├── DAOS.md                  #   Governance innovations + failures
│       ├── PLATFORM-COOPERATIVES.md #   7 case studies
│       ├── PREDICTION-MARKETS-MECHANISM-DESIGN.md # 6-layer incentive architecture
│       └── ACADEMIC-THEORETICAL-FRAMEWORKS.md     # Game theory, complexity, alignment
│
├── EFFORT-Unsolved-Problems/          # Effort 2: Resolving hard problems (completed)
│   ├── EFFORT.md                     # 12 problems, 4 threads, 20 sub-topics
│   ├── 01-AI-GOVERNANCE.md           # P1, P7, P10: Recursion, legitimacy, impossibility
│   ├── 02-IDENTITY-REPUTATION.md     # P2, P4, P5, P6: Sybil, valuation, concentration
│   ├── 03-ECONOMICS-SUSTAINABILITY.md # P3, P12: Cold-start, competition
│   ├── 04-LEGAL-SOCIAL.md           # P8, P9, P11: Legal, meaning, purpose decay
│   └── SYNTHESIS.md                  # Cross-thread verdict: proceed to design
│
├── EFFORT-System-Design/             # Effort 3: Formal architecture (Phases 1-3 complete)
│   ├── EFFORT.md                     # 5 phases, 18 tasks
│   ├── 01-ARCHITECTURE.md           # Master 6-layer specification
│   ├── 02-FORMAL-MODELS.md          # Game theory + power-law bounding (19 propositions)
│   ├── 03-AI-ALIGNMENT-CONTRIBUTIONS.md # Multi-principal AI + contribution attribution
│   └── 04-SIMULATIONS-EXPERIMENTS.md # 3 simulations + 5 experiment protocols
│
├── .claude-project/                   # Project orchestration
│   ├── config.yaml
│   └── PROJECT.md → orchestration     # Symlink to orchestration state
└── README.md                          # This file
```

## Research Summary

### Effort 1: Brainstorming Research (17 documents, 13,000+ lines, 300+ sources)

Analyzed why every organizational model fails and what AI changes:

- **Human Nature Taxonomy:** 16 negative tendencies (power-seeking, free-riding, tribalism, self-deception...) and 6 positive tendencies (cooperation, creativity, empathy...) derived from 3 root drives
- **Hedge-and-Crack Framework:** Democracy, socialism, corporatism, capitalism, and 5 alternative models each build hedges against human nature — and each eventually fails through specific cracks
- **Capitalism's Unique Insight:** "Don't fight the river — build a waterwheel." Capitalism harnesses self-interest rather than suppressing it, but monopoly, financialization, and externalities are its cracks
- **AI's Impact:** Reduces coordination costs 30-90% (Coase thesis), democratizes knowledge across 7 professions, enables new organizational forms, but creates new capture risks
- **Minimum Viable Hedge Set:** The most robust finding — 6 hedges that appear across every successful model: small groups, transparent tracking, credible exit, bounded rewards, plural monitoring, automatic renewal

### Effort 2: Unsolved Problems (5 documents, 4,000+ lines, 340+ sources)

Resolved 12 hard problems that blocked system design:

| Problem | Verdict | Key Finding |
|---------|---------|-------------|
| P1: Recursive AI Governance | Manageable | Circular mutual constraint (no final authority) |
| P2: Sybil Resistance | Partially solved | Layered composable identity for pilot |
| P3: Cold-Start Economics | Manageable | "Come for the AI tool, stay for the commons" |
| P4: Non-Code Contribution | Partially solved | Team-outcome + peer allocation + AI signals |
| P5: Price-Signal Equivalent | Partially solved | Five-mechanism hybrid (weakest link) |
| P6: Concentration Bounding | Managed, not solved | Five-mechanism bounding stack; continuous intervention |
| P7: AI Governance Legitimacy | Achievable | Procedural justice (Tyler): voice + contestability |
| P8: Legal Framework | Solved | Colorado LCA with 4 membership classes |
| P9: Meaning of Work | Partially solved | Five-Function Replacement Framework (Jahoda) |
| P10: Impossibility Trade-offs | Mathematically unsolvable | Layer-specific trade-off configurations |
| P11: Purpose Decay | Managed, not solved | 6 renewal mechanisms; ~40-60 year ceiling |
| P12: Internal Competition | Solved | Fork threat as governance discipline |

**Verdict:** No dealbreakers. Proceed to system design. P5 and P6 require continuous monitoring.

### Effort 3: System Design (4 documents, 4,150+ lines)

Formal architecture specification:

- **6-Layer Architecture** with exact mechanisms, parameters, and thresholds for each layer
- **Three-Chamber Governance:** AI Governance Engine (~90% of decisions) + Sortition Assembly (~8%) + Community Referendum (~2%), with 4-tier escalation ladder
- **Game-Theoretic Proof:** Cooperation is Nash equilibrium + evolutionarily stable under the hedge set (19 formal propositions, 1 theorem)
- **Power-Law Bounding:** Safe parameter region proven; counterfactual shows bounding would compress DAO Gini from 0.99 to 0.3-0.5
- **15 Constitutional Principles** in 3 priority tiers, with supermajority + time-delay amendment process
- **Multi-Principal AI Alignment:** Extends Constitutional AI to organizational governance with 3+ independent providers
- **Three-Signal Attribution:** Team-outcome + AI quality assessment + market signals for non-code contribution valuation
- **5 Experiment Protocols** ready for execution (governance legitimacy RCT, gaming red team, Forg formation trial, constitutional AI comparison, take-rate sensitivity)
- **Estimated pilot cost:** $600K-$1.1M over 30 months for 200 participants

## Falsification Conditions

The research maintains 5 conditions under which the project should be abandoned or pivoted:

1. AI capability plateaus (undermines the transaction-cost argument)
2. Human nature is not the primary failure mode (wrong design focus)
3. AI governance is fundamentally illegitimate (premise fails)
4. Concentration is structurally inevitable (commons reproduces the problem) — **partially triggered; requires monitoring**
5. Transition costs exceed benefits (not worth building)

## What's Next

**Phases 4-5 of System Design** — building the actual prototype:
- Implement minimum viable platform with the 6 hedges
- Run the 5 designed experiments with 200 pilot participants
- Iterate based on empirical findings
- If warranted, scale via federation architecture

The design is complete enough to begin. The research concluded: *"The path forward is not advocacy but experimentation."*

## Important Note

This concept is one manifestation of what the world might look like. The deeper question — how to steer AI-driven change toward a better world — may lead to very different models. The design includes falsification conditions and is built to discover where it's wrong, not to prove it's right.

## Owner

Trent Peterson

## Status

System design complete (Phases 1-3). Ready for prototype implementation (Phase 4).
