# SSICR-009 — Open-Ended Strategic RSI

**Subtitle:** Competitive Structural Self-Improvement, Strategic Relay Co-Evolution, and Governed Open-Ended Growth  
**Project:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)  
**Version:** 1.0.0 — Research Framework  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Conceptual architecture and testable research proposals; not an empirically validated system

## Abstract

Recursive self-improvement (RSI) is often framed as improvement within an individual AI system: stronger models, better agents, more efficient tools, or improved evaluators. Strategic RSI extends this frame to multiple autonomous subjects that adapt not only their internal capabilities but also their strategies, UIRTU-Relay configurations, opponent models, and institutional relationships. The resulting system is **coupled structural evolution**, not merely parallel self-improvement. This paper proposes a framework for open-ended strategic RSI in competitive, cooperative, adversarial, and mixed-motive environments. It distinguishes subject sovereignty from delegated unit optimization, formalizes several interacting growth loops, describes a governed simulation-and-selection architecture, and introduces comparative-advantage maps as the principal knowledge product. Particular attention is given to endogenous evaluation, simulator exploitation, uncertainty, resource allocation, and the difference between epistemic revision and unauthorized goal drift. The framework is intended for controlled, reproducible research, beginning with competitive AI research-and-development organizations.

**Keywords:** strategic RSI; structural self-improvement; UIRTU-Relay; competitive co-evolution; multi-agent simulation; comparative advantage maps; strategic worldview; scoring forest; counter-evidence; human strategic sovereignty

---

## 1. Introduction: Beyond Isolated RSI

An isolated RSI loop can be represented schematically as:

\[
I_{t+1}=F(I_t,E_t),
\]

where \(I_t\) is an intelligence system and \(E_t\) is the evidence available for improvement. This is a useful abstraction but insufficient for strategic environments. An improvement by one subject may alter competitors' opportunities, collaborators' incentives, resource prices, evaluation benchmarks, and the institutions governing subsequent interaction.

In such settings, improvement is not a private trajectory. It is a **relational process**: the improvement of one subject changes the selection environment of others, whose responses then change the first subject's options.

This paper asks:

1. What exactly evolves when RSI is embedded in competitive UIRTU-Relay systems?
2. How can a system distinguish strategic adaptation from mere scaling of agent counts?
3. How can open-ended exploration be made measurable without falsely assuming a globally optimal strategy?
4. How can human or organizational strategic sovereignty be maintained when automated search operates at a speed and scale beyond direct human inspection?

The proposed answer is **Open-Ended Strategic RSI (OE-SRSI)**: bounded, evidence-driven structural adaptation across intelligence units, Relay topology, strategic policies, models of other subjects, and empirical worldview assumptions.

## 2. Scope and Terminology

### 2.1 RSI, UIRTU, and strategic subject

- **RSI subsystem:** a bounded mechanism for evaluating and modifying capabilities or structures. An RSI subsystem is not automatically a sovereign subject.
- **UIRTU:** a composable intelligence unit with a defined interface, state, task semantics, evaluation hooks, and Relay participation rules. This paper uses the project's UIRTU terminology without assuming that every multi-agent group meets the contract.
- **Strategic subject:** an accountable decision locus with objectives, authority boundaries, resources, and an identifiable evaluation perspective.
- **Strategic Relay:** a governed interaction or delegation among units or subjects, potentially cooperative, competitive, adversarial, or mixed-motive.
- **Strategic RSI:** recursive improvement of strategies and the structural mechanisms that produce, evaluate, and execute them.

### 2.2 Open-ended does not mean unconstrained

Open-endedness means that the search space can grow through newly discovered units, links, abstractions, strategies, and empirical principles. It does **not** imply unrestricted execution, unlimited compute, self-authorized goal revision, or guaranteed progress.

A practical system requires explicit budgets, permitted actions, auditability, sandbox isolation, and termination conditions.

## 3. Five Coupled Growth Axes

The proposed framework separates five growth axes to avoid collapsing every improvement into a single scalar capability score.

| Axis | Evolving object | Example | Key risk |
|---|---|---|---|
| G1 — Unit | Local UIRTU or RSI capability | Better research evaluator | Benchmark overfitting |
| G2 — Relay | Composition and dependency structure | Replace sequential pipeline with verified parallel branches | Coordination failure |
| G3 — Strategy | Policy and resource allocation | Shift from concentrated to diversified R&D | Short-term metric chasing |
| G4 — Relational | Models and agreements among subjects | Form a standards consortium | Information leakage or collusion |
| G5 — Worldview | Evidence-based strategic principles | Revise assumptions about when openness helps | Ideological lock-in |

These axes are coupled but analytically distinct. A stronger unit can make a previously unattractive Relay viable. A changed Relay can alter the feasible strategy set. A competitor's response can invalidate an earlier principle. A governance rule can prohibit an otherwise high-scoring strategy.

**Proposition 1 — Multi-Axis Strategic Growth.** Strategic RSI should be evaluated across changes in capabilities, Relay structure, strategies, inter-subject relationships, and empirical worldview assumptions, rather than through one aggregate performance score alone.

## 4. From Private Improvement to Coupled Co-Evolution

Let strategic subject \(i\) have state

\[
X_i^t=(U_i^t,R_i^t,\pi_i^t,M_i^t,W_i^t),
\]

where \(U\) denotes intelligence units, \(R\) Relay architecture, \(\pi\) strategic policy, \(M\) models of other subjects and the environment, and \(W\) empirical worldview assumptions. Let \(G_t\) denote shared governance and institutional conditions.

A general coupled transition is:

\[
X_i^{t+1}=F_i(X_i^t,\{X_j^t\}_{j\ne i},E_t,G_t,\xi_t),
\]

with \(E_t\) observed evidence and \(\xi_t\) stochastic factors. This is a modeling template, not a proven law of strategic evolution.

Four effects deserve separate measurement:

1. **Direct improvement:** an internal modification improves a task outcome under fixed opponents.
2. **Response effect:** other subjects adapt, changing the value of that modification.
3. **Composition effect:** changing the Relay graph creates capabilities not attributable to individual units alone.
4. **Institutional effect:** new rules, contracts, or norms change future feasible actions.

A simulation that measures only the first effect cannot establish strategic superiority.

---

![Fig-007 — Social Structural Co-Evolution](../figures/Fig-007-Social-Structural-Co-Evolution.png)

*Figure 7. Coupled evolution of strategic subjects, Relay architectures, strategies, and institutions.*

---

## 5. Strategic Selection Is Contextual

For strategy \(\pi\), Relay configuration \(R\), context \(c\), opponent population \(\Omega\), and evaluation horizon \(h\), define a vector of outcomes:

\[
\mathbf{Y}(\pi,R\mid c,\Omega,h)
= (q,k,r,a,s,\ldots),
\]

where components may include quality, cost, robustness, adaptability, and safety. The interpretation of each component must be documented; not all components should be reduced to one utility score.

A subject-specific evaluation can be written as:

\[
V_i(\pi,R\mid c,\Omega,h;\theta_i),
\]

where \(\theta_i\) encodes authorized priorities and constraints. Comparative advantage against a baseline \(b\) is:

\[
\Delta_i(\pi,b\mid c,\Omega,h)
=V_i(\pi,R\mid c,\Omega,h;\theta_i)
 - V_i(b,R_b\mid c,\Omega,h;\theta_i).
\]

A positive estimate does not imply universal superiority. It is conditional on the subject, scoring specification, scenario distribution, model fidelity, and uncertainty interval.

**Proposition 2 — Advantage Regions, Not a Winner.** The principal result of strategic RSI research should be a revisable map of where strategy families exhibit comparative advantages, where they fail, and how sensitive those findings are to assumptions and opponent adaptation.

## 6. A Governed Open-Ended Strategic RSI Loop

A proposed runtime consists of the following stages:

```text
Authorized subject objectives, constraints, and budgets
                         |
                         v
            Strategy and Relay candidate generation
                         |
                         v
           Contract checks and sandbox admission
                         |
                         v
       Multi-subject, multi-scenario simulation
                         |
                         v
         Multi-perspective scoring and uncertainty
                         |
                         v
       Counter-strategy / counter-evidence search
                         |
                         v
           Independent validation and audit
                         |
                         v
       Strategic Advantage Map / precedent registry
                         |
                         v
     Principle extraction and worldview proposals
                         |
                         v
     Human-governed selection or further simulation
                         |
                         +------> next candidate generation
```

The loop is not an automatic permission to deploy. Sandbox admission and real-world authorization are separate decisions.

### 6.1 Candidate generation

Candidates may modify parameters, unit choice, Relay topology, scheduling, resource allocation, or strategy family. Each candidate should state what changed and why it may help.

### 6.2 Controlled simulation

Run each candidate across multiple scenario seeds, opponent populations, resource conditions, and time horizons. Maintain a matched baseline to reduce confounding.

### 6.3 Adversarial challenge

Search for counter-strategies and failure contexts, not only favorable demonstrations. Record newly discovered weaknesses as first-class evidence.

### 6.4 Validation and retention

Use independent scenario sets and, where possible, alternative simulator implementations or empirical benchmarks. Retain a candidate only with provenance, uncertainty, and explicit scope of applicability.

## 7. Adaptive Compute Allocation

Open-ended strategic spaces grow combinatorially. Brute-force exhaustive search is generally infeasible. The compute budget should be allocated to improve information value rather than maximize raw simulation count.

A practical hierarchy is:

1. **Broad exploration:** inexpensive candidate sampling and diversity checks.
2. **Screening:** low-fidelity simulation and elimination of dominated candidates.
3. **Focused comparison:** paired runs with common random seeds and relevant opponent mixes.
4. **Adversarial stress testing:** deliberately seek difficult contexts and adaptive opponents.
5. **High-fidelity validation:** expensive runs for a smaller set of promising candidates.
6. **Map update:** prioritize uncertain boundaries and areas where a different strategy may dominate.

The allocation policy itself should be compared against uniform allocation and random search. More elaborate search is not automatically better.

## 8. Opponent Adaptation and Evaluation Leakage

A candidate may look superior against static opponents and fail against adapting ones. Evaluation should therefore include:

- Static baseline opponents for reproducibility.
- Previously unseen opponent policies for generalization.
- Adaptive opponents that respond during repeated interaction.
- Mixed populations with different objectives and constraints.
- Explicitly withheld stress scenarios to detect overfitting.

Training and evaluation populations must be separated. When candidates are repeatedly tested against the same evaluation pool, that pool becomes part of the training process; a fresh independent test is then required.

## 9. Structural RSI Versus Strategic RSI

Structural RSI focuses on modifications to the intelligence system's own architecture or evaluation process. Strategic RSI includes those changes but adds interaction-dependent selection and relational evolution.

| Question | Structural RSI | Strategic RSI |
|---|---|---|
| What improves? | Internal capability and structure | Capability, strategy, relationships, worldview assumptions |
| Evaluation context | Often task-oriented | Explicitly multi-subject and adaptive |
| Success artifact | Improved structure with evidence | Conditional advantage regions and failure boundaries |
| Key feedback | Internal task/evaluator feedback | Internal plus opponent and institutional response |
| Governance | Modification and evaluator controls | Additional cross-subject authority and strategic controls |

The distinction is conceptual: real implementations may overlap extensively.

## 10. Worldview Evolution Without Goal Drift

A Strategic Worldview Forest stores multiple empirical perspectives and strategy-selection principles. It should not be treated as a mechanism for automatically rewriting a subject's fundamental values.

Separate:

- **Epistemic updates:** revising causal assumptions, forecasts, strategy applicability, and confidence in evidence.
- **Normative updates:** changing objectives, rights, prohibitions, or authorized risk tolerances.

Epistemic updates may be proposed automatically and evaluated with evidence. Normative updates require authorization by the relevant subject or governance process.

A proposed principle should carry:

```yaml
principle_id: PRIN-EXAMPLE-001
claim: "Diversified research relays may improve resilience under volatile task demand."
source_map_regions: [SAM-REGION-EXAMPLE-12]
applicability:
  environment: "simulated AI R&D organizations"
  constraints: ["bounded coordination overhead", "verified unit interfaces"]
evidence_status: hypothetical
counter_evidence: []
confidence: uncalibrated
revision_policy: "retest on new opponents and workloads"
authority_effect: "none; advisory only"
```

This is an illustrative schema fragment, not a validated empirical finding.

## 11. Relay Contracts and Strategic Boundaries

Cross-subject Relay should explicitly constrain:

1. Identity and accountable owner.
2. Objective and scoring authority.
3. Information visibility and data retention.
4. Permitted actions and external effects.
5. Learning permissions and reuse of contributed data.
6. Governance, audit, revocation, and dispute resolution.

The system must distinguish a strategic subject from a tool it owns or invokes. Access to a tool does not imply permission to change the owner's objectives. Relay across a boundary does not silently transfer strategic sovereignty.

## 12. Anti-Goodhart and Counter-Evidence Governance

Open-ended optimization can amplify weaknesses in evaluation. The following controls are central:

- **Metric plurality:** evaluate outcomes from multiple authorized perspectives.
- **Held-out environments:** separate search from independent testing.
- **Simulator criticism:** maintain explicit uncertainty about behavioral and institutional assumptions.
- **Provenance:** trace results to versions, seeds, scenarios, models, and scoring contracts.
- **Failure retention:** preserve counterexamples and negative findings rather than deleting them.
- **Evaluator governance:** restrict unilateral changes to evaluation criteria by the system being scored.
- **Safety gates:** prohibit unauthorized or harmful real-world actions regardless of simulated reward.

A system that improves its score by exploiting a simulator has not necessarily improved its real-world strategy.

## 13. OTHERS and Open-Subject Modeling

Social and organizational subjects are incompletely specified. Their preferences, culture, alliances, and capabilities may change endogenously. Rather than forcing unknown influences into fixed coefficients, the framework reserves an **OTHERS evidence space** for:

- Unexplained outcomes and residuals.
- Missing subject attributes or relationships.
- Surprising adaptation or institutional effects.
- Contradictions between independent simulation models.
- Candidate new mechanisms requiring validation.

OTHERS must not become a universal excuse for model failure. Each entry needs a traceable observation, a hypothesis, and a test or an explicit unresolved status.

## 14. Institutional Co-Evolution

Repeated strategic interaction may produce new coordination arrangements, rules, standards, or governance constraints. Such institutions may improve cooperation, but may also create lock-in, exclusion, or concentration of power.

Model institutional state as \(G_t\), with a separate transition:

\[
G_{t+1}=H(G_t,\{a_i^t\},E_t),
\]

where \(a_i^t\) are authorized subject actions. The model should permit both institution formation and breakdown. Do not infer desirable institutional outcomes from the existence of a stable equilibrium.

## 15. Reference Scenario: Competitive AI R&D Organizations

Consider three simulated AI research organizations with different initial capabilities and priorities:

- **Organization A:** concentrated research resources and a tightly controlled Relay architecture.
- **Organization B:** distributed research units and modular Relay composition.
- **Organization C:** mixed internal and external research Relay under explicit data-sharing contracts.

Each subject receives a bounded compute budget, task queue, evaluation contract, and strategy-selection policy. Candidate strategies may alter unit allocation, internal workflow, evaluation frequency, and permitted collaboration. No claim is made that one organization is superior in advance.

### 15.1 Experimental conditions

Vary task volatility, compute scarcity, interface reliability, knowledge-sharing cost, and opponent adaptation. Include at least three experimental regimes:

1. Fixed strategies and fixed Relay structures.
2. Adaptive strategies with fixed Relay structures.
3. Adaptive strategies and adaptive Relay structures.

Add an optional fourth regime allowing evidence-based worldview updates while holding authorized objectives fixed.

### 15.2 Primary outputs

Measure validated task quality, cost per accepted result, time to improvement, variance across seeds, resilience to task shocks, coordination overhead, and frequency of policy or contract violations.

### 15.3 Interpretation

The experiment should identify conditional advantage regions and failure boundaries, not a single global winner. Differences should be reported with uncertainty and sensitivity to simulator assumptions.

## 16. Testable Hypotheses

**H1 — Coupled adaptation:** Under selected dynamic environments, allowing opponent adaptation changes the ranking of strategy families compared with static-opponent evaluation.

**H2 — Relay evolution:** Under heterogeneous workloads, adaptive Relay topology improves at least one prespecified performance metric relative to fixed topology under matched compute budgets, without exceeding authorized risk limits.

**H3 — Conditional mapping:** A context-conditioned advantage map yields better held-out strategy selection than a single global strategy ranking.

**H4 — Counter-evidence:** Independent adversarial testing reduces the gap between in-simulation and held-out performance relative to selection without such testing.

**H5 — Compute allocation:** Adaptive compute allocation discovers equally robust candidates at lower cost, or more robust candidates at equal cost, than uniform allocation on a specified benchmark.

**H6 — Worldview governance:** Separating epistemic updates from normative authorization reduces unauthorized objective changes without materially preventing legitimate model correction.

**H7 — Institutional effects:** Allowing contracts or rules to evolve changes the distribution of outcomes relative to a fixed-institution baseline in at least some repeat-interaction scenarios.

Each hypothesis requires prespecified metrics, statistical comparisons, and failure criteria. Null results remain reportable.

## 17. Validation Protocol

A minimal reproducible evaluation should record:

| Category | Required evidence |
|---|---|
| Environment | Simulator version, dynamics, scenario definitions |
| Subjects | Objectives, permissions, unit inventory, initial resources |
| Search | Candidate generator, budget, stopping rules |
| Opponents | Training population, test population, adaptation rules |
| Scoring | Metric definitions, weights, constraints, evaluator versions |
| Runs | Random seeds, repetitions, confidence intervals |
| Counter-evidence | Failed scenarios, critic findings, unresolved assumptions |
| Governance | Authorized modifications, rejected actions, audit trail |
| Outputs | Advantage-map entries, provenance, transfer limits |

Pre-registering key comparisons and retaining negative results would strengthen the evidence. Any later real-world transfer requires separate validation and appropriate authorization.

## 18. Research Roadmap

**Phase I — Formalize.** Define strategic subjects, Relay contracts, candidate schemas, evaluation perspectives, and reproducibility requirements.

**Phase II — Establish baselines.** Implement a controlled AI R&D simulation with fixed strategies, fixed opponents, and transparent metrics.

**Phase III — Introduce adaptation.** Add strategy search, opponent responses, and Relay-topology changes under matched budgets.

**Phase IV — Stress-test.** Use independent scenarios, alternative simulator assumptions, adversarial critics, and counter-evidence capture.

**Phase V — Build knowledge artifacts.** Produce strategic advantage maps, candidate principles, and revisable worldview branches with explicit provenance.

**Phase VI — Human-governed assessment.** Evaluate whether the artifacts help authorized human decision-makers understand alternatives, limitations, and trade-offs better than simpler summaries.

## 19. Open Research Questions

1. How can open-ended strategy spaces be searched without losing reproducibility?
2. Which Relay topology mutations produce genuine capability gains rather than coordination overhead?
3. How can opponent populations remain diverse without turning into unrealistic caricatures?
4. When do evolving evaluation systems invalidate comparisons across generations?
5. How can uncertainty in subject behavior be represented without arbitrary parameter proliferation?
6. How should map regions be merged or split as evidence accumulates?
7. Can strategic principles transfer across industries, or are they too context-dependent?
8. How can institutional changes be modeled without presupposing their desirability?
9. Which explanations help humans exercise strategic sovereignty rather than defer to automation?
10. How should compute be allocated between exploration, validation, and simulation-model improvement?

## 20. Relationship to the SSICR Research Series

- **SSICR-001:** Generalizes cooperative Relay into strategic relationships.
- **SSICR-002:** Establishes strategic subjects and Relay boundaries.
- **SSICR-003:** Defines strategic control planes and scoring.
- **SSICR-004:** Develops massive multi-strategy simulation as the computational engine.
- **SSICR-005:** Defines strategic comparative advantage maps as knowledge artifacts.
- **SSICR-006:** Connects maps to strategic worldview forests.
- **SSICR-007:** Examines social structural simulation and institutional co-evolution.
- **SSICR-008:** Establishes human strategic sovereignty and authorization boundaries.
- **SSICR-009 (this paper):** Integrates these components into open-ended, governed strategic RSI.
- **SSICR-010:** Will synthesize the unified architecture and research horizon.

Related project lines include Structural Recursive Self-Improvement (SRSI), Universal Control Planes and Scoring Folding (UCPSF), Subjective Structural Intelligence (SSI), Structural Intelligence Framework (SIF), and the UIRTU/Relay research line. These are conceptual relationships, not claims of independent empirical confirmation.

## 21. Limitations and Research Ethics

The framework is prospective. It does not establish that large-scale simulations accurately forecast real organizations, that strategic worldview formation is reliably automatable, or that open-ended RSI necessarily improves outcomes. Simulated advantages may fail under distribution shift, missing institutions, adversarial manipulation, or unmodeled human behavior.

Strategic research can be dual-use. This paper restricts its proposed initial evaluation to controlled AI R&D scenarios and emphasizes bounded action permissions, sandbox isolation, auditability, and human authorization. Competitive evaluation must not be interpreted as permission for deception, unauthorized access, coercion, or harmful real-world operations.

## 22. Conclusion

Open-Ended Strategic RSI expands recursive improvement from a private optimization loop into a coupled system of evolving intelligence units, Relay structures, strategies, relationships, and empirical worldviews. Its central output is not a universal winning strategy, but an evidence-bearing and revisable **Strategic Advantage Map**: a structured account of where alternatives work, where they fail, and why. Strategic Worldview Forests may then organize those findings into transferable, perspective-aware principles, subject to continuing counter-evidence and explicit limits on normative change.

The long-term purpose is to increase the range of strategic possibilities that humans can evaluate—not to silently replace the authority of humans and accountable institutions to choose their future.

> **Strategic intelligence grows not only by improving individual agents, but by learning how capabilities, Relay structures, strategies, and institutions co-evolve—while preserving the sovereignty of the subjects they serve.**

---

## Citation and Release Notes

**Recommended citation:** Tan, Sizhe, and GPT-Obot. (2026). *SSICR-009: Open-Ended Strategic RSI*. In *Strategic Structural Intelligence and Competitive UIRTU-Relay*, version 1.0.0. GitHub repository. DOI to be assigned upon archival release.

**Version note:** This manuscript proposes a research framework and testable hypotheses. It does not report completed experiments or measured performance gains.
