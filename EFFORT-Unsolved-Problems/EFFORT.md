---
type: effort
project: agent-commons
effort_id: EFFORT-Unsolved-Problems
status: not_started
priority: critical
created: 2026-02-13T18:00:00Z
updated: 2026-02-13T18:00:00Z
linked_goal: G12.3
owner: Trent Peterson
progress: 0%
depends_on: EFFORT-Brainstorming-Research
blocks: EFFORT-System-Design
---

# EFFORT: Unsolved Problems — Research & Brainstorming

## Purpose

The research phase (17 documents, 300+ sources) identified a set of **hard, unsolved problems** that must be resolved — or at least deeply understood — before system design can proceed. These aren't implementation details. They are fundamental challenges where the research explicitly said "no known solution exists" or "every system studied has failed at this."

This effort exists because EFFORT-System-Design cannot succeed without answers (or at least well-reasoned approaches) to these problems. Designing around unsolved problems produces wishful thinking, not architecture.

**Approach:** For each problem, research what's been tried, what's emerging, what the frontier looks like, and brainstorm potential solutions — including solutions that don't exist yet. Be honest about what remains genuinely unsolvable.

## The Problems (Consolidated from All Research)

The research surfaces these problems from multiple documents. Here they are consolidated, de-duplicated, and organized into research threads:

### Master Problem List

| # | Problem | Confidence It's Hard | Source | Blocking? |
|---|---------|---------------------|--------|-----------|
| P1 | Recursive AI Governance | Very High | [[CROSS-AREA-SYNTHESIS]] 6.2 #1 | Yes — no system design without this |
| P2 | Sybil Resistance | Very High | [[CROSS-AREA-SYNTHESIS]] 4.3 #2, 6.2 #2 | Yes — QF, reputation, democracy all exploitable |
| P3 | Cold-Start / Sustainability Economics | High | [[CROSS-AREA-SYNTHESIS]] 4.2, 6.2 #3 | Yes — if economics don't work, nothing works |
| P4 | Non-Code Contribution Valuation | High | [[CROSS-AREA-SYNTHESIS]] 4.3 #4, 6.2 #4 | Partial — can launch code-only first |
| P5 | Price-Signal Equivalent | High | [[CROSS-AREA-SYNTHESIS]] 4.3 #6 | Partial — without it, calculation problem recurs |
| P6 | Power-Law / Concentration Bounding | High | [[CROSS-AREA-SYNTHESIS]] 6.4, [[CAPITALISM]] 2.1, 2.6 | Yes — concentration enables capture |
| P7 | AI Governance Legitimacy | Moderate-High | [[CROSS-AREA-SYNTHESIS]] 6.2 #5, 6.3 #3 | Yes — if rejected, premise fails |
| P8 | Legal Framework | High | [[CROSS-AREA-SYNTHESIS]] 4.3 #3, [[DAOS]] 6 | Partial — can prototype without, can't scale |
| P9 | Meaning of Work | Moderate | [[CROSS-AREA-SYNTHESIS]] 4.3 #5 | No — but sustainability requires it |
| P10 | Impossibility Trade-off Selection | Mathematical Certainty | [[ACADEMIC-THEORETICAL-FRAMEWORKS]], [[CROSS-AREA-SYNTHESIS]] 6.4 | Yes — must choose what to sacrifice |
| P11 | Purpose Decay Across Generations | High | [[CROSS-AREA-SYNTHESIS]] 6.4, [[ALTERNATIVE-MODELS]] | No — but long-term viability requires it |
| P12 | Internal Competition vs. Fragmentation | Moderate | [[CROSS-AREA-SYNTHESIS]] 7.2 #6, [[CAPITALISM]] 2.1 | No — design question, not blocker |

---

## Research Threads

### Thread 1: AI Governance (P1, P7, P10)

**The core question:** How do you build AI governance that is legitimate, accountable, and resistant to capture — when the AI itself becomes a single point of failure?

**Problems addressed:**
- **P1 — Recursive AI Governance:** Who governs the AI that governs the system? Every proposed solution (plural AI, human oversight, constitutional constraints) just moves the problem. Plural AI can be captured by controlling training data or providers. Human oversight is subject to all Area 1 failure modes. The interpreter of constitutional constraints holds the real power.
- **P7 — AI Governance Legitimacy:** Will people accept AI governance decisions as legitimate? Constitutional democracies derive legitimacy from consent via elections. What is the equivalent for AI governance when the governed cannot fully understand the AI's reasoning? Does acceptance increase or decrease with experience?
- **P10 — Impossibility Trade-off Selection:** Arrow, Gibbard-Satterthwaite, and Myerson-Satterthwaite mathematically prove that no governance system satisfies all desirable properties simultaneously. The system MUST choose which properties to sacrifice. This choice is political, not technical — and no framework exists for making it in an AI-governed context.

**Research areas:**
- [ ] **1.1 Existing AI Governance Models**
  - Anthropic's Constitutional AI — how it works, what it constrains, what it can't do
  - OpenAI's governance structure and its 2023-2024 crisis (board vs. Altman)
  - EU AI Act governance requirements
  - Algorithmic governance in existing platforms (content moderation at Meta, Google, etc.)
  - What do "AI ethics boards" actually do? Track record of corporate AI governance
  - Academic proposals: Dafoe et al. on cooperative AI, Russell on beneficial AI

- [ ] **1.2 Plural AI Architecture**
  - Can multiple AI systems with different training genuinely check each other?
  - What happens when AI systems disagree? Who breaks the tie?
  - Adversarial ML research — can adversarial dynamics be productive rather than destructive?
  - Cost and complexity of running multiple governance AI systems
  - Red-teaming as governance: continuous adversarial testing of governance AI
  - Blockchain oracle problem parallel — multiple independent data sources for consensus

- [ ] **1.3 Human-AI Governance Hybrids**
  - Optimism's bicameral model (Token House + Citizens' House) — can this extend to AI + Human chambers?
  - Jury models: AI proposes, human jury disposes (like grand jury / petit jury split)
  - Escalation ladders: AI handles routine, humans handle contested, constitution handles fundamental
  - Swiss direct democracy model — citizens can challenge any AI decision via referendum
  - What's the right ratio? Which decisions need human judgment vs. AI efficiency?

- [ ] **1.4 Legitimacy Research**
  - Public opinion research on AI decision-making (healthcare, criminal justice, hiring — what's transferable?)
  - Procedural justice research (Tyler) — perceived fairness depends more on process than outcome
  - Transparency vs. explainability vs. contestability — which matters most for legitimacy?
  - What makes people accept algorithmic decisions they disagree with?
  - Religious/cultural dimensions of AI governance acceptance across societies

- [ ] **1.5 The Impossibility Trade-off Framework**
  - Map Arrow's impossibility to specific Agent Commons governance decisions
  - Which properties does each existing system sacrifice? (Democracy sacrifices efficiency. Corporations sacrifice non-dictatorship. DAOs sacrifice participation.)
  - What should the commons sacrifice? Propose 2-3 concrete trade-off configurations
  - Can different trade-offs apply at different governance layers? (Efficiency at Layer 5, fairness at Layer 1)
  - Mechanisms for making the trade-off choice itself legitimate (meta-governance)

**Key sources to find:** Anthropic Constitutional AI papers, EU AI Act text, Tyler's procedural justice research, Dafoe et al. cooperative AI, Russell's "Human Compatible", existing AI ethics board post-mortems, public opinion polling on AI decision-making

**Desired output:** A concrete proposal for AI governance architecture that addresses recursion, legitimacy, and impossibility trade-offs — or an honest statement of why this can't be fully solved and what the best available mitigation is.

---

### Thread 2: Identity & Reputation (P2, P4, P5, P6)

**The core question:** How do you know who people are, what they've contributed, and what their contributions are worth — in a system where gaming, faking, and concentrating are the natural human responses to any measurement system?

**Problems addressed:**
- **P2 — Sybil Resistance:** No existing solution is simultaneously privacy-preserving, Sybil-resistant, and accessible. Worldcoin requires biometric submission to a private company. Proof of Humanity requires existing social connections. BrightID requires trust networks. Without Sybil resistance, QF, reputation, and democratic governance are all exploitable.
- **P4 — Non-Code Contribution Valuation:** Git tracks code. Nothing equivalent exists for design, strategy, mentoring, community-building, or relationship management — the highest-value contributions in the AI era.
- **P5 — Price-Signal Equivalent:** Capitalism's price system compresses supply, demand, quality, scarcity, and opportunity cost into a single actionable signal. Multi-dimensional reputation is informationally inferior. Without this density, the calculation problem recurs.
- **P6 — Power-Law / Concentration Bounding:** Preferential attachment produces concentration regardless of design. Piketty's r > g shows even bounded inequality compounds. Every empirical system studied developed extreme concentration. Need mathematical conditions for bounding below governance-capture threshold.

**Research areas:**
- [ ] **2.1 Sybil Resistance: State of the Art**
  - Worldcoin / World ID — biometric iris scanning, privacy concerns, adoption data
  - Proof of Humanity — vouching chain, strengths and vulnerabilities
  - BrightID — social graph verification, Sybil detection algorithms
  - Gitcoin Passport — composable identity with multiple stamps, gaming resistance data
  - Government digital identity (Estonia e-Residency, India Aadhaar) — can government ID be leveraged without government control?
  - Zero-knowledge proofs for identity — can you prove uniqueness without revealing identity?
  - Web-of-trust models (PGP lineage) — scaling limitations and modern variants
  - Emerging research: decentralized identity (DID), verifiable credentials (W3C standard)

- [ ] **2.2 Non-Code Contribution Tracking**
  - What do existing platforms track? (Figma activity, Notion edits, Slack engagement, meeting participation)
  - Peer evaluation systems — 360-degree review research, accuracy, gaming
  - Outcome-based attribution — attributing value based on project success rather than activity
  - AI-assisted evaluation — can LLMs assess design quality, strategic thinking, mentorship impact?
  - "Invisible work" research (Daniels 1987, Star & Strauss 1999) — taxonomy of unmeasured contributions
  - Shapley value estimation for team contributions — computational approaches
  - Buurtzorg, Morning Star — how do successful self-managing orgs handle non-code attribution?

- [ ] **2.3 Price-Signal Mechanisms for a Commons**
  - Quadratic funding as a pricing mechanism for public goods — Gitcoin's $60M+ experiment, what the data shows about information aggregation quality
  - Prediction markets as value signals — can prediction markets estimate the value of contributions?
  - Internal markets / organizational markets — Hewlett-Packard's internal prediction markets, Google's internal resource allocation
  - Combinatorial auctions for project prioritization — each participant bids on what matters
  - Retroactive public goods funding (Optimism's model) — fund based on demonstrated value, not predicted value
  - Harberger taxes as a commons pricing mechanism — Weyl/Posner's proposal
  - Can AI create synthetic price signals from multi-dimensional data?

- [ ] **2.4 Concentration Bounding**
  - Mathematical models of preferential attachment with countermeasures (time-decay, caps, quadratic weighting)
  - Empirical concentration data from open-source (contributor distribution), DAOs (token distribution), Stack Overflow (reputation distribution)
  - What concentration level enables governance capture? Is there a quantifiable threshold?
  - Progressive mechanisms: quadratic voting (cost increases with votes), time-decay on reputation, contribution caps per period
  - Network science: can you design attachment rules that bound power-law exponents?
  - Redistribution mechanisms: reputation taxation, universal basic reputation, periodic resets
  - Historical precedents: antitrust, progressive taxation, land reform — what worked?

- [ ] **2.5 Reputation Gaming Resistance**
  - Documented gaming strategies for every major reputation system (eBay, Stack Overflow, Uber, Amazon, academic citations)
  - AI-assisted gaming: LLM-generated fake contributions, automated Sybil creation
  - Multi-signal systems — does combining signals increase gaming resistance or just increase attack surface?
  - Adversarial reputation evaluation — red teams specifically trying to game the system
  - Dynamic mechanism adjustment — can the reputation system evolve faster than the gamers?
  - Credential fraud detection research — what transfers from academic fraud detection?

**Key sources to find:** Worldcoin/BrightID/Gitcoin Passport technical papers, W3C DID/VC specifications, Shapley value computation research, Gitcoin QF analysis data, Barabasi/Albert preferential attachment extensions, reputation gaming literature, Harberger tax analysis

**Desired output:** For each sub-problem, a ranked list of candidate solutions with honest assessment of trade-offs. For Sybil resistance specifically: a concrete recommendation (even if imperfect) that could work for a 50-200 person pilot.

---

### Thread 3: Economics & Sustainability (P3, P12)

**The core question:** How does a commons sustain itself economically and survive the growth phase — when every comparable attempt has either failed to scale or become the extractive platform it was designed to replace?

**Problems addressed:**
- **P3 — Cold-Start / Sustainability Economics:** No platform cooperative has competed at scale with VC-funded incumbents. The 5-8% take rate is untested. Capitalism hasn't solved public goods pricing in 300 years. Harvard estimated open-source value at >$8.8T with total funding in low hundreds of millions.
- **P12 — Internal Competition vs. Fragmentation:** Capitalism's most powerful anti-decay mechanism is competition, but monopoly is the rational endgame. How to preserve competitive discipline via forking without fragmenting the commons into nonviable pieces?

**Research areas:**
- [ ] **3.1 Cold-Start Strategies That Actually Worked**
  - Platform cold-start research (Chen/Terwiesch, Evans/Schmalensee) — successful strategies by platform type
  - Stocksy's bootstrap (leveraged iStockphoto founder's community and credibility)
  - Wikipedia's bootstrap (leveraged Nupedia's content + volunteer ethos + zero-cost participation)
  - Linux's bootstrap (leveraged Linus's kernel + academic community + free as in beer)
  - Ethereum's bootstrap (leveraged Bitcoin community + ICO funding mechanism)
  - What niche could Agent Commons target where incumbents are structurally weak?
  - Can AI itself provide the cold-start advantage? (AI-native capabilities that traditional platforms can't offer)
  - Community-first vs. product-first vs. capital-first strategies

- [ ] **3.2 Commons Revenue Models**
  - Open-source revenue models ranked by sustainability: consulting (Red Hat $3.4B), open-core (MongoDB $20B+), SaaS (GitHub $200M ARR), sponsorship (Wikipedia $150M/yr), marketplace fees (Apple 30%, Shopify 2.9%), certification/training
  - What's the actual cost structure for an AI-governed commons? (AI compute, infrastructure, dispute resolution, development, legal)
  - The take rate question: where's the Laffer curve for commons fees? Too low = unsustainable, too high = extractive
  - Tiered pricing models — free for individuals, paid for commercial use, premium for enterprise
  - Can the commons itself generate revenue from AI-produced outputs? (App store model from the README)
  - Protocol revenue: Ethereum's model ($2B+ annual fees for protocol operation)
  - Public goods funding mechanisms (QF matching pools, retroactive funding, grants)

- [ ] **3.3 Competing with VC-Funded Platforms**
  - What structural advantages does a commons have that a VC platform cannot replicate?
  - Trust and alignment as competitive moat (users prefer non-extractive platforms when quality is comparable)
  - Network effects: can the commons build defensible network effects?
  - The "marathon vs. sprint" thesis — can the commons survive the sprint phase?
  - Cooperative federations as scale mechanism (CoopCycle, Decidim, Loomio shared infrastructure)
  - Can regulatory arbitrage help? (EU Digital Markets Act, antitrust actions creating space)
  - What if the commons doesn't need to beat platforms, but to be the infrastructure platforms are built on?

- [ ] **3.4 Internal Competition Design**
  - Fork dynamics in open source — when do forks help vs. harm the ecosystem?
  - Market design for internal competition — can multiple Forgs compete on the same project without fragmentation?
  - Tournament models (Netflix Prize, Kaggle competitions) — do they produce better outcomes?
  - Wikipedia's model: competition within one system (edit wars) vs. Fandom's fork
  - Healthy vs. destructive competition — what are the empirical markers?
  - Can AI mediate competitive dynamics? (Matching Forgs to projects based on comparative advantage rather than letting all compete on everything)

**Key sources to find:** Chen's platform cold-start research, Evans/Schmalensee platform economics, open-source sustainability reports (Tidelift, Linux Foundation), Ethereum economics analysis, CoopCycle/Decidim case studies, Netflix Prize post-mortem, EU DMA analysis

**Desired output:** A concrete economic plan for a commons pilot — revenue model, pricing, cold-start strategy, and competitive positioning. Include sensitivity analysis: what happens if take rate is too low? Too high? If growth is slower than expected?

---

### Thread 4: Legal & Social Infrastructure (P8, P9, P11)

**The core question:** What legal structure can house an AI-governed commons, and how does it remain meaningful to humans when AI handles the productive work?

**Problems addressed:**
- **P8 — Legal Framework:** No legal structure exists for AI-governed commons. DAOs face general partnership liability, tax ambiguity, securities risk, and cross-jurisdictional complexity. Agent Commons adds AI governance liability and employment classification questions.
- **P9 — Meaning of Work:** If AI handles production, what provides purpose, identity, and social connection? Unemployment research shows life satisfaction loss exceeds income loss. The commons must be psychologically fulfilling.
- **P11 — Purpose Decay Across Generations:** Kibbutzim lost purpose in the second generation. Mondragon's cooperative culture has weakened. Open-source suffers maintainer burnout. No system has maintained intrinsic motivation across generations without institutional renewal.

**Research areas:**
- [ ] **4.1 Legal Structures for AI-Governed Organizations**
  - Wyoming DAO LLC (2021) — what it covers, what it doesn't, precedent cases
  - Marshall Islands DAO Act — broader scope, practical adoption
  - Vermont Blockchain-Based LLC — earlier approach, lessons
  - Swiss foundation model (Ethereum Foundation) — governance flexibility
  - UK Community Interest Company — social enterprise structure
  - Cooperative law across jurisdictions — which best fits a commons?
  - Can an AI be a legal person? (Current status, emerging proposals)
  - Employment classification for Forg members — are they employees, contractors, partners, or something new?
  - IP ownership: who owns the output of a Forg? (Work-for-hire, open-source licensing, commons ownership)
  - AI governance liability: who is responsible when AI governance makes a bad decision?
  - Cross-jurisdictional complexity: can a commons have a single legal home?

- [ ] **4.2 Purpose & Meaning in a Post-AI-Production World**
  - Jahoda's latent deprivation theory — the 5 non-financial functions of work (time structure, social contact, collective purpose, status/identity, regular activity)
  - Frankl's logotherapy — meaning through creative values, experiential values, attitudinal values
  - Csikszentmihalyi's flow research — conditions for intrinsic motivation in work
  - Maker movement, open-source motivation (Lerner/Tirole) — why do people contribute to public goods for free?
  - Craft economies and artisan identity — can AI create a new artisan class?
  - UBI experiments and meaning — Finland, Stockton data on psychological effects
  - The "experience economy" (Pine/Gilmore) — does AI push economic value toward experiences and transformation?
  - What work is meaningful when AI can do everything? Curation, judgment, teaching, care, creation, governance

- [ ] **4.3 Sustaining Purpose Across Generations**
  - Why did kibbutz purpose fade? (Abramitzky's data: second generation didn't choose the ideology)
  - Why did Mondragon's cooperative culture weaken? (Globalization pressure, generational shift, scale)
  - Why does open-source suffer burnout? (Sustainability crisis, emotional labor, entitlement culture)
  - What sustained purpose across generations? Religious organizations (centuries), military traditions, academic institutions, craft guilds
  - Renewal mechanisms: can the commons build purpose-renewal into its structure?
  - Initiation and onboarding as purpose-building (military basic training, religious conversion, academic orientation)
  - Can shared governance participation itself create purpose? (Tocqueville's argument about democratic participation)
  - Generational autonomy: each generation should be able to re-negotiate the commons constitution

**Key sources to find:** Wyoming DAO LLC statute and case law, Marshall Islands DAO Act, Swiss foundation governance, Jahoda's "Employment and Unemployment" (1982), Csikszentmihalyi's "Flow", Abramitzky's kibbutz research, Lerner/Tirole open-source motivation, Pine/Gilmore experience economy, religious institution longevity research

**Desired output:** A legal framework recommendation (which jurisdiction, which structure, how to handle employment/IP/liability). A framework for meaning-creation in the commons. A set of purpose-renewal mechanisms that could sustain motivation across generations.

---

## Cross-Cutting Concerns

These apply across all threads:

### The Honesty Constraint

For each problem, the research must honestly assess:
1. **Can this be solved?** Or is it an inherent trade-off that must be managed?
2. **What's the best available solution?** Even if imperfect
3. **What happens if it can't be solved?** Does the commons concept survive? In what reduced form?
4. **Is this a reason to give up?** Some problems may be dealbreakers. Be honest about which.

### Falsification Conditions

The following conditions from [[CROSS-AREA-SYNTHESIS]] 6.3 should be actively monitored. If evidence emerges for any of them during this research, document it honestly:

1. AI capability plateaus (undermines the entire transaction-cost argument)
2. Human nature is not the primary failure mode (wrong design focus)
3. AI governance is fundamentally illegitimate (premise fails)
4. Concentration is structurally inevitable (commons reproduces the problem)
5. Transition costs exceed benefits (not worth building)

---

## Success Criteria

- [ ] Each of the 12 problems has a research document with current state-of-the-art, candidate solutions, and honest assessment
- [ ] Blocking problems (P1, P2, P3, P6, P7, P10) have at least one viable approach — even if imperfect — that could work for a 50-200 person pilot
- [ ] For each problem, the "can this be solved?" question is answered honestly
- [ ] At least one problem is identified as a potential dealbreaker with conditions under which the project should be abandoned or pivoted
- [ ] The research produces concrete inputs for EFFORT-System-Design — not just "more research needed" but specific mechanism recommendations
- [ ] Falsification conditions are actively evaluated against new evidence

## Dependencies

- **Depends on:** [[EFFORT-Brainstorming-Research]] (completed) — provides the problem identification
- **Blocks:** [[EFFORT-System-Design]] (not_started) — system design cannot proceed without approaches to these problems

## Progress Log

### 2026-02-13: Effort Created
- Consolidated 12 unsolved problems from 17 research documents and 5 project files
- Organized into 4 research threads: AI Governance, Identity & Reputation, Economics & Sustainability, Legal & Social Infrastructure
- Identified 6 blocking problems, 3 partial blockers, 3 non-blocking but important
- Structured research areas with 20 sub-topics across 4 threads

## Tags

unsolved-problems, research, ai-governance, sybil-resistance, sustainability, identity, reputation, legal-framework, meaning-of-work
