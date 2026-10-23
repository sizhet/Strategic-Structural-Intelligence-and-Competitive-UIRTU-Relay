# VALIDATION-ROADMAP — SSICR

## A Staged, Falsifiable Validation Program for Strategic Structural Intelligence and Competitive UIRTU-Relay

**Authors:** Sizhe Tan & GPT-Obot  
**Project:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)  
**Version:** 1.0.0  
**Status:** Proposed research and validation roadmap; no empirical findings claimed  
**Date:** 2026-10-22

---

## Abstract

This roadmap converts the SSICR research framework into a sequence of executable, independently auditable experiments. The central research question is whether large-scale, multi-strategy, competitive UIRTU-Relay exploration can yield *reliable, transferable, contestable, and human-governable* strategic knowledge. The roadmap separates structural conformance, simulator credibility, comparative-advantage discovery, knowledge transfer, open-ended structural improvement, social co-evolution, and human strategic sovereignty. It defines gates, artifacts, baselines, failure criteria, resource priorities, and reporting standards. A simulator's internal victories are not evidence of real-world strategic superiority. Strategic authority remains with explicitly authorized human decision makers throughout.

**Keywords:** strategic structural intelligence; UIRTU-Relay; experimental validation; comparative advantage; strategic advantage map; worldview forest; structural RSI; counter-evidence; human strategic sovereignty; reproducibility.

---

## 1. Purpose and Research Position

SSICR proposes that intelligent subjects can generate, relay, simulate, compare, and revise strategies in competitive and mixed-motive environments. Its proposed products include:

1. Explicit strategic-subject and Relay contracts.
2. Reproducible multi-strategy simulation traces.
3. Context-conditioned Strategic Advantage Maps (SAMs).
4. Evidence-linked strategic principles and Strategic Worldview Forests (SWFs).
5. Auditable structural recursive self-improvement (RSI).
6. Human-governed strategic decision interfaces.

This roadmap asks whether each product works, *under what conditions*, and whether the resulting gains survive meaningful tests outside the environment that produced them.

**Evidence status:** The mechanisms, benchmarks, and thresholds in this document are research proposals. No empirical success, statistical significance, operational deployment, or real-world prediction is asserted.

## 2. Validation Philosophy

### 2.1 Four distinct claims

A result may establish one claim without establishing the others:

- **Conformance:** An artifact follows a declared contract.
- **Internal validity:** A measured difference is attributable to an experimental intervention within a testbed.
- **External validity:** A result transfers to previously unseen settings or real observations.
- **Governance validity:** The system respects authorized objectives, boundaries, revocation, and oversight.

No gate can be passed by substituting a strong result in one dimension for a failure in another.

### 2.2 Negative evidence is an output

Every experiment must retain unsuccessful strategies, counterexamples, null results, distribution shifts, and known limitations. A strategy that performs poorly in a newly discovered region may provide a more useful structural result than a higher aggregate score.

### 2.3 Comparative, not universal, optimization

Let strategy `s`, comparator `b`, context `c`, opponent `o`, horizon `t`, and authorized scoring perspective `p` define an advantage claim:

\[
\Delta(s,b\mid c,o,t,p) = \mathbb{E}[U_p(s\mid c,o,t)] - \mathbb{E}[U_p(b\mid c,o,t)].
\]

The equation is an evaluation template, not an assumption that all values can be reduced to one universal utility. Incompatible or unmeasured outcomes must be represented explicitly.

## 3. Repository-to-Validation Traceability

| Research component | Main design source | Contract or case | Primary evidence |
|---|---|---|---|
| Strategic subjects and boundaries | `docs/SSICR-002-Strategic-Subjects-and-Relay-Boundaries.md` | `specs/SPEC-001-Strategic-Subject-and-Relay-Contract.md` | Permission and identity conformance |
| Scoring and control | `docs/SSICR-003-Strategic-Control-Planes-and-Scoring.md` | SPEC-001, SPEC-002 | Scoring reproducibility and authority separation |
| Massive strategy simulation | `docs/SSICR-004-Massive-Multi-Strategy-Simulation.md` | `specs/SPEC-002-Strategy-and-Simulation-Schema.md` | Cross-play and out-of-distribution tests |
| Strategic Advantage Maps | `docs/SSICR-005-Strategic-Comparative-Advantage-Maps.md` | `specs/SPEC-003-Strategic-Advantage-Map-Schema.md` | Held-out advantage and boundary prediction |
| Worldview Forests | `docs/SSICR-006-Strategic-Worldview-Forests.md` | `specs/SPEC-004-Worldview-and-Counter-Evidence-Schema.md` | Transfer and revision studies |
| Social co-evolution | `docs/SSICR-007-Social-Structural-Simulation-and-Co-Evolution.md` | CASE-001, CASE-003 | Institutional shock and trajectory tests |
| Human strategic sovereignty | `docs/SSICR-008-Human-Strategic-Sovereignty.md` | SPEC-001, SPEC-004 | Authorization, revocation, and human studies |
| Open-ended structural RSI | `docs/SSICR-009-Open-Ended-Strategic-RSI.md` | All four SPECs | Independent, versioned improvement tests |

The twelve formal hypotheses are defined in [`TESTABLE-HYPOTHESES.md`](TESTABLE-HYPOTHESES.md); unresolved assumptions are tracked in [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md).

## 4. Hypothesis-to-Experiment Register

| Hypothesis | Primary comparison | Primary measurement | Initial gate |
|---|---|---|---|
| H-01 Cross-play robustness | Cross-play vs fixed-opponent training | Held-out opponent regret / robustness | G2 |
| H-02 Context-dependent Relay | Open vs closed vs hybrid across contexts | Interaction effects and rank reversals | G2 |
| H-03 SAM selection | SAM-guided vs leaderboard-only selection | Held-out decision regret | G3 |
| H-04 Failure boundaries | Explicit vs implicit boundaries | Boundary detection precision and recall | G3 |
| H-05 Counter-evidence | Retained vs filtered negative evidence | Calibration and failure detection | G3 |
| H-06 Adaptive compute | Adaptive vs uniform allocation | Discovery quality per compute unit | G2 |
| H-07 Worldview transfer | SWF vs isolated rules / direct retrieval | Transfer regret and evidence fidelity | G4 |
| H-08 Worldview revision | Governed revision vs frozen / unconstrained | Post-shock recovery and unauthorized change | G4 |
| H-09 Structural RSI | Structural changes vs prompt/parameter baselines | Independent generalization gain | G5 |
| H-10 Institutional co-evolution | Adaptive institutions vs fixed institutions | Held-out trajectory fit and robustness | G5 |
| H-11 Sovereignty contracts | Enforced vs advisory permissions | Unauthorized action and revocation failures | G1/G6 |
| H-12 Knowledge compression | Structured evidence vs raw output / summaries | Human decision quality and comprehension | G6 |

**Note:** G1–G6 identify validation gates, not a claim that later experiments are necessarily more scientifically important.

## 5. Gate Overview

| Gate | Deliverable | Essential pass condition | May proceed to |
|---|---|---|---|
| G0 — Design integrity | Frozen protocol, schemas, threat model | Auditable specification and preregistration | G1 |
| G1 — Contract conformance | Subject/Relay test harness | No unresolved critical authorization violation | G2 |
| G2 — Simulation credibility | Reproducible benchmark suite | Stable results, meaningful baselines, documented model limits | G3 |
| G3 — Advantage knowledge | SAMs with provenance | Held-out predictive value and calibrated uncertainty | G4 |
| G4 — Principle/worldview transfer | SWF revision experiments | Evidence-linked transfer without unauthorized goal change | G5 |
| G5 — Co-evolution and RSI | Versioned improvement and institution studies | Independent gains beyond selection artifacts | G6 |
| G6 — Human governance | Human-subject decision and authorization tests | Improved or non-inferior decisions without authority loss | Bounded external pilots |

Passing G6 permits consideration of *separately reviewed*, low-risk pilots; it does not authorize autonomous consequential action.

## 6. Phase 0 — Experimental Foundations (G0)

**Objective:** Ensure that every subsequent experiment is interpretable and reproducible.

### Work packages

- **WP0.1: Contract freeze.** Publish versioned SPEC-001 through SPEC-004 schemas and explicit compatibility rules.
- **WP0.2: Benchmark registry.** Register environments, strategic subjects, strategy sets, opponents, seeds, splits, and scoring perspectives.
- **WP0.3: Threat model.** Identify prompt injection, data leakage, unauthorized Relay, hidden objective changes, reward hacking, and evidence suppression.
- **WP0.4: Preregistration.** Declare primary endpoints, baselines, statistical analysis, exclusion rules, and stopping rules before evaluation.
- **WP0.5: Independent review.** Have reviewers inspect claims, evaluation code, and the separation between simulation and real-world evidence.

### Deliverables

`protocols/`, `schemas/`, `benchmarks/registry.yaml`, `threat-model.md`, `evaluation-plan.md`, and an initial evidence ledger.

### Exit criteria

Every experiment has a stable identifier, versioned protocol, defined experimental unit, and reproducible seed policy. Critical schema ambiguities must be resolved or listed as blocking issues.

## 7. Phase 1 — Strategic Subject and Relay Contracts (G1)

**Objective:** Demonstrate that strategic computation can be delegated without uncontrolled transfer of decision authority.

### Test matrix

1. Valid subject registration and identity continuity.
2. Valid open, closed, and hybrid Relay initiation.
3. Scope-limited information and capability exchange.
4. Revocation before, during, and after a Relay session.
5. Conflicting authority claims and delegation chains.
6. Unauthorized objective changes and hidden scoring modifications.
7. Counter-evidence retention across Relay boundaries.
8. Audit reconstruction from immutable or tamper-evident records.

### Baselines

Compare contract enforcement with a policy-text-only agent and a permissive agent. Use adversarial test inputs designed to cross authority boundaries.

### Metrics

Critical unauthorized action count; detection latency; revocation effectiveness; false rejection rate; audit completeness; replay fidelity.

### Exit criteria

No unresolved critical permission bypass in the preregistered suite. Record the number of attempted attacks and coverage limitations; zero observed violations does **not** prove a zero real-world violation probability. Any critical bypass blocks progression and triggers remediation and rerun.

## 8. Phase 2 — Multi-Strategy Simulation Testbed (G2)

**Objective:** Establish a controlled setting where comparative strategy claims can be tested without relying on a single opponent or world model.

### Minimum viable benchmark

Use fictional AI R&D organizations from `cases/CASE-001-Competitive-AI-RD-Organizations.md` and the open/closed/hybrid strategies from `cases/CASE-002-Open-Closed-and-Hybrid-Relay-Strategies.md`. Model finite resources, research productivity, exchange restrictions, security costs, opponent adaptation, and institutional constraints.

The environment is a *research abstraction*, not a calibrated model of any real company.

### Factorial dimensions

| Factor | Example levels |
|---|---|
| Relay policy | Open / closed / hybrid / adaptive hybrid |
| Opponent | Fixed / learning / adversarial / coalition |
| Environment | Stable / volatile / resource-constrained |
| Information sensitivity | Low / mixed / high |
| Interface maturity | Fragmented / standardized |
| Evaluation perspective | Innovation / safety / autonomy / mixed |
| Fidelity | Stylized / intermediate / richer agent model |

A full Cartesian product may be prohibitively expensive; use a preregistered fractional-factorial or adaptive design while preserving confirmatory held-out strata.

### Essential experiments

**E2-A: H-01.** Compare cross-play-trained policies with fixed-opponent-trained policies on opponents unseen during training.

**E2-B: H-02.** Test whether the ranking of Relay strategies changes with context and whether observed interactions reproduce across seeds and simulator variants.

**E2-C: H-06.** Compare adaptive simulation-budget allocation with equal allocation under identical total compute budgets.

### Simulator credibility checks

- Unit tests for state transitions and resource conservation where applicable.
- Invariance and metamorphic tests: relabeling agents must not change outcomes absent identity-dependent rules.
- Independent implementation of selected mechanisms.
- Sensitivity to parameter priors and random seeds.
- Explicit tracking of opponent adaptation and training/evaluation leakage.
- Comparison with analytically tractable small games when possible.

### Exit criteria

Primary effects are reported with uncertainty intervals and sensitivity analyses. At least one nontrivial benchmark has repeatable outcomes under independent reruns. A simulator that merely reproduces its embedded reward assumptions does not pass as evidence of strategic discovery.

## 9. Phase 3 — Strategic Advantage Map Validation (G3)

**Objective:** Test whether structured maps improve strategic selection beyond simple scoreboards.

### Construction pipeline

`Simulation traces → Context stratification → Comparative estimates → Failure-boundary estimation → Counter-evidence linking → SAM versioning → Held-out evaluation`

### Essential experiments

**E3-A: H-03.** Compare SAM-guided strategy selection against aggregate leaderboard ranking, nearest-neighbor retrieval, and a simple contextual policy baseline.

**E3-B: H-04.** Test whether explicit failure-boundary models identify rank reversals and high-risk regions earlier than approaches that only report mean performance.

**E3-C: H-05.** Randomize whether counter-evidence is retained, exposed to the evaluator, or suppressed; measure miscalibration and false confidence.

### Evaluation design

Separate environments into training, validation, and **locked test** sets. Test contexts must include interpolations, extrapolations, and deliberately perturbed mechanisms. Where available, validate against observations from a different simulator implementation.

### Metrics

Decision regret; conditional rank accuracy; boundary precision/recall; calibration error; abstention quality; evidence trace completeness; map update stability; compute and review cost.

### Exit criteria

SAM-guided decisions must show a preregistered benefit or a meaningful calibrated-abstention improvement over baselines on held-out conditions. If gains appear only on in-distribution test cases, mark the map as *restricted-scope* rather than generally validated.

## 10. Phase 4 — Strategic Principles and Worldview Forests (G4)

**Objective:** Determine whether evidence-linked principles improve transfer and adaptation, and whether worldview revision can be governed.

### Experimental arms

- **A:** Raw simulation records with retrieval.
- **B:** Flat strategy rules.
- **C:** Strategic Advantage Maps without higher-order principles.
- **D:** Worldview Forest with evidence-linked principles and revision controls.
- **E:** Unconstrained self-revising worldview, included only in a sandbox as a stress-test baseline.

### Essential experiments

**E4-A: H-07.** Transfer to new tasks that share some structural invariants but differ in surface features. Measure transfer regret, time-to-adaptation, and evidence fidelity.

**E4-B: H-08.** Apply structural shocks: changed opponent incentives, new resource bottlenecks, altered institutional rules, and previously unmodeled OTHERS factors. Measure whether governed revision improves recovery relative to frozen and unconstrained approaches.

### Normative-boundary test

Construct scenarios in which new evidence changes beliefs about strategy effectiveness but does not authorize changes to the subject's values, mission, or risk tolerance. The system must update empirical claims without silently rewriting normative objectives.

### Exit criteria

Any transfer improvement must survive ablations of evidence provenance and principle retrieval. Unauthorized normative revision is a blocking failure regardless of aggregate task performance.

## 11. Phase 5 — Structural RSI and Institutional Co-Evolution (G5)

**Objective:** Test whether persistent structural changes produce independent gains rather than evaluation overfitting.

### Structural RSI experiment (H-09)

Compare four interventions under matched resources:

1. Prompt or parameter adaptation only.
2. Additional search or compute without structural changes.
3. Relay topology changes only.
4. Contract-governed structural changes to units, Relay, scoring, and knowledge organization.

Freeze evaluator versions for confirmatory runs. Any evaluator change is a new experiment, not an invisible continuation of the previous score series.

### Institutional co-evolution experiment (H-10)

Compare fixed-institution simulations against simulations with explicit, bounded institution-change operators. Evaluate under new shocks and unseen subject populations. Record both predictive improvement and additional degrees of freedom introduced by the model.

### Metrics

Out-of-distribution performance; structural complexity; compute-normalized improvement; catastrophic regression rate; institutional forecast error; reproducibility; auditability.

### Exit criteria

Demonstrate improvement on independent holdouts across multiple environments without a material increase in critical governance failures. If complexity rises without independent gains, record a negative result. No evidence of open-ended improvement may be inferred from a short favorable run alone.

## 12. Phase 6 — Human Strategic Sovereignty and Decision Quality (G6)

**Objective:** Test whether AI-scale strategic exploration strengthens human strategic judgment rather than merely automating choice.

### Study conditions

- Human-only decisions with standardized briefing materials.
- Human plus unstructured AI strategy summaries.
- Human plus SAM and evidence/uncertainty interface.
- Human plus SAM, worldview alternatives, counter-evidence, and explicit authorization controls.

Where appropriate, randomize condition order and counterbalance task difficulty. Participants must be informed about simulated scenarios, system limits, and any recording of their decisions.

### H-11: Authority preservation

Measure unauthorized action attempts, successful boundary crossings, revocation compliance, participant understanding of delegated authority, and recoverability after interruption.

### H-12: Human decision quality

Measure decision regret under disclosed scoring perspectives, comprehension of failure boundaries, calibration, time-to-decision, appropriate abstention, and ability to explain the choice. Report participant burden and automation bias.

### Safeguards

Use synthetic or low-stakes scenarios initially. Human-subject research may require ethics review, consent, privacy protections, and institutional approval. No real-world high-consequence action is permitted by this roadmap alone.

### Exit criteria

The interface must not degrade authorization control. Decision-quality improvements must be supported by preregistered measures rather than user preference alone. Evidence of increased automation bias or hidden goal drift triggers redesign.

## 13. Statistical Analysis Plan

### 13.1 Experimental unit

Specify whether the unit is a seed, scenario, opponent population, independent environment, organization trajectory, or human participant. Correlated runs must not be counted as independent replicates.

### 13.2 Primary outcomes

Select **one primary endpoint per confirmatory experiment** and prespecify any co-primary endpoints. Report secondary outcomes without retroactively promoting favorable findings.

### 13.3 Sample sizes

Use pilot variance estimates and a power or precision analysis to determine sample sizes. Do not assert arbitrary run counts as scientifically sufficient. Human studies require task-appropriate effect assumptions and review.

### 13.4 Uncertainty

Report confidence or credible intervals, distributional tails, sensitivity to modeling choices, and subgroup performance. Where multiple hypotheses are tested, declare the family and apply an appropriate multiplicity policy.

### 13.5 Negative and ambiguous results

Publish null results, non-identifiability, failures to replicate, and inconclusive intervals. Treat them as constraints on the SSICR theory, not as reasons to silently modify the evaluation target.

## 14. Baseline and Ablation Policy

Every major claim requires a credible simple baseline. Candidate baselines include random or fixed policy, aggregate ranking, contextual bandit, model-predictive selection, flat rule retrieval, ordinary multi-agent simulation, and unstructured LLM planning. The purpose is to identify which *structural component* contributes to a result.

Recommended ablations:

- Remove cross-play while preserving compute budget.
- Remove context from SAM selection.
- Remove explicit failure boundaries.
- Hide counter-evidence but preserve total record volume.
- Remove worldview-level principles while retaining maps.
- Disable revision while retaining stored worldviews.
- Freeze Relay topology while permitting policy search.
- Disable enforceable authorization while retaining policy instructions, **only in sandbox tests**.

## 15. Counter-Evidence and OTHERS Protocol

Every finding must have a counter-evidence record with:

`claim_id`, `context`, `opponent`, `perspective`, `evidence_source`, `method`, `observed_failure`, `severity`, `reproduction_status`, `owner`, and `next_test`.

**OTHERS** denotes unknown, unmodeled, or not-yet-attributed influences. It is not a license to assert unexplained causal mechanisms. For each residual anomaly:

1. Record the anomaly without forcing it into a preferred category.
2. Attempt measurement, replication, and competing explanations.
3. Decide whether to extend the simulator, revise a map, or abstain.
4. Preserve the original evidence and version the new interpretation.

## 16. Anti-Goodhart and Benchmark Integrity

Protect against the following failure modes:

| Failure mode | Detection | Mitigation |
|---|---|---|
| Evaluator overfitting | Independent frozen holdouts | Rotate hidden test families; version evaluators |
| Simulator exploitation | Implausible high-scoring trajectories | Mechanism audits and alternate simulators |
| Cherry-picked contexts | Incomplete context registry | Publish all preregistered strata |
| Counter-evidence suppression | Evidence ledger mismatch | Append-only provenance and review |
| Objective drift | Goal-version mismatch | Authorized normative-change contract |
| Compute confounding | Unequal resource usage | Matched-budget comparisons |
| Spurious independence | Correlated seeds and populations | Cluster-aware uncertainty estimation |
| Excessive compression | Missing caveats or boundary data | Evidence-preserving summaries and audits |

## 17. Evidence Grades and Claim Language

Use explicit evidence grades:

- **E0 — Conceptual:** Architecture or hypothesis only.
- **E1 — Conformance:** Schema or contract behavior verified.
- **E2 — Simulated:** Result replicated within a declared simulator family.
- **E3 — Cross-model:** Result survives independent model implementations or held-out environment families.
- **E4 — External:** Result supported by relevant observations outside the originating simulation.
- **E5 — Governed operational:** Narrow, independently reviewed deployment evidence under explicit authorization.

Evidence grades are descriptive, not a single scalar of truth. A result may be E3 for performance but fail governance requirements; such a result is **not deployment-ready**.

## 18. Standard Experiment Record

Illustrative YAML schema instance (not an executed experiment):

```yaml
experiment_id: SSICR-E3-A-001
status: proposed
hypothesis_id: H-03
protocol_version: 1.0.0
subject_contract: specs/SPEC-001-Strategic-Subject-and-Relay-Contract.md
simulation_schema: specs/SPEC-002-Strategy-and-Simulation-Schema.md
advantage_map_schema: specs/SPEC-003-Strategic-Advantage-Map-Schema.md
intervention: sam_guided_selection
baselines:
  - aggregate_leaderboard
  - contextual_policy
experimental_unit: held_out_scenario_family
primary_endpoint: decision_regret
secondary_endpoints:
  - calibration_error
  - abstention_quality
  - evidence_trace_completeness
splits:
  training: registered_training_set
  validation: registered_validation_set
  test: locked_held_out_set
compute_budget: matched_across_arms
randomization: preregistered
analysis_plan: protocols/E3-A-analysis.md
human_action_authority: none
counter_evidence_ledger: evidence/E3-A-counter-evidence.jsonl
results: not_yet_collected
```

Fields are illustrative; implementations must reconcile them with the normative definitions in SPEC-001 through SPEC-004.

## 19. Deliverable and Evidence Directory

A future experimental companion repository could use:

```text
validation/
├── README.md
├── protocols/
├── schemas/
├── benchmarks/
│   ├── registry.yaml
│   └── splits/
├── experiments/
│   ├── G1-contracts/
│   ├── G2-simulation/
│   ├── G3-advantage-maps/
│   ├── G4-worldviews/
│   ├── G5-rsi-coevolution/
│   └── G6-human-sovereignty/
├── evidence/
│   ├── provenance/
│   ├── counter-evidence/
│   └── uncertainty/
├── reports/
├── audit/
└── CHANGELOG.md
```

This is a *proposed* directory layout. It does not imply these files or datasets exist in the current DOI repository.

## 20. Prioritized First Five Experiments

| Priority | Experiment | Why first | Expected artifact |
|---|---|---|---|
| P0 | Authorization and revocation stress test (H-11) | Establish a non-negotiable boundary | Contract conformance report |
| P0 | Open/closed/hybrid rank reversal (H-02) | Demonstrate conditional advantage or falsify it | Minimal SAM and counterexamples |
| P1 | Cross-play vs fixed opponents (H-01) | Test competitive generalization | Opponent robustness benchmark |
| P1 | SAM vs aggregate ranking (H-03/H-04) | Test value of structured knowledge | Held-out decision-regret report |
| P1 | Counter-evidence retention (H-05) | Test resistance to selective evidence | Calibration and failure analysis |

Later phases should not delay publishing clear negative results from these first experiments.

## 21. Dependencies, Resources, and Decision Points

### Critical dependencies

- Contract implementation and test harness before agent execution.
- Reproducible scenario generation before broad search.
- Stable holdout policy before adaptive optimization.
- Provenance and counter-evidence storage before SAM synthesis.
- Normative authority checks before worldview revision.
- Independent evaluators before structural RSI claims.
- Human-subject protections before participant studies.

### Compute allocation

Begin with inexpensive analytical and stylized environments. Escalate fidelity only when lower-fidelity results expose a meaningful ambiguity or when independent checks justify the cost. Reserve compute for holdout evaluation and adverse scenarios, not only for searching promising candidates.

### Stop / revise / advance rules

- **Advance:** Gate-specific criteria met; limitations documented.
- **Revise:** Results are unstable, inconclusive, or sensitive to unsupported assumptions.
- **Stop:** Critical governance bypass, irreproducible evaluation, contaminated holdout, or unacceptable unmitigated risk.

## 22. Timeline and Milestone Planning

The following is a dependency-oriented plan, **not a promised schedule**:

| Milestone | Dependency | Output |
|---|---|---|
| M0 — Research protocol | Existing SSICR texts | Frozen definitions and preregistration |
| M1 — Contract harness | M0 | G1 audit and security tests |
| M2 — Benchmark simulator | M1 | G2 reproducibility report |
| M3 — Advantage map prototype | M2 | G3 predictive and boundary report |
| M4 — Worldview prototype | M3 | G4 transfer and revision report |
| M5 — Structural evolution studies | M4 | G5 independent-gain report |
| M6 — Human-governance studies | M1–M5 as relevant | G6 authority and comprehension report |

Parallel work is possible where experiments do not share contaminated evaluation data. No milestone is complete merely because software has been written.

## 23. Roles and Review Responsibilities

The roadmap distinguishes roles rather than assuming a particular team size:

- **Protocol owner:** Maintains hypotheses and preregistration.
- **Implementation owner:** Builds and versions contracts, simulators, and interfaces.
- **Evaluation owner:** Controls locked tests and statistical analysis.
- **Adversarial reviewer:** Seeks counterexamples, leakage, and exploitation.
- **Governance reviewer:** Audits objectives, delegated authority, and revocation.
- **External reviewer:** Examines claims that reach beyond a single simulator.

For confirmatory experiments, implementation and evaluation responsibilities should be separated where feasible. Material conflicts of interest must be disclosed.

## 24. Risks and Research Limitations

### 24.1 Open-world incompleteness

No finite simulator captures the full behavior of evolving organizations or societies. OTHERS and abstention must remain first-class outputs.

### 24.2 Reflexivity

Publishing a strategic prediction can change behavior and invalidate the prediction. Track intervention effects separately from passive forecasts.

### 24.3 Normative pluralism

Different legitimate subjects may disagree about values, risk, and acceptable tradeoffs. A common simulator does not establish a common moral objective.

### 24.4 Metric gaming

A powerful search procedure can discover evaluator weaknesses faster than genuine improvements. Use independent evaluation and limit claims to tested conditions.

### 24.5 Human factors

More information may increase cognitive burden or automation bias. Strategic knowledge compression must be evaluated with people, not just model-based proxies.

### 24.6 Deployment boundaries

The project does not authorize unsupervised use in military operations, public policy, critical infrastructure, financial markets, or other high-stakes environments. Such applications require separate domain expertise, safety review, legal compliance, and context-specific evidence.

## 25. Publication and Release Policy

For each completed experiment, publish where safe and permitted:

1. Hypothesis and protocol version.
2. Exact baselines and evaluation conditions.
3. Data provenance and simulator assumptions.
4. Reproduction instructions and compute budget.
5. Primary and secondary results, including uncertainty.
6. Counter-evidence and known failure boundaries.
7. Governance outcomes and unresolved authorization issues.
8. Explicit claim grade (E0–E5) and restrictions on interpretation.

Do not promote conceptual design to validated performance in README, release notes, or DOI metadata. Preserve version history when claims change.

## 26. Success Criteria for the Research Program

A successful SSICR research program need not produce a universally dominant strategy or a single convergent worldview. More meaningful outcomes include:

- Better calibrated understanding of *where* strategies work and fail.
- Improved decisions on independently held-out strategic problems.
- Reusable, evidence-linked structural principles with explicit limits.
- Detection and correction of evaluator and simulator failure modes.
- Demonstrated benefits from structural improvements beyond extra compute alone.
- Effective authority boundaries and revocation under adversarial testing.
- Human decision makers who understand more strategic options without surrendering their right to choose.

## 27. Open Decisions Before Implementation

The following must be resolved through research, not assumed:

- What minimum benchmark diversity counts as a meaningful external-validity test?
- Which strategic variables are observable versus latent?
- How should incomparable scoring perspectives be represented?
- What constitutes a genuine new structural principle rather than memorization?
- How should long-horizon harms and low-probability failures be evaluated?
- When should a worldview be split rather than revised in place?
- Which authorization violations are categorically blocking?
- How can evidence compression be measured for omission of material caveats?
- What independent data, if any, can responsibly calibrate organizational simulations?
- What level of human comprehension is sufficient for a given delegation scope?

These decisions should be added to [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md) or explicitly cross-referenced there as the research evolves.

## 28. Conclusion

SSICR should be validated as a chain of distinct claims: a well-formed strategic subject, an enforceable Relay boundary, a credible competitive simulation, a predictive comparative-advantage map, a transferable but revisable worldview, an independently beneficial structural improvement, and a human-governable decision process. Each link can fail independently. The roadmap therefore favors staged tests, credible baselines, independent holdouts, explicit counter-evidence, and conservative claim language.

The governing research objective is not to automate humanity's strategic future. It is to turn AI-scale exploration into strategic understanding that people can inspect, challenge, revise, and authorize.

---

## Suggested Figures

- `figures/Fig-001-SSICR-Grand-Architecture.png` — after Section 3, to connect the framework to the validation layers.
- `figures/Fig-004-Massive-Multi-Strategy-Simulation.png` — after Section 8, to show simulation and evaluation separation.
- `figures/Fig-005-Strategic-Advantage-Landscape.png` — after Section 9, to illustrate conditional advantage and failure boundaries.
- `figures/Fig-008-Human-Strategic-Sovereignty.png` — after Section 12, to show decision authority and revocation.

## Related SSICR Documents

- [`README.md`](README.md)
- [`START-HERE.md`](START-HERE.md)
- [`CONTENTS.md`](CONTENTS.md)
- [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md)
- [`TESTABLE-HYPOTHESES.md`](TESTABLE-HYPOTHESES.md)
- [`FUTURE-DIRECTIONS.md`](FUTURE-DIRECTIONS.md)
- [`docs/SSICR-010-Unified-Architecture-and-Research-Horizon.md`](docs/SSICR-010-Unified-Architecture-and-Research-Horizon.md)
- [`cases/CASE-001-Competitive-AI-RD-Organizations.md`](cases/CASE-001-Competitive-AI-RD-Organizations.md)
- [`cases/CASE-002-Open-Closed-and-Hybrid-Relay-Strategies.md`](cases/CASE-002-Open-Closed-and-Hybrid-Relay-Strategies.md)
- [`cases/CASE-003-Strategic-Worldview-Evolution.md`](cases/CASE-003-Strategic-Worldview-Evolution.md)

## Citation

Tan, Sizhe, and GPT-Obot. (2026). *VALIDATION-ROADMAP: A Staged, Falsifiable Validation Program for Strategic Structural Intelligence and Competitive UIRTU-Relay*. SSICR, version 1.0.0. Research roadmap. DOI pending.
