---
created: 2026-02-13T20:00:00Z
updated: 2026-02-13T20:00:00Z
type: research
parent_effort: EFFORT-Unsolved-Problems
thread: 2
problems_addressed:
  - P2 (Sybil Resistance)
  - P4 (Non-Code Contribution Valuation)
  - P5 (Price-Signal Equivalent)
  - P6 (Power-Law / Concentration Bounding)
backlinks:
  - [[EFFORT]]
  - [[CROSS-AREA-SYNTHESIS]]
  - [[01-organizational-failures/CAPITALISM]]
  - [[03-models-and-precedents/DAOS]]
  - [[03-models-and-precedents/ACADEMIC-THEORETICAL-FRAMEWORKS]]
  - [[03-models-and-precedents/PREDICTION-MARKETS-MECHANISM-DESIGN]]
---

# Thread 2: Identity & Reputation

**The core question:** How do you know who people are, what they've contributed, and what their contributions are worth -- in a system where gaming, faking, and concentrating are the natural human responses to any measurement system?

This document covers four interrelated unsolved problems:

- **P2 -- Sybil Resistance:** Proving uniqueness without sacrificing privacy or accessibility
- **P4 -- Non-Code Contribution Valuation:** Measuring what Git cannot track
- **P5 -- Price-Signal Equivalent:** Replacing capitalism's information compression for a commons
- **P6 -- Power-Law / Concentration Bounding:** Preventing reputation from becoming the new capital

These problems are deeply coupled. Sybil resistance is the foundation -- without it, every measurement and reputation mechanism is exploitable. Contribution valuation feeds reputation. Reputation feeds governance power. Governance power concentrates. Concentration captures governance. The entire stack must be considered together.

---

## 2.1 Sybil Resistance: State of the Art

### What Exists Today

The Sybil problem -- proving that each participant in a system represents exactly one unique person -- remains one of the hardest unsolved problems in decentralized systems. Every approach involves a fundamental trade-off between privacy, accessibility, and resistance strength. No solution satisfies all three simultaneously.

#### Biometric Approaches

**Worldcoin / World ID** uses iris scanning via a physical device called the Orb to create a cryptographic identity. As of 2025, 12-16 million people have registered their iris scans and received a World ID (Forrester, 2025; 3MinRead, 2025). The system uses zero-knowledge proofs so that applications can verify "this is a unique human" without receiving the biometric data itself.

Strengths: Strong Sybil resistance (iris patterns are unique and difficult to forge). ZK proofs preserve some privacy after initial scan. Scale is growing.

Weaknesses: Requires biometric submission to a private company controlled by Sam Altman. Countries including Brazil, Colombia, Germany, Hong Kong, India, Kenya, Portugal, Spain, and South Korea have investigated, restricted, or banned the Orb for privacy violations (BeInCrypto, 2025). Spain ordered deletion of stored iris records. Vitalik Buterin warned that "a singular, universally linked identity risks online privacy and individual freedom" (Buterin, 2025). The Orb personal device slated for 2026 may reduce centralization concerns but does not eliminate them.

**Humanity Protocol** uses palm biometrics with zero-knowledge proofs, launching on Arbitrum. Palm data is hashed and fed into ZK circuits that prove uniqueness without revealing the biometric input (Messari, 2025). Mainnet launched August 2025 with zkTLS. Over 2 million Human IDs issued during testnet. The $H token airdrop was restricted to verified humans only.

Strengths: Less invasive than iris scanning. No biometric data stored -- only hashes. ZK architecture is privacy-preserving by design.

Weaknesses: Still requires a physical biometric capture event. Palm scanning hardware availability is limited. Newer and less battle-tested than Worldcoin.

#### Social Graph Approaches

**Proof of Humanity (PoH)** uses a vouching chain combined with video verification. Registered users vouch for new applicants; challenged submissions go through an on-chain dispute process via Kleros. If a submission is rejected for Sybil attack or identity theft, all vouchers are also removed from the registry (Kleros FAQ, 2025).

Strengths: Decentralized -- no single entity controls registration. Punishes vouchers who enable Sybils. Human-readable verification via video.

Weaknesses: Vulnerable to coordinated Sybil rings where fake personas vouch for each other (Humanode, 2025). Getting a voucher is hard without existing connections, creating an accessibility barrier. Gas fees and deposits can reach $600+, which is exclusionary. Deepfake AI threatens video verification. The system may "inadvertently centralize around hub individuals or exclude those outside major social circles" (Frontiers in Blockchain, 2020).

**BrightID** builds a social graph from peer-to-peer connections and runs Sybil-detection algorithms (SybilRank, GroupSybilRank, Aura) on the graph structure (BrightID, 2025). Verification nodes analyze the graph and determine whether users are unique. The assumption is that Sybils have limited genuine social connections to real users.

Strengths: No biometrics. Fully decentralized verification. Open-source analysis tools. Multiple independent algorithms can be applied.

Weaknesses: Requires building real social connections, which creates cold-start problems. SybilRank relies on the assumption of limited Sybil-honest connections, which sophisticated attackers can circumvent by gradually building genuine-looking connections (KAIST, 2025). Graph analysis is computationally expensive at scale.

#### Composable / Stamp-Based Approaches

**Gitcoin Passport / Human Passport** aggregates multiple identity signals ("stamps") from both Web2 (Twitter, Google) and Web3 (BrightID, PoH, on-chain activity) into a composite score. Acquired by the Holonym Foundation in 2025 and now part of human.tech (The Defiant, 2025). The 2025 update includes a machine learning Sybil Detection Model that analyzes wallet behavior in real time, and Cross-chain Intelligence that combines activity across multiple EVM chains.

Strengths: Composable -- the more stamps verified, the higher the score. Does not depend on any single mechanism. ML-powered behavioral analysis adds a dynamic layer. No single biometric requirement.

Weaknesses: Each individual stamp is weaker than a dedicated Sybil mechanism. Gaming one stamp is easy; the question is whether gaming enough stamps to reach the threshold is hard enough. The system essentially measures "cost of forgery" -- how expensive it is to create a convincing fake identity (Gitcoin, 2025). This means wealthy or sophisticated attackers have an advantage.

#### Government-Issued Digital Identity

**Estonia's e-Residency** provides government-issued digital identity to over 100,000 e-residents globally (e-Estonia, 2025). Background checks take 3-8 weeks. The system uses decentralized data exchange rather than a central database, with encrypted communication between independent databases.

**India's Aadhaar** has enrolled over 1.3 billion people using biometric (fingerprint + iris) and demographic data. It provides strong uniqueness guarantees but under government control.

Strengths: Government identity is the strongest existing Sybil resistance -- states have centuries of experience tracking individuals. Estonia's system demonstrates that government ID can be extended to non-citizens.

Weaknesses: Requires trusting a government -- antithetical to the decentralized ethos of a commons. Government ID excludes undocumented populations. Government surveillance concerns are real. Cannot be the sole mechanism for a system designed to operate outside government authority.

#### Emerging Standards

**W3C Verifiable Credentials 2.0** was published as a W3C Standard in May 2025, providing a stable foundation for decentralized identity (W3C, 2025). The W3C DID Core specification has also reached recommendation status. The Digital Credentials API is projected to advance to Candidate Recommendation in 2026-2027, potentially aligning with Europe's EU Digital Identity Wallet rollout.

Strengths: Standards-based interoperability. Privacy-preserving by design. Supported by major industry players. Not tied to any single biometric or social graph.

Weaknesses: Standards define the envelope, not the Sybil resistance mechanism. VCs can attest to anything -- the strength depends entirely on the issuer. A VC from a government is strong; a VC from a friend is weak. The standard enables good Sybil solutions but does not itself constitute one.

### What Works and What Doesn't

The honest assessment of the current landscape:

| Approach | Sybil Resistance | Privacy | Accessibility | Gaming Resistance |
|----------|-----------------|---------|---------------|-------------------|
| Worldcoin/Biometric | Strong | Weak (biometric capture) | Moderate (needs Orb) | Strong |
| Humanity Protocol | Strong | Moderate (ZK + palm) | Moderate (needs device) | Moderate (newer) |
| Proof of Humanity | Moderate | Moderate | Weak (cost, connections) | Weak (deepfakes, rings) |
| BrightID | Moderate | Strong | Moderate (needs graph) | Moderate |
| Gitcoin Passport | Moderate | Moderate | Strong | Moderate (cost of forgery) |
| Government ID | Very Strong | Weak (state surveillance) | Variable by country | Strong |
| W3C VC/DID | Depends on issuer | Strong (by design) | Strong (standards-based) | Depends on issuer |

No single solution occupies the top-right corner of all four dimensions.

### What's Emerging (Frontier Research)

**Zero-Knowledge Proof-of-Identity (ZK-PoI):** A 2019 paper by Cerezo Sanchez (updated through 2025) proposes using ZK proofs to prove uniqueness against a government-issued identity without revealing which identity. The user proves "I am one of the set of valid identity holders" without revealing which one. This bridges government Sybil resistance with cryptographic privacy (arXiv:1905.09093).

**Self-Sovereign Identity with Attested Execution:** Research published in 2025 combines secure processor attestation with ZK membership proofs to create Sybil-resistant identity without centralized biometric storage (ResearchGate, 2025).

**AI-Enhanced Behavioral Analysis:** Human Passport's ML-powered Sybil detection model analyzes wallet behavior patterns across chains in real time. This represents a shift from static credentials to dynamic behavioral signals -- harder to game because the attacker must simulate realistic behavior patterns over time, not just produce a credential once.

**Composable Trust Layers:** The trend is toward layered approaches where multiple weak signals combine into strong assurance. This mirrors security's "defense in depth" principle. The W3C VC standard enables this architecturally; the remaining challenge is calibrating how many and which signals constitute "enough" for different contexts.

### Implications for Agent Commons

The Agent Commons needs Sybil resistance for three specific functions:

1. **Governance voting** -- one person, one vote (or one person, one allocation in QF)
2. **Reputation integrity** -- contributions attributed to real, unique individuals
3. **Economic fairness** -- rewards distributed to actual contributors, not sock puppets

Different functions may tolerate different Sybil resistance levels. Governance voting needs the strongest guarantees. Contribution attribution can tolerate some ambiguity if the system is self-correcting over time.

### Concrete Recommendation for 50-200 Person Pilot

**Recommended approach: Layered composable identity with graduated trust levels.**

**Layer 1 (Baseline -- required for participation):**
- Government-issued identity verified through a privacy-preserving mechanism. For a 50-200 person pilot, this can be as simple as a trusted onboarding coordinator who verifies ID in person or via video call and issues a signed credential. This is the "Proof of Humanity lite" approach -- it uses the existing social infrastructure of the founding community.
- This deliberately sacrifices decentralization for pragmatism at pilot scale. At 50-200 people, you likely know or can verify everyone. The decentralized mechanisms become necessary at scale, not at pilot.

**Layer 2 (Enhanced -- unlocks full governance participation):**
- Gitcoin Passport / Human Passport score above a threshold, combining multiple stamps (GitHub account age, on-chain activity history, social account verification).
- BrightID verification through connections within the pilot community.
- Both layers combined provide composable assurance.

**Layer 3 (Progressive trust -- reputation over time):**
- Contribution history within the commons itself becomes the strongest long-term Sybil signal. A sock puppet that maintains realistic contribution patterns for months is expensive to operate.
- Time-weighted activity analysis catches accounts that suddenly appear or behave anomalously.

**Why this works for a pilot:** At 50-200 people, the community is small enough that social knowledge supplements technical mechanisms. The founding members know each other. The risk is not a massive Sybil army; it is someone creating 2-3 accounts for extra voting power. The layered approach makes this expensive enough to deter without requiring iris scans.

**Why this needs to evolve:** This approach does not scale to 10,000+ participants where social knowledge breaks down. Before scaling, the commons must adopt or develop stronger technical Sybil resistance. The W3C VC + ZK-PoI direction is the most promising path for scale, but it is not production-ready today.

**Trade-offs accepted:** This recommendation sacrifices full decentralization at pilot scale. It relies on a trusted onboarding process, which creates a temporary centralization point. The bet is that pilot-scale trust can bootstrap the contribution-history layer, which becomes the strongest signal at scale.

### Can P2 Be Solved?

**Partially.** No solution simultaneously achieves strong Sybil resistance, full privacy, universal accessibility, and full decentralization. This is a fundamental trade-off, not a temporary gap. But the trade-off can be managed:

- **Best available approach:** Composable layered identity (Human Passport architecture) with ZK proofs for privacy and graduated trust levels based on behavior over time.
- **What happens if it can't be solved:** The commons must accept either (a) weaker Sybil resistance and design governance mechanisms that are more resilient to moderate Sybil presence (e.g., requiring supermajorities, quadratic mechanisms that reduce Sybil advantage), or (b) stronger identity requirements that sacrifice some privacy/accessibility.
- **Is this a dealbreaker?** No. The layered approach is "good enough" for a pilot and plausibly extensible. The deeper risk is that AI-generated Sybils become so cheap and convincing that even layered approaches fail -- see Section 2.5.

---

## 2.2 Non-Code Contribution Tracking

### What Exists Today

Git tracks code contributions with forensic precision: who wrote each line, when, how it changed over time, who reviewed it. This creates an objective (if imperfect) record of code contribution. Nothing comparable exists for design, strategy, mentoring, community building, documentation, project management, or relationship work.

#### Platform Activity Tracking

Existing tools track activity, not value:

- **Figma** tracks design file edits, comments, and iterations
- **Notion/Confluence** tracks page edits and views
- **Slack/Discord** tracks messages, reactions, and channel participation
- **Meeting platforms** track attendance and duration
- **GitHub** tracks issues, PRs, reviews, and discussions (beyond code)

The fundamental problem: activity is not contribution. Someone who writes 100 Slack messages may contribute less than someone who writes one message that reframes the entire problem. Measuring activity incentivizes busywork.

#### Peer Evaluation Systems

**360-degree feedback** is the most studied peer evaluation mechanism. Meta-analytic research found interrater reliability is moderate at best: subordinates showed mean reliability of .30, peers .37, and supervisors .50 (APA, 2012). A separate meta-analysis of 26 longitudinal studies (Smither, London, and Reilly, 2005) found 360 feedback does produce significant behavioral improvements.

However, gaming is documented and significant: manipulation of feedback ratings has been reported at GE, IBM, and Amazon. People are strategic in evaluating others to improve their own chances of being positively evaluated (APA, 2012). Structured feedback reduces bias-related discrepancies by 25% (Journal of Applied Psychology meta-analysis), but does not eliminate them.

**Coordinape** (used by Yearn Finance, BanklessDAO, Index Coop, and hundreds of other DAOs) implements peer-to-peer compensation allocation. Each member receives 100 GIVE tokens per epoch and distributes them to peers based on perceived contribution. Over 100 DAOs currently use Coordinape (CoinDesk, 2022; The Defiant, 2025).

Documented problems: Users forget to log contributions throughout the month, leading to incomplete information at allocation time. Founders consistently receive more tokens than their actual contribution warrants due to social dynamics -- team members are reluctant to give founders low allocations (RnDAO, 2025). This is a form of status bias that mirrors traditional organizational hierarchy.

**SourceCred** used a graph-based algorithm to calculate "Cred" based on how much value a contribution brought to a project. The system allowed each community to set its own weights for different contribution types, enabling non-code contributions (Discord moderation, onboarding calls, documentation) to earn Cred (SourceCred, 2022).

SourceCred's experiment is particularly instructive because it tried and ultimately wound down. The organization announced its wind-down in 2022, with contributors acknowledging that SourceCred was "better suited for smaller communities with emotional maturity and a high level of existing trust" (SourceCred Discourse, 2022). The algorithm could track activity but struggled to assess quality. It worked in high-trust environments and broke in low-trust ones -- exactly backwards from what a commons needs.

#### Outcome-Based Attribution

Rather than measuring activity or peer perception, outcome-based systems attribute value based on project results. Optimism's Retroactive Public Goods Funding (RPGF) embodies this approach: fund projects based on demonstrated impact rather than predicted impact (Optimism, 2025).

In 2024, RPGF rewarded over 400 builders with 20M OP across 3 rounds. However, the program acknowledged significant challenges: "Retro Funding is not reliable enough to drive contributions as [builders] have no way of knowing how impact is measured and when upcoming rounds will take place" (Optimism Governance Forum, 2025). This is the fundamental tension of retroactive funding -- it rewards past value but provides no forward-looking signal to guide current effort.

#### The "Invisible Work" Problem

Star and Strauss (1999) established the foundational taxonomy of invisible work in their landmark paper "Layers of Silence, Arenas of Voice." Their central insight: "No work is inherently either visible or invisible. We always 'see' work through a selection of indicators." What gets measured depends on what we choose to make visible, and that choice is political (Star & Strauss, 1999).

Types of invisible work identified include:
- **Articulation work** -- the effort of coordinating, scheduling, and making things fit together
- **Emotional labor** -- managing others' emotions, creating psychological safety, resolving conflict
- **Background maintenance** -- keeping systems running, onboarding newcomers, maintaining documentation

These are precisely the contributions that become more valuable as AI handles routine production. The highest-value human contributions in an AI-augmented system -- mentoring, relationship building, strategic framing, community cultivation -- are the hardest to measure.

### What Works and What Doesn't

| Approach | Measures | Gaming Resistance | Quality Assessment | Scalability |
|----------|----------|-------------------|-------------------|-------------|
| Activity tracking | Quantity | Very weak | None | High |
| 360-degree review | Peer perception | Moderate | Moderate | Low-moderate |
| Coordinape (GIVE tokens) | Peer allocation | Moderate | Moderate | Moderate |
| SourceCred (graph algorithm) | Activity + graph position | Moderate | Weak | Moderate |
| Outcome-based (RPGF) | Project results | Strong | Strong | Low (requires evaluation) |
| Shapley value | Marginal contribution | Strong (theoretical) | Strong (theoretical) | Very low (computational) |

#### Shapley Values: The Theoretical Gold Standard

The Shapley value from cooperative game theory provides the mathematically unique fair allocation that satisfies efficiency, symmetry, dummy player, and additivity axioms (Shapley, 1953). It calculates each player's average marginal contribution across all possible coalitions.

For team contribution attribution, Shapley values answer: "How much did each person contribute to the team's output?" by considering what would have happened with every possible subset of the team.

The problem is computational: calculating exact Shapley values requires evaluating 2^n coalitions for n players. For a 20-person team, that is over 1 million coalitions. Approximation methods exist (Monte Carlo sampling of coalition orderings), but they require a well-defined value function -- you need to be able to answer "what would this subset of the team have produced?" which is counterfactual and often unknowable.

Practical applications have been limited to domains where the value function is well-defined: marketing attribution (which channels contributed to a sale), ML feature importance (SHAP values), and simple cooperative games. Extending to complex team work where contributions interact non-linearly remains an open research problem.

### What's Emerging (Frontier Research)

**AI-Assisted Contribution Evaluation:** LLMs can potentially assess qualitative contributions -- evaluating design quality, strategic insight, documentation clarity, or mentoring effectiveness. The 2025 LLM evaluation landscape includes frameworks like TruLens (for transparency and fairness) and RAGAS (for retrieval-augmented generation quality) (ConfidentAI, 2025; Galileo, 2025).

The potential: An LLM with access to project context could evaluate "this design review identified a fundamental architectural flaw that saved 3 weeks of rework" versus "this design review rubber-stamped an existing decision." The challenge: LLM evaluation is itself gameable (prompt engineering to make contributions look more impressive), subject to bias (training data skews toward certain contribution styles), and requires ground truth for calibration.

**Self-Managing Organization Models:** Buurtzorg (14,000+ employees, no middle management) demonstrates that non-hierarchical organizations can function at scale without individual contribution metrics. Teams of up to 12 nurses are collectively responsible for outcomes, with peer support and coaching replacing individual performance review (Springer, 2024). Morning Star uses a similar collective accountability model.

The insight: these organizations solve the attribution problem by dissolving it -- they measure team outcomes, not individual contributions. Individual accountability comes from small team social dynamics (everyone knows who is pulling their weight at Dunbar scale). This suggests the Agent Commons might not need to solve individual contribution valuation at the Forg level if Forgs are small enough for social accountability to work.

**Contribution DAGs (Directed Acyclic Graphs):** Some projects are experimenting with recording contributions as nodes in a graph, with edges representing dependencies. "Alice's design enabled Bob's implementation which enabled Carol's launch." This creates a causal attribution chain that is more nuanced than individual activity metrics but less computationally intensive than full Shapley values.

### Implications for Agent Commons

The Agent Commons has a structural advantage for contribution tracking: AI governance can observe contributions in real time across all platforms. An AI system with access to the project repository, communication channels, design tools, and meeting records could construct a far richer picture of contribution than any human reviewer or simple algorithm.

However, this creates a surveillance tension: comprehensive AI observation of all contributions is the most powerful evaluation mechanism but also the most invasive. The system must balance observation depth with contributor privacy and autonomy.

**Recommended approach for the commons:**

1. **Team-level outcomes as the primary metric** -- Forgs are evaluated on what they produce, not on individual activity within the Forg. This follows the Buurtzorg model and avoids Goodhart's Law at the individual level.

2. **Peer allocation within Forgs** -- Coordinape-style GIVE tokens for intra-Forg distribution, acknowledging that teammates have the best information about individual contributions. Keep Forgs small enough (5-15 people) for social accountability.

3. **AI-assisted quality signals** -- LLM evaluation of contribution artifacts (design documents, code reviews, strategic analyses) as a supplementary signal, not a primary metric. Use for identifying exceptional contributions that peers might undervalue (the "invisible work" problem).

4. **Contribution DAGs for cross-Forg attribution** -- When Forg outputs depend on other Forgs' work, record the dependency chain. This enables approximate Shapley-like attribution at the inter-Forg level without requiring individual-level computation.

### Can P4 Be Solved?

**Not completely.** The fundamental problem is that the highest-value contributions in an AI-augmented system -- mentoring, strategic insight, relationship building, community cultivation -- are precisely those that resist quantification. Goodhart's Law (Goodhart, 1975) guarantees that any specific metric will be gamed: "When a measure becomes a target, it ceases to be a good measure."

- **Best available approach:** Multi-layered evaluation combining team outcomes, peer allocation, AI-assisted quality signals, and contribution dependency graphs. No single mechanism; the combination provides resilience.
- **What happens if it can't be solved:** The commons defaults to measuring what can be measured (code, artifacts, explicit deliverables) and under-compensating what cannot (mentoring, community building, emotional labor). This reproduces the exact bias that traditional organizations have.
- **Is this a dealbreaker?** No, but it is a significant design constraint. The commons can launch with imperfect contribution measurement and iterate. The key is to avoid locking in a single metric that creates perverse incentives. The Buurtzorg insight -- dissolve the problem via small-team social accountability -- is the most pragmatic path.

---

## 2.3 Price-Signal Mechanisms for a Commons

### The Problem: Hayek's Ghost

Friedrich Hayek's 1945 essay "The Use of Knowledge in Society" established the foundational argument: the information available to society is the aggregate of dispersed knowledge possessed by individuals, and it is conceptually impossible to convey this information to a central authority for processing (Hayek, 1945). The price system solves this by compressing supply, demand, quality, scarcity, and opportunity cost into a single actionable number.

The economic calculation problem, first articulated by Mises in 1920 and elaborated by Hayek, is the reason central planning failed: without price signals, planners cannot know what to produce, in what quantities, using which resources. The Soviet Union's systemic misallocation -- producing mountains of unwanted goods while critical needs went unmet -- was the empirical confirmation.

The Agent Commons faces a version of this problem. It produces public goods, shared infrastructure, and knowledge with near-zero marginal cost -- precisely the domains where price signals break down. Without a mechanism that aggregates dispersed information about value, the commons risks the same calculation problem that killed central planning.

Multi-dimensional reputation (measuring contribution quality, community standing, governance participation, etc.) is informationally inferior to prices because it cannot be compressed into a single actionable signal. A contributor with "high code quality, moderate community engagement, low governance participation" does not translate into "this person's work is worth X." The system needs information density that reputation alone cannot provide.

### What Exists Today

#### Quadratic Funding (QF)

Gitcoin's implementation of Buterin, Hitzig, and Weyl's (2019) quadratic funding mechanism has distributed over $67 million to more than 5,000 projects (Gitcoin, 2025). The most recent round (May 2025) distributed over $1.2 million to 235 projects.

QF works by amplifying small contributions: the matching formula weighs the number of individual contributors more than the amount contributed. This means a project with 100 $1 donations receives more matching funds than a project with one $100 donation, even though the direct funding is identical.

**As a price signal:** QF aggregates distributed preferences about which public goods are valuable. The amount of matching funding a project receives reflects community-wide demand, weighted toward broad support over concentrated support. This is closer to a price signal than a vote because it incorporates intensity of preference (people contribute real money) and corrects for plutocratic bias (quadratic weighting).

**Documented problems:**
- **Sybil vulnerability:** The simplest attack is splitting contributions across multiple accounts. "As the number of original contributions decrease in size but increase in number, the ratio of matching funds to donations increases" -- this is the exact mathematical property that makes QF good for aggregation and also makes it vulnerable to Sybils (Gitcoin, 2025).
- **Collusion:** About 35 flags were reported in GG8 for collusion (Block Science, 2022). As match pools grew from $450k (GG7) to $965k (GG11), gaming incentives increased proportionally.
- **Quality improvements are real but costly:** The GG20 round showed a 20% decrease in crowdfunders but improved quality (fewer Sybils, more substantial contributions). Defense requires continuous ML tuning and human review.
- **Information aggregation quality:** QF reflects demand for projects but not the quality of their outputs. A popular project may produce mediocre results; an unpopular project may produce breakthrough work. QF is a demand signal, not a quality signal.

#### Retroactive Public Goods Funding (RPGF)

Optimism's RPGF attempts to solve the quality problem by funding based on demonstrated impact rather than predicted demand. In 2024, over 400 builders received 20M OP across three rounds (Optimism, 2025). The program has 850M OP dedicated to ongoing retroactive funding.

**As a price signal:** RPGF is a backward-looking value assessment. Evaluators examine what projects actually produced and allocate rewards accordingly. This provides quality information that QF lacks.

**Documented problems:**
- Builders cannot predict funding, making it unreliable as a forward-looking signal: "builders have no way of knowing how impact is measured and when upcoming rounds will take place" (Optimism Governance Forum, 2025).
- Evaluator capture risk -- a small number of evaluators determine allocation for a large pool.
- The 2025 evolution toward ongoing impact evaluation (rather than discrete rounds) may address the unpredictability concern.

#### Prediction Markets as Value Signals

Google ran internal prediction markets from 2005, using artificial currency ("Goobles") to forecast product launch dates, office openings, and strategic decisions (Harvard Business School, 2008). HP and Microsoft ran similar internal markets. External prediction markets have exploded: from less than $100 million/month in early 2024 to over $13 billion/month by late 2024 (InternationalBanker, 2025).

**As a price signal for contributions:** Prediction markets could estimate "what is the probability that Project X delivers significant value within 6 months?" This creates a forward-looking value signal that QF and RPGF lack. If prediction market prices correlate with actual outcomes, they provide real-time information aggregation about project value.

**Limitations:** Prediction markets require well-defined resolution criteria (what counts as "significant value"?). They work best for binary or quantifiable outcomes, not for qualitative assessment. Thin markets (few participants) produce noisy signals. Internal prediction markets at Google showed that employees were well-calibrated on technology questions but poorly calibrated on business strategy questions (Google Prediction Market Paper, Duke CS).

#### Harberger Tax / Common Ownership Self-Assessed Tax (COST)

Weyl and Posner's proposal in "Radical Markets" (2018): property owners self-assess their property's value and pay tax on that assessed value. Anyone can purchase the property at the self-assessed price, creating an incentive for honest valuation. If you under-assess, someone buys your property cheaply. If you over-assess, you pay excessive tax.

**As a commons mechanism:** COST could apply to resource allocation within the commons. Forgs could self-assess the value of resources they hold (compute time, expert talent, priority access) and pay a tax to the commons pool. This creates a continuously updated price signal for scarce resources without requiring a traditional market.

Vitalik Buterin has noted that COST is "becoming increasingly popular in the Ethereum world as a way to actually set real prices in meaningful markets" (Buterin, 2018). The mathematical property is that a tax set between zero and the turnover rate optimizes for both allocative and investment efficiency -- though never perfectly for both simultaneously.

**Limitations:** COST requires that assets be well-defined and transferable. It is unclear how to apply COST to intangible commons resources like "the attention of a domain expert" or "community trust." The mechanism also requires sufficient liquidity -- if nobody wants to buy the asset at any price, the self-assessment has no market check.

#### Combinatorial Auctions

Participants bid on bundles of items or projects, expressing preferences over combinations rather than individual items. This mechanism has been used for spectrum auctions (FCC) and could be adapted for commons project prioritization.

**As a commons mechanism:** Agents could use reputation tokens to bid on project bundles, expressing "I value the combination of Project A and Project B more than either alone." This captures complementarities that simple voting or QF cannot.

**Limitations:** Computationally complex (NP-hard in general). Requires participants to have clear preferences over bundles, which is cognitively demanding. Practical implementations require approximation algorithms.

### What's Emerging

**AI-Generated Synthetic Price Signals:** The frontier question is whether AI can create price-like information density from multi-dimensional data. Research on multi-scale forecasting combines historical price dynamics with semantic representations from unstructured text using attention-based architectures (arXiv, 2025). Principal Component Analysis reduces dimensionality while preserving information content.

Applied to a commons: an AI system with access to contribution data, project outcomes, community sentiment, and resource allocation could potentially generate a synthetic "value signal" that compresses multi-dimensional information into an actionable number. This is speculative but represents the most promising direction for resolving the calculation problem without traditional prices.

**Dynamic Quadratic Funding:** Gitcoin's 2025 strategy includes "Dynamic Quadratic Funding" that adjusts eligibility and caps to benefit emerging builders and reduce concentration (Gitcoin, 2025). This is an evolution of static QF that incorporates temporal and contextual factors into the matching formula.

**Hybrid Forward-Backward Mechanisms:** Combining QF (forward-looking demand signal) with RPGF (backward-looking quality signal) could create a more complete value picture. A project funded via QF in year 1 gets RPGF bonuses in year 2 if it delivers demonstrated impact. This creates both a demand signal and a quality feedback loop.

### Implications for Agent Commons

The commons cannot rely on a single price-signal equivalent. The recommendation is a multi-mechanism approach:

1. **Quadratic funding** for project selection and resource allocation (demand signal)
2. **Retroactive evaluation** for quality assessment and reward adjustment (quality signal)
3. **Internal prediction markets** for forward-looking value estimation of ongoing projects
4. **Harberger-style self-assessment** for scarce resource allocation within the commons
5. **AI-synthesized composite signal** that compresses these four inputs into a single "commons value index" per project/contributor -- the synthetic price signal

This is more complex than capitalism's price system. That complexity is the honest cost of operating in the domain where prices fail.

### Can P5 Be Solved?

**Not with the same elegance as prices.** Capitalism's price system achieves its information density through decentralized market transactions over centuries of institutional evolution. The commons cannot replicate this in a designed system. The calculation problem is real and does not go away just because the system is a commons rather than a command economy.

- **Best available approach:** Multi-mechanism hybrid (QF + RPGF + prediction markets + Harberger + AI synthesis). This provides multiple complementary signals that together approximate the information density of prices, at the cost of greater complexity.
- **What happens if it can't be solved:** The commons allocates resources less efficiently than a market economy. Projects that are popular but low-quality get over-funded (QF bias). Projects that are high-quality but obscure get under-funded (discovery problem). The system drifts toward the very misallocation problems that plagued central planning, albeit in milder form.
- **Is this a dealbreaker?** Potentially. If the commons consistently misallocates resources, it will produce worse outcomes than capitalist alternatives, and contributors will leave. The bet is that AI synthesis of multiple signals can approach price-like information density. This is unproven. The honest answer: this is the most intellectually dangerous of the four problems because the failure mode is invisible (gradual efficiency loss) rather than catastrophic (sudden collapse).

---

## 2.4 Concentration Bounding

### The Mathematical Challenge

Preferential attachment -- the principle that nodes with more connections attract connections faster ("the rich get richer") -- produces power-law degree distributions in virtually all networks studied (Barabasi & Albert, 1999). The resulting power-law exponent gamma = (2 + alpha) / alpha, with a minimum of gamma = 3 for linear preferential attachment (Wikipedia, Scale-free networks). This means extreme concentration is the mathematical default for any system with network effects.

Piketty's r > g framework provides the economic parallel: when the return on capital exceeds economic growth, wealth concentrates. Historical data from 16 countries (1870-2020) shows that a one percentage point increase in the r - g gap is associated with a 3.7% increase in the top 1% wealth share (Tandfonline, 2025). Though empirical support is mixed across countries, the mathematical mechanism is clear: even small persistent advantages compound into extreme concentration over time.

The question for the Agent Commons is not whether concentration will occur -- it will -- but whether it can be bounded below the threshold where it enables governance capture.

### Empirical Concentration Data

#### DAOs: Extreme Concentration

The most alarming empirical data comes from DAOs, which were explicitly designed for decentralized governance. The Cambridge Centre for Alternative Finance (December 2024) found that the 10 largest DeFi DAOs had Gini coefficients ranging from 0.97 to 0.99 for token distribution (DL News, 2024). For context, South Africa, the most income-unequal country in the world, had a Gini coefficient of 0.63. MakerDAO's Gini coefficient was 0.99.

At Aave, the top 121 wallets hold over 73% of token supply (Cambridge, 2024). The minimal quorum size -- the fewest number of addresses that could unilaterally decide a vote -- is often around 3 (arXiv:2410.13095). Research characterizes this as conforming to the "iron law of oligarchy": a statistically significant correlation exists between larger DAOs and greater inequality (arXiv:2407.10945).

The governance capture mechanism is self-reinforcing: "Early adopters or participants with more resources who acquired tokens at lower prices are more likely to gain disproportionate influence over governance decisions, and this dynamic reinforces itself in a negative feedback loop" (BeInCrypto, 2025). Those with more tokens shape governance to favor policies that benefit them, further consolidating power.

#### Open Source: The 1% Rule

Research on Apache Software Foundation projects found Gini index values between 0.6 and 0.9 for 88.97% of analyzed projects (PLOS One, 2016). Contributor engagement follows a power-law distribution. The "90-9-1 rule" (90% lurk, 9% contribute sparingly, 1% create most content) was found to be inaccurate -- the actual ratio is closer to 75-20-5 -- but the extreme concentration is real (ResearchGate, Participation Inequality).

In Linux kernel development, only 7.5% of contributions (measured by lines changed) came from individual developers; the rest came from corporate contributors (Oracle, 2025). This represents a different form of concentration: corporate rather than individual.

#### Stack Overflow: Reputation Concentration

Stack Overflow's reputation system, designed as a meritocracy, produces extreme inequality. Research identified four types of reputation fraud including voting rings where communities form to upvote each other repeatedly (arXiv:2111.07101). The detection algorithms flag suspicious communities, with 60-80% of flagged users subsequently experiencing reputation reductions -- but this means 20-40% of flagged users were wrongly identified or evaded enforcement.

### What Concentration Level Enables Governance Capture?

This is the critical threshold question. Research provides some guidance:

- **DAO governance:** When the minimal quorum size is 3 or fewer addresses, governance capture is trivially achievable (arXiv:2410.13095). A working threshold appears to be: if the top 10% of participants control more than 50% of voting power, governance capture becomes feasible through coalition formation.
- **The Nakamoto coefficient** measures the minimum number of entities needed to compromise a system. For many DAOs, this is single digits (Cornell, 2023).
- **Practical threshold for the commons:** Governance capture becomes dangerous when any coalition smaller than the square root of total participants can control outcomes. For a 200-person pilot, this means capture by fewer than ~14 people. For 10,000 participants, capture by fewer than ~100.

### Countermeasures: What's Been Tried

#### Quadratic Voting

Quadratic voting (QV) makes each additional vote on the same issue progressively more expensive: 1 vote costs 1 credit, 2 votes cost 4 credits, 3 votes cost 9 credits (Lalley & Weyl, 2015). The theoretical result: expected inefficiency decays like 1/n as population grows, meaning QV approaches optimal outcomes at scale (Lalley & Weyl, 2015).

QV reduces the power of concentrated holdings because a whale with 10,000 credits gets only 100 votes (sqrt of 10,000), while 100 people with 100 credits each get 10 votes each (1,000 total votes). This is a 10:1 advantage reduction compared to 100:1 under simple token voting.

Limitation: QV assumes credits are distributed equally or purchased at market rates. If credits can be accumulated through contribution (like reputation), QV alone does not prevent concentration -- it only mitigates its governance impact. Additionally, QV with unequal budgets can be combined with reputation scores, as explored in federated learning contexts (arXiv:2401.01168).

#### Time Decay on Reputation

If reputation decays over time (e.g., 20% annual decay), inactive historical contributors lose influence while active contributors maintain it. This prevents "founding member capture" where early contributors accumulate permanent advantage.

Network science research shows that integrable aging destroys the power-law tail of preferential attachment models (Springer, 2017). The mathematical result: time decay can genuinely change the degree distribution from power-law to exponential, which would eliminate extreme concentration.

Limitation: Time decay punishes sabbaticals, caregiving leave, and legitimate periods of reduced participation. It penalizes people for having lives outside the commons. Design must include mechanisms for "reputation freezing" during justified absences.

#### Contribution Caps Per Period

Hard caps on how much reputation or influence any single participant can earn per time period. This is analogous to progressive taxation -- the marginal return on contribution effort decreases at high levels.

Limitation: May discourage exceptional contribution. If the best designer in the commons hits their reputation cap in week 2 of the month, they have no incentive to continue contributing that month. The cap must be set high enough to avoid discouraging genuine high performers while low enough to bound concentration.

#### Redistribution Mechanisms

**Reputation taxation:** A percentage of accumulated reputation is redistributed to all participants each period, analogous to wealth taxation. This directly counters r > g by reducing r for the highest holders.

**Universal basic reputation (UBR):** Every verified participant receives a base allocation of reputation each period, regardless of contribution. This creates a floor and reduces relative concentration even as absolute concentration grows.

**Periodic partial resets:** Reputation is partially reset at regular intervals (e.g., annually), with some portion carried forward and the rest redistributed. This prevents indefinite accumulation while still rewarding long-term participation.

### Historical Precedents

**Antitrust:** The Progressive Era (1890s-1920s) developed most of the analytic tools for combating economic concentration. Antitrust enforcement appears to work -- concentration in U.S. manufacturing began rising after merger policy became less aggressive with the 1982 Merger Guidelines (Peltzman). But antitrust requires external enforcement authority, which a self-governing commons must generate internally.

**Progressive taxation:** Tax policy has historically been the most effective tool for reducing inequality (Equitable Growth, 2025). Top marginal rates above 70% (as in the 1950s-70s US) correlate with lower concentration. But taxation requires a state; the commons equivalent is reputation taxation, which has no historical precedent at scale.

**Land reform:** India's land reform legislation (1958-1992) showed measurable poverty reduction effects (LSE, Besley). Georgist land value taxation captures "unearned income" from land appreciation and redistributes it. The Harberger tax generalizes this principle to all property. The commons parallel: capturing "unearned reputation" from network effects and redistributing it.

### Network Science Design Rules

Can you design attachment rules that bound power-law exponents? The research says: conditionally, yes.

- **Spatial preferential attachment** (where nodes have physical positions and connection probability depends on distance) produces bounded power-law exponents (arXiv:1210.3830). The commons equivalent: limiting how much reputation from distant communities translates across contexts.
- **Fitness models with aging** show that aging effects (time decay) destroy power-law tails when aging is integrable (Springer, 2017). This is the mathematical justification for time-decay mechanisms.
- **Random removal of nodes** impacts scale-free networks very little, but targeted removal destroys connectivity quickly (Wikipedia, Scale-free networks). This means the commons is robust to random participant departure but vulnerable to targeted removal/departure of high-concentration nodes -- another argument for bounding concentration.

### Implications for Agent Commons

The evidence strongly suggests that concentration is the default outcome and must be actively countered. The question is not whether to implement bounding mechanisms but which combination provides the best protection without destroying incentives.

**Recommended bounding stack:**

1. **Quadratic mechanisms everywhere:** QV for governance, QF for funding, quadratic weighting for reputation influence. This provides a sqrt(n) reduction in concentration impact across all systems.

2. **Time decay with freezing:** 15-25% annual reputation decay, with the ability to freeze reputation during verified absences. This prevents permanent founding-member advantage while accommodating real life.

3. **Contribution caps per epoch:** Logarithmic caps on reputation earned per period. A contributor earning 2x the median is rewarded. A contributor earning 100x hits a cap. The specific threshold requires empirical calibration.

4. **Universal basic reputation:** Every verified member receives a base reputation allocation each period. This ensures even new or low-contribution members have governance voice and reduces the Gini coefficient by raising the floor.

5. **Transparency and monitoring:** Publish concentration metrics (Gini, Nakamoto coefficient, minimal quorum size) in real time. Set explicit thresholds for governance alerts (e.g., if Nakamoto coefficient drops below sqrt(N), trigger redistribution).

### Falsification Condition #4: "Concentration is structurally inevitable"

**Assessment: Partially supported but not conclusive.**

The evidence is concerning. Every empirical system studied -- DAOs, open source, Stack Overflow, academic citations, ride-sharing platforms -- develops extreme concentration. DAO Gini coefficients of 0.97-0.99 are not edge cases; they are the norm. The mathematical models (preferential attachment, r > g) explain why concentration is the default.

However, "structurally inevitable" is stronger than "the default outcome." The mathematical models also show that countermeasures can change the distribution: time decay destroys power-law tails. Quadratic mechanisms reduce concentration impact by sqrt(n). Progressive caps limit accumulation.

The honest assessment: Concentration is the overwhelming default. Bounding it requires active, continuous, multi-mechanism intervention. The question is whether a system can sustain that intervention over time without the bounding mechanisms themselves being captured by concentrated interests. This is the recursive governance problem (P1) manifesting within the concentration problem (P6).

The strongest evidence against structural inevitability comes from Buurtzorg: 14,000+ employees, no hierarchy, no concentration of formal power. But Buurtzorg's nurses do not compete for scarce rewards -- they provide healthcare in autonomous teams. The commons may have a more competitive dynamic that drives concentration harder.

### Can P6 Be Solved?

**Managed, not solved.** Concentration can be bounded through continuous active intervention, but it cannot be eliminated. The mathematical and empirical evidence is overwhelming: preferential attachment, compounding returns, and network effects produce concentration in every system with even weak feedback loops.

- **Best available approach:** The five-mechanism bounding stack described above (quadratic mechanisms, time decay, caps, UBR, transparency). No single mechanism is sufficient; the combination provides layered protection.
- **What happens if it can't be solved:** The commons reproduces the same power concentration as any other system, just denominated in reputation rather than money. Governance capture follows. The commons becomes a new form of plutocracy dressed in egalitarian language. This is exactly what happened to DAOs.
- **Is this a dealbreaker?** Potentially. This is the falsification condition that the research most strongly supports. The saving grace is that the failure mode is gradual (concentration compounds over years, not days), giving the system time to detect and respond. The real question is whether the governance mechanisms for adjusting the bounding parameters can themselves resist capture. If the most-concentrated participants vote to weaken the bounding mechanisms -- which is the rational self-interested action -- the system fails. This means the bounding mechanisms must be constitutional (not subject to normal governance votes) or protected by external structure.

---

## 2.5 Reputation Gaming Resistance

### The Universal Law of Gaming

Every reputation system ever deployed at scale has been gamed. This is not a bug in specific implementations -- it is a structural property of measurement in adversarial environments. Goodhart's Law (1975) states the principle: "When a measure becomes a target, it ceases to be a good measure." Campbell's Law extends it: "The more any quantitative social indicator is used for social decision-making, the more subject it will be to corruption pressures and the more apt it will be to distort and corrupt the social processes it is intended to monitor."

The Agent Commons must design for gaming as a certainty, not a possibility.

### Documented Gaming Across Platforms

#### eBay

When eBay removed the reputation history of all sellers, sellers with previously low scores "portrayed themselves as high quality sellers and manipulated buyers" (Resnick & Zeckhauser, ResearchGate). Strategic behavior in eBay's reputation system is well-documented: sellers time their feedback strategically, retaliate against negative reviews, and create new accounts to escape bad histories.

#### Stack Overflow

Research identified four types of reputation fraud (arXiv:2111.07101):
1. **Voting rings** -- communities forming to upvote each other repeatedly
2. **Sockpuppet accounts** -- one person operating multiple accounts for self-upvoting
3. **Question-answer collusion** -- pre-arranged Q&A pairs designed to harvest reputation
4. **Tag manipulation** -- gaming tag choices to maximize reputation from the same content

Detection algorithms flag suspicious users, with 60-80% confirmed as gaming. Stack Overflow uses "several daily heuristics to detect strange user upvoting patterns" with automatic nullification. A 2016 report from a top-2% user cautioned that voting rings had seen "a spike recently" (SO Blog, 2009).

#### Amazon

Amazon blocked over 275 million suspected fake reviews in 2024 (Amazon, 2024). Despite machine learning models analyzing thousands of data points (reviewer history, account relationships, behavioral patterns) and Large Language Models analyzing text for incentivized review cues and Deep Graph Neural Networks mapping seller-reviewer-product networks, internal audits show 16% of reviews may still be fake or manipulated. In competitive categories (supplements, electronics, home goods), 30-40% of reviews show manipulation signals (SalesDuo, 2025).

Amazon's arms race is instructive: the most sophisticated detection system in e-commerce, backed by billions of dollars of engineering investment, still fails to catch a significant fraction of gaming. This suggests an inherent upper bound on detection effectiveness.

#### Uber

Uber's rating system demonstrates gaming driven by survival pressure: drivers with low ratings are deactivated. Research documented "cherry picking" (selecting profitable, high-rated rides), "reputation auditing" (constantly monitoring and disputing ratings), and collective algorithm manipulation (drivers simultaneously turning off apps to create artificial scarcity and surge pricing) (Vasudevan & Chan, 2022; ResearchGate, 2019).

The rating system also exhibits bias: negative reviews are weighted far more heavily than positive ones, creating asymmetric incentives. Drivers optimize for "not getting 1-star reviews" rather than "providing excellent service" -- a textbook Goodhart's Law distortion.

#### Academic Citations

Citation gaming is an entire industry. Documented strategies include (Springer, 2025; MIT Press, 2019):
- **Self-citation inflation** -- preferentially citing own papers to boost h-index
- **Citation cartels** -- groups colluding to cite each other, charging $5-$10 per reference
- **Salami slicing** -- splitting one study into multiple minimally publishable units that cite each other
- **Gift authorship** -- adding names to papers for mutual citation benefit
- **Editorial coercion** -- editors requiring citations to their journal's papers as a condition of publication

The h-index "can be more easily gamed than the number of total citations, with self-citers preferentially citing papers that readily boost the H-index" (PMC, 2024).

### AI-Assisted Gaming: The New Frontier

The convergence of LLMs and reputation systems creates qualitatively new gaming threats:

**LLM-generated fake contributions:** An LLM can produce plausible code, documentation, design reviews, strategic analyses, and community discussions at scale. In an experimental framework on Mastodon, "participants correctly identified the nature of bot versus human users only 42% of the time despite knowing the presence of both bots and humans" (arXiv:2402.07940). If human judges cannot distinguish LLM contributions from human contributions in controlled experiments, how will a commons reputation system do so?

**Automated Sybil creation:** "Fraud-as-a-Service" using dark LLMs, deepfake voice/video, and agentic AI workflows can automate the entire fraud pipeline (Masood, 2025). The threat model has shifted "from human actors leveraging GenAI tools to autonomous agents capable of independent reasoning, planning, and execution" (arXiv:2601.21963). A sophisticated attacker could create an army of LLM-powered sock puppets, each maintaining a realistic-looking contribution pattern, interacting with the community, and accumulating reputation over months.

**Scale of threat:** A university competition produced 252 unique fake news stories using LLMs (NAACL, 2025). Criminal enterprises use AI to create "thousands of social media posts, articles, and comments that promote fraudulent schemes, creating the illusion of a massive, organic community interest" (CyberSecurityInstitute, 2025). The cost of creating a convincing fake identity with AI assistance is dropping rapidly.

### Multi-Signal Systems: More Resistance or More Attack Surface?

Combining multiple reputation signals (code quality + peer review + community engagement + governance participation) theoretically increases gaming resistance because gaming all dimensions simultaneously is harder than gaming any single dimension.

But it also increases attack surface. Modern multi-modal AI attacks "combine multiple media types, with a synthetic identity potentially including a forged document, an AI-generated selfie, and manipulated behavioral signals, all designed to reinforce the illusion of legitimacy" (Microblink, 2025). Multi-signal systems may give attackers more dimensions to exploit rather than fewer.

The key variable is whether the signals are independent. If an attacker who games one signal can easily transfer that credibility to other signals (e.g., high GitHub reputation makes peer reviewers more lenient), then multi-signal provides little additional resistance. If the signals are genuinely independent (gaming code quality does not help with gaming community building), then multi-signal provides multiplicative resistance.

### Dynamic Mechanism Adjustment

Can the reputation system evolve faster than the gamers? This is the core question of adversarial mechanism design.

The evidence is mixed. Amazon's detection system, with billions of dollars of engineering investment, runs an ongoing arms race against review manipulators and still fails to catch 16%+ of fakes. But Amazon faces an asymmetric problem: the attackers are financially motivated and professionally organized. In a commons, the gaming motivation is reputation and governance power, which may attract less sophisticated adversaries -- or may attract more sophisticated ones if the stakes are high enough.

**AI-enhanced detection has potential:** Dynamic behavioral analysis (monitoring contribution patterns over time) is harder to game than static credential verification because the attacker must maintain realistic behavior patterns continuously, not just pass a one-time check. The Human Passport ML model that analyzes wallet behavior in real time represents this approach (The Defiant, 2025).

**Red teaming as institutional practice:** The commons should continuously employ adversarial teams whose explicit job is to game the reputation system. Any successful gaming strategy discovered by the red team triggers a mechanism adjustment. This creates an institutional immune system that evolves in response to attacks.

### Implications for Agent Commons

**The gaming problem cannot be solved; it can only be managed through continuous adversarial evolution.**

Recommended gaming resistance architecture:

1. **Multi-signal with independence enforcement:** Combine signals from genuinely independent dimensions (code quality, peer review, governance participation, community building). Ensure that credibility in one dimension does not automatically transfer to others.

2. **Behavioral analysis over credential verification:** Weight long-term behavioral patterns more heavily than point-in-time credentials. A contribution history that looks realistic over 6 months is harder to fake than a set of verified stamps.

3. **AI-powered anomaly detection:** Use LLMs to detect LLM-generated contributions. Use graph neural networks to detect coordinated gaming rings. Use behavioral analysis to detect pattern anomalies. This is an arms race that the commons must actively fight.

4. **Institutional red teaming:** Permanent adversarial team with incentives to discover gaming strategies. Publish anonymized red team reports to build community gaming awareness.

5. **Graceful degradation:** Design the governance and reward systems to function acceptably even with 5-15% gaming. If the system breaks when 5% of participants are fake, it is too fragile. If it functions adequately with 15% gaming, it has sufficient margin.

6. **Constitutional protections:** Some reputation rules (like the bounding mechanisms from Section 2.4) should be protected from modification by normal governance processes. If a gaming cartel gains governance power, they should not be able to vote to remove the anti-gaming mechanisms.

---

## Ranked Solution Candidates

### P2: Sybil Resistance

| Rank | Approach | Feasibility | Privacy | Accessibility | Recommendation |
|------|----------|-------------|---------|---------------|----------------|
| 1 | Layered composable identity (pilot) | High | Moderate | High | **Recommended for pilot** |
| 2 | Human Passport + ML behavioral analysis | High | Moderate | High | Scale-up path |
| 3 | ZK-Proof-of-Identity against government ID | Medium | High | Moderate | Long-term aspiration |
| 4 | Humanity Protocol (palm biometrics + ZK) | Medium | Moderate | Moderate | Worth monitoring |
| 5 | BrightID social graph | Medium | High | Moderate | Supplementary signal |
| 6 | Worldcoin (iris scanning) | High (technical) | Low | Moderate | Unacceptable privacy trade-off |

### P4: Non-Code Contribution Valuation

| Rank | Approach | Accuracy | Gaming Resistance | Scalability | Recommendation |
|------|----------|----------|-------------------|-------------|----------------|
| 1 | Team-level outcomes (Buurtzorg model) | Moderate | High | High | **Primary mechanism** |
| 2 | Peer allocation within small teams (Coordinape) | Moderate | Moderate | Moderate | Intra-Forg distribution |
| 3 | AI-assisted quality signals | Unknown | Low-moderate | High | Supplementary, experimental |
| 4 | Contribution DAGs for cross-team attribution | Moderate | Moderate | Moderate | Inter-Forg attribution |
| 5 | Outcome-based retroactive evaluation (RPGF) | High | High | Low | Quality correction layer |
| 6 | Shapley value estimation | High (theoretical) | High | Very low | Research interest only |

### P5: Price-Signal Equivalent

| Rank | Mechanism | Information Density | Gaming Resistance | Maturity | Recommendation |
|------|-----------|-------------------|-------------------|----------|----------------|
| 1 | Quadratic funding | Moderate (demand signal) | Moderate (Sybil-dependent) | Proven | **Primary allocation** |
| 2 | Retroactive public goods funding | High (quality signal) | Moderate (evaluator risk) | Proven | Quality correction |
| 3 | Internal prediction markets | Moderate (forward signal) | Moderate (thin markets) | Moderate | Project valuation |
| 4 | Harberger self-assessment | High (for tangible resources) | Strong | Experimental | Resource allocation |
| 5 | AI-synthesized composite signal | Unknown | Unknown | Speculative | **Long-term aspiration** |
| 6 | Combinatorial auctions | High (preference bundles) | Moderate | Theoretical | Research interest |

### P6: Concentration Bounding

| Rank | Mechanism | Effectiveness | Incentive Impact | Maturity | Recommendation |
|------|-----------|---------------|-----------------|----------|----------------|
| 1 | Quadratic mechanisms (voting, funding) | Strong (sqrt reduction) | Low (preserves signal) | Proven | **Core mechanism** |
| 2 | Time decay with freezing | Strong (destroys power-law) | Moderate (penalizes absence) | Theoretical | **Core mechanism** |
| 3 | Real-time concentration monitoring | Enables response | None (measurement only) | Feasible | **Essential infrastructure** |
| 4 | Universal basic reputation | Moderate (raises floor) | Low | Untested | Worth piloting |
| 5 | Logarithmic contribution caps | Moderate (bounds top) | Moderate (caps excellence) | Untested | Calibrate empirically |
| 6 | Periodic partial resets | Strong (prevents accumulation) | High (discourages long-term) | Untested | Use cautiously |

---

## Cross-Cutting Assessment

### The Coupling Problem

These four problems are not independent. They form a dependency chain:

```
Sybil Resistance (P2)
    |
    v
Contribution Measurement (P4) --- affects accuracy of --->  Price Signals (P5)
    |                                                           |
    v                                                           v
Reputation Accumulation  -------- drives ---------->  Concentration (P6)
    |                                                           |
    v                                                           v
Governance Power  <------------- enables capture ----  Concentrated Power
    |
    v
Gaming Resistance (P2+)  <-- gamers attack weakest link in the chain
```

Weakness at any point propagates through the entire system. Sybil resistance is foundational because it protects every other mechanism. But even perfect Sybil resistance cannot prevent concentration if contribution measurement or price signals systematically favor certain types of work. And even bounded concentration cannot prevent governance capture if gaming erodes the integrity of the bounding mechanisms.

### The Goodhart Cascade

The deepest problem across all four areas is the Goodhart Cascade: any measurable quantity, once it becomes a target, ceases to measure what it was intended to measure. This applies recursively:

1. Measure contributions -> contributions are gamed
2. Measure gaming detection -> gaming evolves to evade detection
3. Measure detection evolution -> meta-gaming emerges
4. Measure the measurement system -> you are now playing Goodhart's Law against itself

The only escape from the Goodhart Cascade is to keep the measurement targets ambiguous, multidimensional, and continuously changing. This is computationally expensive and creates its own governance challenges (who decides how the targets change?).

The most honest conclusion: **a commons cannot permanently solve the identity and reputation problems. It can only maintain an evolving equilibrium between measurement, gaming, and adjustment.** The system must be designed for perpetual adaptation, not permanent stability.

### What Remains Genuinely Unsolvable

1. **Perfect Sybil resistance without biometrics or trust assumptions.** The mathematical reality is that identity is either grounded in something physical (biometrics, physical presence) or something social (trust networks, vouching). There is no pure cryptographic solution to "this is a unique human."

2. **Measuring the highest-value contributions.** The contributions that matter most in an AI-augmented system -- strategic insight, mentoring, community trust, creative vision -- are precisely those that resist quantification. Any system that claims to measure them will either be wrong or be gamed.

3. **Price-signal-equivalent information density from non-market mechanisms.** Capitalism's price system achieves its power through billions of decentralized transactions. No designed mechanism can replicate this information density. Multi-mechanism approaches can approximate it but at higher complexity and lower reliability.

4. **Permanent concentration bounding.** Every bounding mechanism can itself be captured by concentrated interests. The bounding must be constitutionally protected, but constitutions can be amended. The recursion does not terminate.

### What the Agent Commons Should Do

Given these constraints, the pragmatic path is:

1. **Accept imperfection.** Design for "good enough" at each layer, not for perfection. A system that functions with 85% accuracy across all four problems is more viable than one that achieves 99% on one and 50% on the others.

2. **Design for adaptability, not stability.** Build the mechanisms to be adjustable, not fixed. The parameters (decay rates, caps, quadratic weights, Sybil thresholds) should be tunable in response to observed gaming and concentration. The governance of these parameters is itself a hard problem (P1), but it is more tractable than designing a system that never needs adjustment.

3. **Start small, learn fast.** The 50-200 person pilot has structural advantages: social knowledge supplements technical mechanisms, gaming incentives are lower (the stakes are small), and the community can iterate quickly. Use the pilot to calibrate every parameter before attempting scale.

4. **Invest in detection over prevention.** Perfect prevention is impossible. Invest in the ability to detect gaming, Sybils, and concentration quickly, and in the institutional processes to respond. The AI governance layer should continuously monitor these metrics and flag anomalies.

5. **Constitutional protections for the bounding mechanisms.** The anti-concentration and anti-gaming mechanisms must be harder to change than normal governance decisions. This requires a constitutional structure where fundamental protections require supermajority + time delay + cross-layer approval to modify.

---

## Sources

### Sybil Resistance

- [Worldcoin Orb Identity Verification Device Faces Headwinds](https://www.forrester.com/blogs/worldcoin-orb-identity-verification-device-faces-headwinds-in-mass-adoption/) - Forrester
- [Worldcoin's Global Identity System: Privacy Risk or Innovation?](https://beincrypto.com/worldcoin-digital-id-privacy-risk-or-innovation/) - BeInCrypto
- [How Sam Altman's Worldcoin Is Reshaping Digital Identity](https://www.3minread.com/how-sam-altmans-worldcoin-is-reshaping-digital-identity-and-crypto-in-2025) - 3MinRead
- [Regulatory compliance, personal privacy and equitable access with Worldcoin](https://world.org/blog/world/regulatory-compliance-personal-privacy-equitable-access-worldcoin) - World.org
- [Understanding Humanity Protocol](https://messari.io/report/understanding-humanity-protocol-a-comprehensive-overview) - Messari
- [Humanity Protocol: Biometric Sybil Resistance](https://university.mitosis.org/humanity-protocol-biometric-sybil-resistance-for-decentralized-identity/) - Mitosis University
- [Using Graph Analysis to Prevent Sybil Attacks](https://gov.proofofhumanity.id/t/using-graph-analysis-to-prevent-sybil-attacks/3103) - PoH Governance
- [Exploring Anti-Sybil Approaches: Proof of Humanity](https://blog.humanode.io/exploring-anti-sybil-approaches-proof-of-humanity/) - Humanode
- [Who Watches the Watchmen? Sybil-Resistance in PoP Protocols](https://www.frontiersin.org/journals/blockchain/articles/10.3389/fbloc.2020.590171/full) - Frontiers in Blockchain
- [BrightID: Trust Engine](https://web3classdao.github.io/kaist2025/reports/brightid/) - KAIST 2025
- [BrightID AntiSybil](https://github.com/BrightID/BrightID-AntiSybil) - GitHub
- [Human Passport (formerly Gitcoin Passport)](https://passport.human.tech/) - Human.tech
- [Sybil-Resistance Tool Human Passport](https://thedefiant.io/news/security/sybil-resistance-tool-human-passport-launches-new-features-for-base) - The Defiant
- [Building Sybil Resistance using Cost of Forgery](https://www.gitcoin.co/blog/cost-of-forgery) - Gitcoin
- [Zero-Knowledge Proof-of-Identity](https://arxiv.org/abs/1905.09093) - arXiv (Cerezo Sanchez)
- [Sybil-Resistant SSI with Attested Execution](https://www.researchgate.net/publication/388371900) - ResearchGate
- [e-Residency of Estonia](https://www.e-resident.gov.ee) - Estonian Government
- [W3C Verifiable Credentials 2.0](https://www.w3.org/press-releases/2025/verifiable-credentials-2-0/) - W3C
- [VCs and DIDs Technical Landscape](https://ref.gs1.org/docs/2025/VCs-and-DIDs-tech-landscape) - GS1
- [Fostering AI alignment through blockchain and ZK proofs](https://link.springer.com/article/10.1007/s10586-025-05729-8) - Springer Cluster Computing

### Non-Code Contribution Tracking

- [Star & Strauss, "Layers of Silence, Arenas of Voice"](https://link.springer.com/article/10.1023/A:1008651105359) - CSCW 1999
- [360-Degree Feedback: Evidence-Based Answers](https://www.apa.org/pubs/journals/features/cpb-64-3-157.pdf) - APA
- [Do 360 Evaluations Work?](https://www.apa.org/monitor/2012/11/360-evaluations) - APA Monitor
- [SourceCred: Calculating Cred and Grain](https://research.protocol.ai/blog/2020/sourcecred-an-introduction-to-calculating-cred-and-grain/) - Protocol Labs
- [SourceCred Organization Winding Down](https://discourse.sourcecred.io/t/sourcecred-the-organization-is-winding-down/1383) - SourceCred Discourse
- [Coordinape Decentralized Compensation Tool](https://www.coindesk.com/tech/2022/08/25/web3-workplace-platform-coordinape-launches-decentralized-compensation-tool-for-daos) - CoinDesk
- [DAO Compensation: AI-Reputation-Based Vesting](https://johal.in/dao-compensation-ai-reputation-based-vesting/) - Johal
- [Compensation in Early-Stage Teams](https://www.rndao.io/blog/post/compensation-in-early-stage-teams) - RnDAO
- [Buurtzorg: Scaling Up Self-Managing Teams](https://link.springer.com/article/10.1007/s41469-024-00184-y) - Journal of Organization Design
- [Shapley Value: Cooperative Game to Explainable AI](https://link.springer.com/article/10.1007/s43684-023-00060-8) - Springer
- [Shapley Value](https://en.wikipedia.org/wiki/Shapley_value) - Wikipedia
- [Beyond Code: Open Source, Mentorship and Microcks](https://www.cncf.io/blog/2025/08/14/beyond-code-open-source-mentorship-and-microcks/) - CNCF

### Price Signals and Mechanism Design

- [Hayek, "The Use of Knowledge in Society"](https://www.econlib.org/library/Essays/hykKnw.html) - Econlib (1945)
- [Economic Calculation Problem](https://en.wikipedia.org/wiki/Economic_calculation_problem) - Wikipedia
- [How to Attack and Defend Quadratic Funding](https://www.gitcoin.co/blog/how-to-attack-and-defend-quadratic-funding) - Gitcoin
- [Gitcoin Grants Round 11 Anti-Fraud Evaluation](https://medium.com/block-science/gitcoin-grants-round-11-anti-fraud-evaluation-results-50f4b0f15125) - BlockScience
- [Gitcoin Grants 20: Results & Recap](https://www.gitcoin.co/blog/gitcoin-grants-20-results-recap) - Gitcoin
- [Gitcoin Grants 2025 Strategy](https://www.gitcoin.co/blog/gitcoin-grants-2025-strategy) - Gitcoin
- [Evolution of Retro Funding in 2025](https://gov.optimism.io/t/the-evolution-of-retro-funding-in-2025/9414) - Optimism Governance
- [Lessons Learned from Two Years of RPGF](https://gov.optimism.io/t/lessons-learned-from-two-years-of-retroactive-public-goods-funding/9239) - Optimism Governance
- [Retroactive Public Goods Funding](https://medium.com/ethereum-optimism/retroactive-public-goods-funding-33c9b7d00f0c) - Optimism
- [Corporate Prediction Markets: Google, Ford](https://funginstitute.berkeley.edu/wp-content/uploads/2014/04/CorporatePredictionMarkets1.pdf) - Berkeley Fung Institute
- [Prediction Markets at Google](https://www.hbs.edu/faculty/Pages/item.aspx?num=34562) - Harvard Business School
- [Radical Markets](https://journals.openedition.org/oeconomia/6984?lang=en) - Posner & Weyl
- [Vitalik Buterin on Radical Markets](https://vitalik.ca/general/2018/04/20/radical_markets.html) - vitalik.ca
- [Harberger Tax as Crypto's Sustainable Business Model](https://timdaub.github.io/2022/03/28/harberger-tax-can-cryptos-sustainable-business-model/) - Tim Daub
- [Quadratic Voting](https://www.ias.edu/sites/default/files/sss/pdfs/Rodrik/workshop%2014-15/Weyl-Quadratic_Voting.pdf) - Lalley & Weyl

### Concentration and Power Laws

- [Future of Algorithmic Organization: Large Scale Analysis of DAOs](https://arxiv.org/html/2410.13095v1) - arXiv
- [DAO Governance: Voting Power, Participation, and Controversy](https://dl.acm.org/doi/10.1145/3777416) - ACM DLT
- [New Cambridge Research: Shocking Concentration in DAO Governance](https://www.dlnews.com/articles/defi/cambridge-analysis-reveals-consolidation-of-dao-governance/) - DL News
- [Paradox of Power: How DAOs Struggle with Centralization](https://beincrypto.com/dao-governance-challenges-long-term-viability/) - BeInCrypto
- [Governance of DAOs: Voter Characteristics and Power Concentration](https://arxiv.org/html/2407.10945v1) - arXiv
- [Decentralizing Governance: Dynamics and Challenges of DAOs](https://www.frontiersin.org/journals/blockchain/articles/10.3389/fbloc.2025.1538227/full) - Frontiers in Blockchain
- [Inequalities in Open Source: Contributor Commits in ASF](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0152976) - PLOS One
- [Participation Inequality and the 90-9-1 Principle](https://www.researchgate.net/publication/346265944) - ResearchGate
- [Scale-free Network](https://en.wikipedia.org/wiki/Scale-free_network) - Wikipedia
- [Barabasi-Albert Model](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) - Wikipedia
- [Dynamics of Power Laws: Fitness and Aging in Preferential Attachment](https://link.springer.com/article/10.1007/s10955-017-1841-8) - Journal of Statistical Physics
- [Spatial Preferential Attachment Networks](https://arxiv.org/pdf/1210.3830) - arXiv
- [Piketty r-g and Wealth Concentration](https://libertystreeteconomics.newyorkfed.org/2015/07/a-discussion-of-thomas-pikettys-capital-in-the-twenty-first-century-by-how-much-is-r-greater-than-g/) - NY Fed
- [A Tale of Two Rates: Return on Capital and Wealth Concentration](https://www.tandfonline.com/doi/full/10.1080/09538259.2025.2492268) - Taylor & Francis
- [DAO Voting Mechanism Resistant to Whale Problems](https://www.frontiersin.org/journals/blockchain/articles/10.3389/fbloc.2024.1405516/full) - Frontiers in Blockchain

### Reputation Gaming

- [Reputation Gaming in Stack Overflow](https://arxiv.org/abs/2111.07101) - arXiv (Mazloomzadeh & Uddin)
- [Reputation Gaming in Crowd Technical Knowledge Sharing](https://dl.acm.org/doi/10.1145/3691627) - ACM TOSEM
- [Trust Among Strangers: eBay's Reputation System](https://www.researchgate.net/publication/228955281) - ResearchGate
- [Reputation and Feedback Systems in Online Platforms](https://faculty.haas.berkeley.edu/stadelis/Annual_Review_Tadelis.pdf) - Tadelis, Berkeley
- [The Rating Game: Discipline of Uber's Ratings](https://www.researchgate.net/publication/332114372) - ResearchGate
- [Gamification and Work Games: Uber Drivers](https://journals.sagepub.com/doi/full/10.1177/14614448221079028) - New Media & Society
- [Amazon's Crackdown on Fake Reviews 2025](https://salesduo.com/blog/amazon-crackdown-fake-reviews-2025/) - SalesDuo
- [Amazon's Actions Against Fake Review Brokers](https://www.aboutamazon.com/news/policy-news-views/amazons-latest-actions-against-fake-review-brokers) - AboutAmazon
- [Citation Cartels: Manipulating Metrics](https://www.proof-reading-service.com/blogs/academic-publishing/citation-cartels-manipulating-the-metrics-of-authors-and-journals) - Proof Reading Service
- [From Integrity to Inflation: Citation Practices](https://link.springer.com/article/10.1007/s10805-025-09631-1) - Journal of Academic Ethics
- [Gaming the Metrics: Misconduct and Manipulation](https://direct.mit.edu/books/oa-edited-volume/4598/Gaming-the-MetricsMisconduct-and-Manipulation-in) - MIT Press
- [LLMs Among Us: AI in Digital Discourse](https://arxiv.org/html/2402.07940v1) - arXiv
- [Have LLMs Reopened Pandora's Box of AI-Generated Fake News?](https://aclanthology.org/2025.naacl-long.142.pdf) - NAACL
- [Inside the Dark LLM Economy](https://medium.com/@adnanmasood/inside-the-dark-llm-economy-powering-modern-scams-661eda9036d6) - Masood
- [Industrialized Deception: LLM-Generated Misinformation](https://arxiv.org/html/2601.21963) - arXiv
- [Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart%27s_law) - Wikipedia
- [Goodhart's Law, Campbell's Law, and the Cobra Effect](https://psychsafety.com/goodharts-law-campbells-law-and-the-cobra-effect/) - PsychSafety

### General

- [Antitrust Reform: An Economic Perspective](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-082222-070822) - Annual Reviews
- [Tax Policy as Competition Policy](https://rooseveltinstitute.org/event/tax-policy-as-competition-policy/) - Roosevelt Institute
- [Land Reform, Poverty Reduction and Growth: India](https://www.lse.ac.uk/economics/Assets/Documents/personal-pages/tim-besley/data/land-reform-poverty-reduction-growth.pdf) - LSE (Besley)
- [Digital Commons](https://policyreview.info/concepts/digital-commons) - Internet Policy Review
- [FedQV: Leveraging Quadratic Voting in Federated Learning](https://arxiv.org/abs/2401.01168) - arXiv
