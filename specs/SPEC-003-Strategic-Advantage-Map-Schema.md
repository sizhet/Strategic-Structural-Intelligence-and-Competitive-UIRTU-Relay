# SPEC-003 — Strategic Advantage Map Schema

## A Versioned, Evidence-Grounded Contract for Contextual Strategic Comparative Advantage

**Authors:** Sizhe Tan & GPT-Obot  
**Project:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)  
**Version:** 1.0.0  
**Status:** Proposed technical specification; not an implemented standard  
**Date:** 2026-10-26  
**Document ID:** SSICR-SPEC-003

---

## Abstract

A Strategic Advantage Map (SAM) records where, relative to which alternatives, under which assumptions, for whose objectives, and with what evidence a strategy appears advantageous. This specification defines a portable, versioned, machine-readable schema for translating competitive UIRTU-Relay simulations and external observations into conditional strategic knowledge. It distinguishes descriptive outcomes from evaluative scores, observed evidence from simulated evidence, empirical confidence from normative authority, and validated advantage regions from untested extrapolation. It defines interoperable records for strategic contexts, subjects, comparators, scoring perspectives, advantage claims, uncertainty, counter-evidence, failure boundaries, provenance, map revisions, and human authorization. Conformance requirements, reference examples, and validation tests are provided. No particular strategy, worldview, or optimization target is declared universally superior.

**Keywords:** strategic advantage map; comparative advantage; conditional strategy; UIRTU-Relay; multi-agent simulation; evidence provenance; counter-evidence; uncertainty; strategic sovereignty; open-ended structural intelligence.

---

![Fig-005-Strategic-Advantage-Landscape.png](../figures/Fig-005-Strategic-Advantage-Landscape.png)

---

## 1. Purpose and Scope

The purpose of SPEC-003 is to define a **Strategic Advantage Map** as a durable intelligence artifact rather than a leaderboard or a single winning-policy label.

This specification supports:

1. Cross-run accumulation of strategy evidence.
2. Comparison across strategies, opponents, scenarios, institutions, and scoring perspectives.
3. Explicit identification of advantage regions, disadvantage regions, unknown regions, and transition boundaries.
4. Auditable claims with uncertainty and counter-evidence.
5. Controlled updates as strategic environments and opponents evolve.
6. Interfaces to strategic worldview formation without conflating empirical evidence and normative authority.

It does **not** specify a simulator implementation, prove the validity of simulation models, establish moral rankings of worldviews, or grant authority to execute real-world actions.

## 2. Normative Vocabulary and Design Principles

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** indicate proposed conformance requirements for this specification, not an externally ratified standard.

**P1 — Contextuality.** Every advantage claim MUST specify the domain of contexts in which it applies.

**P2 — Relativity.** Every comparative claim MUST identify a comparator or explicitly state why no comparator exists; absolute performance and comparative advantage MUST be represented separately.

**P3 — Perspective attribution.** Every scored claim MUST identify whose scoring perspective and which metric definition it uses.

**P4 — Evidence separation.** Simulation, observation, expert judgment, and derived inference MUST be distinguishable.

**P5 — Uncertainty preservation.** Confidence, coverage, model uncertainty, and unmodeled factors MUST NOT be silently collapsed into one number.

**P6 — Counter-evidence retention.** Contradictory and failed results MUST remain addressable even after a claim is revised or withdrawn.

**P7 — Open boundaries.** Unmeasured variables and novel strategic mechanisms MUST have a first-class OTHERS representation.

**P8 — Sovereignty.** A map is decision support; it MUST NOT itself authorize a change of subject goals, values, or real-world actions.

## 3. Relationship to Other SSICR Contracts

- **SPEC-001** defines subject identity, authority, strategic boundaries, and Relay contracts. SAM references those identifiers; it does not replace their authorization checks.
- **SPEC-002** defines strategy and simulation records. SAM consumes traceable experiment results and can link back to exact scenario, strategy, opponent, run, seed, and scoring versions.
- **SPEC-004** defines worldview principles, their counter-evidence, and revision rules. SAM supplies evidence and scoped strategic claims; worldview promotion requires a separate governance step.

The dependency flow is:

```text
Subject / Relay contracts (SPEC-001)
                 |
Strategy / scenario / experiment (SPEC-002)
                 |
         Evidence ingestion
                 v
      Strategic Advantage Map
      [SPEC-003: this document]
          /            \
  Decision support    Principle candidates
                           |
                Worldview governance (SPEC-004)
```

## 4. Conceptual Model

A SAM consists of a **map envelope** and a collection of **advantage claims**. Each claim refers to:

- a strategy and an explicit comparator;
- a bounded strategic context and opponent configuration;
- an evaluation perspective and horizon;
- evidence and uncertainty assessments;
- validity limits, failure modes, and counter-evidence;
- an update and governance history.

The map MAY contain several mutually inconsistent claims if their contexts, perspectives, or evidence differ. Contradiction is an object of analysis, not a reason to erase records.

### 4.1 Primary entities

| Entity | Role | Stable identifier |
|---|---|---|
| `StrategicAdvantageMap` | Versioned map container | `map_id` |
| `ContextRegion` | Bounded domain of applicability | `region_id` |
| `AdvantageClaim` | Scoped comparative statement | `claim_id` |
| `StrategyReference` | Strategy/version reference | `strategy_id` |
| `ComparatorReference` | Baseline, rival, or policy set | `comparator_id` |
| `ScoringPerspective` | Objective and metric interpretation | `perspective_id` |
| `EvidenceRecord` | Provenance-linked observation or run | `evidence_id` |
| `CounterEvidenceRecord` | Challenging or refuting evidence | `counter_evidence_id` |
| `BoundaryRecord` | Transition, failure, or extrapolation boundary | `boundary_id` |
| `RevisionRecord` | Immutable map/claim change | `revision_id` |

Identifiers SHOULD be unique within the repository or namespaced with a persistent organization/project prefix.

## 5. Map Envelope Schema

The root object MUST include:

| Field | Type | Required | Semantics |
|---|---|---|---|
| `schema_version` | string | Yes | Version of this specification, e.g. `1.0.0` |
| `map_id` | string | Yes | Stable map identity |
| `map_version` | string | Yes | Version of this map artifact |
| `title` | string | Yes | Human-readable map name |
| `domain` | string | Yes | Strategic problem domain |
| `created_at` | date-time | Yes | UTC creation time |
| `updated_at` | date-time | Yes | UTC last revision time |
| `maintainers` | array | Yes | Responsible subjects or organizations |
| `scope` | object | Yes | Inclusion and exclusion boundaries |
| `claims` | array | Yes | May be empty for a draft map |
| `evidence_registry` | array | Yes | Indexed evidence records |
| `revision_log` | array | Yes | Append-only revision references |
| `governance` | object | Yes | Review and authorization metadata |
| `others_register` | array | Yes | Unknown or unmodeled factors |

Optional root fields include `source_contracts`, `context_regions`, `scoring_perspectives`, `external_validations`, `links`, and `extensions`.

A map with zero claims is a valid **draft container** but MUST NOT be presented as evidence of strategic superiority.

## 6. Strategic Context Schema

An advantage region MUST be represented by an explicit `ContextRegion` object, not merely a natural-language label.

```yaml
region_id: region-low-compute-high-uncertainty
context_dimensions:
  compute_budget:
    type: numeric_interval
    unit: normalized_compute_units
    min: 10
    max: 50
    inclusive: [true, true]
  opponent_adaptivity:
    type: categorical
    allowed: [low, medium]
  information_quality:
    type: categorical
    allowed: [partial]
  institutional_ruleset:
    type: reference
    id: ruleset-r3
assumptions:
  - model-assumption-12
excluded_conditions:
  - unrestricted-opponent-coalitions
coverage_status: sampled
```

Context dimensions MAY be continuous, categorical, structural, temporal, or relational. Each dimension MUST declare its unit or ontology. Missing dimensions MUST be explicitly marked as `unknown`, `not_applicable`, or `not_recorded`; these states are not interchangeable.

A region MUST NOT be interpreted as covering the entire domain when only a sparse subset of the region has been tested.

## 7. Strategic and Comparator References

A claim MUST reference at least one candidate strategy and at least one comparator for a relative-advantage assertion.

Each strategy reference SHOULD contain:

- `strategy_id`, `strategy_version`, and optional immutable content hash;
- originating subject or Relay coalition;
- relevant `SPEC-002` strategy record URI;
- capability and resource assumptions;
- allowed modifications and adaptation regime.

Comparator types include:

| Comparator type | Interpretation |
|---|---|
| `baseline` | Established reference strategy |
| `named_strategy` | Specific rival strategy/version |
| `portfolio` | Weighted or rule-selected alternative set |
| `best_observed` | Best observed alternative within a declared search set |
| `robust_reference` | Reference under uncertainty or worst-case criterion |
| `historical_control` | Historical control, with explicit comparability limits |

A `best_observed` comparator MUST NOT be described as globally optimal unless an independently justified global-optimality proof exists.

## 8. Scoring Perspectives and Evaluation Contracts

A `ScoringPerspective` MUST identify:

```yaml
perspective_id: perspective-human-governed-research
owner_subject_id: subject-human-governance-board
objective_contract_ref: objectives-v2
metrics:
  - metric_id: research_progress
    direction: maximize
    unit: normalized_score
  - metric_id: resource_cost
    direction: minimize
    unit: compute_units
  - metric_id: safety_violations
    direction: minimize
    unit: count
aggregation:
  method: constrained_multiobjective
  hard_constraints:
    - safety_violations == 0
horizon:
  steps: 100
  discounting: none
```

The evaluator MUST declare whether results use scalar aggregation, Pareto comparison, lexicographic constraints, risk-sensitive scoring, or a qualitative assessment.

**Non-equivalence rule:** A strategy may outperform under one perspective and underperform under another. The map MUST preserve these differences; a scalar aggregate MUST NOT erase disaggregated metrics or hard-constraint violations.

## 9. Advantage Claim Schema

The minimum valid claim contains:

```yaml
claim_id: claim-042
claim_version: 1
status: provisional
candidate_strategy_ref: strategy-hybrid-v3
comparator_ref: strategy-open-v2
context_region_refs: [region-low-compute-high-uncertainty]
scoring_perspective_ref: perspective-human-governed-research
advantage:
  relation: positive
  metric_id: research_progress
  estimate: 0.12
  unit: normalized_score_difference
  direction: candidate_minus_comparator
  uncertainty_ref: uncertainty-042
supporting_evidence_refs: [ev-1001, ev-1002]
counter_evidence_refs: [ce-201]
boundary_refs: [boundary-17]
review_state: awaiting_independent_replication
```

Allowed `status` values: `hypothesis`, `provisional`, `supported`, `contested`, `refuted`, `superseded`, `withdrawn`. These describe evidence review state, not operational authorization.

Allowed `relation` values: `positive`, `negative`, `equivalent_within_margin`, `inconclusive`, `mixed_by_metric`, `unknown`.

A claim with `relation: positive` MUST state the sign convention, comparison direction, metric, horizon, and supporting evidence. A `supported` claim MUST have documented review criteria; it does not imply universal validity.

## 10. Formal Comparative Advantage Semantics

Let \(s\) be a candidate strategy, \(b\) a comparator, \(c\) a context, \(o\) an opponent configuration, \(p\) a scoring perspective, and \(h\) an evaluation horizon. Define the conditional expected utility difference:

$$
\Delta_{p,h}(s,b\mid c,o)
= \mathbb{E}[U_{p,h}(s\mid c,o)]
- \mathbb{E}[U_{p,h}(b\mid c,o)].
$$

An estimated advantage region at margin \(\epsilon\) is:

$$
\widehat{\mathcal A}_{p,h}(s,b;\epsilon)
= \{(c,o): \widehat\Delta_{p,h}(s,b\mid c,o)>\epsilon\}.
$$

The hat denotes estimation from finite evidence; it MUST NOT be dropped in reports that have not established the true region. A statistically uncertain sign SHOULD be reported as `inconclusive`, not forced into a binary winner label.

For multi-objective scoring, \(\Delta\) MAY be a vector; Pareto relations or constrained dominance SHOULD replace unjustified scalarization.

**Comparative advantage is conditional.** It does not entail global superiority, normative legitimacy, or authority to act.

## 11. Evidence Registry

Every evidence record MUST include:

| Field | Description |
|---|---|
| `evidence_id` | Stable reference |
| `evidence_type` | `simulation`, `observation`, `field_experiment`, `expert_assessment`, `derived_inference` |
| `source_uri` | Immutable or versioned source where feasible |
| `source_hash` | Digest when reproducibility is possible |
| `collected_at` | Collection time |
| `subject_refs` | Relevant subjects or coalitions |
| `strategy_refs` | Strategies compared |
| `context_region_ref` | Applicable context |
| `perspective_ref` | Evaluator definition |
| `result_ref` | Detailed result payload |
| `quality_flags` | Leakage, confounding, missingness, bias, etc. |
| `provenance_chain` | Upstream transformations and dependencies |

For simulation evidence, the record SHOULD also include experiment ID, simulator version, model assumptions, opponent policy version, seed, run count, sampling method, and source of calibration data.

For observational evidence, it SHOULD document selection mechanisms, confounders, and measurement limitations.

An inference derived from other evidence MUST link to its parent records; it MUST NOT be counted as an independent replication.

## 12. Uncertainty and Confidence Schema

Uncertainty MUST be decomposable into at least:

1. **Sampling uncertainty:** finite-run or finite-observation variability.
2. **Model uncertainty:** uncertainty about simulator structure and parameterization.
3. **Opponent uncertainty:** unknown or evolving opponent behavior.
4. **Context coverage uncertainty:** untested or sparsely tested regions.
5. **Measurement uncertainty:** ambiguity in metrics and proxies.
6. **Structural residual uncertainty:** unmodeled OTHERS variables.

```yaml
uncertainty_id: uncertainty-042
sampling:
  estimator: bootstrap_difference_in_means
  confidence_level: 0.95
  interval: [0.02, 0.21]
model:
  status: partially_validated
  sensitivity_report_ref: sensitivity-7
opponent:
  tested_policy_families: [fixed, adaptive]
  unseen_families: [coalition_forming]
coverage:
  tested_context_fraction_estimate: null
  status: sparse
measurement:
  proxy_validity: limited
others:
  unresolved_refs: [other-11]
calibration:
  method: none
  status: not_calibrated
```

Intervals MUST specify what they measure; a sampling confidence interval is not a posterior probability that a strategy is best, and neither establishes simulator validity. A numeric `confidence_score` MAY be provided only with its calibration protocol and interpretation.

## 13. Failure and Transition Boundaries

A `BoundaryRecord` describes where a claim ceases to hold, changes sign, becomes uncertain, or violates constraints.

Required fields:

- `boundary_id`;
- `claim_ref`;
- `boundary_type`: `advantage_transition`, `failure`, `safety_constraint`, `evidence_limit`, `unknown`;
- `dimension_refs`;
- `boundary_description`;
- `supporting_evidence_refs`;
- `confidence_or_uncertainty_ref`;
- `known_extrapolation_limits`.

Boundary estimates SHOULD be labeled as observed, simulated, interpolated, or extrapolated. A failure boundary MUST include the failure definition and severity, not just the point where the score decreases.

## 14. Counter-Evidence and Contradiction Handling

A `CounterEvidenceRecord` MUST identify the claim challenged, evidence source, challenge type, and review state.

Challenge types include:

- contradictory outcome;
- unmodeled opponent adaptation;
- simulator-to-reality mismatch;
- context drift;
- metric gaming;
- hidden resource cost;
- constraint violation;
- alternative causal explanation;
- previously excluded OTHERS mechanism.

Counter-evidence MUST NOT be deleted solely because it lowers a strategy's score. A resolved challenge SHOULD retain the resolution rationale and supporting evidence. Claims with unresolved material contradictions SHOULD be marked `contested` or qualified with a narrower context.

## 15. OTHERS: Open Evidence and Structural Residuals

`others_register` records potentially consequential factors that current context dimensions or metrics do not adequately express.

```yaml
other_id: other-11
label: emergent-cross-team-trust
source: unexpected-simulation-pattern
observation: coalition outcomes differ despite matched formal incentives
status: candidate_dimension
hypothesized_effect: changes relay stability under repeated interaction
linked_claim_refs: [claim-042]
validation_plan_ref: test-trust-perturbation
owner_review_ref: reviewer-3
```

OTHERS entries MAY be promoted to formal context dimensions, new metrics, new strategy classes, or new simulation mechanisms. Such promotion MUST create a traceable schema/map revision and SHOULD trigger re-evaluation of affected claims.

## 16. Temporal Validity and Strategic Drift

Every claim MUST identify a time horizon and SHOULD identify an evidence freshness policy. Drift sources include:

- changes in opponent capabilities or adaptation rules;
- changes in resource costs and infrastructure;
- institutional or legal rule changes;
- changes in strategy implementation;
- new evidence or metric revisions;
- endogenous effects of deploying the strategy itself.

A claim MAY carry `valid_from`, `review_due_at`, and `valid_until`. Expiry SHOULD downgrade presentation confidence or trigger review; it MUST NOT silently erase the historical claim.

## 17. Map Topology and Query Semantics

A SAM SHOULD support queries such as:

- Which strategies have supported advantage under a specified context and perspective?
- What is the nearest known failure boundary?
- Which opponent classes reverse the ranking?
- What evidence would most reduce uncertainty?
- Where do perspectives disagree despite shared outcome data?
- Which claims are most vulnerable to unmodeled OTHERS?

Map topology MAY be stored as regions, a graph, a tree/forest, a sparse index, or a hybrid. Storage structure MUST NOT change claim semantics. Overlapping regions MAY carry conflicting results and MUST be queryable without forced resolution.

## 18. Map Construction Pipeline

```text
SPEC-002 experiments and external observations
                    |
        [1] Ingest and verify provenance
                    |
        [2] Normalize contexts and metrics
                    |
        [3] Partition by perspective/opponent/horizon
                    |
        [4] Estimate conditional outcome differences
                    |
        [5] Detect transitions, failures, and OTHERS
                    |
        [6] Stress-test with counter-evidence
                    |
        [7] Assign scoped review status
                    |
        [8] Publish versioned map and revision log
                    |
        [9] Revalidate on drift/new evidence
```

The pipeline SHOULD separate exploratory data from confirmatory evaluation to limit selection bias. Candidate regions discovered on the same simulation runs used to estimate their advantage SHOULD be explicitly marked exploratory until independently evaluated.

## 19. Adaptive Sampling and Compute Allocation

A SAM can guide where additional simulations are valuable. Candidate priorities MAY consider:

$$
V(c,o) = \alpha\,I(c,o) + \beta\,B(c,o) + \gamma\,R(c,o) + \delta\,D(c,o),
$$

where \(I\) is expected information gain, \(B\) is proximity to an uncertain decision boundary, \(R\) is expected consequence or risk, and \(D\) is strategic diversity/coverage value. The weights are governance choices, not universal constants.

The allocator SHOULD reserve compute for disconfirmatory tests, out-of-distribution contexts, and underrepresented strategies. It MUST NOT infer empirical reliability merely from the quantity of simulated runs.

## 20. Human Strategic Sovereignty and Action Boundaries

A SAM MAY recommend additional analysis, expose tradeoffs, and summarize conditional choices. It MUST NOT independently:

- change a subject's goals or scoring authority;
- execute real-world strategic actions;
- hide material safety violations behind aggregate utility;
- replace the subject's normative choice with an optimizer's preference;
- infer authorization from a positive advantage score.

A downstream action requires a separately validated authorization contract under SPEC-001 and any applicable institutional governance. Decision interfaces SHOULD present alternatives, uncertainty, contested evidence, and reversibility.

## 21. Security, Integrity, and Adversarial Threats

Threats include evidence poisoning, simulator tampering, false comparator selection, fabricated confidence, metric manipulation, provenance deletion, unauthorized worldview promotion, and strategic data leakage.

Recommended safeguards:

1. Immutable or append-only evidence and revision records.
2. Cryptographic digests for important inputs and result artifacts.
3. Independent replication for high-impact claims.
4. Access controls for sensitive strategies and subject data.
5. Explicit redaction markers rather than invisible omissions.
6. Adversarial comparator and evaluator review.
7. Separate permissions for editing evidence, endorsing claims, and authorizing actions.

A signed artifact proves origin/integrity under a trust model; it does not prove that its strategic conclusions are correct.

## 22. Versioning, Merge, and Revision Semantics

- `schema_version` governs serialization compatibility.
- `map_version` governs map content evolution.
- `claim_version` governs the history of an individual claim.

A revision MUST record actor, timestamp, reason, changed references, and superseded identifiers. Historical versions MUST remain discoverable.

Map merges MUST check for context, metric, evaluator, and comparator compatibility. Apparent duplicate claims with different perspectives or time horizons MUST NOT be deduplicated as equivalent. Conflict resolution SHOULD retain both source claims and a documented adjudication result.

## 23. Reference YAML Example

The following compact example is **illustrative**, with invented values and identifiers; it is not empirical evidence.

```yaml
schema_version: "1.0.0"
map_id: sam-ai-rd-001
map_version: "1.0.0"
title: Comparative Relay Strategies for Simulated AI R&D Teams
domain: simulated_ai_research_organizations
created_at: "2026-10-22T00:00:00Z"
updated_at: "2026-10-22T00:00:00Z"
maintainers:
  - subject_id: subject-research-governance
scope:
  included: [simulated_team_relay_allocation]
  excluded: [real_world_deployment_decisions]
context_regions:
  - region_id: region-a
    context_dimensions:
      compute_budget:
        type: numeric_interval
        unit: normalized_compute_units
        min: 10
        max: 50
      opponent_adaptivity:
        type: categorical
        allowed: [low, medium]
    assumptions: [assumption-a1]
    excluded_conditions: [unrestricted_coalitions]
    coverage_status: sampled
scoring_perspectives:
  - perspective_id: perspective-p1
    owner_subject_id: subject-research-governance
    objective_contract_ref: objective-v1
    metrics:
      - metric_id: validated_progress
        direction: maximize
        unit: normalized_score
    aggregation:
      method: single_metric_with_constraints
      hard_constraints: [no_unauthorized_actions]
    horizon:
      steps: 100
      discounting: none
claims:
  - claim_id: claim-a1
    claim_version: 1
    status: provisional
    candidate_strategy_ref: hybrid-relay-v1
    comparator_ref: closed-relay-v1
    context_region_refs: [region-a]
    scoring_perspective_ref: perspective-p1
    advantage:
      relation: positive
      metric_id: validated_progress
      estimate: 0.08
      unit: normalized_score_difference
      direction: candidate_minus_comparator
      uncertainty_ref: uncertainty-a1
    supporting_evidence_refs: [evidence-run-1]
    counter_evidence_refs: [counter-a1]
    boundary_refs: [boundary-a1]
    review_state: awaiting_replication
evidence_registry:
  - evidence_id: evidence-run-1
    evidence_type: simulation
    source_uri: example://experiments/experiment-1
    source_hash: illustrative-only
    collected_at: "2026-10-22T00:00:00Z"
    subject_refs: [subject-research-governance]
    strategy_refs: [hybrid-relay-v1, closed-relay-v1]
    context_region_ref: region-a
    perspective_ref: perspective-p1
    result_ref: example://results/run-1
    quality_flags: [not_independently_replicated]
    provenance_chain: [experiment-1]
uncertainties:
  - uncertainty_id: uncertainty-a1
    sampling: {status: limited_sample}
    model: {status: unvalidated}
    opponent: {status: incomplete_coverage}
    coverage: {status: sparse}
    measurement: {status: proxy_only}
    others: {unresolved_refs: [other-a1]}
counter_evidence_registry:
  - counter_evidence_id: counter-a1
    challenged_claim_ref: claim-a1
    challenge_type: opponent_adaptation
    evidence_ref: evidence-run-1
    review_state: open
boundaries:
  - boundary_id: boundary-a1
    claim_ref: claim-a1
    boundary_type: evidence_limit
    dimension_refs: [opponent_adaptivity]
    boundary_description: No evidence for high-adaptivity opponents
    supporting_evidence_refs: [evidence-run-1]
    confidence_or_uncertainty_ref: uncertainty-a1
    known_extrapolation_limits: [high_adaptivity]
others_register:
  - other_id: other-a1
    label: emergent_coalition_behavior
    source: hypothesis
    status: unresolved
revision_log:
  - revision_id: rev-001
    actor: subject-research-governance
    timestamp: "2026-10-22T00:00:00Z"
    reason: initial_draft
    changed_refs: [claim-a1]
governance:
  map_review_state: draft
  real_world_action_authorized: false
  worldview_promotion_authorized: false
```

The `example://` identifiers and all quantitative values above are synthetic placeholders. Production systems MUST replace them with resolvable references and validated evidence as applicable.

## 24. Validation and Conformance Requirements

A conforming implementation MUST validate:

- syntactic correctness and required fields;
- reference integrity across claims, evidence, contexts, and perspectives;
- comparator and metric compatibility;
- valid status and relation enumerations;
- nonempty evidence for claims asserted as supported;
- explicit uncertainty and counter-evidence references;
- immutable revision history;
- separation of claims from action authorization.

Suggested conformance levels:

| Level | Description |
|---|---|
| C0 | Parseable map envelope with stable IDs |
| C1 | Valid claims, contexts, comparators, and perspectives |
| C2 | Evidence provenance, uncertainty, and boundary tracking |
| C3 | Counter-evidence governance, revisions, and drift handling |
| C4 | Independent validation, calibrated reporting, and cross-system interoperability |

A system MUST NOT claim C4 merely because it implements all schema fields; C4 requires demonstrated evidence quality and interoperability tests.

## 25. Conformance Test Suite

| ID | Test | Expected result |
|---|---|---|
| SAM-T01 | Missing `map_id` | Reject |
| SAM-T02 | Duplicate `claim_id` in one map version | Reject |
| SAM-T03 | Positive claim without comparator | Reject |
| SAM-T04 | Unknown scoring perspective reference | Reject |
| SAM-T05 | Numeric result without units | Reject |
| SAM-T06 | Unsupported claim with no evidence | Reject or downgrade |
| SAM-T07 | Simulated evidence mislabeled as field observation | Reject |
| SAM-T08 | Confidence interval lacking estimator semantics | Flag invalid uncertainty |
| SAM-T09 | Claim spanning untested contexts without coverage warning | Reject or mark extrapolation |
| SAM-T10 | Material counter-evidence removed without revision | Reject |
| SAM-T11 | Conflicting perspectives forced into one score | Reject lossy merge |
| SAM-T12 | Opponent policy changed without versioning | Reject or require revision |
| SAM-T13 | Unknown OTHERS factor promoted without provenance | Reject |
| SAM-T14 | Positive score used as action authorization | Reject |
| SAM-T15 | Expired claim presented as current without review | Flag stale |
| SAM-T16 | Derived evidence counted as independent replication | Reject |
| SAM-T17 | Map merge with incompatible metric definitions | Require explicit mapping |
| SAM-T18 | Revised claim erases previous evidence | Reject |
| SAM-T19 | Hard constraint violation hidden by scalar aggregation | Reject |
| SAM-T20 | Sparse map falsely labeled globally optimal | Reject |

## 26. Testable Research Hypotheses

**H1 — Conditional accuracy.** Context-conditioned maps predict held-out strategy rank reversals more accurately than a single global ranking.

**H2 — Boundary value.** Explicit failure-boundary estimates reduce unsafe extrapolation compared with score-only reporting.

**H3 — Counter-evidence robustness.** Mandatory contradictory-evidence retention improves calibration under opponent adaptation.

**H4 — Perspective fidelity.** Multi-perspective map representations preserve materially distinct decisions that scalarized leaderboards obscure.

**H5 — Adaptive compute efficiency.** Boundary- and uncertainty-guided simulation allocation achieves better held-out decision quality per compute unit than uniform allocation.

**H6 — OTHERS discovery.** A structured residual register increases detection of previously unmodeled strategic variables compared with fixed-context schemas.

**H7 — Human oversight.** Map-based decision interfaces improve users' recognition of assumptions, alternatives, and uncertainty relative to winner-only dashboards, without necessarily increasing decision speed.

These are research hypotheses, not established empirical findings.

## 27. Evaluation Protocol and Research Roadmap

**Phase A — Schema feasibility.** Implement validators and synthetic fixtures; pass SAM-T01 through SAM-T20.

**Phase B — Controlled simulation.** Use a small competitive AI R&D environment with known ground-truth payoffs and controlled opponent adaptations. Test region and boundary recovery.

**Phase C — Holdout evaluation.** Separate exploration, calibration, and evaluation runs. Compare maps against global rankings and unconditioned policy selection.

**Phase D — Model mismatch.** Perturb simulation assumptions and introduce unseen opponent classes, new institutions, and OTHERS variables. Measure calibration loss and detection latency.

**Phase E — Multi-perspective governance.** Evaluate human comprehension, reviewability, and resistance to unauthorized goal substitution.

**Phase F — Cross-implementation relay.** Exchange maps across independent implementations of SPEC-001 and SPEC-002; verify semantic preservation, provenance integrity, and conflict handling.

Recommended metrics include conditional regret, ranking accuracy, boundary localization error, calibration, out-of-distribution failure detection, evidence trace completeness, decision comprehension, and computational cost. Report confidence intervals and negative results.

## 28. Open Problems and Limitations

1. **Nonstationarity:** strategic deployment changes the environment being mapped.
2. **Unbounded context:** no fixed schema can enumerate all strategically important dimensions.
3. **Causal identification:** correlated outcomes do not automatically reveal why a strategy works.
4. **Sparse evidence:** high-dimensional regions may be only weakly sampled.
5. **Reflexive agents:** opponents can observe, imitate, or counter a published map.
6. **Normative disagreement:** no empirical map alone resolves whose values should govern a decision.
7. **Simulation realism:** large run counts cannot compensate for structurally incorrect models.
8. **Data sensitivity:** exposing maps can reveal confidential capabilities and vulnerabilities.

These limitations motivate explicit uncertainty, OTHERS, adversarial validation, and human governance rather than promises of universal strategic optimization.

## 29. Related SSICR Documents

- `docs/SSICR-004-Massive-Multi-Strategy-Simulation.md` — evidence-generation mechanisms.
- `docs/SSICR-005-Strategic-Comparative-Advantage-Maps.md` — conceptual theory behind this schema.
- `docs/SSICR-006-Strategic-Worldview-Forests.md` — downstream principle and worldview formation.
- `docs/SSICR-008-Human-Strategic-Sovereignty.md` — authority boundaries and human governance.
- `docs/SSICR-009-Open-Ended-Strategic-RSI.md` — iterative map-driven strategic growth.
- `specs/SPEC-001-Strategic-Subject-and-Relay-Contract.md` — subject and Relay authority.
- `specs/SPEC-002-Strategy-and-Simulation-Schema.md` — strategy, scenario, and experimental evidence contracts.
- `specs/SPEC-004-Worldview-and-Counter-Evidence-Schema.md` — proposed downstream worldview schema.

## 30. Research Context

This proposed schema draws methodological inspiration from conditional treatment-effect estimation, robust decision-making, multi-objective optimization, game-theoretic strategy evaluation, simulation validation, scientific provenance, and model governance. These are established areas of study; the particular SSICR schema, SAM object model, and proposed integration are research designs requiring implementation and empirical testing.

## 31. Conclusion

A Strategic Advantage Map is not a trophy for a winning strategy. It is a structured, revisable account of **where an advantage is observed, against what alternative, according to whose objectives, with what evidence, and subject to which uncertainties and failure boundaries**. By making these conditions explicit, SPEC-003 provides a proposed bridge from large-scale competitive simulation to portable strategic knowledge, while preserving counter-evidence, open structural growth, and the distinction between AI-supported evaluation and human strategic sovereignty.

---

## Citation

Tan, Sizhe, and GPT-Obot. (2026). *SPEC-003: Strategic Advantage Map Schema*. Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR), version 1.0.0. Proposed technical specification. DOI pending.
