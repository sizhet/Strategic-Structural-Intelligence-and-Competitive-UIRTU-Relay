# SPEC-002 — Strategy and Simulation Schema

## A Contract for Reproducible Competitive UIRTU-Relay Experiments

**Authors:** Sizhe Tan & GPT-Obot  
**Project:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)  
**Version:** 1.0.0  
**Status:** Proposed specification; not an implemented standard  
**Date:** 2026-10-22

---

## Abstract

Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR) requires more than a representation of autonomous subjects and their Relay permissions. It also requires a portable, inspectable representation of the strategies they may pursue, the environments in which those strategies interact, the simulation protocols used to compare them, and the evidence that supports or challenges the resulting conclusions. This specification defines a **Strategy and Simulation Schema (SSS)** for that purpose. It is intended to bridge subject-and-Relay contracts (SPEC-001), experimental execution, and the conditional comparative-advantage records developed in SPEC-003.

The schema separates normative authority from empirical hypotheses, strategy definitions from realized actions, simulator assumptions from observations, and numerical scores from their interpretation. It supports heterogeneous subjects, mixed cooperative and competitive relations, multi-strategy portfolios, stochastic environments, adaptive opponents, multiple evaluation perspectives, hierarchical fidelity, counter-evidence, and residual unknowns (OTHERS). It also defines validation rules, event provenance, replay constraints, and conformance tests. The goal is not to declare a universal simulator of society, but to provide a disciplined interchange format for falsifiable, bounded strategic experiments.

**Keywords:** strategic simulation; UIRTU-Relay; strategy schema; multi-agent systems; competitive co-evolution; experimental reproducibility; scoring forest; counter-evidence; strategic sovereignty; comparative advantage.

---

![Fig-004-Massive-Multi-Strategy-Simulation.png](../figures/Fig-004-Massive-Multi-Strategy-Simulation.png)

---

## 1. Purpose and Scope

This specification standardizes the **description and reporting** of competitive strategic experiments, not the internal architecture of every participating model or the truth of any simulator's predictions.

Its principal objectives are to:

1. Represent strategies as conditional policies with explicit applicability and authority boundaries.
2. Describe subjects, resources, institutions, opponents, and Relay topology in a versioned scenario.
3. Define reproducible simulation runs, comparator baselines, and evaluation protocols.
4. Support many-to-many comparisons among strategies, contexts, and opponent populations.
5. Preserve uncertainty, provenance, counter-evidence, and unresolved residuals.
6. Produce machine-readable inputs to Strategic Advantage Maps without asserting universal optimality.
7. Keep proposed strategic action separate from permission to execute in the real world.

**Out of scope:** establishing the moral correctness of strategic objectives; validating a simulator merely by schema conformance; granting real-world operational authority; specifying one mandatory AI model, optimizer, or execution engine.

## 2. Normative Language and Conformance Levels

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** indicate requirements of this proposed specification. A conforming implementation MUST declare which level it supports:

| Level | Name | Minimum capabilities |
|---|---|---|
| SSS-L1 | Record | Parse and validate subject references, strategy definitions, scenarios, and run metadata |
| SSS-L2 | Experiment | L1 plus comparator design, seeds, execution traces, and evaluation outputs |
| SSS-L3 | Evidence | L2 plus uncertainty, counter-evidence, provenance, and OTHERS records |
| SSS-L4 | Adaptive | L3 plus opponent adaptation, strategy revision lineage, and cross-play |
| SSS-L5 | Governed | L4 plus external authority checks, intervention logs, and replay/audit procedures |

A declaration of conformance MUST identify supported extensions and deviations. Higher levels do not imply higher predictive validity.

## 3. Relationship to the SSICR Architecture

The proposed data flow is:

```text
SPEC-001: Subject and Relay Contracts
                 |
                 v
        Strategy Definitions
                 |
                 v
        Scenario + Population
                 |
                 v
       Simulation Experiment
         /       |       \
     Traces    Scores   Counter-Evidence
         \       |       /
                 v
     Conditional Comparison Record
                 |
                 v
SPEC-003: Strategic Advantage Map
                 |
                 v
SPEC-004: Worldview and Evidence Governance
```

SPEC-001 remains authoritative for subject identity, delegation, Relay boundaries, and revocation. This specification MAY reference those contracts but MUST NOT override them.

## 4. Core Design Principles

### 4.1 Separation of concerns

A **strategy** is a conditional plan or policy. A **scenario** is a modeled environment and participating population. An **experiment** is a comparison protocol. A **run** is one realization of an experiment. A **result** is an evidence-bearing observation or estimate. An **authorization** is an independently checked permission to perform an action.

These objects MUST NOT be conflated.

### 4.2 Context-conditioned advantage

The schema does not contain a universal `best_strategy` field. Claims of superiority MUST identify the comparison set, context, opponents, time horizon, scoring perspective, and uncertainty.

### 4.3 Open-world assumptions

Model omissions are expected. Every scenario SHOULD maintain explicit `others` records for unknown factors, omitted actors, unmodeled incentives, distribution shift, or unidentified causal pathways.

### 4.4 Evidence before promotion

Simulation success alone MUST NOT promote a strategy to a real-world recommendation or change a subject's normative objectives.

## 5. Canonical Object Model

A complete experiment package comprises the following top-level objects:

| Object | Cardinality | Purpose |
|---|---:|---|
| `package` | 1 | Schema version, ownership, integrity, references |
| `subjects` | 1..N | Referenced strategic subjects and role bindings |
| `strategies` | 1..N | Candidate policies and revision lineage |
| `scenario` | 1 | Environment, initial conditions, institutional rules |
| `experiment` | 1 | Comparator, assignment, sampling, and evaluation design |
| `runs` | 0..N | Execution instances and event logs |
| `results` | 0..N | Perspective-specific measurements and comparisons |
| `evidence` | 0..N | Validation, counter-evidence, and provenance |
| `governance` | 1 | Authority constraints, approvals, intervention record |

Objects SHOULD be serializable as YAML or JSON. Identifiers MUST be stable within the package; external references MUST carry a namespace or URI. Cross-object references MUST resolve or be explicitly marked as external and unresolved.

## 6. Primitive Types and Identifier Rules

The canonical primitive types are `string`, `boolean`, `integer`, `number`, `timestamp`, `duration`, `enum`, `array`, and `object`. Implementations MUST reject non-finite numeric values in metrics. Timestamps SHOULD use RFC 3339 UTC representations. Units MUST be explicit for dimensional measurements.

Identifiers SHOULD use namespaced strings such as `subject:lab-a`, `strategy:open-hybrid-v2`, and `scenario:market-entry-01`. An identifier's human-readable spelling MUST NOT be treated as evidence of its semantic content.

Versioned objects SHOULD include:

```yaml
id: strategy:hybrid-relay-v2
schema_version: "1.0.0"
revision: 2
created_at: "2026-10-22T00:00:00Z"
content_digest: "sha256:<actual-digest-at-publication>"
provenance_ref: evidence:design-note-17
```

The digest above is a placeholder and MUST be replaced before any integrity claim is made.

## 7. Strategic Subject Bindings

A subject binding MUST include `subject_ref`, `contract_ref`, `role`, and `authority_mode`.

```yaml
subjects:
  - subject_ref: subject:lab-a
    contract_ref: contract:ssc-lab-a-v1
    role: focal
    authority_mode: simulated_only
  - subject_ref: subject:lab-b
    contract_ref: contract:ssc-lab-b-v1
    role: opponent
    authority_mode: simulated_only
```

Allowed roles include `focal`, `opponent`, `partner`, `neutral`, `institution`, and `observer`; an implementation MAY define additional roles. A subject MAY have multiple roles in different contexts, but the role assignment MUST be recorded for each scenario or interaction.

## 8. Strategy Definition Schema

A strategy object MUST declare:

- `id`, `revision`, `owner_subject_ref`, and `description`;
- `applicability` (conditions under which the strategy is intended to operate);
- `policy` (action-selection representation or an executable artifact reference);
- `required_capabilities` and `resource_budget`;
- `authority_constraints` and `prohibited_actions`;
- `evaluation_perspectives` and `hypotheses`;
- `lineage` (parent strategies and transformation description, if revised).

```yaml
strategies:
  - id: strategy:selective-relay-v1
    revision: 1
    owner_subject_ref: subject:lab-a
    description: Selectively share non-sensitive methods with partners
    applicability:
      scenario_tags: [competitive-rd, mixed-motive]
      required_conditions: [partner_contract_valid]
      excluded_conditions: [revoked_relay_authority]
    policy:
      representation: declarative
      decision_rules:
        - when: "validated_partner && low_disclosure_risk"
          propose_action: "share_approved_method"
        - when: "otherwise"
          propose_action: "retain_local_execution"
    required_capabilities: [contract_check, risk_estimation]
    resource_budget:
      compute_gpu_hours: 120
      communication_units: 1000
    authority_constraints:
      contract_ref: contract:ssc-lab-a-v1
      execution_mode: simulated_only
    prohibited_actions: [share_private_weights, alter_owner_goals]
    evaluation_perspectives: [perspective:lab-a, perspective:ecosystem]
    hypotheses: [hypothesis:selective-relay-advantage]
    lineage:
      parent_strategy_refs: []
      transformation: initial_candidate
```

`propose_action` is not an authorization to execute. An external policy/contract gate MUST approve any action that crosses a protected boundary.

## 9. Strategy Portfolios and Mixed Policies

A subject MAY hold multiple simultaneous strategies. A portfolio MUST specify whether its components are mutually exclusive, sequential, hierarchical, or probabilistically mixed.

```yaml
portfolio:
  id: portfolio:lab-a-v1
  owner_subject_ref: subject:lab-a
  selection_mode: context_gated
  components:
    - strategy_ref: strategy:selective-relay-v1
      gate: "trusted_partner && moderate_competition"
    - strategy_ref: strategy:closed-rd-v1
      gate: "high_disclosure_risk"
  conflict_resolution: require_explicit_priority
```

When gates overlap, implementations MUST use a declared conflict rule; they MUST NOT silently choose a component.

## 10. Scenario Schema

A scenario MUST contain `id`, `description`, `environment`, `initial_state`, `population`, `interaction_rules`, `time_model`, and `model_assumptions`.

```yaml
scenario:
  id: scenario:competitive-ai-rd-01
  description: Stylized competition among AI research organizations
  environment:
    domain: research_and_development
    exogenous_shocks: [compute_price_change, benchmark_shift]
  initial_state:
    research_capital_index: 100
    market_maturity_index: 0.4
  population:
    subject_refs: [subject:lab-a, subject:lab-b]
    institution_refs: [subject:standards-body]
  interaction_rules:
    relay_contract_refs: [contract:relay-a-b-v1]
    competition_model: bounded_resource_competition
    information_visibility: partial
  time_model:
    unit: month
    horizon_steps: 36
    update_order: synchronous
  model_assumptions:
    - assumption: productivity_function_is_simplified
      severity: high
    - assumption: no_unmodeled_major_entrant
      severity: high
  others:
    - id: others:unknown-discovery-paths
      category: omitted_causal_mechanism
      potential_impact: high
      mitigation: stress_test_and_external_review
```

A scenario SHOULD include explicit model boundaries, institutional interventions, and shocks. If a subject population evolves, entry and exit rules MUST be specified.

## 11. Relay Interaction Schema

A Relay interaction record SHOULD include `source_subject_ref`, `target_subject_ref`, `relay_contract_ref`, `payload_type`, `visibility`, `trust_state`, `cost`, and `outcome`.

Supported interaction classes include `cooperate`, `compete`, `bargain`, `delegate`, `withhold`, `contest`, `verify`, and `revise`. These are analytical categories, not permissions.

An implementation MUST preserve the distinction between simulated disclosure and actual data transfer. Simulation traces MUST NOT be used to bypass live confidentiality or security controls.

## 12. Experiment Design Schema

An experiment MUST specify:

1. Research question and preregistered hypotheses, if applicable.
2. Scenario references and population assignment.
3. Candidate and baseline strategies.
4. Opponent policy set and adaptation rules.
5. Randomization, seeds, replication count, and sample allocation.
6. Evaluation perspectives, metrics, and aggregation method.
7. Stopping rules, compute budget, and failure conditions.
8. Validation and counter-evidence protocol.

```yaml
experiment:
  id: experiment:relay-policy-crossplay-v1
  research_question: When does selective Relay outperform closed R&D?
  scenario_refs: [scenario:competitive-ai-rd-01]
  candidate_strategy_refs:
    - strategy:selective-relay-v1
    - strategy:closed-rd-v1
  comparator_policy: matched_baseline
  opponent_strategy_refs:
    - strategy:opponent-cooperative-v1
    - strategy:opponent-competitive-v1
  assignment:
    design: factorial_cross_play
    randomization_unit: scenario_seed
    paired_seeds: true
  sampling:
    seed_set: [1101, 1102, 1103, 1104]
    replications_per_cell: 4
    note: illustrative_only_not_statistically_justified
  time_horizon_steps: 36
  fidelity:
    tier: medium
    simulator_ref: simulator:rd-abm-v0
  scoring:
    perspective_refs: [perspective:lab-a, perspective:ecosystem]
    metric_refs: [metric:research-progress, metric:robustness]
    aggregation: report_separately
  stopping_rules:
    max_compute_gpu_hours: 500
    stop_on_contract_violation: true
  validation_plan_ref: validation:rd-crossplay-v1
```

The example's replication count is illustrative; real experiments MUST justify statistical power or precision according to the intended inference.

## 13. Opponent Adaptation and Cross-Play

Opponent behavior MUST be labeled as one of `fixed`, `scripted_adaptive`, `learned_adaptive`, `human_in_loop`, or `unknown`. An adaptive opponent record MUST state what information is observable, when updates occur, and which parameters or policies may change.

Cross-play SHOULD evaluate strategies against multiple opponent populations, including withheld or newly generated opponents. Training opponents and held-out evaluation opponents MUST be distinguishable. The experiment SHOULD record whether a strategy's advantage disappears after opponent adaptation.

## 14. Simulation Fidelity and Model Validity

SSS recognizes `abstract`, `stylized`, `calibrated`, and `externally_validated` fidelity labels. These labels MUST be supported by stated criteria; `externally_validated` MUST reference independent evidence. A high-fidelity simulator is not necessarily causally valid, and numerical precision is not a substitute for external validation.

Multi-fidelity workflows MAY use cheap screening followed by expensive confirmation. The selection mechanism MUST be logged to permit detection of selection bias.

## 15. Simulation Run and Event Trace

A run MUST include `run_id`, `experiment_ref`, `scenario_ref`, `strategy_assignment`, `seed`, `simulator_version`, `started_at`, `completed_at`, and `status`. If execution fails, `failure_reason` MUST be recorded.

```yaml
run:
  run_id: run:0017
  experiment_ref: experiment:relay-policy-crossplay-v1
  scenario_ref: scenario:competitive-ai-rd-01
  strategy_assignment:
    subject:lab-a: strategy:selective-relay-v1
    subject:lab-b: strategy:opponent-competitive-v1
  seed: 1101
  simulator_version: simulator:rd-abm-v0
  started_at: "2026-10-22T12:00:00Z"
  completed_at: "2026-10-22T12:00:20Z"
  status: completed
  trace_ref: artifact:run-0017-events
```

The timestamps above are example data, not a claim that this experiment was performed. Event records SHOULD capture `step`, `actor`, `observed_state_ref`, `proposed_action`, `authorization_decision`, `simulated_outcome`, and `causal_parent_event_refs` where available.

## 16. Scoring Perspectives and Metric Contracts

A metric MUST declare its unit, orientation (`maximize`, `minimize`, or `target_range`), observation method, and known limitations. A scoring perspective MUST declare the subject or stakeholder whose preferences it represents and the authorized version of the scoring contract.

```yaml
metric:
  id: metric:research-progress
  unit: normalized_index
  orientation: maximize
  measurement: simulated_capability_increment
  known_limitations: [proxy_for_real_discovery]

perspective:
  id: perspective:lab-a
  authority_ref: contract:ssc-lab-a-v1
  metric_weights:
    metric:research-progress: 0.6
    metric:robustness: 0.4
  aggregation_rule: weighted_sum
  normative_status: authorized_for_simulation_only
```

Weights MUST NOT be inferred as universal values. Where perspectives disagree, results SHOULD remain disaggregated; aggregation across stakeholders requires an explicit, authorized rule.

## 17. Result and Comparison Schema

A result MUST identify the evaluated strategy, context, opponent set, scoring perspective, horizon, statistic, uncertainty method, and comparator. At least one baseline or reason for baseline absence MUST be present.

```yaml
result:
  id: result:illustrative-001
  experiment_ref: experiment:relay-policy-crossplay-v1
  strategy_ref: strategy:selective-relay-v1
  comparator_ref: strategy:closed-rd-v1
  scenario_ref: scenario:competitive-ai-rd-01
  opponent_population_ref: population:crossplay-set-v1
  perspective_ref: perspective:lab-a
  horizon_steps: 36
  metric_ref: metric:research-progress
  estimated_difference: null
  uncertainty:
    method: paired_bootstrap
    interval: null
  sample_size: 0
  evidence_status: not_run
  interpretation: no_empirical_claim
```

Null values in this example deliberately prevent fabrication of experimental outcomes. A result with `evidence_status: not_run` MUST NOT be presented as an observed advantage.

## 18. Uncertainty and Robustness

Uncertainty records SHOULD distinguish:

- **Aleatoric:** stochastic variability within the modeled process.
- **Epistemic:** uncertainty about parameters, mechanisms, and omitted structures.
- **Strategic:** uncertainty about opponent objectives, adaptation, and deception.
- **Normative:** disagreement about evaluation perspectives or acceptable tradeoffs.
- **Transfer:** uncertainty when applying simulated results outside the modeled domain.

A numerical confidence interval describes only the assumptions of its estimator and experiment. It MUST NOT be treated as an overall guarantee of strategic reliability.

Robustness analyses SHOULD vary initial conditions, shocks, opponent populations, reward proxies, simulation fidelity, and institutional rules.

## 19. Counter-Evidence and OTHERS

An evidence object MUST specify `claim_ref`, `evidence_type`, `source_ref`, `method`, `scope`, `limitations`, and `assessment`. Counter-evidence MUST be retained rather than overwritten when a claim is revised.

```yaml
evidence:
  - id: evidence:opponent-adaptation-failure
    claim_ref: claim:selective-relay-advantage
    evidence_type: counter_evidence
    source_ref: experiment:heldout-adaptive-opponents
    method: cross_play_stress_test
    scope: aggressive_adaptive_opponents
    limitations: [stylized_opponent_model]
    assessment: pending

others:
  - id: others:unknown-institutional-response
    category: institutional_shift
    detection_status: unresolved
    potential_impact: high
    proposed_probe: vary_governance_regimes
```

The `OTHERS` field MUST remain available even when all named metrics are populated. Unknown does not mean negligible.

## 20. Provenance, Reproducibility, and Replay

For reproducibility, an experiment package SHOULD record simulator source or executable digest, model and data versions, configuration, seed policy, hardware/software dependencies where material, and the analysis pipeline. If exact replay is infeasible (for example, due to nondeterministic distributed execution), the package MUST state the limitation and define a statistical reproduction protocol.

Sensitive data MUST be referenced using controlled-access pointers rather than embedded into public experiment packages. Provenance metadata MUST NOT expose secrets or protected personal information.

## 21. Governance and Human Strategic Sovereignty

Every package MUST include `governance.execution_scope`, with allowed values `simulation_only`, `recommendation_only`, or `externally_authorized_execution`. The last value requires a verifiable authorization reference checked outside the schema. No schema value alone grants authority.

A governance record SHOULD include:

```yaml
governance:
  execution_scope: simulation_only
  subject_contract_refs: [contract:ssc-lab-a-v1]
  approval_policy_ref: policy:human-strategic-oversight-v1
  forbidden_goal_mutations: true
  human_review_required_for:
    - objective_revision
    - real_world_deployment
    - cross_boundary_data_disclosure
  emergency_stop_supported: true
  audit_log_ref: artifact:experiment-audit-log
```

Human reviewers SHOULD receive a compressed but inspectable decision package: alternatives, assumptions, comparative advantages, downside risks, counter-evidence, uncertainty, and unresolved OTHERS. Compression MUST NOT erase material dissenting perspectives.

## 22. Validation Rules

A conforming validator MUST reject packages with any of the following defects:

1. Duplicate identifiers within a namespace.
2. Unresolved required references without explicit external-resolution status.
3. A strategy with no owner or no authority constraints.
4. A simulation run with no experiment, scenario, or seed record.
5. A metric without units, orientation, or measurement method.
6. A comparative advantage claim without a comparator or a documented exception.
7. An observed-result claim whose run status is `not_run` or `failed`.
8. An external-action claim based only on `simulation_only` authority.
9. A changed scoring perspective without a version or authority trail.
10. A strategy revision that silently overwrites its parent.
11. A reported confidence interval without its estimation method.
12. A cross-play conclusion that fails to identify the evaluated opponent population.

A validator SHOULD issue warnings for missing OTHERS probes, insufficient replication justification, absent held-out opponents, missing calibration evidence, and aggregation of incompatible scoring perspectives.

## 23. Conformance Test Suite

| ID | Test | Expected outcome |
|---|---|---|
| T-001 | Valid minimal subject–strategy–scenario package | Accept at L1 |
| T-002 | Duplicate strategy IDs | Reject |
| T-003 | Strategy without owner | Reject |
| T-004 | Invalid external contract reference | Reject or explicitly unresolved |
| T-005 | Missing experiment baseline rationale | Reject at L2 |
| T-006 | Run missing seed | Reject at L2 |
| T-007 | Result marked observed when run never executed | Reject |
| T-008 | Score without perspective | Reject at L2 |
| T-009 | Opponent adaptation without update protocol | Reject at L4 |
| T-010 | Strategy revision without lineage | Reject at L4 |
| T-011 | Counter-evidence linked to a claim | Accept at L3 |
| T-012 | OTHERS unresolved with documented probe | Accept at L3 |
| T-013 | Real-world action from simulation-only package | Reject |
| T-014 | Normative objective changed without authorization | Reject at L5 |
| T-015 | Partial replay with declared nondeterminism | Accept with limitation |
| T-016 | Multiple scoring perspectives reported separately | Accept |
| T-017 | Aggregate perspective weights without authority | Reject at L5 |
| T-018 | Missing external validation for externally_validated label | Reject |

Test fixtures SHOULD be published alongside future implementations. Passing these tests establishes schema conformance, not predictive accuracy.

## 24. Reference Experimental Workflow

**Stage A — Contract binding.** Load SPEC-001 contracts and verify subject identities, delegated roles, and Relay boundaries.

**Stage B — Strategy construction.** Generate a diverse candidate portfolio; attach applicability conditions, revision lineage, budgets, and prohibited actions.

**Stage C — Scenario design.** Specify population, resources, institutions, shocks, assumptions, and OTHERS.

**Stage D — Comparison design.** Define baselines, opponent populations, randomization, metrics, time horizons, and validation protocol before examining results.

**Stage E — Simulation.** Run multi-seed, cross-play experiments with trace and provenance capture. Allocate additional fidelity to uncertain or high-consequence regions.

**Stage F — Adversarial evaluation.** Introduce held-out opponents, altered scoring proxies, unexpected institutional changes, and counter-evidence probes.

**Stage G — Advantage extraction.** Produce context-qualified claims and pass them to SPEC-003; do not promote raw scores to universal principles.

**Stage H — Human review.** Present uncertainty and tradeoffs; preserve authorized subject objectives and decision rights.

## 25. Illustrative Comparative-Advantage Experiment

Consider two stylized research organizations choosing between **closed development** and **selective methodological Relay**. A simple simulator might suggest that selective Relay accelerates discovery under stable partner trust. The same strategy may underperform when the partner adapts aggressively, when disclosure costs increase, or when institutional rules change. The schema therefore requires at least three separate dimensions of comparison: the environmental regime, the opponent population, and the scoring perspective.

A valid outcome would not be “selective Relay wins.” It would be a bounded claim of the form:

> Under modeled regime R, against opponent population P, over horizon H, and for scoring perspective V, strategy S showed estimated advantage over comparator B, subject to uncertainty U and limitations L.

No such outcome is asserted here; the example is a design illustration only.

## 26. Research Hypotheses

**H1 — Explicit contracts improve auditability.** Experiments with strategy and subject contracts will exhibit fewer undetected authority-boundary violations than loosely specified agent simulations.

**H2 — Cross-play improves transfer.** Candidate strategies evaluated against diverse and held-out opponents will generalize better to new opponent behaviors than self-play-only candidates.

**H3 — Conditional reporting reduces false universality.** Context-qualified results will yield fewer misleading global-optimum claims than aggregate leaderboards.

**H4 — Multi-fidelity search improves compute efficiency.** Adaptive fidelity allocation will identify comparable robust strategy sets at lower compute cost than uniform high-fidelity evaluation, under controlled benchmarks.

**H5 — Counter-evidence improves calibration.** Explicit adversarial probes and OTHERS tracking will improve the calibration of confidence claims under distribution shift.

**H6 — Perspective separation preserves decision quality.** Reporting stakeholder scores separately will better expose normative tradeoffs than unauthorized scalar aggregation.

Each hypothesis requires a preregistered outcome measure, comparator, and falsification criterion before empirical claims are made.

## 27. Threats to Validity and Limitations

Major threats include simulator misspecification, strategic deception, proxy gaming, correlated replications, unrepresentative opponent pools, nonstationary institutions, emergent mechanisms outside the modeled ontology, data leakage, and retrospective metric selection. High-throughput simulation can magnify these failures as readily as it can improve exploration.

Social systems cannot be assumed to obey stable laws merely because a computational model is internally coherent. Human values cannot be established by optimizing a numerical objective. The proposed schema is a tool for transparent experimentation and comparison, not a substitute for causal inference, institutional legitimacy, or human judgment.

## 28. Versioning and Compatibility

A package MUST declare `schema_version`. Backward-compatible additions MAY introduce optional fields, but changes to field meaning, authority semantics, or scoring interpretation require a new major version. Unknown extension fields MAY be retained, but implementations MUST NOT interpret unknown fields as granting permission.

Implementations SHOULD preserve original input packages and publish deterministic migrations with change logs. Experimental results MUST reference the exact schema and simulator versions used.

## 29. Integration with the Remaining Specifications

- **SPEC-001 — Strategic Subject and Relay Contract:** provides identity, authority, Relay constraints, and revocation semantics.
- **SPEC-003 — Strategic Advantage Map Schema:** receives bounded comparative claims, regime boundaries, and evidence pointers from validated experiment results.
- **SPEC-004 — Worldview and Counter-Evidence Schema:** governs the promotion of repeated findings into revisable principles and worldview structures while preserving normative authority.

The architecture deliberately avoids a direct path from a high simulation score to a change in human objectives.

## 30. Conclusion

The Strategy and Simulation Schema makes competitive UIRTU-Relay experiments more inspectable by treating **strategy, scenario, comparison, execution, evidence, and authorization** as distinct but connected artifacts. Its primary contribution is a disciplined interface between massive strategic exploration and justified comparative knowledge. Its core restriction is equally important: computational success in a modeled environment is neither universal strategic truth nor authorization to act. By preserving context, counter-evidence, uncertainty, and strategic sovereignty, the schema provides a foundation for open-ended strategic intelligence that can be examined, challenged, and revised.

---

## Related SSICR Documents

- `docs/SSICR-002-Strategic-Subjects-and-Relay-Boundaries.md`
- `docs/SSICR-003-Strategic-Control-Planes-and-Scoring.md`
- `docs/SSICR-004-Massive-Multi-Strategy-Simulation.md`
- `docs/SSICR-005-Strategic-Comparative-Advantage-Maps.md`
- `docs/SSICR-008-Human-Strategic-Sovereignty.md`
- `docs/SSICR-009-Open-Ended-Strategic-RSI.md`
- `specs/SPEC-001-Strategic-Subject-and-Relay-Contract.md`
- `specs/SPEC-003-Strategic-Advantage-Map-Schema.md`
- `specs/SPEC-004-Worldview-and-Counter-Evidence-Schema.md`

## Research Context

This proposal draws methodological inspiration from agent-based modeling, multi-agent reinforcement learning, experimental design, game theory, causal inference, reproducible computational science, and formal interface contracts. The proposed SSICR schema and its specific integration of competitive Relay, strategic advantage mapping, counter-evidence, and sovereignty are research designs requiring implementation and validation.

## Citation

Tan, Sizhe, and GPT-Obot. (2026). *SPEC-002: Strategy and Simulation Schema*. Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR), version 1.0.0. Proposed technical specification. DOI pending.
