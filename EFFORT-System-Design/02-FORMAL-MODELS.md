---
created: 2026-02-13T22:00:00Z
updated: 2026-02-13T22:00:00Z
type: formal-models
parent_effort: EFFORT-System-Design
tasks:
  - "1.2 Formal Game-Theoretic Model"
  - "1.4 Power-Law Bounding Theory"
status: completed
backlinks:
  - [[EFFORT-System-Design/EFFORT]]
  - [[EFFORT-Unsolved-Problems/SYNTHESIS]]
  - [[EFFORT-Unsolved-Problems/01-AI-GOVERNANCE]]
  - [[EFFORT-Unsolved-Problems/02-IDENTITY-REPUTATION]]
  - [[EFFORT-Brainstorming-Research/CROSS-AREA-SYNTHESIS]]
---

# Formal Models: Game-Theoretic Equilibrium and Power-Law Bounding

This document provides the mathematical foundations for the Agent Commons system design, covering two interrelated formal models:

- **Part A** develops a game-theoretic model of the Agent/Forg/Commons system, identifying conditions under which cooperation is a Nash equilibrium and analyzing the evolutionary stability of that equilibrium under the minimum viable hedge set.
- **Part B** develops a power-law bounding theory, providing mathematical conditions under which reputation and influence concentration can be bounded below governance-capture thresholds through the five-mechanism bounding stack.

**Notational conventions.** Sets are denoted by uppercase calligraphic letters ($\mathcal{A}$), individual elements by lowercase ($a_i$), cardinalities by $|\cdot|$ or $N$. Functions are lowercase italic ($f, g, u$). Probabilities are $P(\cdot)$, expectations $\mathbb{E}[\cdot]$. All logarithms are natural unless stated otherwise. Time is discrete, indexed by $t \in \{0, 1, 2, \ldots\}$, with each period representing one governance epoch (nominally one month).

---

## Part A: Game-Theoretic Model

### A.1 Model Setup

#### Agent Types and Populations

The model defines three agent types, corresponding to the three-layer architecture from [[CROSS-AREA-SYNTHESIS]] Section 3.1:

**Definition A.1 (Agent Types).** The system consists of:

1. **Individual Agents** $\mathcal{I} = \{a_1, a_2, \ldots, a_N\}$, each representing a verified unique participant. $N = |\mathcal{I}|$ is the commons population.

2. **Forgs** $\mathcal{F} = \{F_1, F_2, \ldots, F_M\}$, where each Forg $F_j \subseteq \mathcal{I}$ is a team of $|F_j| \in [3, 12]$ individuals. Forgs are temporary and overlapping: an individual may belong to multiple Forgs. $M = |\mathcal{F}|$.

3. **The Commons** $\mathcal{C}$, a single platform agent that maintains infrastructure, governance, and reputation systems. In a multi-commons ecosystem, $\mathcal{C} = \{C_1, C_2, \ldots, C_K\}$, but for the core model we treat a single commons.

#### Strategy Spaces

**Definition A.2 (Individual Strategies).** Each individual $a_i$ chooses from strategy space $S_I$:

| Strategy | Description | Behavioral pattern |
|----------|-------------|--------------------|
| $\sigma_C$ (cooperate) | Contribute genuinely, participate in governance, respect norms | Positive-sum behavior |
| $\sigma_R$ (free-ride) | Consume commons resources without proportional contribution | Extract value while appearing cooperative |
| $\sigma_G$ (game) | Optimize for reputation metrics rather than genuine value | Goodhart exploitation |
| $\sigma_X$ (extract) | Actively capture governance or economic mechanisms for private benefit | Rent-seeking and power concentration |
| $\sigma_E$ (exit) | Leave the commons, taking portable reputation and contributions | Exercise the fork/ragequit right |

**Definition A.3 (Forg Strategies).** Each Forg $F_j$ chooses from strategy space $S_F$:

| Strategy | Description |
|----------|-------------|
| $\phi_Q$ (quality-produce) | Deliver high-quality output, maintain Forg reputation |
| $\phi_L$ (corner-cut) | Minimize effort while meeting minimum observable quality thresholds |
| $\phi_K$ (fork) | Split from commons, taking members and IP to a competing commons |
| $\phi_D$ (fragment) | Dissolve into individuals who re-form without institutional memory |

**Definition A.4 (Commons Strategies).** The commons $\mathcal{C}$ (operationalized as the governance AI + constitutional constraints + human oversight) chooses from strategy space $S_C$:

| Strategy | Description |
|----------|-------------|
| $\gamma_M$ (maintain-integrity) | Enforce constitutional constraints, bound concentration, sustain public goods |
| $\gamma_D$ (drift-toward-extraction) | Gradually increase take rate, reduce investment in commons goods, favor incumbents |
| $\gamma_P$ (capture) | Governance becomes a tool of a concentrated coalition, rules rewritten to favor the coalition |

The commons strategy is not chosen by a unitary actor but emerges from the interaction of AI governance, human oversight, and constitutional constraints. We model the effective strategy as $\gamma \in S_C$.

#### Payoff Structure

**Definition A.5 (Individual Payoff Function).** The payoff to individual $a_i$ in period $t$ is:

$$u_i(t) = w_i(t) + \alpha \cdot R_i(t) + \beta \cdot G_i(t) + \mu \cdot m_i(t) - c_i(t)$$

where:
- $w_i(t)$ = economic returns (share of Forg revenue, QF distributions, patronage)
- $R_i(t)$ = reputation stock (governance influence, matching priority, status)
- $G_i(t)$ = governance power (voting weight, committee eligibility)
- $m_i(t)$ = meaning/satisfaction (intrinsic motivation from the work itself; per Jahoda's five functions and SDT's three needs, from [[SYNTHESIS]] Section 4.5)
- $c_i(t)$ = effort cost of the chosen strategy
- $\alpha, \beta, \mu > 0$ are conversion weights reflecting individual valuation of reputation, power, and meaning relative to economic returns

**Assumption A.1.** The effort costs are ordered: $c(\sigma_C) > c(\sigma_G) > c(\sigma_R) > c(\sigma_X)$. Genuine cooperation is costlier than gaming, which is costlier than free-riding, which is costlier than pure extraction. Exit cost $c(\sigma_E)$ depends on the portability of reputation and contributions.

**Definition A.6 (Forg Payoff Function).** The payoff to Forg $F_j$ is:

$$U_j(t) = V_j(t) \cdot (1 - \tau) - \sum_{a_i \in F_j} c_i(t) + \rho \cdot Q_j(t)$$

where:
- $V_j(t)$ = gross value produced by the Forg (market revenue + QF matching + RPGF rewards)
- $\tau$ = commons take rate ($\tau \in [0.05, 0.12]$ per [[SYNTHESIS]] Section 4.3)
- $Q_j(t)$ = quality reputation of the Forg (affects future matching priority)
- $\rho > 0$ = weight on Forg reputation

**Definition A.7 (Commons Payoff Function).** The commons payoff is:

$$W(t) = \tau \cdot \sum_{j=1}^{M} V_j(t) + P(t) - I(t) - L_{\text{exit}}(t)$$

where:
- First term = take rate revenue from all Forgs
- $P(t)$ = public goods value generated (network effects, shared infrastructure, knowledge base)
- $I(t)$ = infrastructure and governance costs (AI inference, legal compliance, dispute resolution)
- $L_{\text{exit}}(t) = \sum_{a_i \in \text{exiters}} \ell(a_i, t)$ = legitimacy/network loss from member exits

#### Information Structure

**Assumption A.2 (Information).** The information available to each agent type:

- **Individuals** observe: their own contributions, the reputation scores of all agents (public), Forg-level outcomes (public), governance decisions and reasoning (public per transparency requirement), aggregate concentration metrics (public). They do *not* observe the true strategies of other individuals.
- **Forgs** additionally observe: intra-Forg contributions (social accountability at Dunbar scale; per [[02-IDENTITY-REPUTATION]] Section 2.2, small teams enable social monitoring).
- **The Commons** (governance AI) observes: all public information plus contribution analytics, behavioral patterns, anomaly signals, and concentration metrics. It does *not* perfectly observe true intent or the distinction between genuine cooperation and sophisticated gaming.

**Assumption A.3 (Signal Noise).** The governance AI detects strategy $\sigma$ with noise:

$$P(\text{detect } \sigma_i \mid \text{true } \sigma_i) = 1 - \epsilon_{\sigma}$$

where $\epsilon_{\sigma_C} \approx 0$ (cooperation is easy to observe), $\epsilon_{\sigma_R} \in [0.1, 0.3]$ (free-riding is moderately detectable), $\epsilon_{\sigma_G} \in [0.2, 0.5]$ (gaming is harder to distinguish from cooperation), $\epsilon_{\sigma_X} \in [0.1, 0.4]$ (extraction depends on subtlety).

These ranges are grounded in empirical data: Amazon's review detection catches 84% of fakes ($\epsilon \approx 0.16$); Stack Overflow's heuristics confirm 60-80% of flagged users ($\epsilon \approx 0.2-0.4$); per [[02-IDENTITY-REPUTATION]] Section 2.5.

---

### A.2 Cooperation Equilibrium Analysis

#### Axelrod Conditions in the Commons Context

**Proposition A.1 (Axelrod Conditions for Cooperation).** Cooperation ($\sigma_C$) can be sustained as a Nash equilibrium in a repeated game if four conditions hold (Axelrod, 1984):

1. **Repeated interaction** — agents expect to interact again in the future
2. **Recognition** — agents can identify each other and recall past behavior
3. **Low termination probability** — the probability that the interaction ends in any given period is low
4. **Punishment** — defectors experience consequences

**Mapping to the Agent Commons:**

| Axelrod Condition | Commons Mechanism | Strength |
|------|------|------|
| Repeated interaction | Forgs are ongoing (multi-project); commons membership is persistent; individuals re-encounter each other | Strong: median Forg duration is bounded below by project timescales (months, not days) |
| Recognition | Multi-dimensional reputation system provides public history of past behavior | Strong: AI-tracked contribution history is more complete than any human memory |
| Low termination probability | Commons is a persistent institution; individuals come and go but the commons endures | Moderate: any individual Forg may dissolve, but commons-level interaction continues |
| Punishment | Reputation loss from detected defection; exclusion from high-quality Forgs; reduced governance voice; exit of cooperators reduces network value | Strong: multi-channel punishment (reputation, economic, social) |

**Theorem A.1 (Folk Theorem Application).** In the repeated game $\Gamma$ where individuals interact within the commons over indefinite periods with discount factor $\delta \in (0,1)$, any payoff vector that Pareto-dominates the one-shot Nash equilibrium can be sustained as a subgame perfect equilibrium if $\delta$ is sufficiently close to 1.

*Proof sketch.* Standard folk theorem for infinitely repeated games with imperfect monitoring (Fudenberg, Levine, Maskin, 1994). The key requirement is that the monitoring structure allows statistical discrimination between cooperators and defectors. By Assumption A.3, the detection probability $1 - \epsilon_\sigma > 0.5$ for all non-cooperative strategies, satisfying the identifiability condition. The commons governance AI aggregates signals across time, improving detection accuracy with duration. $\square$

**Corollary A.1.** The minimum discount factor $\delta^*$ for sustaining cooperation is decreasing in the detection probability $(1-\epsilon)$. Better monitoring makes cooperation easier to sustain.

#### Effect of Each Minimum Viable Hedge on Equilibrium

The minimum viable hedge set from [[CROSS-AREA-SYNTHESIS]] Section 3.2 consists of six mechanisms. We model the effect of each on the cooperation equilibrium.

**Hedge 1: Small Groups (Dunbar Scale)**

**Proposition A.2.** Reducing Forg size from $n$ to $n' < n$ increases the probability of detecting defection within the Forg by a factor of approximately $n/n'$.

*Argument.* In a group of $n$ people, each individual is observed by $n-1$ others. The probability that *no one* detects defection is $(1 - p_{\text{individual}})^{n-1}$, where $p_{\text{individual}}$ is the probability that a single observer detects defection. Thus $P(\text{detect}) = 1 - (1-p)^{n-1}$. For small $p$, this is approximately $(n-1) \cdot p$, which scales linearly with group size. However, the individual detection probability $p$ is inversely related to group size (attention dilution): $p \propto 1/n$. The net effect: $P(\text{detect}) \approx (n-1)/n$, which is nearly constant, but the *social cost* of detected defection is higher in smaller groups (exclusion from a 5-person team is more costly than exclusion from a 50-person team because alternative teams are scarcer at small scale).

At Forg sizes of 5-12 (Buurtzorg model), social accountability creates near-complete monitoring. The payoff to free-riding in a small Forg is:

$$u_R^{\text{small}} = w_R - P(\text{detect}) \cdot \text{penalty} \approx w_R - (1 - \epsilon_{\text{small}}) \cdot \text{penalty}$$

where $\epsilon_{\text{small}} \ll \epsilon_{\text{large}}$. For Dunbar-scale teams, $\epsilon_{\text{small}} \approx 0.05$ (you can fool your 5-person team about 5% of the time). This makes free-riding unprofitable whenever $\text{penalty} > w_R / 0.95$.

**Hedge 2: Transparent Contribution Tracking**

**Proposition A.3.** Transparent contribution tracking reduces the information asymmetry between cooperators and defectors by providing a public signal correlated with true strategy.

*Formally.* Let $s_i(t)$ be the public contribution signal for agent $a_i$ at time $t$. Define the signal-to-noise ratio:

$$\text{SNR} = \frac{\mathbb{E}[s_i \mid \sigma_C] - \mathbb{E}[s_i \mid \sigma_R]}{\text{Var}(s_i \mid \sigma)^{1/2}}$$

Transparent tracking (extending GitHub's contribution graph beyond code) increases SNR by:
- Adding signal dimensions (code + design + governance + community)
- Reducing the variance through AI-verified activity logs
- Making the signal public, enabling peer verification

Higher SNR directly reduces $\epsilon_\sigma$ in Assumption A.3, strengthening the detection condition in Theorem A.1.

**Hedge 3: Credible Exit (Fork Right)**

**Proposition A.4 (Exit as Disciplining Device).** The credible threat of exit creates an outside option $\bar{u}_i$ that disciplines the commons against drift toward extraction.

*Model.* If the commons plays $\gamma_D$ (drift toward extraction), individual payoff under cooperation drops to:

$$u_i(\sigma_C, \gamma_D) = w_i \cdot (1 - \Delta\tau) + \alpha R_i + \beta G_i + \mu m_i - c_C - \delta_{\text{decay}} \cdot P(t)$$

where $\Delta\tau$ is the increased extraction and $\delta_{\text{decay}}$ reflects declining public goods investment.

The exit payoff is:

$$\bar{u}_i = R_i^{\text{portable}} \cdot v_{\text{external}} + w_i^{\text{market}} - c_E$$

where $R_i^{\text{portable}}$ is the fraction of reputation portable to a forked or external commons, $v_{\text{external}}$ is the value of that reputation externally, and $c_E$ is the switching cost.

**Key result:** The commons must maintain $u_i(\sigma_C, \gamma_M) > \bar{u}_i$ for a sufficient fraction of members to prevent exit cascades. This creates an upper bound on extraction:

$$\tau < \tau^* \text{ where } \tau^* \text{ solves } u_i(\sigma_C, \gamma_M, \tau) = \bar{u}_i$$

The more portable the reputation ($R_i^{\text{portable}} \to R_i$) and the lower the switching cost ($c_E \to 0$), the tighter the bound on extraction. This is why reputation portability and low fork cost are essential design features.

**Empirical grounding:** The io.js fork of Node.js resolved a governance crisis in 8 months. Approximately 30% of open-source forks become more successful than the parent project ([[CROSS-AREA-SYNTHESIS]] Section 3.2). The fork threat is empirically credible.

**Hedge 4: Bounded Proportional Rewards**

**Proposition A.5.** Floors and ceilings on rewards reduce the incentive for extreme strategies.

*Model.* Define the reward function as:

$$w_i = \min\left(\bar{w}, \max\left(\underline{w}, f(c_i, Q_i)\right)\right)$$

where $\underline{w}$ is the floor (UBR), $\bar{w}$ is the ceiling (contribution cap), and $f$ is the base reward function.

The floor $\underline{w} > 0$ ensures that the payoff to cooperation is bounded below, reducing the risk of cooperation. The ceiling $\bar{w}$ ensures that the payoff to extraction is bounded above. Together:

$$u_X - u_C \leq (\bar{w} - \underline{w}) + \alpha(\bar{R} - \underline{R}) - (c_C - c_X)$$

If the spread $\bar{w} - \underline{w}$ is bounded and $\bar{R} - \underline{R}$ is bounded (via concentration bounding, see Part B), then the advantage of extraction over cooperation is bounded. This limits the temptation to defect.

**Hedge 5: Plural Adversarial Monitoring**

**Proposition A.6.** Using $k$ independent monitoring systems (plural AI + human oversight + prediction markets + community red-teaming) reduces the probability of undetected defection exponentially in $k$.

*Formally.* If each monitoring system independently detects defection with probability $p_m$ and the systems are structurally independent (different providers, different training data, per [[01-AI-GOVERNANCE]] Section 1.2), then:

$$P(\text{undetected}) = \prod_{m=1}^{k} (1 - p_m)$$

For $k = 4$ systems each with $p_m = 0.7$: $P(\text{undetected}) = 0.3^4 = 0.0081$.

**Caveat:** True independence is hard to achieve (AI models share training data, biases correlate). If correlation $\rho$ exists between detection failures, the bound weakens:

$$P(\text{undetected}) \geq \left(\frac{1}{k}\sum_m (1-p_m)\right)^k \cdot f(\rho)$$

where $f(\rho) > 1$ is an increasing function of correlation. The adversarial relationship requirement (different providers with different corporate incentives, per [[01-AI-GOVERNANCE]] Section 1.2) is the mechanism for minimizing $\rho$.

**Warning from research:** Covert collusion between AI agents has been demonstrated in healthcare settings (arXiv, Many-to-One Adversarial Consensus, 2025). Independence must be structural, verified through red-teaming, and never assumed.

**Hedge 6: Automatic Renewal**

**Proposition A.7.** Term limits with period $T$ prevent entrenchment equilibria by ensuring that governance positions are contested at regular intervals.

*Model.* Without renewal, a governance position held by agent $a_i$ for duration $d$ produces incumbency advantage:

$$G_i(t) = G_0 + \eta \cdot d$$

where $\eta > 0$ is the rate of incumbency advantage accumulation (network effects, information asymmetry, institutional knowledge). After long tenure $d \gg T$, the incumbency advantage exceeds the cost of challenging, making displacement infeasible.

With term limit $T$, governance positions reset every $T$ periods:

$$G_i(t) = G_0 + \eta \cdot (t \mod T)$$

This bounds the maximum incumbency advantage at $\eta \cdot T$, ensuring that governance capture requires re-capture every $T$ periods. For $T = 6$ months (per sortition assembly design in [[01-AI-GOVERNANCE]]), the maximum incumbency advantage is bounded at $6\eta$.

#### Combined Equilibrium Conditions

**Theorem A.2 (Cooperation Equilibrium Under Hedge Set).** Define the *cooperation premium* as:

$$\Delta u_i = u_i(\sigma_C, \sigma_{-i}^C, \gamma_M) - \max_{\sigma \neq \sigma_C} u_i(\sigma, \sigma_{-i}^C, \gamma_M)$$

Cooperation is a Nash equilibrium if $\Delta u_i > 0$ for all agents $a_i$. Under the full hedge set, the cooperation premium is:

$$\Delta u_i \approx \underbrace{(w_C - w_R^{\text{detected}})}_{\text{economic incentive}} + \underbrace{\alpha \cdot (R_C - R_D) \cdot (1-\epsilon)}_{\text{reputation incentive}} + \underbrace{\mu \cdot (m_C - m_D)}_{\text{meaning incentive}} - \underbrace{(c_C - c_D)}_{\text{effort cost difference}}$$

where subscript $D$ denotes the best non-cooperative strategy, $\epsilon$ is the combined detection failure rate under plural monitoring, and the meaning differential $m_C - m_D$ reflects the intrinsic satisfaction from genuine cooperation.

**Parameter ranges for cooperation dominance.** Cooperation is a Nash equilibrium when:

1. $\epsilon < \epsilon^* \equiv \frac{(w_C - w_R) + \mu(m_C - m_D)}{(w_C - w_R) + \alpha(R_C - R_D)}$ — detection must be good enough
2. $\tau < \tau^*$ from Proposition A.4 — extraction must be bounded
3. $c_C - c_D < (1-\epsilon) \cdot [\alpha(R_C - R_D) + (w_C - w_R^{\text{detected}})] + \mu(m_C - m_D)$ — cooperation cost premium must be compensated by reputation + economic + meaning differentials

---

### A.3 Defection and Gaming Analysis

#### Free-Riding Dynamics

**Proposition A.8 (Free-Riding Threshold).** Free-riding ($\sigma_R$) becomes the dominant strategy when:

$$c_C - c_R > (1-\epsilon_R) \cdot \text{penalty}_R + \mu \cdot (m_C - m_R)$$

That is, when the saved effort from free-riding exceeds the expected penalty plus the meaning loss.

In a commons of size $N$ with $n_R$ free-riders, the detection probability for each free-rider depends on the ratio $n_R/N$. If too many agents free-ride simultaneously, the monitoring system is overwhelmed (anomaly detection works by comparing against a baseline of cooperative behavior; if the baseline shifts, anomalies become normal).

**Critical free-rider fraction:** Let $n_R^*$ be the maximum number of free-riders the monitoring system can detect. For the system designed to tolerate 5-15% gaming (per [[02-IDENTITY-REPUTATION]] Section 2.5), $n_R^*/N \approx 0.15$. Beyond this threshold, free-riding detection degrades, creating a tipping point.

**Implication:** The system must maintain $n_R < n_R^*$ through a combination of detection and deterrence. The hedge set provides deterrence through penalties; the multi-signal monitoring provides detection. The 5-15% tolerance margin is a design parameter that must be calibrated empirically during the pilot.

#### Goodhart Gaming

**Proposition A.9 (Goodhart's Law as a Game).** When reputation metric $R$ is used to allocate rewards, agents maximize $R$ rather than the underlying value $V$ that $R$ was designed to measure.

*Formally.* Let $V_i$ be the true value of agent $a_i$'s contribution and $R_i = V_i + \eta_i$ be the observed reputation, where $\eta_i$ is the gaming noise (the gap between measured and true value). A gamer invests effort in increasing $\eta_i$ rather than $V_i$.

The payoff to gaming is:

$$u_G = f(V_i + \eta_i) \cdot (1 - P(\text{detect gaming})) + f(V_i + \eta_i) \cdot P(\text{detect}) \cdot (1 - \text{penalty fraction}) - c_G(\eta_i)$$

where $c_G(\eta_i)$ is the cost of producing gaming noise $\eta_i$.

**The multi-signal defense:** If reputation is composed of $k$ independent signals, $R_i = \sum_{s=1}^{k} R_i^{(s)}$, and gaming requires effort $c_G^{(s)}$ for each signal, the total gaming cost is:

$$c_G^{\text{total}} = \sum_{s=1}^{k} c_G^{(s)}(\eta_i^{(s)})$$

If signals are genuinely independent (gaming one does not reduce the cost of gaming others), the cost of comprehensive gaming scales linearly in $k$. For $k = 4$ signals (code quality + peer review + governance participation + community building), comprehensive gaming costs 4x more than single-signal gaming.

**Caveat:** Signal independence is an assumption, not a guarantee. Per [[02-IDENTITY-REPUTATION]] Section 2.5, if credibility in one dimension transfers to others, the independence assumption fails and the linear cost scaling collapses.

#### Sybil Game

**Definition A.8 (Sybil Attack).** A Sybil attacker creates $s$ fake identities, each passing Sybil resistance with probability $p_{\text{pass}}$ at cost $c_{\text{Sybil}}$ per identity. The attacker uses $s$ identities to inflate reputation and governance power.

**Proposition A.10 (Sybil Profitability).** The expected payoff from a Sybil attack with $s$ identities is:

$$u_{\text{Sybil}}(s) = s \cdot p_{\text{pass}} \cdot \left[\text{QF advantage}(s) + \text{governance advantage}(s)\right] - s \cdot c_{\text{Sybil}}$$

Under **quadratic funding**, the Sybil advantage from splitting a contribution $D$ across $s$ identities is:

$$\text{QF advantage}(s) = \left(\sum_{i=1}^{s} \sqrt{D/s}\right)^2 - D^2 = D \cdot (s - 1)$$

Wait—more precisely, the matching under QF for a project receiving contributions $\{d_1, \ldots, d_n\}$ is proportional to $\left(\sum_i \sqrt{d_i}\right)^2$. If one donor splits $D$ into $s$ equal parts:

$$\left(\sum_{i=1}^{s} \sqrt{D/s}\right)^2 = s \cdot D$$

vs. the single donation matching component:

$$\left(\sqrt{D}\right)^2 = D$$

The Sybil gain is $(s-1) \cdot D$ in additional matching. This is the fundamental QF Sybil vulnerability documented in [[02-IDENTITY-REPUTATION]] Section 2.3.

**The Sybil resistance threshold:** The Sybil attack is unprofitable when:

$$s \cdot c_{\text{Sybil}} > (s-1) \cdot D \cdot p_{\text{pass}}^s + \text{governance gain}(s)$$

For the layered identity system (pilot), $c_{\text{Sybil}} \approx c_{\text{onboarding}} + c_{\text{stamps}} + c_{\text{time-to-build-history}}$. At pilot scale with trusted onboarding, $c_{\text{Sybil}}$ is high (requires fooling a human coordinator). At scale, the cost depends on the Sybil resistance stack.

**Key result:** The cost of Sybil resistance $c_{\text{Sybil}}$ must scale at least linearly with the expected gain per Sybil identity. If the commons grows and rewards increase, Sybil resistance must correspondingly increase.

#### Coalition Capture Analysis

**Proposition A.11 (Governance Capture by Coalition).** A coalition $\mathcal{K} \subset \mathcal{I}$ of $k = |\mathcal{K}|$ agents can capture governance if:

$$\sum_{a_i \in \mathcal{K}} G_i(t) > \theta_{\text{gov}} \cdot \sum_{a_i \in \mathcal{I}} G_i(t)$$

where $\theta_{\text{gov}}$ is the governance decision threshold (simple majority: $\theta = 0.5$; supermajority: $\theta = 2/3$).

**Under quadratic governance weighting:** If voting power is $\sqrt{G_i}$ rather than $G_i$, the capture condition becomes:

$$\sum_{a_i \in \mathcal{K}} \sqrt{G_i(t)} > \theta_{\text{gov}} \cdot \sum_{a_i \in \mathcal{I}} \sqrt{G_i(t)}$$

This is harder to achieve with concentrated holdings. A single agent with $G = 10000$ has voting power $100$ under quadratic weighting vs. $10000$ under linear. 100 agents with $G = 100$ each have collective voting power $100 \times 10 = 1000$. The concentration advantage is reduced by a factor of $\sqrt{G_{\text{max}}/G_{\text{median}}}$.

**The Nakamoto threshold:** We define governance capture as feasible when the Nakamoto coefficient $\mathcal{N}$ (minimum number of agents whose combined governance power exceeds $\theta_{\text{gov}}$) drops below $\sqrt{N}$:

$$\mathcal{N} < \sqrt{N} \implies \text{governance capture is dangerously feasible}$$

For a 200-person pilot, $\sqrt{200} \approx 14$. If fewer than 14 people could control governance, capture is feasible. For 10,000 participants, $\sqrt{10000} = 100$.

**Constitutional protection:** Constitutional amendments require supermajority $\theta_{\text{const}} = 2/3$ plus a time delay $\Delta t_{\text{amendment}} \geq 3$ months (per [[01-AI-GOVERNANCE]] Section 1.5). This means:

$$\sum_{a_i \in \mathcal{K}} \sqrt{G_i} > \frac{2}{3} \sum_{a_i \in \mathcal{I}} \sqrt{G_i}$$

AND the coalition must maintain this majority for at least $\Delta t_{\text{amendment}}$ periods, during which monitoring may detect the capture attempt and trigger counter-mobilization.

#### Fork Threat as Credible Punishment

**Proposition A.12 (Fork as Nash Equilibrium).** Forking is a Nash equilibrium for the forking party when:

$$\underbrace{u_i^{\text{fork}}}_{\text{payoff in new commons}} > \underbrace{u_i^{\text{stay}}}_{\text{payoff under captured governance}}$$

where:

$$u_i^{\text{fork}} = R_i^{\text{portable}} \cdot v_{\text{new}} + w_i^{\text{new}} \cdot (1 - \tau_{\text{new}}) - c_{\text{fork}}$$

$$u_i^{\text{stay}} = w_i^{\text{old}} \cdot (1 - \tau_{\text{old}} - \Delta\tau_{\text{extraction}}) + \alpha R_i^{\text{old}} + \beta G_i^{\text{diminished}}$$

The fork threat is credible when:
1. $R_i^{\text{portable}} / R_i > \lambda$ — sufficient reputation portability ($\lambda > 0.5$ recommended)
2. $c_{\text{fork}} < c_{\text{threshold}}$ — fork cost is bounded (IP under Apache 2.0, data exportable)
3. A critical mass $n_{\text{fork}} > n_{\text{min}}$ of members would fork simultaneously

**The fork deterrence effect on commons behavior:** The commons knows that playing $\gamma_D$ (drift toward extraction) triggers exit probability $P(\text{fork} \mid \gamma_D)$. The commons payoff under drift is:

$$W(\gamma_D) = (\tau + \Delta\tau) \cdot V_{\text{total}} \cdot P(\text{no fork}) + 0 \cdot P(\text{fork}) - I$$

For $P(\text{fork} \mid \gamma_D) > \Delta\tau / (\tau + \Delta\tau)$, the expected extraction from drift is negative. This is the formal mechanism by which fork threat disciplines governance.

---

### A.4 Evolutionary Game Theory

#### Replicator Dynamics

**Definition A.9 (Replicator Equation).** Let $x_\sigma(t)$ be the fraction of the individual population playing strategy $\sigma$ at time $t$. The replicator dynamics are:

$$\dot{x}_\sigma = x_\sigma \left[\pi(\sigma, \mathbf{x}) - \bar{\pi}(\mathbf{x})\right]$$

where $\pi(\sigma, \mathbf{x})$ is the expected payoff to strategy $\sigma$ against population profile $\mathbf{x} = (x_C, x_R, x_G, x_X, x_E)$, and $\bar{\pi} = \sum_\sigma x_\sigma \pi(\sigma, \mathbf{x})$ is the population mean payoff.

#### Can Defectors Invade a Cooperating Population?

**Proposition A.13.** Starting from $\mathbf{x} = (1, 0, 0, 0, 0)$ (all cooperators), a small mutant fraction $\epsilon$ of strategy $\sigma_D$ can invade if $\pi(\sigma_D, \mathbf{x}^C) > \pi(\sigma_C, \mathbf{x}^C)$.

Under the full hedge set:

$$\pi(\sigma_R, \mathbf{x}^C) = w_R + \alpha R_R - (1-\epsilon_R) \cdot \text{penalty}_R - c_R$$

$$\pi(\sigma_C, \mathbf{x}^C) = w_C + \alpha R_C + \mu m_C - c_C$$

The free-rider invades when:

$$(w_R - w_C) + (c_C - c_R) > (1-\epsilon_R) \cdot \text{penalty}_R + \alpha(R_C - R_R) + \mu \cdot m_C$$

**Key insight:** The meaning term $\mu \cdot m_C$ provides an *intrinsic* defense against invasion that does not depend on monitoring quality. Even with perfect free-riding (undetected, $\epsilon_R = 1$), cooperation survives if:

$$(c_C - c_R) < \alpha(R_C - R_R) + \mu \cdot m_C + (w_C - w_R)$$

This is the formal expression of the [[SYNTHESIS]] finding that meaning and purpose mechanisms are not optional luxuries but structural defenses.

#### Can Cooperators Invade an Extractive Population?

**Proposition A.14 (Cold-Start Problem).** Starting from $\mathbf{x} = (0, 0, 0, 1, 0)$ (all extractors), a small cooperating mutant fraction $\epsilon$ cannot invade because:

1. The cooperator's contributions are extracted by the surrounding population
2. Reputation gains are meaningless in a system where reputation is gamed
3. The meaning payoff is destroyed by the extractive environment

This is the formal statement of the cold-start problem from [[SYNTHESIS]] Section 7.2. Cooperators cannot bootstrap a cooperative equilibrium from within a fully extractive system.

**Resolution (Bootstrap Strategy):** The cold-start requires one of:

1. **Selective entry:** Start with a pre-screened population of cooperators (the 50-200 person pilot with trusted onboarding). This is equivalent to starting at $\mathbf{x} \approx (1, 0, 0, 0, 0)$ and defending against invasion, which is tractable per Proposition A.13.

2. **External subsidy:** Provide payoff to cooperators that exceeds the extractive surplus (grant funding during the cold-start phase). Per [[SYNTHESIS]] Section 4.3, the 24-month pilot plan assumes grant-heavy funding in Year 1.

3. **Network effects:** A commons with even a small cooperating population may provide unique value (AI governance tools, matching markets) unavailable elsewhere, creating $w_C^{\text{commons}} > w_X^{\text{market}}$ even at small scale.

#### Evolutionary Stability

**Definition A.10.** Strategy $\sigma^*$ is an **Evolutionary Stable Strategy (ESS)** if for every mutant strategy $\sigma' \neq \sigma^*$:

$$\pi(\sigma^*, \sigma^*) > \pi(\sigma', \sigma^*) \quad \text{or} \quad \left[\pi(\sigma^*, \sigma^*) = \pi(\sigma', \sigma^*) \text{ and } \pi(\sigma^*, \sigma') > \pi(\sigma', \sigma')\right]$$

**Proposition A.15 (Cooperation as ESS).** Under the full hedge set, cooperation $\sigma_C$ is an ESS if:

1. $\epsilon < \epsilon^*$ (detection is sufficient) — from Theorem A.2
2. $\mu \cdot m_C > c_C - c_R - (w_R - w_C)$ (meaning provides residual defense) — from Proposition A.13
3. The fork threat maintains $u_C^{\text{stay}} > \bar{u}$ (outside option disciplines the commons) — from Proposition A.4

When all three hold, no mutant strategy can invade a cooperating population. The system is stable against evolutionary drift.

**What breaks evolutionary stability:**

- Monitoring degradation ($\epsilon \to 1$): If the governance AI is captured or degrades, gaming becomes undetectable.
- Meaning decay ($\mu \to 0$ or $m_C \to 0$): Per [[SYNTHESIS]] Section 5.2 on purpose decay, meaning erodes over generational timescales (40-60 years for comparable organizations).
- Fork cost increase ($c_E \to \infty$): If switching costs increase (lock-in, non-portable reputation), the exit threat loses credibility.

#### Multi-Commons Competition

**Proposition A.16.** In a population of $K$ competing commons instances, selection favors commons with:

1. Higher aggregate member payoff $\sum_i u_i$ (attracts and retains members)
2. Lower free-rider fraction $n_R/N$ (produces higher-quality output)
3. Lower concentration (Nakamoto coefficient $> \sqrt{N}$, preventing capture)

The inter-commons evolutionary dynamics select for better governance: commons that drift toward extraction lose members to better-governed alternatives. This is the formal analogue of capitalism's creative destruction ([[CROSS-AREA-SYNTHESIS]] Section 3.1, Layer 5) operating at the inter-commons level.

**Condition for selection to work:** There must be sufficiently low switching costs between commons instances. If switching costs are high, poor-governance commons can trap members (the employer lock-in problem). Reputation portability is the mechanism that keeps switching costs low.

---

### A.5 Mechanism Design Integration

#### Quadratic Funding and the Payoff Matrix

**Proposition A.17.** QF changes the individual payoff matrix by:

1. **Reducing free-riding incentive:** QF matching amplifies small contributions, so even modest cooperation generates disproportionate matching. The marginal return on the first dollar of contribution is higher than under linear funding, incentivizing some contribution even for free-riders.

2. **Introducing collusion incentive:** QF's mathematical structure rewards breadth of support. A project with genuine broad support gets more matching. But a project with *coordinated fake* broad support (Sybil attack) gets the same advantage. This creates a new strategic dimension: collude-to-appear-popular.

*Formally.* The matching received by project $p$ is:

$$M_p = \left(\sum_{i=1}^{n_p} \sqrt{d_{ip}}\right)^2 - \sum_{i=1}^{n_p} d_{ip}$$

The collusion payoff for $k$ agents coordinating contributions of $d/k$ each:

$$M_p^{\text{collusion}} = \left(k \cdot \sqrt{d/k}\right)^2 - d = k \cdot d - d = (k-1) \cdot d$$

vs. single honest contribution: $M_p^{\text{honest}} = d - d = 0$ (no matching for a single contributor).

**Net effect on equilibrium:** QF strengthens cooperation incentives (matching rewards genuine broad support) but weakens them along the collusion dimension (matching also rewards coordinated fake support). The net effect depends on the strength of Sybil resistance and collusion detection. QF is cooperation-promoting if and only if Sybil resistance is adequate.

#### Time-Decaying Reputation and Evolutionary Dynamics

**Proposition A.18.** Time decay with rate $\lambda$ changes the evolutionary dynamics by:

1. **Preventing incumbency lock-in:** Without decay, early cooperators accumulate reputation advantages that make them increasingly hard to displace, even if they switch to free-riding or extraction. With decay, a former cooperator who switches to free-riding sees their reputation (and thus payoff advantage) decline exponentially.

2. **Rewarding sustained cooperation:** The steady-state reputation under continuous cooperation is $R^* = c / \lambda$ where $c$ is the contribution rate per period. This is bounded regardless of tenure, preventing permanent dominance by founders.

3. **Creating vulnerability windows:** During legitimate absences (caregiving, sabbatical), reputation decays. The "freezing" mechanism (per [[02-IDENTITY-REPUTATION]] Section 2.4) mitigates this but introduces a new gaming dimension: claiming false absences to freeze reputation while contributing elsewhere.

**Effect on replicator dynamics:** Decay rate $\lambda$ appears in the payoff function as:

$$\pi(\sigma, \mathbf{x}, \lambda) = \pi_0(\sigma, \mathbf{x}) - \lambda \cdot \alpha \cdot R_i(t)$$

Higher $\lambda$ reduces the advantage of all strategies proportionally to accumulated reputation. This compresses the payoff distribution, making the population more mixed (less dominated by any single strategy). The evolutionary dynamics become more fluid — advantageous strategies spread faster but also decay faster.

#### Fork Threat and Commons Behavior

**Proposition A.19.** The fork threat changes the commons' optimal strategy from $\gamma_D$ toward $\gamma_M$ by making the cost of extraction endogenous.

Without fork threat: The commons faces no competitive discipline. The optimal extraction rate is:

$$\tau^*_{\text{no fork}} = \arg\max_\tau \tau \cdot V(\tau) \text{ where } V'(\tau) < 0$$

This is the standard Laffer curve maximum. The commons extracts up to the revenue-maximizing rate.

With fork threat: The effective revenue function becomes:

$$W(\tau) = \tau \cdot V(\tau) \cdot [1 - P_{\text{fork}}(\tau)]$$

where $P_{\text{fork}}(\tau)$ is the probability of a fork at take rate $\tau$, with $P_{\text{fork}}'(\tau) > 0$. This shifts the optimum toward lower extraction:

$$\tau^*_{\text{fork}} < \tau^*_{\text{no fork}}$$

The stronger the fork threat (lower fork costs, higher reputation portability), the more constrained the commons.

#### Combined Mechanism Assessment

**Conjecture A.1 (Full Stack Cooperation).** Under the combined mechanism stack — QF allocation + time-decaying reputation + quadratic governance weighting + fork threat + plural monitoring + bounded rewards + automatic renewal — the cooperative strategy profile $(\sigma_C, \phi_Q, \gamma_M)$ is both a Nash equilibrium and an ESS, provided:

1. Sybil resistance parameter $c_{\text{Sybil}} > c^*_{\text{Sybil}}(\tau, V)$ (identity security scales with economic stakes)
2. Detection probability $(1 - \epsilon) > 0.85$ (combined multi-signal detection is above threshold)
3. Meaning payoff $\mu \cdot m_C > 0$ (participants find the work meaningful)
4. Reputation portability $\lambda_{\text{portable}} > 0.5$ (fork threat is credible)
5. Concentration bounding keeps Nakamoto coefficient $> \sqrt{N}$ (no coalition can capture governance)

*This is a conjecture, not a theorem. A proof would require:* (a) explicit payoff parameterization from pilot data, (b) verification that the combined mechanism effects do not create unexpected interaction terms that destabilize the equilibrium, and (c) computational verification that no mixed-strategy deviation is profitable. The simulation work in Phase 2 (Task 2.1) should test this conjecture computationally.

---

## Part B: Power-Law Bounding Theory

### B.1 The Concentration Problem

#### Formal Statement

**Definition B.1 (Preferential Attachment).** In a network where new connections form with probability proportional to existing degree:

$$P(\text{new connection to node } i) = \frac{k_i + a}{\sum_j (k_j + a)}$$

where $k_i$ is the degree (connections, reputation, influence) of node $i$ and $a \geq 0$ is an offset parameter, the asymptotic degree distribution follows a power law:

$$P(k) \propto k^{-\gamma}, \quad \gamma = 2 + a/m$$

where $m$ is the number of connections per new node (Barabasi & Albert, 1999). For linear preferential attachment ($a = 0$, $m = 1$), $\gamma = 3$.

**Translation to Commons Context.** In the Agent Commons, "degree" is reputation/influence. Successful contributors attract more collaboration requests, more visibility, more governance opportunities. Each of these increases future reputation, creating preferential attachment:

$$P(\text{new contribution credit to } a_i) \propto R_i(t)$$

Without intervention, reputation follows $P(R) \propto R^{-\gamma}$ with $\gamma \in [2, 3]$, producing extreme concentration.

#### Empirical Concentration Data

**Fact B.1.** Observed concentration in comparable systems:

| System | Gini Coefficient | Nakamoto Coefficient | Source |
|--------|-----------------|---------------------|--------|
| Top 10 DeFi DAOs | 0.97 - 0.99 | 3-10 | Cambridge Centre, DL News 2024 |
| Apache OSS projects | 0.6 - 0.9 (89% of projects) | Not reported | PLOS One 2016 |
| Stack Overflow reputation | Extreme (top 1% dominates) | Not reported | arXiv:2111.07101 |
| Compound DAO voting | Top 10 = 57.86% | ~5 | ScienceDirect 2024 |
| Uniswap DAO voting | Top 10 = 44.72% | ~8 | ScienceDirect 2024 |
| U.S. income (reference) | 0.49 | N/A | Census 2024 |
| South Africa (most unequal country) | 0.63 | N/A | World Bank |

DAOs — the closest existing analogue to the Agent Commons — have Gini coefficients 50-60% higher than the most unequal country on Earth.

#### Governance Capture Threshold

**Definition B.2 (Governance Capture Threshold).** The system is vulnerable to governance capture when:

$$\mathcal{N}(t) < \sqrt{N(t)}$$

where $\mathcal{N}(t)$ is the Nakamoto coefficient (minimum entities to control >50% of governance power) and $N(t)$ is the total population.

For the pilot ($N = 200$): $\mathcal{N}_{\text{safe}} > 14$
For scale ($N = 10000$): $\mathcal{N}_{\text{safe}} > 100$

**Definition B.3 (Gini Target).** The target Gini coefficient for the commons reputation distribution is:

$$\text{Gini}(R) < G^* = 0.6$$

This is below the level observed in even the most unequal countries, and far below DAO levels. It is achievable in principle (many cooperatives and small organizations maintain Gini < 0.5 for income) but requires active intervention.

---

### B.2 Countermeasure Analysis

#### B.2.1 Time Decay

**Model.** Reputation for agent $a_i$ at time $t$ with time decay rate $\lambda$:

$$R_i(t) = \sum_{j: t_j \leq t} c_{ij} \cdot e^{-\lambda(t - t_j)}$$

where $c_{ij}$ is the reputation credit from contribution $j$ at time $t_j$.

**Proposition B.1 (Steady-State Reputation Under Decay).** If agent $a_i$ contributes at constant rate $r_i$ (reputation credit per period), the steady-state reputation is:

$$R_i^* = \lim_{t \to \infty} R_i(t) = \frac{r_i}{\lambda}$$

*Proof.* For continuous contributions at rate $r_i$:

$$R_i^* = \int_0^\infty r_i \cdot e^{-\lambda s} \, ds = \frac{r_i}{\lambda}$$

For discrete periods: $R_i^* = r_i \cdot \sum_{k=0}^\infty e^{-\lambda k} = r_i / (1 - e^{-\lambda})$. For small $\lambda$, $(1 - e^{-\lambda}) \approx \lambda$, recovering the continuous result. $\square$

**Corollary B.1 (Concentration Bound Under Decay).** The Gini coefficient of steady-state reputation is equal to the Gini coefficient of contribution rates $\{r_i\}$, independent of history:

$$\text{Gini}(R^*) = \text{Gini}(\{r_i / \lambda\}) = \text{Gini}(\{r_i\})$$

This is a key result: time decay destroys historical concentration. The reputation distribution reflects only current contribution rates, not accumulated history. Historical advantages wash out with time constant $1/\lambda$.

**Proposition B.2 (Power-Law Destruction).** If reputation evolves with preferential attachment plus time decay (aging), the power-law tail is destroyed when the aging function is integrable (Springer, 2017; [[02-IDENTITY-REPUTATION]] Section 2.4). Specifically, the degree distribution transitions from:

$$P(k) \propto k^{-\gamma} \quad (\text{power law, without decay})$$

to:

$$P(k) \propto e^{-\lambda k / m} \quad (\text{exponential, with integrable decay})$$

where $m$ is the average contribution rate. The exponential distribution has finite moments and bounded tails — no single agent can have reputation that scales as a power of the system size.

**Decay rate calibration.** What $\lambda$ bounds Gini below $G^* = 0.6$?

If contribution rates $r_i$ are themselves power-law distributed (the natural distribution for productivity), $P(r) \propto r^{-\alpha}$ with $\alpha > 2$, then:

$$\text{Gini}(\{r_i\}) = \frac{1}{2\alpha - 3} \quad (\text{for } \alpha > 2)$$

For Gini = 0.6: $\alpha = 2 + 1/(2 \cdot 0.6) = 2.83$. Empirically, productivity distributions typically have $\alpha \in [2.5, 3.5]$, giving Gini(r) $\in [0.25, 0.5]$ for contribution rates alone. This suggests that time decay alone — by reducing reputation concentration to the concentration of contribution rates — may be sufficient to achieve $\text{Gini} < 0.6$, provided contribution rates are not too concentrated.

**Recommended decay rate:** $\lambda \in [0.015, 0.025]$ per month, corresponding to 15-25% annual decay. At $\lambda = 0.02$:
- Half-life of reputation: $t_{1/2} = \ln 2 / 0.02 \approx 35$ months (about 3 years)
- Steady-state concentration reflects only the last ~3-5 years of contributions
- A founder who stops contributing sees reputation halve every 3 years

**Reputation freezing:** During verified absences, set $\lambda_{\text{effective}} = 0$. The frozen reputation $R_i^{\text{frozen}}$ remains constant. This requires a governance mechanism to verify the absence is legitimate, adding gaming surface.

#### B.2.2 Quadratic Weighting

**Model.** Governance power is the square root of reputation:

$$G_i = \sqrt{R_i}$$

**Proposition B.3 (Quadratic Compression of Gini).** If reputation has distribution $F_R$ with Gini coefficient $\text{Gini}_R$, the Gini coefficient of governance power $G = \sqrt{R}$ satisfies:

$$\text{Gini}_G < \text{Gini}_R$$

*Proof sketch.* The Gini coefficient is sensitive to the ratio of values. For any concave transformation $g(R)$ (and $\sqrt{\cdot}$ is concave), the Lorenz curve of $g(R)$ lies weakly above the Lorenz curve of $R$, implying $\text{Gini}_{g(R)} \leq \text{Gini}_R$. The inequality is strict when $R$ is non-degenerate. $\square$

**Quantitative bound.** If reputation follows a Pareto distribution with shape parameter $\alpha > 2$:

$$\text{Gini}_R = \frac{1}{2\alpha - 1}$$

After quadratic transformation $G = R^{1/2}$, the transformed variable is Pareto with shape $2\alpha$:

$$\text{Gini}_G = \frac{1}{2(2\alpha) - 1} = \frac{1}{4\alpha - 1}$$

| $\alpha$ | $\text{Gini}_R$ | $\text{Gini}_G$ (quadratic) | Reduction |
|-------|----------|------------|-----------|
| 2.0 | 0.333 | 0.143 | 57% |
| 2.5 | 0.250 | 0.111 | 56% |
| 3.0 | 0.200 | 0.091 | 55% |

Quadratic weighting approximately halves the Gini coefficient of the governance power distribution.

**Concentration ratio impact.** If the top $p$-fraction of agents holds share $S_p$ of total reputation, their share of governance power is:

$$S_p^G = \frac{\sum_{i \in \text{top-}p} \sqrt{R_i}}{\sum_{j} \sqrt{R_j}} < S_p^R$$

For example, if the top 1% holds 50% of reputation (typical for DAOs), their share of quadratic governance power is approximately $\sqrt{0.01 \cdot N} \cdot \sqrt{R_{\text{top}}} / (\sqrt{N} \cdot \sqrt{\bar{R}})$, which works out to roughly $\sqrt{S_p \cdot p} = \sqrt{0.5 \cdot 0.01} = \sqrt{0.005} \approx 7\%$. The concentration reduction is dramatic.

#### B.2.3 Contribution Caps

**Model.** Contribution credit per period is capped:

$$c_i^{\text{capped}}(t) = \min(c_i(t), C_{\max})$$

where $C_{\max}$ is the maximum credit per epoch.

**Proposition B.4 (Cap Effect on Steady-State).** Under time decay with rate $\lambda$ and contribution cap $C_{\max}$, the maximum steady-state reputation is:

$$R_{\max}^* = \frac{C_{\max}}{\lambda}$$

Regardless of an agent's true contribution rate, their reputation cannot exceed $R_{\max}^*$.

**The Nakamoto coefficient under caps.** If all agents contribute at the cap ($c_i = C_{\max}$ for active contributors), they all converge to $R_{\max}^*$. The minimum number of agents to control 50% of governance power is:

$$\mathcal{N} = \lceil N_{\text{active}} / 2 \rceil$$

In practice, most agents contribute below the cap. Let $f$ be the fraction at the cap. Then:

$$\mathcal{N} \geq f \cdot N_{\text{active}} / 2 + \text{additional agents needed from below-cap contributors}$$

**Cap calibration.** The cap should bind at the extreme tail (top 1%) but not at the excellent level (top 10%). If the contribution rate distribution has median $\tilde{r}$ and the top 1% contributes at rate $r_{99}$:

Recommended: $C_{\max} \in [5\tilde{r}, 10\tilde{r}]$

For a log-normal distribution of contributions (a reasonable assumption for knowledge work), $r_{99} / \tilde{r} \approx e^{2.33 \cdot \sigma}$ where $\sigma$ is the log-standard-deviation. For $\sigma = 1$ (typical for productivity): $r_{99}/\tilde{r} \approx 10.3$. Setting $C_{\max} = 10\tilde{r}$ would bind only the top ~1%.

**Using logarithmic caps instead of hard caps.** An alternative is logarithmic compression:

$$c_i^{\text{log}}(t) = C_0 \cdot \ln\left(1 + \frac{c_i(t)}{C_0}\right)$$

This is smooth (no discontinuity at the cap), preserves the ordering of contributions, and provides diminishing marginal credit. The effective cap is soft: doubling contribution from $C_0$ to $2C_0$ adds only $\ln(2) \approx 0.69$ units of additional credit.

#### B.2.4 Universal Basic Reputation (UBR)

**Model.** Every verified active member receives baseline reputation $R_{\min}$ per period:

$$R_i(t) = R_{\min} + R_i^{\text{earned}}(t)$$

**Proposition B.5 (UBR Effect on Gini and Nakamoto).** Adding UBR $R_{\min}$ to all agents:

*Gini effect:*
$$\text{Gini}_{\text{with UBR}} = \text{Gini}_{\text{earned}} \cdot \frac{\bar{R}_{\text{earned}}}{\bar{R}_{\text{earned}} + R_{\min}}$$

*Proof.* The Gini coefficient of $X + c$ where $c$ is a constant and $X$ is a non-negative random variable is:

$$\text{Gini}(X + c) = \text{Gini}(X) \cdot \frac{\mathbb{E}[X]}{\mathbb{E}[X] + c}$$

Setting $X = R_{\text{earned}}$ and $c = R_{\min}$ gives the result. $\square$

The Gini reduction depends on the ratio $R_{\min}/\bar{R}_{\text{earned}}$:

| $R_{\min}/\bar{R}_{\text{earned}}$ | Gini Reduction Factor | Effect |
|------|------|------|
| 0.1 | 0.91 | 9% Gini reduction |
| 0.25 | 0.80 | 20% Gini reduction |
| 0.5 | 0.67 | 33% Gini reduction |
| 1.0 | 0.50 | 50% Gini reduction |

*Nakamoto effect:* UBR directly increases the Nakamoto coefficient because the floor on reputation means that even low-reputation agents contribute meaningfully to the denominator. Under quadratic governance weighting:

$$\mathcal{N}_{\text{with UBR}} > \mathcal{N}_{\text{without UBR}}$$

The improvement is most dramatic when UBR is large relative to earned reputation for the majority of members.

**Trade-off:** High UBR dilutes the signal value of reputation. If $R_{\min} \gg \bar{R}_{\text{earned}}$, reputation ceases to differentiate between high and low contributors. The system must calibrate $R_{\min}$ to provide meaningful governance floor without destroying incentive information.

**Recommended range:** $R_{\min} / \bar{R}_{\text{earned}} \in [0.1, 0.3]$. This provides 9-23% Gini reduction while preserving >70% of the signal-to-noise ratio in reputation differentiation.

#### B.2.5 Real-Time Monitoring and Redistribution

**Model.** At each monitoring interval $\Delta t_{\text{monitor}}$, the system computes:

1. $\text{Gini}(t) = $ Gini coefficient of current reputation distribution
2. $\mathcal{N}(t) = $ Nakamoto coefficient
3. $S_{p}(t) = $ share of top $p$% in governance power

**Definition B.4 (Alert Triggers).** Redistribution is triggered when:

$$\mathcal{N}(t) < 2\sqrt{N(t)} \quad \text{(early warning)}$$

$$\mathcal{N}(t) < \sqrt{N(t)} \quad \text{(critical alert)}$$

$$\text{Gini}(t) > G^* = 0.6 \quad \text{(concentration alert)}$$

**Redistribution algorithm.** When triggered:

1. Increase decay rate: $\lambda \to \lambda + \Delta\lambda$ for the top $p$% of reputation holders
2. Increase UBR: $R_{\min} \to R_{\min} + \Delta R_{\min}$
3. Lower contribution cap: $C_{\max} \to C_{\max} - \Delta C$
4. Alert the community for governance review

**Proposition B.6 (Concentration Growth Between Monitoring Intervals).** Between monitoring intervals of length $\Delta t$, the maximum change in Gini is bounded by:

$$|\text{Gini}(t + \Delta t) - \text{Gini}(t)| \leq \frac{2 \cdot C_{\max} \cdot \Delta t}{N \cdot \bar{R}(t)}$$

*Argument.* In each period, the maximum reputational change for any single agent is $C_{\max}$ (the contribution cap). The Gini coefficient changes by at most $2/(N \cdot \bar{R})$ per unit of reputational change at the extremes (this is an approximation valid for large $N$). Over $\Delta t$ periods, the bound follows by linearity.

For $C_{\max} = 10\tilde{r}$, $\Delta t = 1$ month, $N = 200$, $\bar{R} = 100$ (arbitrary units):

$$|\Delta \text{Gini}| \leq \frac{2 \cdot 10 \cdot 1}{200 \cdot 100} = 0.001$$

Concentration can increase by at most 0.1 Gini points per month under these parameters. Monthly monitoring is sufficient to catch concentration trends before they reach critical levels.

---

### B.3 Combined Bounding Stack

#### Interaction Effects

**Proposition B.7 (Combined Bounding).** The five mechanisms interact as follows:

1. **Time decay + Caps:** Time decay bounds steady-state reputation at $C_{\max}/\lambda$. The cap prevents rapid accumulation; the decay prevents slow accumulation. Together, they provide both rate limiting and stock limiting. The interaction is synergistic: either mechanism alone has a loophole (caps allow indefinite accumulation at the cap rate; decay alone still permits high transient reputation).

2. **Quadratic weighting + UBR:** Quadratic weighting compresses the top; UBR raises the floor. Together, they compress both tails of the governance power distribution. The Gini of governance power under both is:

$$\text{Gini}_{G}^{\text{combined}} = \text{Gini}(\sqrt{R_{\text{earned}} + R_{\min}}) < \text{Gini}(\sqrt{R_{\text{earned}}}) < \text{Gini}(R_{\text{earned}})$$

The combined compression is multiplicative: if quadratic weighting reduces Gini by factor $q$ and UBR reduces it by factor $u$, the combined reduction is approximately $q \cdot u$.

3. **Monitoring + All mechanisms:** Monitoring enables adaptive tuning of all other parameters. Without monitoring, the parameters are static and may become misaligned as the population evolves. With monitoring, the system can increase $\lambda$, decrease $C_{\max}$, increase $R_{\min}$, or adjust the quadratic exponent in response to observed concentration.

#### Adversarial Failure Conditions

**Proposition B.8 (Conditions for Bounding Stack Failure).** The combined bounding stack fails when:

1. **Constitutional capture:** A coalition amends the constitution to weaken bounding mechanisms. This requires supermajority ($> 2/3$ of governance power) sustained for $\geq 3$ months (the constitutional amendment process from [[01-AI-GOVERNANCE]]).

Under the combined stack, achieving $2/3$ of *quadratic* governance power requires:

$$\sum_{i \in \mathcal{K}} \sqrt{R_i + R_{\min}} > \frac{2}{3} \sum_{j} \sqrt{R_j + R_{\min}}$$

With UBR and caps, this is extremely difficult for a small coalition. Even if the top agent has $R_{\max} = C_{\max}/\lambda$, their quadratic power is $\sqrt{C_{\max}/\lambda + R_{\min}}$, while the total is approximately $N \cdot \sqrt{\bar{R} + R_{\min}}$. The required coalition size is:

$$k > \frac{2}{3} \cdot N \cdot \frac{\sqrt{\bar{R} + R_{\min}}}{\sqrt{R_{\max} + R_{\min}}}$$

For $R_{\max} = 10\bar{R}$ (cap is 10x median) and $R_{\min} = 0.2\bar{R}$:

$$k > \frac{2}{3} \cdot N \cdot \frac{\sqrt{1.2}}{\ \sqrt{10.2}} \approx \frac{2}{3} \cdot N \cdot 0.34 \approx 0.23N$$

A coalition of 23% of the population would be needed to amend the constitution even with maximum reputation. For $N = 200$, this is 46 people—a substantial conspiracy.

2. **Monitoring system compromise:** If the concentration monitoring system is disabled or reports false data, the adaptive mechanisms cannot respond. This is a single point of failure that must be protected by constitutional constraints (monitoring cannot be disabled by normal governance vote) and redundancy (multiple independent monitoring implementations).

3. **Gaming the decay mechanism:** If agents find ways to artificially refresh reputation (e.g., transferring contributions through intermediaries, creating artificial contribution events), the decay mechanism is bypassed. Multi-signal monitoring should detect anomalous refresh patterns, but sophisticated gaming may evade detection.

4. **External concentration:** If reputation within the commons is bounded but external economic concentration (wealth, social capital, organizational resources) enables capture through indirect channels (funding campaigns, hiring lobbyists, acquiring Sybil identities), the internal bounding stack is insufficient. This is the "money in politics" problem applied to the commons.

#### Parameter Space for Safe Operation

**Theorem B.1 (Safe Parameter Region).** The system maintains $\mathcal{N} > \sqrt{N}$ and $\text{Gini} < G^*$ if the following conditions hold simultaneously:

$$\lambda > \lambda_{\min} = \frac{C_{\max}}{R_{\max}^{\text{target}}} \quad \text{(decay fast enough to bound maximum reputation)}$$

$$C_{\max} < C_{\max}^{\text{safe}} = \lambda \cdot G^{*-1} \cdot \bar{r} \quad \text{(cap tight enough to bound Gini)}$$

$$R_{\min} > R_{\min}^{\text{safe}} = \frac{\bar{R}_{\text{earned}} \cdot (G^* - \text{Gini}_{\text{target}})}{1 - G^*} \quad \text{(UBR high enough for target Gini)}$$

$$\Delta t_{\text{monitor}} < \Delta t_{\max} = \frac{\Delta\text{Gini}_{\text{tolerable}} \cdot N \cdot \bar{R}}{2 \cdot C_{\max}} \quad \text{(monitoring frequent enough)}$$

These conditions define a region in parameter space $(\lambda, C_{\max}, R_{\min}, \Delta t_{\text{monitor}})$ within which the system is provably safe.

#### Sensitivity Analysis

**Proposition B.9.** Ranking parameters by sensitivity (largest effect on concentration outcomes per unit change):

1. **Time decay rate $\lambda$** — Most important. Determines the steady-state reputation distribution. A 50% change in $\lambda$ changes steady-state maximum reputation by 50% (linear sensitivity).

2. **Contribution cap $C_{\max}$** — Second most important. Directly bounds the input to the reputation function. But $C_{\max}$ also affects incentives: too low and excellent contributors are discouraged.

3. **Quadratic exponent** — Third. The exponent $q$ in $G = R^q$ determines compression. $q = 0.5$ (square root) reduces Gini by ~50%. $q = 0.33$ (cube root) would reduce it by ~67%. But more aggressive compression reduces the informational value of reputation.

4. **UBR $R_{\min}$** — Fourth. Effective at reducing Gini but introduces dilution trade-off. The marginal effect on Gini decreases as $R_{\min}$ increases (diminishing returns per Proposition B.5 formula).

5. **Monitoring interval $\Delta t_{\text{monitor}}$** — Least important for steady-state, but critical for transient safety. Short intervals are needed only if there are rapid concentration events (e.g., Sybil attacks, mass exit of low-reputation members).

---

### B.4 Empirical Calibration

#### Pilot Starting Parameters

Based on the analysis above and the empirical data from [[02-IDENTITY-REPUTATION]], the recommended starting parameters for the 200-person pilot are:

| Parameter | Recommended Value | Rationale |
|-----------|-------------------|-----------|
| $\lambda$ (monthly decay rate) | 0.02 (21% annual) | Half-life ~35 months; destroys power-law tails per Proposition B.2; within the 15-25% annual range from [[02-IDENTITY-REPUTATION]] |
| $C_{\max}$ (monthly cap) | $10 \times$ median monthly contribution | Binds only top ~1% of contributors; preserves incentives for top 10% |
| $R_{\min}$ (monthly UBR) | $0.2 \times \bar{R}_{\text{earned}}$ | 16% Gini reduction per Proposition B.5; preserves 80%+ signal-to-noise |
| Quadratic exponent $q$ | 0.5 (square root) | Standard QV specification; ~50% Gini compression on governance power |
| $\Delta t_{\text{monitor}}$ | Monthly | Sufficient per Proposition B.6; manageable computational cost at pilot scale |
| $\mathcal{N}$ alert threshold | $2\sqrt{N} = 28$ (early), $\sqrt{N} = 14$ (critical) | Per Definition B.4 |
| $\text{Gini}$ alert threshold | 0.5 (early), 0.6 (critical) | Below any comparable system's observed Gini |

#### Calibration from Observed Data

During the pilot, the following data should be collected for calibration:

1. **Monthly contribution rate distribution** $\{r_i\}$ — used to calibrate $C_{\max}$ relative to median
2. **Reputation Gini trajectory** — if rising, increase $\lambda$ or decrease $C_{\max}$
3. **Nakamoto coefficient trajectory** — if declining, trigger redistribution per B.2.5
4. **Contributor satisfaction vs. caps** — if top contributors report frustration with caps, consider raising $C_{\max}$ or switching to logarithmic compression
5. **Governance participation rate vs. UBR** — if low-reputation members do not participate in governance despite UBR, the floor may be too low

#### Counterfactual: Bounding Stack Applied to DAO Data

**Thought experiment.** How would the bounding stack have performed if applied to the observed Compound DAO distribution (top 10 = 57.86%, Gini $\approx 0.99$)?

Starting from Compound's distribution:

1. **Quadratic weighting** alone: reduces top-10 share from 57.86% to approximately $\sqrt{0.5786 \cdot 0.01}/\sqrt{0.01} \approx 7.6\%$ of quadratic governance power. Gini drops from 0.99 to approximately 0.90.

2. **Adding time decay** ($\lambda = 0.02$): if applied from the start, historical token accumulation would have decayed. The steady-state concentration would reflect only recent activity, not early token distribution. Estimated Gini: 0.5-0.7 (depending on the distribution of active participation rates).

3. **Adding caps + UBR**: further compression. Estimated Gini under full stack: 0.3-0.5.

This is a rough estimate, but it suggests the bounding stack could have reduced DAO concentration from 0.99 to the 0.3-0.5 range — comparable to well-functioning cooperatives. The key qualifier: DAOs have token-based governance (purchased), while the commons has contribution-based governance (earned). The initial distribution is likely less concentrated in a contribution-based system, making the bounding stack's job easier.

---

## Synthesis: Interaction Between Parts A and B

### Can the System Achieve Both Cooperation Equilibrium AND Bounded Concentration?

**The tension.** Bounded concentration (Part B) reduces the rewards for top contributors. This potentially undermines the cooperation incentive (Part A), because the payoff to genuine high-quality cooperation is compressed.

**Formal statement of the tension.** From Theorem A.2, cooperation requires:

$$u_C - u_D > 0 \implies \text{rewards for cooperation must exceed rewards for defection by enough to compensate effort cost}$$

From Theorem B.1, bounding requires:

$$R_{\max}^* = C_{\max} / \lambda \text{ is bounded} \implies \text{maximum reputation (and thus reward) is capped}$$

If $C_{\max}/\lambda$ is too low, the reward for exceptional cooperation $w_C$ approaches the reward for mediocre cooperation, reducing the incentive to invest exceptional effort. In the limit, everyone contributes at the minimum level — a race to the bottom that destroys commons value.

**Resolution.** The tension is real but manageable through the following mechanisms:

1. **Caps bind at the tail, not the body.** Setting $C_{\max} = 10\tilde{r}$ means that 90-99% of contributors are unaffected by caps. The incentive structure is fully intact for the vast majority. Only the extreme tail — contributors at 10x+ the median — experience diminished marginal returns.

2. **Meaning provides intrinsic incentive independent of reputation bounds.** The term $\mu \cdot m_C$ in the cooperation payoff is not affected by reputation caps. High-quality contributors who find the work intrinsically meaningful (SDT's autonomy, competence, relatedness) continue to cooperate even with bounded extrinsic rewards.

3. **Time decay applies to governance, not economic returns.** Per [[SYNTHESIS]] Section 4.6, economic returns (patronage distributions) should not decay even as governance reputation decays. A past contributor retains their earned economic share indefinitely. Only governance influence decays. This preserves the economic incentive while bounding governance concentration.

4. **The fork threat ensures competition.** If the commons caps rewards too aggressively, top contributors can fork to create a commons with different parameters. This competitive pressure prevents the commons from setting parameters that destroy cooperation incentives.

### Are There Trade-offs?

**Yes.** Three explicit trade-offs emerge from the combined analysis:

**Trade-off 1: Bounding stringency vs. contribution incentive.** Tighter bounds (lower $C_{\max}$, higher $\lambda$, larger $R_{\min}$) reduce concentration but also reduce differentiation between high and low contributors. The optimal point depends on the elasticity of contribution effort with respect to marginal reputation reward — an empirical parameter that must be measured during the pilot.

**Trade-off 2: Detection investment vs. cooperation overhead.** Better monitoring (lower $\epsilon$) strengthens the cooperation equilibrium but increases surveillance. The monitoring-intrinsic motivation trade-off (Gneezy & Rustichini, 2000) suggests that some monitoring reduces cooperation by crowding out intrinsic motivation. The optimal monitoring level is interior, not maximal.

**Trade-off 3: Fork cost vs. stability.** Low fork costs strengthen the exit threat that disciplines governance (Part A) but also make the commons more fragile — any disagreement can trigger fragmentation. Excessively low fork costs may produce a "commons of one" where nobody stays long enough to build institutional capacity.

### Parameter Recommendations for the Pilot

Based on the combined analysis, the recommended pilot parameters balance cooperation incentives with concentration bounding:

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Take rate $\tau$ | 0.08 (8%) | Economic sustainability floor from [[SYNTHESIS]] Section 4.3 |
| Decay rate $\lambda$ | 0.02/month | Destroys power-law tails; half-life ~3 years |
| Contribution cap $C_{\max}$ | $10 \times$ median | Binds only extreme tail; preserves incentives for 99% |
| UBR $R_{\min}$ | $0.2 \times \bar{R}$ | 16% Gini reduction; preserves reputation signal |
| Quadratic exponent | 0.5 | Standard; ~50% governance Gini compression |
| Monitoring interval | Monthly | Sufficient for pilot-scale concentration dynamics |
| Sybil cost target | $> \$500$ per fake identity | Deters casual Sybils; sophisticated attacks addressed by behavioral monitoring |
| Detection probability $(1-\epsilon)$ | $> 0.85$ combined | Achievable with 4 independent signals at $p_m = 0.6$ each |
| Fork cost | Low (Apache 2.0 IP, portable reputation) | Credible exit threat; disciplines governance |
| Constitutional amendment | $2/3$ supermajority + 3-month delay | Protects bounding mechanisms from capture |

### What Simulations Should Test

The Phase 2 simulations (Tasks 2.1-2.3) should specifically test:

1. **Cooperation equilibrium robustness:** Vary detection probability $\epsilon$ and meaning weight $\mu$ to find the boundary of the cooperation equilibrium. Identify which parameter, when degraded, causes the fastest collapse.

2. **Bounding stack effectiveness:** Simulate 5-10 years of commons operation with different bounding parameter sets. For each, measure the Gini trajectory and Nakamoto coefficient. Identify parameter ranges where $\text{Gini} < 0.6$ and $\mathcal{N} > \sqrt{N}$ are maintained.

3. **Combined cooperation + bounding:** Simulate the full system with both cooperation strategies and concentration dynamics. Verify Conjecture A.1 computationally. Identify whether there are parameter regions where cooperation equilibrium and bounded concentration are simultaneously achievable.

4. **Attack resistance:** Simulate:
   - Sybil attacks with varying $s$ and $c_{\text{Sybil}}$
   - Coalition capture attempts with varying coalition size $k$
   - Gaming cartels that coordinate Goodhart exploitation across multiple signals
   - Flash governance attacks (temporary reputation accumulation for single vote)
   - Extractive fork-and-drain (fork, extract value, abandon the fork)

5. **Evolutionary dynamics:** Run multi-generation simulations where agents enter and exit. Test whether cooperators persist as the dominant strategy across 100+ generations, or whether defection strategies gradually invade as meaning decays ($\mu \to 0$).

6. **Multi-commons competition:** Simulate 5-10 competing commons with different parameter sets. Verify Proposition A.16: does selection favor better governance? Does competition produce a race to the bottom on take rates?

---

## Appendix: Summary of Propositions

| ID | Statement | Status | Depends On |
|----|-----------|--------|------------|
| A.1 | Cooperation sustained under Axelrod conditions | Established | Folk theorem |
| A.2 | Small groups increase detection | Supported | Dunbar-scale monitoring |
| A.3 | Transparent tracking reduces information asymmetry | Supported | GitHub precedent |
| A.4 | Credible exit disciplines commons | Supported | Fork empirical data |
| A.5 | Bounded rewards reduce extreme strategy incentive | Supported | Floor/ceiling mechanism |
| A.6 | Plural monitoring reduces undetected defection exponentially | Supported (with correlation caveat) | Independence assumption |
| A.7 | Term limits prevent entrenchment | Supported | Rotation mechanism |
| A.8 | Free-riding threshold | Derived | Detection probability |
| A.9 | Goodhart gaming formalized | Established | Campbell's Law |
| A.10 | Sybil profitability condition | Derived | QF mathematics |
| A.11 | Coalition capture condition | Derived | Governance threshold |
| A.12 | Fork as Nash equilibrium | Conditional | Portability and cost |
| A.13 | Defector invasion of cooperating population | Conditional | Hedge set parameters |
| A.14 | Cold-start problem formalized | Established | Bootstrap required |
| A.15 | Cooperation as ESS | Conditional conjecture | Three conditions |
| A.16 | Multi-commons selection | Conditional | Low switching costs |
| A.17 | QF effect on payoff matrix | Established | QF mathematics |
| A.18 | Time decay effect on evolution | Derived | Decay rate |
| A.19 | Fork threat disciplines commons | Derived | Credible exit |
| B.1 | Steady-state reputation under decay | Proved | Geometric series |
| B.2 | Power-law destruction by decay | Established | Springer 2017 |
| B.3 | Quadratic compression of Gini | Proved | Concave transformation |
| B.4 | Cap effect on steady-state | Proved | Bounded input |
| B.5 | UBR effect on Gini | Proved | Translation invariance |
| B.6 | Concentration growth bound | Derived | Cap bounds input |
| B.7 | Combined bounding interactions | Argued | Component analysis |
| B.8 | Bounding stack failure conditions | Argued | Adversarial analysis |
| B.9 | Parameter sensitivity ranking | Argued | Comparative analysis |
| Conj. A.1 | Full stack cooperation equilibrium | Conjecture | Simulation needed |
| Thm. B.1 | Safe parameter region | Derived | Combined conditions |

---

## Sources

**Game Theory and Mechanism Design:**
- Axelrod, R. (1984). "The Evolution of Cooperation." Basic Books.
- Fudenberg, D., Levine, D., & Maskin, E. (1994). "The Folk Theorem with Imperfect Public Information." Econometrica.
- Lalley, S. & Weyl, G. (2015). "Quadratic Voting." Working Paper.
- Buterin, V., Hitzig, Z., & Weyl, G. (2019). "A Flexible Design for Funding Public Goods." Management Science.
- Arrow, K. (1951). "Social Choice and Individual Values." Wiley.
- Myerson, R. & Satterthwaite, M. (1983). "Efficient Mechanisms for Bilateral Trading." J. Economic Theory.

**Power Laws and Network Science:**
- Barabasi, A-L. & Albert, R. (1999). "Emergence of Scaling in Random Networks." Science 286:509-512.
- Springer (2017). "Dynamics of Power Laws: Fitness and Aging in Preferential Attachment Trees." J. Statistical Physics.
- Piketty, T. (2014). "Capital in the Twenty-First Century." Harvard University Press.

**Empirical Concentration Data:**
- DL News (2024). Cambridge Centre for Alternative Finance: DAO Gini coefficients 0.97-0.99.
- ScienceDirect (2024). "Analyzing Voting Power in Decentralized Governance."
- PLOS One (2016). "Inequalities in Open Source: Contributor Commits in ASF."
- arXiv:2111.07101. "Reputation Gaming in Stack Overflow."
- arXiv:2410.13095. "Future of Algorithmic Organization: Large Scale Analysis of DAOs."

**Gaming and Adversarial Dynamics:**
- Goodhart, C. (1975). "Problems of Monetary Management."
- Campbell, D. (1979). "Assessing the Impact of Planned Social Change."
- Gneezy, U. & Rustichini, A. (2000). "A Fine Is a Price." J. Legal Studies.
- arXiv:2402.07940. "LLMs Among Us: AI in Digital Discourse."
- arXiv (2025). "Many-to-One Adversarial Consensus: Exposing Multi-Agent Collusion Risks."

**Behavioral and Organizational:**
- Jahoda, M. (1982). "Employment and Unemployment: A Social-Psychological Analysis."
- Ryan, R.M. & Deci, E.L. (2000). "Self-Determination Theory."
- Tyler, T. (2006). "Why People Obey the Law." Princeton University Press.
- Ostrom, E. (1990). "Governing the Commons." Cambridge University Press.

**Applied Systems:**
- Gitcoin (2025). Quadratic Funding documentation and round results.
- Optimism (2025). Retroactive Public Goods Funding documentation.
- Shapley, L. (1953). "A Value for n-person Games." Contributions to the Theory of Games.
- Freeman, J. (1972). "The Tyranny of Structurelessness."
