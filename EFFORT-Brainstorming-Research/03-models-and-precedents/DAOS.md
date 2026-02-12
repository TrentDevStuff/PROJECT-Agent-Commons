---
created: 2026-02-12T23:30:00Z
updated: 2026-02-12T23:30:00Z
type: research
parent_effort: EFFORT-Brainstorming-Research
research_area: 03-models-and-precedents
thread: "3.3"
status: draft
backlinks:
  - [[RESEARCH]]
  - [[OPEN-SOURCE]]
  - [[GITHUB-INFRASTRUCTURE]]
  - [[SYNTHESIS]]
---

# 3.3 DAOs (Decentralized Autonomous Organizations): The Closest Precedent and the Biggest Cautionary Tale

## Central Question

DAOs attempted exactly what Agent Commons proposes -- decentralized, code-governed organizations. What went wrong, and what can be salvaged?

## Why This Matters for Agent Commons

DAOs are the most direct predecessor of the Agent Commons concept. They share the same ambition: replace traditional organizational hierarchy with decentralized governance, use code to enforce rules, distribute value to contributors, and enable self-organizing teams to produce goods and services without corporate structure.

If DAOs had succeeded, Agent Commons might not be necessary. But DAOs, as commonly implemented, have largely failed at their stated goals -- not because decentralized organization is impossible, but because the specific mechanisms DAOs adopted (token voting, on-chain governance, "code is law") recreated the very problems they claimed to solve, particularly plutocracy and low participation.

The critical question for Agent Commons: is DAO failure attributable to the specific mechanisms used (token voting, blockchain infrastructure, crypto-economic incentives), or to the fundamental impossibility of decentralized governance at scale? If the former, Agent Commons might succeed with different mechanisms. If the latter, Agent Commons will fail for the same reasons.

This section argues it is primarily the former -- DAOs failed because of specific design choices, not because decentralized organization is impossible -- but with important caveats about what decentralized organization can and cannot do.

---

## 1. The DAO Hack (2016) -- Detailed Post-Mortem

### 1.1 What Was "The DAO"?

"The DAO" (always capitalized to distinguish it from the generic concept of a DAO) was a decentralized venture capital fund built on the Ethereum blockchain in 2016. It was created by Slock.it, a German company developing Ethereum-based smart contracts.

The concept was audacious: instead of a traditional VC fund (where a small number of partners decide how to invest other people's money), The DAO would allow anyone to invest by purchasing DAO tokens, and all token holders would vote on which projects to fund. The fund's rules were encoded entirely in smart contracts -- self-executing code on the Ethereum blockchain that would enforce the rules without human intermediaries.

**The Crowdfunding**

The DAO launched its token sale on April 30, 2016. Over 28 days, approximately 11,000 investors contributed roughly 12.7 million ETH -- worth approximately $150 million at the time. This was the largest crowdfunding in history at that point. The DAO held approximately 14% of all Ether in existence.

The enthusiasm was extraordinary. The crypto community saw The DAO as proof that decentralized governance could manage significant capital. The DAO's own promotional materials framed it as "a paradigm shift in the very idea of economic organization... a DAO that aimed to be as decentralized as Ethereum itself."

### 1.2 The Exploit

On June 17, 2016, an attacker exploited a vulnerability in The DAO's smart contract code -- a "re-entrancy" bug that allowed the attacker to repeatedly withdraw funds before the contract updated its balance. The attack drained approximately 3.6 million ETH (roughly $60 million at the time) into a "child DAO" controlled by the attacker.

**The Technical Detail**

The vulnerability was in The DAO's "splitDAO" function, which allowed token holders to withdraw their funds by creating a new child DAO. The function sent ETH to the caller before updating the internal balance. The attacker's contract called splitDAO recursively -- receiving payment each time but never allowing the balance update to execute. This is the classic re-entrancy attack, well-known in computer security but not anticipated by The DAO's developers.

The code had been publicly available. Security researchers had warned about the vulnerability weeks before the attack. Slock.it acknowledged the bug but did not patch it in time. The DAO had no mechanism for emergency code updates -- because its design philosophy held that the code was the governance, and changing the code required a governance vote that took time The DAO did not have.

### 1.3 The Governance Failure

The DAO hack was not primarily a technical failure -- it was a governance failure. Specifically:

**"Code is law" vs. human judgment.** The DAO's operating philosophy held that the smart contract code was the definitive expression of the organization's rules. What the code allowed was, by definition, permitted. Under this philosophy, the attacker did not steal anything -- they used the code as it was written. The "exploit" was simply a clever use of the code's actual functionality.

This philosophy collapsed under contact with reality. The investors who lost $60 million did not consider the attack legitimate, regardless of what the code technically permitted. The gap between "what the code allows" and "what participants consider fair" was enormous.

**No emergency mechanism.** The DAO had no mechanism for emergency action. To modify the code, a governance vote was required. The vote took days. The attack took hours. The system was designed to prevent unilateral action -- which is a good hedge against power-seeking -- but at the cost of preventing emergency response.

**No human judgment in the loop.** The DAO's design explicitly excluded human judgment from governance. This was the point -- the code was supposed to be more trustworthy than human governance. But it meant that when the code was wrong (i.e., when it allowed behavior that violated the organization's intent), there was no correction mechanism.

### 1.4 The Ethereum Hard Fork

The Ethereum community faced an unprecedented decision: should the blockchain itself be modified to reverse the attack?

**Arguments for the fork:**
- $60 million was stolen. The investors were victims of a bug, not willing participants in a risky gamble (well, also that, but the bug was the proximate cause).
- The attacker's funds were locked in a child DAO with a 28-day waiting period. There was time to act.
- Ethereum was a young platform. Allowing its largest project to be destroyed by a bug would damage confidence in the entire ecosystem.

**Arguments against the fork:**
- "Code is law." If the blockchain can be modified to reverse outcomes the community dislikes, it is not trustless -- it is governed by whoever controls the forking process.
- Modifying the blockchain sets a precedent. If Ethereum forks to reverse one attack, who decides when to fork for the next one? This gives enormous power to whoever can organize a fork.
- The attack was not illegal. Under the "code is law" philosophy, the attacker used the code as written. Changing the rules retroactively is what authoritarian governments do.

**The Decision**

After heated community debate, the Ethereum community executed a hard fork on July 20, 2016, creating two blockchains:
- **Ethereum (ETH)** -- the forked chain, with the DAO attack reversed (investors got their money back).
- **Ethereum Classic (ETC)** -- the unforked chain, preserving the "code is law" principle (attacker keeps the funds).

The majority of the community followed ETH. Ethereum Classic survived as a minority chain.

### 1.5 What This Teaches

**Lesson 1: Code cannot replace governance -- it can only encode governance.**

The DAO's mistake was conflating rules with the medium used to express them. A smart contract is a tool for enforcing rules, not a substitute for the judgment that decides what the rules should be. Human governance is messy precisely because it must accommodate unforeseen circumstances, ambiguity, and evolving values. Code cannot do this -- it can only execute the rules as written at the time of writing.

**Agent Commons implication:** AI governance is not the same as "code is law." AI can exercise judgment that smart contracts cannot. But AI governance still encodes the values and biases of whoever built and trained the AI. The risk is not "code is law" but "training data is law" -- a different form of the same problem.

**Lesson 2: Emergency mechanisms are essential.**

Every resilient system (democracy, corporations, even military units) has emergency mechanisms that allow rapid response when normal governance is too slow. The DAO's design eliminated this capacity. Agent Commons must build emergency mechanisms that are fast enough for crises but constrained enough to prevent abuse.

**Lesson 3: Governance legitimacy comes from participant consent, not technical purity.**

The Ethereum hard fork was technically "impure" -- it violated the immutability principle that blockchains are built on. But it was legitimate because the community chose it. The purity of "code is law" was less important to most participants than the fairness of "don't let a bug destroy $60 million." Agent Commons must prioritize legitimacy (do participants accept the governance outcome?) over theoretical purity (does the governance mechanism meet some abstract design criterion?).

**Lesson 4: Forking as ultimate governance mechanism.**

The Ethereum/Ethereum Classic split is the most dramatic example of forking as governance. The community could not agree on whether to reverse the attack, so it split into two communities, each following its preferred governance outcome. Both survived. This is the forking mechanism in its most extreme form -- and it worked, in the sense that it preserved choice for both factions.

---

## 2. Token-Voting Plutocracy -- The Core Failure

### 2.1 The Mechanism and Its Logic

Most DAOs allocate voting power proportionally to token holdings. If you hold 10% of a DAO's governance tokens, you have 10% of the voting power. The logic:

- **Sybil resistance.** The fundamental challenge of online governance is preventing one person from creating many accounts to manipulate votes. Requiring financial stake (token ownership) makes this expensive. One token, one vote solves the Sybil problem the same way one share, one vote solves it in corporate governance.
- **Skin in the game.** Token holders have financial exposure to the DAO's decisions. Bad decisions reduce token value, hurting token holders. This aligns incentives: those who bear the consequences of decisions should make the decisions. (Nassim Taleb's argument, applied to organizational governance.)
- **Ease of implementation.** Token-weighted voting is trivially implementable on a blockchain. Tokens are countable, transferable, and verifiable. No identity system is needed -- just wallet addresses.

### 2.2 Why This Recreates Shareholder Capitalism

The logical outcome of one-token-one-vote is identical to one-share-one-vote: plutocracy. Those with more financial resources have more governance power. This is not a bug in the implementation -- it is the direct, predictable consequence of the design choice.

The crypto community's stated goal was to create organizations free from the power concentration of traditional corporate governance. But by choosing token voting as the governance mechanism, they recreated the exact power structure they claimed to replace. A DAO with token voting is functionally equivalent to a publicly traded corporation -- except without the regulatory protections (SEC oversight, board fiduciary duty, proxy access rules) that partially check shareholder power in conventional corporations.

**Token Concentration Data**

Research from multiple sources has documented extreme token concentration in major DAOs:

- **Chainalysis (2022)** reported that in most DAOs, fewer than 1% of token holders control more than 90% of voting power.
- **DeepDAO** analytics has tracked DAO governance participation across hundreds of DAOs and consistently finds that governance decisions are dominated by a handful of large holders ("whales").
- **A16z Crypto's "Governance of DAOs" research (2022)** documented that in Uniswap, Compound, and other DeFi governance DAOs, the top 10 addresses typically control 50-80% of voting power.
- **Messari (2023)** reported that in many DAOs, the founding team and early investors retain majority voting power through token allocations that were determined before the DAO launched.

This concentration is structural, not incidental. Token distributions in most DAOs follow power-law distributions because:

1. **Founding teams allocate themselves large token holdings** (typically 15-25% of total supply) as compensation for building the project.
2. **Early investors receive large allocations** (typically 15-30%) through private sales before the token is publicly available.
3. **Token purchases on the open market** favor those with more capital.
4. **Yield farming and staking** allow large holders to accumulate more tokens over time (a capital-compounds-into-capital dynamic identical to the corporate world).

### 2.3 Voter Apathy

Even among token holders, voting participation is extremely low:

- **Typical DAO governance proposal turnout: 1-10% of token supply.** Chainalysis and DeepDAO data consistently show single-digit percentage participation rates for routine governance proposals.
- **Optimism's DAO** achieved 10-15% turnout on major governance votes -- considered high by DAO standards.
- **Compound** governance proposals routinely pass with fewer than 50 unique addresses voting.
- **Uniswap** temperature checks and governance proposals typically see participation from a few hundred addresses out of hundreds of thousands of token holders.

The causes mirror voter apathy in democracy (documented in the Area 1 analysis), with an additional factor:

- **Rational apathy** -- my vote is unlikely to affect the outcome, so why spend time researching and voting? This is the standard collective action problem.
- **Complexity** -- DAO governance proposals are often highly technical (DeFi parameter changes, smart contract upgrades, treasury allocation). Most token holders lack the expertise to evaluate them.
- **Gas costs** -- on Ethereum mainnet, voting requires a transaction that costs gas (money). For small token holders, the cost of voting may exceed the value of their vote. (This has been partially addressed by off-chain voting tools like Snapshot, which allow gasless voting, but these sacrifice the security guarantees of on-chain governance.)
- **Speculative holders** -- many token holders bought tokens as speculative investments, not to participate in governance. They have no interest in governance and no intention of participating.

### 2.4 Whale Domination -- Case Studies

**The Uniswap DeFi Education Fund Incident (2021)**

In June 2021, a Uniswap governance proposal to create a "DeFi Education Fund" and allocate 1 million UNI tokens (worth approximately $25 million at the time) passed with support from a small number of large holders. Shortly after receiving the tokens, the fund sold 500,000 UNI on the open market, causing significant price impact. The community was outraged.

The incident demonstrated:
- A small number of whale votes could direct millions of dollars of community treasury.
- There was no mechanism to prevent immediate liquidation of treasury allocations.
- The "governance" was functionally identical to a small group of insiders making decisions with other people's money.

**The Beanstalk Governance Attack (2022)**

In April 2022, an attacker borrowed a large amount of cryptocurrency through a flash loan (a loan that must be repaid in the same transaction), used the borrowed tokens to gain voting power in the Beanstalk DAO, passed a malicious governance proposal that drained the treasury ($182 million), and repaid the loan -- all in a single blockchain transaction.

This was not a code exploit like The DAO hack. It was a legitimate governance action: the attacker had the votes (even if temporarily) and the governance mechanism executed as designed. The system worked exactly as intended -- and the intended design was catastrophically vulnerable.

### 2.5 Is This Different From Corporate Shareholder Voting?

The honest answer: it is substantively the same, and in some ways worse.

| Dimension | Corporate Shareholder Voting | DAO Token Voting |
|-----------|------------------------------|-------------------|
| Power distribution | Proportional to shares held | Proportional to tokens held |
| Concentration | High (institutional investors) | Very high (founding teams, VCs) |
| Regulatory oversight | SEC, proxy rules, fiduciary duty | None (or minimal, depending on jurisdiction) |
| Board as intermediary | Yes (board governs, shareholders elect board) | No (token holders vote directly on all decisions) |
| Participation rate | Low (retail shareholders rarely vote; institutional investors always do) | Very low (1-10% typical) |
| Flash loan attack | Not possible (share ownership requires settlement) | Possible on some platforms |
| Identity verification | Required (KYC for share ownership) | Not required (pseudonymous wallets) |

The critical difference is that corporate governance has a century of regulatory infrastructure (securities law, fiduciary duty, proxy access, disclosure requirements) that partially constrains shareholder power. DAO governance has none of this. The DAO community reinvented shareholder capitalism without the guardrails -- and got a worse version.

---

## 3. Successful DAOs -- What Makes Them Work

Not all DAOs have failed. Several have achieved functional governance, real utility, and sustained community engagement. Examining what distinguishes these from the failures is essential.

### 3.1 MakerDAO -- Governance of the DAI Stablecoin

**What It Does**

MakerDAO governs the Maker Protocol, which issues DAI -- a decentralized stablecoin pegged to the US dollar. MKR token holders vote on critical parameters: collateral types, stability fees (interest rates), debt ceilings, and risk parameters. At its peak, MakerDAO managed over $10 billion in collateral.

**What Works**

- **Clear purpose with measurable outcomes.** The DAO's goal is to maintain DAI's peg to $1. This is an unambiguous, measurable objective. Good governance keeps the peg; bad governance breaks it. This clarity of purpose reduces the attack surface for capture -- anyone who damages the peg damages the value of their MKR tokens.
- **Real expertise in governance.** MakerDAO's governance is dominated by a small number of highly engaged, technically sophisticated participants who understand DeFi risk management. This is meritocratic in practice, even though the formal mechanism is token voting.
- **Professional delegates.** MakerDAO has formalized delegation, allowing token holders to delegate their votes to recognized governance experts (delegates) who specialize in evaluating proposals. This is liquid democracy in practice and addresses the voter apathy problem by concentrating governance activity among those with the expertise and motivation to participate.
- **Governance facilitators.** MakerDAO employs governance facilitators who prepare proposal summaries, manage the governance process, and ensure proposals are clearly documented. This addresses the complexity barrier.

**What Does Not Work**

- **MKR concentration.** Despite the functional governance, MKR tokens remain highly concentrated. A16z (Andreessen Horowitz) is one of the largest MKR holders and has significant influence over governance outcomes.
- **Governance fatigue.** Even engaged participants report burnout from the volume and complexity of governance decisions. Risk parameters need frequent adjustment, and each adjustment requires a governance vote.
- **Centralization pressure.** In 2022-2023, Maker founder Rune Christensen proposed "Endgame," a radical restructuring that would fragment Maker into multiple sub-DAOs. The proposal was controversial and its implementation has been complex. Some critics argued that Christensen's influence demonstrated that MakerDAO was still effectively BDFL-governed despite its token-voting structure.

### 3.2 Gitcoin -- Quadratic Funding for Public Goods

**What It Does**

Gitcoin provides infrastructure for funding public goods, primarily open-source software. Its signature mechanism is quadratic funding (described in Section 4.1): a matching pool amplifies small donations so that projects with many small supporters receive more matching than projects with few large supporters.

**What Works**

- **Mechanism design innovation.** Quadratic funding is the most important governance innovation to emerge from the DAO ecosystem. It directly addresses plutocracy by privileging breadth of support over depth of funding.
- **Real-world impact.** Gitcoin Grants has distributed over $60 million to open-source projects, public goods, and community initiatives since 2019. The funding has reached projects that would not have been funded through traditional channels.
- **Sybil resistance through identity.** Gitcoin has invested heavily in Gitcoin Passport, a "proof of humanity" system that uses multiple identity verification methods (social media accounts, ENS domains, on-chain activity) to prevent Sybil attacks on quadratic funding rounds. This addresses one of the fundamental DAO governance challenges.

**What Does Not Work**

- **Sybil attacks remain a persistent challenge.** Despite Gitcoin Passport, every funding round faces attempts to create fake identities to manipulate matching. The cat-and-mouse game between Sybil attackers and Sybil resistance is ongoing and resource-intensive.
- **Gaming the matching formula.** Sophisticated actors coordinate to spread donations across many accounts to maximize matching. The line between legitimate grassroots support and coordinated manipulation is blurry.
- **Governance of Gitcoin itself.** Gitcoin's own governance (the GTC token DAO) suffers from the same voter apathy and concentration problems as other token-voting DAOs. The innovation is in the funding mechanism, not in the DAO governance.

### 3.3 ENS (Ethereum Name Service) -- Infrastructure Governance

**What It Does**

ENS provides human-readable names (like "vitalik.eth") for Ethereum addresses. The ENS DAO governs parameters, treasury allocation, and protocol upgrades.

**What Works**

- **Clear, bounded scope.** ENS governance covers a specific, well-defined piece of infrastructure. The scope of governance decisions is narrow enough that voters can understand the issues.
- **Airdrop-based initial distribution.** ENS distributed governance tokens to users (people who had registered .eth names) rather than investors. This created a more distributed initial token allocation than most DAOs.
- **Steward structure.** ENS governance uses elected stewards in defined working groups (Community, Ecosystem, Meta-Governance, Public Goods) who manage day-to-day operations within budgets approved by token holders. This creates a representative layer that reduces the number of decisions requiring direct token votes.

**What Does Not Work**

- The ENS token airdrop still resulted in concentrated holdings among early large-scale registrants. The distribution was more equitable than most DAOs but still power-law.
- A controversial governance incident in 2022, when an ENS delegate was removed for offensive personal views, revealed tensions between code-based governance and social governance.

### 3.4 Uniswap -- Decentralized Exchange Governance

**What It Does**

Uniswap is the largest decentralized exchange by volume. The Uniswap DAO (UNI token) governs protocol parameters, treasury allocation, and deployments to new blockchains.

**Governance Reality**

Uniswap's governance is widely regarded as one of the least functional major DAOs:

- Participation is extremely low (routinely below 5% of circulating supply).
- Proposals frequently fail to reach quorum.
- The DeFi Education Fund incident (Section 2.4) damaged community trust.
- A16z controls a significant portion of UNI tokens and has outsized influence.
- In practice, Uniswap Labs (the company that built the protocol) continues to drive protocol development, with the DAO serving primarily as a ratification mechanism.

**Lesson:** A successful protocol does not automatically produce successful governance. Uniswap the protocol is extraordinarily successful ($1 trillion+ in cumulative trading volume). Uniswap the DAO is dysfunctional. This suggests that protocol utility and governance quality are independent variables.

### 3.5 Nouns DAO -- Experimental Governance

**What It Does**

Nouns DAO is a novel experiment: one NFT (a "Noun") is auctioned every 24 hours, with all auction proceeds going to the DAO treasury. Each Noun grants one governance vote. The treasury funds proposals voted on by Noun holders.

**What Works**

- **Continuous, equal-increment funding.** Instead of a large initial token sale, funding accrues gradually. This prevents early-holder concentration.
- **One Noun, one vote.** Since each Noun is auctioned individually, the cost of governance power is the market price of a Noun. This is still plutocratic (richer participants buy more Nouns) but the gradual acquisition process and public auctions make accumulation visible.
- **Highly engaged community.** The Nouns community has funded hundreds of creative projects, from physical art installations to charitable initiatives. The DAO has demonstrated that decentralized treasury management can produce diverse, creative funding decisions.
- **Fork mechanism.** In 2023, Nouns implemented a "ragequit" mechanism allowing Noun holders to burn their Nouns and receive a proportional share of the treasury. This is an explicit exit mechanism that disciplines governance -- if holders disagree with the DAO's direction, they can leave with their proportional share.

**What Does Not Work**

- At current Noun prices (tens of thousands of dollars per Noun), governance participation is accessible only to the wealthy. This is a small, exclusive club, not a broad-based organization.
- The daily auction model caps governance expansion at one new participant per day. This is too slow for scaling.
- The ragequit mechanism led to significant treasury outflows in 2023-2024, as some Noun holders concluded they could get more value by ragequitting than by staying. This is the exit option functioning correctly -- but it can drain the treasury if many holders lose confidence simultaneously.

### 3.6 What Successful DAOs Have in Common

| Factor | MakerDAO | Gitcoin | ENS | Nouns |
|--------|---------|---------|-----|-------|
| Clear, bounded purpose | Yes (stablecoin peg) | Yes (public goods funding) | Yes (naming infrastructure) | Partial (treasury allocation) |
| Real utility beyond governance | Yes (DAI) | Yes (grants) | Yes (naming) | Partial (creative funding) |
| Active, expert community | Yes | Yes | Yes | Yes |
| Professional delegates/stewards | Yes | Partial | Yes (stewards) | No |
| Mechanism innovation | Partial (delegation) | Yes (quadratic funding) | Partial (stewards) | Yes (daily auction, ragequit) |

**The pattern:** DAOs that work have a clear, measurable purpose; provide real utility that attracts genuine (not just speculative) participants; cultivate expert governance communities; and innovate beyond simple token voting.

DAOs that fail have vague purposes ("govern the protocol"), attract primarily speculative participants, make no effort to cultivate governance expertise, and rely on vanilla one-token-one-vote mechanisms.

---

## 4. Governance Innovations in DAOs

The DAO ecosystem has produced several governance innovations that go beyond simple token voting. These represent the most transferable learnings from the DAO experiment.

### 4.1 Quadratic Voting and Quadratic Funding

**Mechanism**

In quadratic voting, the cost of votes increases quadratically: 1 vote costs 1 credit, 2 votes cost 4 credits, 3 votes cost 9 credits, and so on. This means that strongly preferring one outcome is expensive, while expressing mild preferences across many issues is cheap. The result: broad-based support wins over concentrated support.

Quadratic funding (Buterin, Hitzig, and Weyl, 2018) applies this to funding decisions. A matching pool amplifies donations to public goods using a quadratic formula: the matching amount is proportional to the square of the sum of the square roots of individual contributions. In practice, this means a project with many $1 donations receives more matching than a project with one $100 donation, even though the total contributions are the same.

**Evidence**

Gitcoin Grants has conducted 20+ quadratic funding rounds since 2019. The results show:

- Small projects with broad community support receive meaningful funding.
- The matching formula does reduce plutocratic influence compared to one-dollar-one-vote.
- The mechanism is vulnerable to collusion (coordinated donations to maximize matching) and Sybil attacks (fake identities to multiply the quadratic effect).

**Transferability to Agent Commons**

Quadratic mechanisms are directly applicable to:
- **Resource allocation** -- distributing commons resources to Forgs based on broad support rather than large-donor influence.
- **Priority setting** -- allowing agents to express preferences over multiple priorities with diminishing marginal influence on any single priority.
- **Reputation weighting** -- if reputation replaces tokens as voting power, quadratic weighting could prevent reputation-wealthy agents from dominating.

**Limitations:** Quadratic mechanisms require Sybil resistance -- a way to ensure each participant is unique. In open-source, where identity is often pseudonymous, this is challenging. Agent Commons must solve the identity problem to use quadratic mechanisms.

### 4.2 Conviction Voting

**Mechanism**

Conviction voting (developed by 1Hive/Commons Stack) allows participants to stake tokens on proposals over time. The longer tokens are staked, the more "conviction" (voting weight) they generate. Conviction accumulates continuously, and proposals pass when conviction reaches a threshold proportional to the resources requested.

**Why It Matters**

Conviction voting addresses several token-voting failures:

- **Reduces voter apathy** -- you stake your tokens and walk away. No need to pay attention to specific vote deadlines.
- **Rewards long-term commitment** -- fleeting opinions have less weight than sustained preferences. This hedges against impulsive decisions and flash-loan attacks.
- **Continuous governance** -- instead of discrete voting events, governance is a continuous flow of preferences. This is more natural than periodic elections.
- **Signal vs. noise** -- weak preferences produce little conviction; strong preferences produce a lot. The mechanism distinguishes between "I kind of care about this" and "I deeply care about this."

**Evidence**

1Hive (a small DeFi community) implemented conviction voting for its treasury allocation. The system functioned but has not been widely adopted, in part because it is more complex than simple token voting and harder for participants to understand.

**Transferability to Agent Commons**

Conviction voting could replace or supplement token voting in Agent Commons:
- Agents stake reputation (rather than tokens) on Forg proposals.
- The longer agents maintain their stake, the more weight their support carries.
- Proposals that attract broad, sustained support pass; proposals that attract temporary or narrow support do not.

### 4.3 Delegation and Liquid Democracy

**Mechanism**

Liquid democracy (also called delegative democracy) allows participants to:
1. Vote directly on any proposal (like direct democracy).
2. Delegate their vote to someone else on a per-topic basis.
3. Revoke delegation at any time and vote directly instead.

Delegates can further delegate to others, creating chains of delegation that can be unwound at any point.

**DAO Implementation**

Several DAOs have implemented forms of delegation:

- **Optimism** (the Ethereum Layer 2 network) has a bicameral governance structure:
  - **Token House** -- token holders delegate to community-selected delegates who vote on protocol upgrades and incentive programs.
  - **Citizens' House** -- "citizens" (non-transferable identity-based membership) vote on retroactive public goods funding.

  Optimism's model is notable because it explicitly separates token-based governance (for protocol decisions with financial consequences) from identity-based governance (for values-based decisions about public goods). This addresses the plutocracy problem directly: the Citizens' House cannot be captured through token accumulation because citizenship is non-transferable.

- **MakerDAO** has professionalized delegation, with recognized delegates who receive compensation for their governance work.

- **Gitcoin** allows token holders to delegate to governance stewards.

**Evidence**

Delegation increases effective participation rates. In MakerDAO, delegation means that even when individual token holders do not vote, their tokens are represented by delegates. Optimism's delegation system has achieved higher effective participation rates than DAOs without delegation.

However, delegation concentrates governance among a small number of delegates, recreating representative democracy. The question becomes: is delegated DAO governance meaningfully different from a traditional representative structure? The answer: the key differences are (a) delegation is per-issue, not periodic, (b) delegation is instantly revocable, and (c) delegates are transparent in their voting record. These are genuine improvements over fixed-term elected representatives.

**Transferability to Agent Commons**

Delegation is essential for Agent Commons governance:
- Most agents will not want to participate in all governance decisions.
- Delegation allows expertise-based governance: delegates who specialize in specific domains (technical architecture, dispute resolution, economic policy) can carry the votes of agents who trust their judgment.
- Per-issue delegation is superior to both direct democracy (which demands too much attention) and fixed-term representation (which creates entrenchment).
- The critical design choice: delegation by reputation (delegating to those with demonstrated expertise) rather than delegation by token wealth (delegating to those with financial stake).

### 4.4 Reputation-Based Voting

**Mechanism**

Vote weight is based on contribution to the community rather than financial stake. The more you contribute, the more governance influence you have.

**Challenges**

This is the holy grail of DAO governance -- and the most difficult to implement:

- **Sybil resistance without financial stake.** If governance power is based on contribution, a malicious actor can create many identities and make small contributions from each to accumulate disproportionate power. Financial stake (token voting) solves Sybil resistance by making attack expensive. Reputation-based voting needs an alternative Sybil resistance mechanism.
- **Defining contribution.** As discussed in the open-source section, measuring contribution is hard. Code commits are measurable but narrow. Community building, mentoring, and emotional labor are valuable but invisible. Whatever metric is used will be gamed (Goodhart's Law).
- **Reputation transferability.** Should reputation earned in one DAO carry weight in another? If yes, early movers accumulate cross-DAO influence. If no, reputation is siloed and non-portable.

**Implementations**

- **Optimism's Citizens' House** is the most significant attempt at non-token-based governance. Citizenship is granted through "attestations" (vouches from existing citizens) and cannot be bought or transferred.
- **Coordinape** allows team members to allocate "GIVE" tokens to each other based on perceived contribution. The allocation is not financial (you cannot keep the tokens) but signals contribution assessment by peers.
- **SourceCred** (now largely inactive) attempted to algorithmically measure contribution to a project by analyzing code commits, issues, and discussions.

**Transferability to Agent Commons**

Agent Commons' governance model is essentially reputation-based voting by another name -- the proposal is that AI judges evaluate contribution and allocate governance power accordingly. The AI replaces the peer-evaluation of Coordinape or the algorithmic analysis of SourceCred.

The advantages of AI over manual reputation assessment:
- AI can process more information (all contributions, not just visible ones).
- AI is not subject to social pressure, tribalism, or status-seeking.
- AI can value diverse contribution types if trained to do so.

The risks of AI-based reputation:
- AI capture (Section 5 below).
- Opacity (humans cannot easily verify AI's reputation assessment).
- Gaming (contributors will optimize for whatever the AI rewards, not for genuine value).
- Bias in training data (if the AI learns from existing reputation systems, it will reproduce their biases).

### 4.5 Optimistic Governance

**Mechanism**

Proposals pass by default unless challenged within a time window. Only challenged proposals require a full governance vote. This reduces voter fatigue by limiting voting to contested decisions.

**Logic**

Most governance proposals are routine and non-controversial. Requiring a full vote for every decision exhausts participants. Optimistic governance reserves the full governance mechanism for disputes -- which is where it is most needed.

**Implementations**

- **Optimism's governance** uses optimistic approval for some proposal types.
- **Arbitrum's governance** includes an optimistic element.
- Several protocols use time-locked proposals that can be vetoed but pass by default.

**Transferability to Agent Commons**

Optimistic governance is highly relevant:
- Most Forg activities should proceed without governance approval (optimistic by default).
- AI monitoring flags anomalies or potential violations.
- Only flagged activities require governance intervention (human or AI review).
- This is the "pull the emergency brake" model recommended in the Area 1 synthesis: "Human override with friction -- Humans must be able to override AI decisions, but the override should be costly enough to prevent casual interference."

### 4.6 Futarchy -- Vote on Values, Bet on Beliefs

**Mechanism**

Robin Hanson's futarchy proposal (2000): "vote on values, bet on beliefs." The community democratically decides what outcomes it values (e.g., maximize the stablecoin's peg accuracy). Then prediction markets are used to determine which policies best achieve those values. The policy that the market predicts will produce the best outcome is adopted.

**Why It Matters**

Futarchy separates two types of decisions:
1. **What do we want?** (Values -- should be decided democratically, because values are subjective.)
2. **How do we get it?** (Beliefs -- should be decided by those with the best information, because effectiveness is empirical.)

This addresses the "voter ignorance" problem in democracy: voters do not need to understand policy details. They only need to specify their values. The market handles the policy analysis.

**Has Any DAO Tried Futarchy?**

Partially:
- **Gnosis** (now gnosis.io) was originally built to enable prediction-market-based governance but pivoted to other products.
- **MetaDAO** on Solana has experimented with futarchy-inspired governance where proposals are evaluated through conditional token markets.
- No major DAO has fully implemented Hanson's futarchy vision.

**Why It Has Not Been Widely Adopted**

- **Market manipulation.** Prediction markets can be manipulated by large holders, especially in thin markets.
- **Complexity.** Most DAO participants do not understand prediction markets, much less conditional prediction markets.
- **Defining values.** "Vote on values" assumes the community can agree on measurable outcome metrics. In practice, translating values into metrics is contentious.

**Transferability to Agent Commons**

Futarchy's conceptual separation (values vs. beliefs) is highly relevant even if the full prediction-market mechanism is not adopted:
- **The community (all agents) votes on values** -- what the commons should optimize for. This is democratic.
- **AI evaluates policy options** based on predicted outcomes relative to those values. This replaces the prediction market with AI modeling.
- This is actually Agent Commons' implicit model: AI governance makes decisions, but the values the AI optimizes for are set by the community.

The critical design question: how does the community set values? If by token voting, it is plutocracy. If by reputation-weighted voting, it depends on reputation measurement. If by equal vote (one agent, one vote), it requires Sybil resistance. Each mechanism has tradeoffs documented elsewhere in this research.

---

## 5. AI Governance vs. Token Governance -- The Critical Comparison

This is the most important section for Agent Commons. The core claim of Agent Commons is that AI governance can succeed where token governance has failed. This claim must be tested rigorously.

### 5.1 Token Voting Failure Modes and Whether AI Governance Avoids Them

| Token Voting Failure Mode | AI Governance Equivalent | Better or Worse? |
|--------------------------|--------------------------|------------------|
| **Plutocracy** (rich holders dominate) | **AI capture** (whoever controls the AI dominates) | Potentially better if AI is plural and independent; potentially worse if AI is controlled by a single entity |
| **Voter apathy** (most holders don't vote) | **No voting required** (AI decides) | Better for decision speed; worse for democratic legitimacy |
| **Flash loan attacks** (temporary power acquisition) | **Prompt injection / adversarial attacks** on AI | Different attack surface, comparable severity |
| **Lack of expertise** (voters don't understand proposals) | **AI has unlimited processing capacity** for analysis | Better for decision quality; worse for human understanding of decisions |
| **Low turnout** leading to minority rule | **AI always "participates"** | Better for coverage; raises questions about legitimacy of algorithmic rule |
| **Sybil attacks** | Depends on identity system; AI may help detect Sybils | Potentially better if AI can detect fake identities |

### 5.2 AI Capture Risk -- The New Failure Mode

Token voting's core failure is plutocracy: money buys power. AI governance's core failure would be AI capture: control over the AI buys power.

**Who builds the AI?** Whoever selects the AI model, designs the training process, chooses the training data, and defines the objective function has more power than any token whale. This is the "constitutional convention" problem: the people who write the rules have power that subsequent governance cannot easily check.

**Who trains the AI?** Training data encodes values. An AI trained on corporate data will value efficiency and profit. An AI trained on cooperative data will value equity and participation. An AI trained on libertarian data will value individual freedom. The training data is the invisible constitution.

**Who operates the AI?** The entity running the AI infrastructure can modify the model, change parameters, or selectively present information. This is operational capture -- the AI governance may be formally independent but operationally dependent on whoever runs the servers.

**How is bias prevented?** Every AI has biases inherited from its training data, design choices, and objective function. These biases are harder to detect than the biases of human governors because AI reasoning is less transparent.

### 5.3 Transparency: On-Chain vs. Algorithmic

Token voting has one significant advantage over AI governance: transparency.

- **On-chain votes are fully transparent.** Every vote is publicly recorded on the blockchain. Anyone can verify the outcome. No one can claim the count was wrong.
- **AI decisions are opaque.** Even with explainability tools, the internal reasoning of AI models is not fully transparent. An AI governance decision can be audited for inputs and outputs, but the reasoning process (the "why") is difficult to verify.

This creates a paradox: token voting is transparent but produces bad outcomes (plutocracy). AI governance might produce better outcomes but is less transparent. Which matters more -- transparency of process or quality of outcome?

The Area 1 synthesis answers this clearly: **both matter**, and they are not in fundamental conflict. The solution is not to choose between transparency and quality but to demand both:

- AI governance decisions must be auditable (inputs, outputs, and reasoning explanations must be public).
- Multiple independent AI systems must check each other (plural monitoring).
- Human review must be possible for any AI decision (democratic accountability).

### 5.4 Speed: Feature or Bug?

AI can make governance decisions orders of magnitude faster than human voting. Is this a virtue?

**Arguments for speed:**
- Organizations need to respond quickly to changing conditions.
- Governance bottlenecks (low turnout, long voting periods) slow decision-making.
- In fast-moving environments (markets, technology), slow governance is death.

**Arguments against speed:**
- Speed in governance enables autocracy. Dictatorships are fast. Democracies are slow. The slowness is a feature, not a bug -- it creates time for deliberation, objection, and course correction.
- Rapid decisions can be rapidly wrong. The DAO hack was fast; the response was not, and that slowness was partly protective (it gave the community time to deliberate rather than react).
- Human governance is slow because humans need time to process information, discuss implications, and reach understanding. Speed that bypasses this process bypasses legitimacy.

**The right answer for Agent Commons:** Different decisions need different speeds. Operational decisions (is this contribution high-quality? does this Forg output meet standards?) should be fast. Governance decisions (should we change the rules? how should we distribute resources? should we remove a participant?) should be slow enough for deliberation and objection. The speed of AI governance should be tuned by decision type, not treated as uniformly fast.

### 5.5 The Alignment Problem at Organizational Scale

The AI alignment problem -- how to ensure AI systems pursue human-intended objectives -- applies directly to AI governance. If the AI governance system optimizes for the wrong objective, it will produce outcomes that are technically "correct" but organizationally harmful.

**Parallels to the alignment problem:**
- **Reward hacking** -- an AI that optimizes a measurable metric will find ways to maximize the metric without achieving the intended outcome. An AI governance system that optimizes for "contribution count" will reward trivial contributions. One that optimizes for "revenue" will neglect public goods.
- **Distributional shift** -- an AI trained on data from one era will make poor decisions when conditions change. An AI governance system trained on a healthy commons will not know how to govern a commons in crisis.
- **Goodhart's Law at organizational scale** -- whatever the AI measures and optimizes, participants will game. This is the Soviet central planning problem with a new engine.

**The Anthropic analogy:** Anthropic's Constitutional AI approach -- where AI behavior is guided by a set of principles (a "constitution") rather than by reinforcement from human preferences alone -- is structurally analogous to what Agent Commons needs. The "constitution" for an Agent Commons AI governance system would be the foundational principles that the AI must uphold -- equivalent to the Debian Social Contract or the U.S. Constitution but encoded as AI alignment constraints.

The critical question: who writes the AI constitution? And how is it changed? If the answer is "the AI's developers," then the AI governance system is ultimately controlled by a small group of technologists -- which is neither democratic nor decentralized. If the answer is "the community," then we need a mechanism for translating community values into AI alignment constraints -- which is the full AI alignment problem applied to organizational governance.

### 5.6 What AI Governance Can Learn From DAO Failures

| DAO Lesson | AI Governance Application |
|-----------|--------------------------|
| Code cannot replace judgment | AI must exercise judgment, not just execute rules. But whose judgment? |
| Emergency mechanisms are essential | AI governance must include fast-response modes with post-hoc review |
| Plutocracy is the default outcome of financial-stake governance | AI governance must not weight financial stake in governance decisions |
| Sybil resistance is the fundamental identity challenge | AI may help detect Sybils but also creates new attack surfaces |
| Voter apathy kills governance | AI reduces the need for mass participation but must maintain legitimacy |
| Concentration of power is the natural outcome | Plural, independent AI systems are essential |
| Successful DAOs have clear, bounded purpose | Agent Commons' AI governance should have clearly defined scope |
| Delegation and professionalized governance improve outcomes | AI governance should be supplemented by human experts and delegates |
| Fork/exit mechanisms discipline governance | Agent Commons must ensure low-cost exit with data and reputation portability |

---

## 6. Legal and Regulatory Issues

### 6.1 DAO Legal Status

As of 2025, DAOs exist in a legal gray area in most jurisdictions:

**Jurisdictions with DAO legislation:**

- **Wyoming, USA (2021)** -- enacted the first DAO-specific legislation, allowing DAOs to register as LLCs. The Wyoming DAO LLC provides limited liability for members and a recognized legal entity for contracts, bank accounts, and litigation. However, many DAOs have not adopted this structure because it requires a registered agent in Wyoming and compliance with LLC governance requirements that may conflict with DAO operations.
- **Marshall Islands (2022)** -- recognized DAOs as legal entities with limited liability. The Marshall Islands DAO Act provides a jurisdiction-agnostic legal wrapper.
- **Switzerland** -- DAOs can organize as associations (Verein) under Swiss civil law. The Swiss framework is relatively permissive but requires identifiable members and governance structure.
- **Cayman Islands** -- Foundation company structures have been used as DAO legal wrappers.
- **Vermont, USA** -- enacted a Blockchain-Based LLC (BBLLC) statute in 2018, predating Wyoming but more limited in scope.
- **Tennessee, USA (2022)** and **Utah, USA (2023)** -- enacted DAO legislation following Wyoming's model.

**The majority of jurisdictions** (including the EU, UK, most US states, and most Asian jurisdictions) have no DAO-specific legislation. DAOs operating in these jurisdictions face:

- **General partnership by default.** In most US states, an unincorporated association of people conducting business together is a general partnership -- meaning all members have unlimited personal liability for the organization's debts and legal obligations.
- **Tax ambiguity.** How are DAO token distributions taxed? As income? Capital gains? Dividends? The answer depends on the jurisdiction and the specific token economics, but there is no clear guidance in most places.
- **Regulatory risk.** The SEC has signaled that many governance tokens may be securities under US law. If governance tokens are securities, DAOs that distributed them without registration may have violated securities law.

### 6.2 Liability

**Who is responsible when a DAO causes harm?**

This is an unsolved legal problem. If a DAO makes a governance decision that results in financial loss (as in The DAO hack), damages (as in a poorly coded smart contract that loses user funds), or legal violations (as in a DAO that enables money laundering), who is liable?

- **Under general partnership rules** -- all members (token holders) are potentially liable.
- **Under LLC/Foundation structures** -- the entity is liable, but personal liability is limited.
- **In practice** -- no major DAO has faced significant litigation that tested these questions at scale. The Ooki DAO case (CFTC, 2022) established that a DAO could be held liable as an unincorporated association, but enforcement against distributed, pseudonymous members remains practically difficult.

### 6.3 Tax Treatment

DAO token distributions face unclear tax treatment:

- **Token rewards for contribution** -- could be income (taxed at ordinary rates), capital gains (taxed at lower rates), or neither (if treated as non-economic).
- **Treasury distributions** -- could be dividends, distributions, or something else.
- **Cross-border complexity** -- DAO members are typically global, creating nexus issues for tax purposes.

Most DAO participants simply self-report as best they can. Tax authorities have not yet developed comprehensive DAO-specific guidance, though the IRS has increasingly focused on cryptocurrency taxation generally.

### 6.4 Practical Barriers to Adoption for Agent Commons

Agent Commons faces the same legal challenges as DAOs, plus additional ones:

- **AI governance liability.** If an AI governance system makes a decision that causes harm, who is liable? The AI developer? The commons operator? The community that set the AI's values? Current AI liability law is nascent and rapidly evolving.
- **Employment vs. independent contractor.** Are agents (individuals working within the commons) employees or independent contractors? This classification matters enormously for taxes, benefits, labor protections, and liability. Most commons participants will likely be classified as independent contractors, which means no health insurance, no employment protections, and no unemployment benefits.
- **Intellectual property.** Who owns work product created within a Forg? The agent who created it? The Forg? The commons? If the commons monetizes it (app store model), what licenses are needed?
- **Securities law.** If the commons distributes economic value to contributors based on contribution, the mechanism may constitute a security under SEC interpretations. This would require registration and compliance with securities law -- a significant barrier.
- **Cross-jurisdictional complexity.** A global commons with participants in dozens of countries faces incompatible regulatory regimes. What is legal in one jurisdiction may be illegal in another.

**The honest assessment:** The legal infrastructure for decentralized organizations does not yet exist. Agent Commons will need to either (a) operate within existing legal frameworks (forming LLCs, complying with securities law, etc.), which may compromise some decentralization goals, or (b) advocate for new legal frameworks, which is a multi-year political process.

The most practical approach is probably a hybrid: a legal entity (LLC, foundation, or cooperative) that provides the necessary legal wrapper for contracts, banking, and liability, while maintaining internal governance that is as decentralized as the legal wrapper allows. This is the approach most functional DAOs have adopted.

---

## 7. Cross-Cutting Synthesis: What Agent Commons Should Learn From DAOs

### 7.1 What DAOs Got Wrong (And Agent Commons Must Avoid)

| DAO Mistake | Root Cause | Agent Commons Design Response |
|-------------|-----------|-------------------------------|
| Token-voting plutocracy | Solving Sybil resistance with financial stake | Reputation-based governance with AI-assisted Sybil resistance |
| "Code is law" rigidity | Conflating rules with the medium | AI governance that exercises judgment; human override mechanisms |
| No emergency mechanisms | Ideological commitment to decentralization above all else | Emergency response modes with post-hoc review and accountability |
| Voter apathy | Too many governance decisions for participants to handle | Optimistic governance (most decisions auto-approve); delegation for contested decisions |
| Flash loan / temporary-power attacks | Instantaneous vote weight from temporary financial stake | Conviction-based mechanisms (sustained commitment required); reputation that cannot be flash-borrowed |
| Regulatory non-compliance | Ideological rejection of existing legal frameworks | Legal wrapper (LLC, foundation, cooperative) that provides compliance while preserving internal decentralization |

### 7.2 What DAOs Got Right (And Agent Commons Should Adopt)

| DAO Innovation | How It Works | Agent Commons Application |
|---------------|-------------|--------------------------|
| **Quadratic funding** | Matches small donations more than large; reduces plutocracy | Resource allocation within the commons; priority-setting |
| **Conviction voting** | Sustained staking = more weight; rewards long-term commitment | Governance participation weighted by sustained engagement |
| **Liquid delegation** | Delegate per-issue, revoke anytime | Expert governance without permanent representation |
| **Optimistic governance** | Auto-approve unless challenged | Reduce governance burden; reserve attention for disputes |
| **Ragequit / exit mechanism** | Leave and take proportional treasury share | Forg members can exit with proportional value; disciplines governance |
| **Transparent treasury** | All financial flows visible on-chain | All commons economic activity transparent and auditable |
| **Sybil resistance innovation** | Gitcoin Passport, attestations, social verification | Identity infrastructure that prevents gaming without requiring financial stake |
| **Bicameral governance (Optimism)** | Token House for protocol, Citizens' House for values | Separate governance tracks for operational decisions vs. values/principles |

### 7.3 The Fundamental Question: Is Agent Commons Sufficiently Different?

Agent Commons proposes to replace token voting with AI governance. The critical question: does this solve the fundamental problems, or does it create equivalently bad new ones?

**Problems that AI governance plausibly solves:**
- Plutocracy (AI does not care how much money you have -- unless trained to).
- Voter apathy (AI does not suffer from apathy -- but legitimacy concerns remain).
- Decision speed (AI can process information and decide quickly).
- Expertise gap (AI can analyze complex proposals that human voters cannot evaluate).

**Problems that AI governance may not solve:**
- Power concentration (AI capture replaces token concentration -- potentially worse because less visible).
- Legitimacy (human participants may not accept AI decisions, especially unfavorable ones).
- Gaming (participants will optimize for whatever the AI rewards, creating Goodhart's Law dynamics).
- The recursive governance problem (who governs the AI? if humans, human nature reasserts itself; if AI, there is no correction mechanism).

**Problems that AI governance creates:**
- Opacity (AI reasoning is harder to audit than on-chain votes).
- Dependence (if the AI fails or is compromised, there is no fallback governance mechanism unless one is built in).
- Value lock-in (the AI's values are set during training and difficult to change; this can prevent necessary value evolution).
- Concentration of technical power (the people who can build and modify the AI have power that non-technical participants cannot match).

**The honest assessment:** AI governance is a different set of tradeoffs, not a solution. It trades the known failures of token voting (plutocracy, apathy) for the less-tested risks of algorithmic governance (capture, opacity, Goodhart's Law). Whether this trade is favorable depends entirely on the implementation -- specifically, on whether the AI governance system satisfies the requirements identified in the Area 1 synthesis:

1. Plural, independent AI systems checking each other.
2. Human override with appropriate friction.
3. Transparency of inputs, outputs, and reasoning.
4. Adversarial AI testing governance AI.
5. Democratic governance of the AI's value system.
6. Sunset and renewal mechanisms for AI governance.

If Agent Commons implements all six, it has a reasonable chance of avoiding DAO-style failures. If it implements fewer than all six, it will likely reproduce equivalent failures with different aesthetics.

---

## Key Sources

### The DAO and Ethereum
- DuPont, Q. (2017). "Experiments in Algorithmic Governance: A History and Ethnography of 'The DAO,' a Failed Decentralized Autonomous Organization." In *Bitcoin and Beyond.* Routledge.
- Mehar, M.I., et al. (2019). "Understanding a Revolutionary and Flawed Grand Experiment in Blockchain: The DAO Attack." *Journal of Cases on Information Technology.*
- Buterin, V. (2016). "Critical Update Re: DAO Vulnerability." Ethereum Foundation Blog.
- Buterin, V. (2014). "DAOs, DACs, DAs and More: An Incomplete Terminology Guide." Ethereum Blog.

### DAO Governance
- Buterin, V. (2021). "Moving Beyond Coin Voting Governance." vitalik.ca.
- Buterin, V., Hitzig, Z., and Weyl, E.G. (2018). "A Flexible Design for Funding Public Goods." *Management Science.*
- a16z Crypto (2022). "Governance of DAOs." Research report.
- Chainalysis (2022). "The State of Web3 Governance." Annual report.
- DeepDAO. Ongoing analytics at deepdao.io.

### Governance Innovations
- Hanson, R. (2000). "Shall We Vote on Values, But Bet on Beliefs?" *Journal of Political Philosophy.*
- Lalley, S.P. and Weyl, E.G. (2018). "Quadratic Voting: How Mechanism Design Can Radicalize Democracy." *American Economic Association Papers & Proceedings.*
- Weyl, E.G. and Posner, E.A. (2018). *Radical Markets: Uprooting Capitalism and Democracy for a Just Society.* Princeton University Press.
- Emmett, J. (2019). "Conviction Voting: A Novel Continuous Decision Making Alternative to Governance." Commons Stack blog.

### Specific DAOs
- MakerDAO. "Governance Documentation." makerdao.com.
- Optimism Collective. "The Optimism Collective." community.optimism.io.
- Nouns DAO. "Nouns DAO Governance." nouns.wtf.
- ENS. "ENS DAO Constitution." docs.ens.domains.

### Legal and Regulatory
- Wright, A. (2021). "The Rise of Decentralized Autonomous Organizations: Opportunities and Challenges." *Stanford Journal of Blockchain Law & Policy.*
- CFTC v. Ooki DAO (2022). Case No. 3:22-cv-05416 (N.D. Cal.).
- Wyoming Decentralized Autonomous Organization Supplement (W.S. 17-31-101 through 17-31-115).

### AI Alignment
- Bai, Y., et al. (2022). "Constitutional AI: Harmlessness from AI Feedback." Anthropic. (For the Constitutional AI approach relevant to AI governance.)
- Russell, S. (2019). *Human Compatible: Artificial Intelligence and the Problem of Control.* Viking. (For alignment applied to governance.)
- Christiano, P. (2014). "Eliciting Latent Knowledge." AI Alignment Forum. (For the challenge of verifying AI governance decisions.)
