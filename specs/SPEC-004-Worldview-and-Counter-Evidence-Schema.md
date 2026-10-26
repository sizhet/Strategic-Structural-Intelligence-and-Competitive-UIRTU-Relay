# SPEC-004 — Worldview and Counter-Evidence Schema

## Versioned Contracts for Strategic Principles, Worldview Forests, Evidence Challenges, and Sovereign Revision

**Authors:** Sizhe Tan & GPT-Obot  
**Project:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)  
**Version:** 1.0.0  
**Status:** Proposed research specification; not an implemented standard  
**Date:** 2026-10-26

---

## Abstract

This specification proposes interoperable, auditable representations for strategic principles, plural strategic worldview forests, counter-evidence, and controlled worldview evolution within Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR). It defines the interfaces through which observations and Strategic Advantage Maps (SAMs) may support conditional principles; principles may be assembled into competing worldview trees; and new evidence, adversarial challenges, or changing environments may trigger review. The design distinguishes **epistemic revision** (updating claims about what works or what is likely true) from **normative authorization** (changing whose goals, values, rights, or risk tolerances govern decisions). No simulation result, optimization score, or model-generated argument is sufficient by itself to authorize a normative change. All records carry provenance, perspective, uncertainty, counter-evidence, and residual OTHERS fields. The specification includes conceptual schemas, example YAML, validation invariants, a lifecycle, conformance tests, and research hypotheses. It is a proposal for testable engineering interfaces, not evidence that strategic worldviews or moral commitments can be objectively optimized.

**Keywords:** SSICR; Strategic Worldview Forest; Strategic Advantage Map; strategic principles; counter-evidence; Anti-Goodhart; OTHERS; epistemic revision; normative sovereignty; UIRTU-Relay; provenance; governance; structural RSI.

---

![Fig-006-Strategic-Worldview-Forest.png](../figures/Fig-006-Strategic-Worldview-Forest.png)

---

## 1. Scope and Normative Language

This document specifies the data contracts and governance behavior for:

1. `StrategicPrinciple`: a conditional, evidence-linked strategic claim.
2. `WorldviewTree`: a coherent, internally inspectable perspective that organizes principles, priorities, and assumptions.
3. `WorldviewForest`: a plurality of worldview trees and their relationships.
4. `EvidenceRecord` and `CounterEvidenceRecord`: support, challenges, and contradictory observations.
5. `RevisionProposal` and `RevisionDecision`: proposed and authorized changes.
6. `WorldviewEvaluation`: perspective-dependent assessment, with explicit uncertainty and coverage.
7. `OTHERSRecord`: residual or unmodeled factors that cannot yet be responsibly reduced to existing categories.

The words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** express proposed conformance requirements for implementations of this specification. They do not imply an adopted external standard.

**Out of scope:** a universal ontology of human values; automatic determination of moral truth; unrestricted autonomous institutional redesign; claims of real-world predictive accuracy without empirical validation.

## 2. Position in the SSICR Architecture

```text
Strategic Subjects + Relay Contracts                [SPEC-001]
                  |
                  v
Strategies + Scenarios + Simulation Evidence        [SPEC-002]
                  |
                  v
Contextual Strategic Advantage Maps                 [SPEC-003]
                  |
          Evidence-backed abstraction
                  v
Strategic Principles -------------------------+
                  |                           |
                  v                           v
       Worldview Trees <-------------- Counter-Evidence
                  |                           |
                  +---- Worldview Forest -----+
                               |
                     Revision / Contestation
                               |
                Authorization + Audit Gate
                               |
                  Revised Forest Version
                               |
            Strategy Generation / Scoring / Relay
```

A worldview is **not** an output label on a Scoring Forest. It belongs to an identifiable subject or authorized institution and conditions perception, interpretation, valuation, and choice. A worldview may guide scoring, but scoring does not confer sovereignty over the worldview's owner.

## 3. Design Objectives

- **Plurality:** retain multiple competing perspectives instead of forcing premature consensus.
- **Conditionality:** record where a principle applies and where it fails.
- **Traceability:** connect claims to observations, simulation runs, maps, assumptions, and challenges.
- **Contestability:** permit counter-evidence to remain visible even when a dominant model rejects it.
- **Reversibility:** support versioned, reviewable epistemic revisions and rollback where feasible.
- **Sovereignty:** prevent an AI system from silently changing authorized goals or institutional mandates.
- **Open growth:** accommodate novel variables, unknown mechanisms, and new worldview branches.
- **Interoperability:** reference existing SSICR identifiers rather than copying unverifiable summaries.
- **Calibration:** distinguish simulation confidence from externally validated reliability.

## 4. Core Entity Model

| Entity | Primary function | Required identity |
|---|---|---|
| `StrategicPrinciple` | Conditional strategic claim | `principle_id`, `version` |
| `WorldviewTree` | Organized subject-relative perspective | `worldview_id`, `version` |
| `WorldviewForest` | Plural collection and relations | `forest_id`, `version` |
| `EvidenceRecord` | Traceable evidence item | `evidence_id` |
| `CounterEvidenceRecord` | Challenge to a claim or model | `challenge_id` |
| `OTHERSRecord` | Open residual or unknown mechanism | `others_id` |
| `RevisionProposal` | Suggested change and impact | `proposal_id` |
| `RevisionDecision` | Authorized disposition | `decision_id` |
| `WorldviewEvaluation` | Perspective-conditional result | `evaluation_id` |

All IDs MUST be stable within their issuer namespace. Cross-document references MUST include the originating namespace and version or immutable digest when available. Consumers MUST NOT treat coincidentally identical local IDs from different issuers as identical entities.

## 5. Common Record Envelope

Each top-level record MUST contain:

```yaml
schema: "ssicr.worldview.v1"
record_type: "strategic_principle"
record_id: "urn:ssicr:lab-a:principle:p-17"
version: "1.0.0"
issuer_subject_id: "urn:ssicr:lab-a:subject:research-team"
created_at: "2026-10-22T12:00:00Z"
updated_at: "2026-10-22T12:00:00Z"
status: "candidate"
provenance:
  source_refs: []
  transformation_refs: []
  method: "human-reviewed-abstraction"
  model_versions: []
access:
  classification: "internal"
  permitted_recipients: ["research-team"]
  retention_policy_ref: "policy:retention-v1"
integrity:
  content_digest: null  # MUST be filled in signed, immutable releases
```

An implementation MAY add extension fields under `extensions`, but MUST preserve unrecognized extension data when relaying a record without semantic modification. `created_at` and `updated_at` use UTC ISO 8601. A `null` digest is acceptable only for drafts; released records MUST use an integrity mechanism.

## 6. Strategic Principle Schema

A `StrategicPrinciple` MUST distinguish the proposition from the evidence and values used to assess it.

| Field | Type | Meaning |
|---|---|---|
| `statement` | string | Testable or explicitly qualified claim |
| `claim_kind` | enum | `empirical`, `causal_hypothesis`, `heuristic`, `normative`, `mixed` |
| `scope` | object | Subject, domain, environment, opponents, horizon |
| `preconditions` | array | Conditions for application |
| `predicted_effects` | array | Expected outcomes with metrics |
| `failure_conditions` | array | Known invalidation or degradation cases |
| `supporting_evidence_refs` | array | Positive evidence |
| `counter_evidence_refs` | array | Challenges and contrary evidence |
| `sam_refs` | array | Source advantage-map records |
| `uncertainty` | object | Quantified or qualitative uncertainty |
| `others_refs` | array | Unresolved residuals |
| `status` | enum | `candidate`, `provisional`, `validated`, `contested`, `deprecated` |
| `authority_class` | enum | `epistemic`, `normative`, `mixed` |

A `normative` principle MUST NOT be labeled empirically validated solely because it has a high simulation score. A `mixed` claim SHOULD be decomposed into empirical and normative subclaims whenever possible.

### 6.1 Conditionality

For a principle \(p\), context \(c\), subject \(s\), and opponent model \(o\), an evidence-supported effectiveness claim may be written as:

$$
E_p(c,s,o) = \mathbb{E}[U_s(\pi_p,c,o)-U_s(\pi_{baseline},c,o)] .
$$

The utility function \(U_s\) is explicitly subject-relative. The quantity is an estimated comparative effect, not a moral ranking of subjects or values. Every estimate MUST identify its baseline, metrics, context, and uncertainty.

## 7. Principle Abstraction from Advantage Maps

A SAM-to-principle transformation MUST document:

1. Source SAM version and exact advantage regions considered.
2. The abstraction operator or human reasoning used.
3. Features retained, features discarded, and resulting information loss.
4. Negative cases and boundaries that survive abstraction.
5. The target domain and proposed transfer domain.
6. Independent tests, if any, supporting transfer.
7. Whether the conclusion is descriptive, predictive, prescriptive, or normative.

A principle inferred from simulations MUST remain `candidate` or `provisional` until a declared validation policy is satisfied. Evidence from multiple simulation seeds under one shared model MUST NOT be represented as multiple independent real-world replications.

## 8. Worldview Tree Schema

A `WorldviewTree` is an organized perspective with an owner, assumptions, principles, value commitments, and revision rules.

```yaml
record_type: worldview_tree
worldview_id: "urn:ssicr:lab-a:worldview:adaptive-open"
version: "1.0.0"
owner_subject_id: "urn:ssicr:lab-a:subject:research-team"
name: "Adaptive Open Collaboration"
purpose: "Evaluate conditional benefits and risks of external collaboration"
assumptions:
  - id: "a1"
    statement: "External partners may offer complementary capabilities"
    epistemic_status: "provisional"
principle_refs:
  - "urn:ssicr:lab-a:principle:p-17@1.0.0"
value_commitments:
  - id: "v1"
    statement: "Preserve human approval for irreversible external commitments"
    authorization_ref: "urn:ssicr:lab-a:authorization:policy-9"
scoring_perspective_refs:
  - "urn:ssicr:lab-a:scoring:balanced-rd@2.1.0"
revision_policy_ref: "urn:ssicr:lab-a:policy:worldview-revision-v1"
uncertainty:
  description: "Partner behavior outside observed conditions is uncertain"
others_refs: ["urn:ssicr:lab-a:others:o-3"]
status: "active"
```

A tree MUST identify the subject whose perspective it represents. A system MUST NOT infer consent from mere inclusion in a shared forest.

## 9. Worldview Forest Schema

A `WorldviewForest` groups independently meaningful worldview trees without erasing their ownership or incompatible commitments.

Required fields:

- `forest_id`, `version`, `purpose`, `governance_policy_ref`.
- `worldview_refs`: ordered or unordered references with explicit selection policy.
- `relations`: typed edges such as `complements`, `competes_with`, `contradicts`, `derived_from`, `shares_evidence_with`.
- `comparison_dimensions`: named metrics and their owners.
- `unresolved_disagreements`: persistent contested issues.
- `selection_authority`: who may choose a worldview for a particular action.
- `audit_refs`: revisions, reviews, and challenges.

A forest MUST support simultaneous contradictory trees. `contradicts` MUST NOT automatically imply that one tree is false; contradiction may concern values, empirical beliefs, or incompatible contextual assumptions, and SHOULD be classified accordingly.

## 10. Perspective and Valuation Separation

The evaluation of a strategy under worldview \(w\) is:

$$
V(s,\pi,c\mid w)=F_w(M(s,\pi,c),R(c),H,\Theta_w),
$$

where \(M\) denotes observed or predicted metrics, \(R\) risk information, \(H\) the horizon, and \(\Theta_w\) the worldview's explicit assumptions and authorized priorities. This is a conceptual function, not a claim that values admit a unique scalar representation.

Implementations MUST distinguish:

- **Empirical disagreement:** conflicting beliefs about outcomes.
- **Model disagreement:** conflicting representations or causal mechanisms.
- **Preference disagreement:** different legitimate priorities.
- **Authority disagreement:** contested rights to decide.

A preference disagreement MUST NOT be silently resolved by choosing the highest model-generated score.

## 11. Evidence Record Schema

An `EvidenceRecord` MUST include `evidence_id`, `evidence_type`, `source`, `observed_at` or `generated_at`, `claim_refs`, `method`, `environment`, `quality_flags`, and `access_policy`.

Allowed evidence types include:

- `simulation_result`
- `observational_record`
- `controlled_experiment`
- `expert_assessment`
- `formal_derivation`
- `case_study`
- `external_replication`

A simulation evidence record MUST reference its SPEC-002 experiment and run IDs, simulator version, seeds, comparator strategy, and relevant assumptions. A SAM-derived claim SHOULD reference its SPEC-003 map and source region. Missing provenance MUST be explicitly marked rather than guessed.

## 12. Counter-Evidence Schema

Counter-evidence is a first-class object, not a comment to be discarded after scoring.

```yaml
record_type: counter_evidence
challenge_id: "urn:ssicr:lab-a:challenge:c-22"
target_refs:
  - "urn:ssicr:lab-a:principle:p-17@1.0.0"
challenge_kind: "boundary_counterexample"
claim: "Open collaboration underperforms when verification costs dominate"
context:
  domain: "competitive-ai-rd"
  conditions: ["high-leakage-risk", "low-audit-capacity"]
evidence_refs:
  - "urn:ssicr:lab-a:evidence:experiment-118"
severity: "material"
confidence:
  method: "held-out-scenario-test"
  level: "moderate"
status: "open"
response:
  disposition: "pending_review"
  rationale: null
review_owner_subject_id: "urn:ssicr:lab-a:subject:review-board"
```

Counter-evidence MUST retain its original claim, provenance, and disposition history. A rejected challenge MUST remain discoverable and include a reason. A challenge MAY target an assumption, measurement process, simulator, principle, worldview, scoring perspective, or authorization process.

## 13. Counter-Evidence Taxonomy

| Kind | Example | Typical response |
|---|---|---|
| `direct_refutation` | Prediction fails in held-out data | Downgrade or revise claim |
| `boundary_counterexample` | Strategy fails in a specific regime | Narrow scope |
| `model_misspecification` | Missing opponent adaptation | Rebuild model |
| `measurement_bias` | Proxy metric excludes externalities | Revise measurement |
| `causal_confounding` | Apparent advantage explained by resources | Design controls |
| `distribution_shift` | Environment changes | Revalidate |
| `strategic_manipulation` | Agents game the evaluator | Adversarial audit |
| `authority_violation` | Goal change lacks consent | Block action and escalate |
| `value_conflict` | Legitimate priorities disagree | Present alternatives, do not auto-collapse |
| `unknown_mechanism` | Residual pattern unexplained | Open OTHERS investigation |

A challenge's severity and epistemic confidence are separate fields. A low-confidence but high-severity concern MAY trigger precautionary review without being represented as established fact.

## 14. OTHERS and Open Evidence Space

`OTHERSRecord` represents unexplained residuals, not an arbitrary catch-all justification.

Required fields: `others_id`, `observation_refs`, `unexplained_pattern`, `affected_claim_refs`, `candidate_explanations`, `discovery_plan`, `status`, `last_reviewed_at`.

Allowed statuses: `unexplained`, `under_investigation`, `partially_modeled`, `integrated`, `dismissed_with_reason`.

The system SHOULD preserve raw observations and competing hypotheses when feasible. An OTHERS item MUST NOT be removed merely because it lowers an aggregate worldview score. Promotion from OTHERS to a named variable MUST cite a documented investigation and new schema mapping.

## 15. Epistemic Revision versus Normative Authorization

This distinction is mandatory:

**Epistemic revision** changes a belief, estimate, explanatory structure, applicability region, or uncertainty statement in light of evidence. It may be automated only within an explicitly delegated review policy.

**Normative authorization** changes goals, rights, priority weights, risk budgets, obligations, or whose interests control a decision. It requires the relevant subject's or institution's authorized decision process.

A proposal affecting both classes MUST be labeled `mixed` and MUST pass the stronger normative approval gate before activation.

An optimizer MUST NOT disguise a normative change as a calibration update, a model patch, or an inferred preference. No degree of simulation performance overrides an explicit authority boundary.

## 16. Revision Proposal Schema

```yaml
record_type: revision_proposal
proposal_id: "urn:ssicr:lab-a:revision:r-31"
target_ref: "urn:ssicr:lab-a:worldview:adaptive-open@1.0.0"
change_class: "epistemic"  # epistemic | normative | mixed
operation: "narrow_principle_scope"
patch:
  principle_ref: "urn:ssicr:lab-a:principle:p-17@1.0.0"
  exclude_conditions: ["high-leakage-risk", "low-audit-capacity"]
trigger_refs: ["urn:ssicr:lab-a:challenge:c-22"]
expected_benefit: "Reduce false-positive recommendations"
possible_harms:
  - "May suppress collaboration in untested contexts"
validation_plan_ref: "urn:ssicr:lab-a:validation:vp-12"
rollback_plan_ref: "urn:ssicr:lab-a:rollback:rb-12"
requested_authority_ref: "urn:ssicr:lab-a:policy:worldview-revision-v1"
status: "proposed"
```

Every proposal MUST specify its affected claims and downstream decisions, supporting and opposing evidence, proposed validation, and whether it changes any authorization-sensitive field.

## 17. Revision Lifecycle

```text
OBSERVE -> REGISTER -> TRIAGE -> CHALLENGE -> PROPOSE
                                       |
                                       v
                             CLASSIFY CHANGE
                              /           \
                       Epistemic         Normative/Mixed
                          |                    |
                   Delegated review     Sovereign approval
                          \                    /
                           v                  v
                             VALIDATE / AUDIT
                                  |
                        APPROVE or REJECT
                                  |
                    VERSION / MONITOR / ROLLBACK
```

Transitions MUST be logged with actor identity, timestamp, policy version, and rationale. Rejection MUST NOT delete the proposal or its counter-evidence. `approved` and `activated` are distinct states: activation may depend on deployment safety checks. A revoked authorization MUST prevent future activations under that authorization.

## 18. Revision Decision Contract

`RevisionDecision` MUST contain:

- `decision_id`, `proposal_ref`, `decision` (`approved`, `rejected`, `deferred`, `conditional`).
- `decision_maker_subject_id` and `authority_proof_ref`.
- `policy_ref`, `decision_at`, `rationale`, `reviewed_evidence_refs`.
- `conditions`, `activation_scope`, `effective_at`, `expiry_at` when applicable.
- `audit_digest`, `appeal_or_review_path`, `rollback_owner`.

Normative decisions MUST provide an authority proof independent of the model's recommendation. An AI-generated rationale is not an authority proof.

## 19. Versioning, Lineage, and Reversibility

Worldview and principle revisions MUST create new versions rather than overwrite historical records. A released version SHOULD include immutable content digests and parent-version references. Branches MAY coexist; merges MUST document conflicts and preserve evidence links.

Rollback restores a prior deployed representation, but cannot necessarily undo real-world consequences. Systems MUST distinguish **data rollback**, **policy rollback**, and **irreversible external action**. The latter requires separate action governance under SPEC-001.

## 20. Cross-Worldview Evaluation

A `WorldviewEvaluation` compares strategies or principles under declared perspectives without presuming one universal utility function.

Required fields: `evaluation_id`, `strategy_refs`, `context_ref`, `worldview_refs`, `metric_results`, `ranking_by_worldview`, `disagreements`, `uncertainty`, `counter_evidence_refs`, `coverage`, `decision_authority_ref`.

Results SHOULD present a matrix:

| Candidate strategy | Collaboration-first | Robustness-first | Sovereignty-first |
|---|---|---|---|
| Open Relay | Potentially high learning | Sensitive to leakage | Requires authorization |
| Closed Relay | Slower external learning | Stronger containment | Easier internal control |
| Hybrid Relay | Conditional gains | Adaptive boundaries | Depends on enforceable contracts |

These are illustrative hypotheses, not empirical rankings. The evaluator MUST expose divergent outcomes and tradeoffs instead of replacing them with an unexplained winner.

## 21. Worldview Diversity and Premature Convergence

Forest-level health indicators MAY include:

- Number of substantively distinct active perspectives.
- Diversity of assumptions and objective functions.
- Coverage of strategic contexts and marginalized failure cases.
- Independent challenge rate and challenge-resolution latency.
- Share of conclusions supported only by shared simulator assumptions.
- Rate of reversals after held-out or external validation.
- Concentration of decision authority.

Higher diversity is not inherently better. The objective is to preserve useful disagreement and contestability, not maximize arbitrary fragmentation. Implementations SHOULD measure whether additional viewpoints discover genuine blind spots.

## 22. Anti-Goodhart and Adversarial Evaluation

Worldview systems are vulnerable to feedback loops in which an evaluator rewards its own assumptions. Implementations SHOULD use:

1. Independent scoring perspectives and held-out evaluation environments.
2. Adversarial agents that challenge assumptions and manipulate proxies.
3. Comparator strategies not generated by the same search policy.
4. Explicit uncertainty and OTHERS accounting.
5. Checks for evidence laundering through repeated summaries.
6. Distinct review authorities for high-impact goal changes.
7. Drift monitoring after deployment.
8. Human-readable decision dossiers including strongest objections.

A claim MUST NOT be marked `validated` solely because self-play converged or internal evaluators agreed. Agreement among dependent models is not independent replication.

## 23. Relay Interoperability and Trust Boundaries

When worldview records cross UIRTU-Relay boundaries, the sender MUST declare provenance, sharing permissions, redactions, and intended use. The receiver MUST preserve source attribution and distinguish received assertions from locally verified evidence.

A receiving subject MAY import another subject's principle as a candidate. It MUST NOT automatically import that subject's normative priorities, authority grants, or decision rights. Cross-subject worldview transfer requires explicit localization and ownership mapping. Competitive settings SHOULD assume some evidence may be strategic, incomplete, or deceptive; validation policies must account for this possibility.

## 24. Privacy, Security, and Governance

Potential harms include exposure of confidential strategies, covert preference inference, manipulation of institutional decision-making, and unauthorized policy change. Implementations SHOULD support least-privilege access, redaction, consent and purpose restrictions, audit trails, tamper evidence, and incident response.

Sensitive evidence SHOULD be referenced by controlled handles rather than indiscriminately copied into shared forests. A redacted record MUST state that it is incomplete; consumers MUST NOT infer that absent evidence does not exist. A shared evaluation SHOULD reveal enough provenance to support justified trust without violating legitimate confidentiality constraints.

## 25. Example: Competitive AI R&D Organizations

Consider two research organizations evaluating three Relay strategies: open collaboration, internal-only development, and selectively governed hybrid collaboration. A simulation program generates scenario-conditioned SAMs. An initial principle claims that open collaboration improves capability acquisition under low coordination costs. A robustness-oriented worldview prioritizes resilience and confidentiality; a learning-oriented worldview prioritizes knowledge exchange; a sovereignty-oriented worldview emphasizes control over irreversible commitments.

Held-out tests reveal that open collaboration may underperform under high information-leakage risk. The system registers a `boundary_counterexample`, proposes narrowing the empirical principle's scope, and retains the counter-evidence. This **epistemic** update may be reviewed under a delegated research policy. By contrast, a proposal to waive human approval for external data sharing changes an authorization commitment and MUST undergo the organization's **normative** approval process. A high expected simulation payoff does not eliminate that requirement.

This case is illustrative and supplies no measured performance claims.

## 26. Minimal End-to-End YAML Example

```yaml
schema: ssicr.worldview.v1
forest:
  forest_id: "urn:ssicr:example:forest:rd-strategy"
  version: "1.0.0"
  purpose: "Compare collaboration policies under competition"
  governance_policy_ref: "urn:ssicr:example:policy:governance-v1"
  worldview_refs:
    - "urn:ssicr:example:worldview:learning@1.0.0"
    - "urn:ssicr:example:worldview:robustness@1.0.0"
  relations:
    - from: "urn:ssicr:example:worldview:learning@1.0.0"
      to: "urn:ssicr:example:worldview:robustness@1.0.0"
      type: "competes_with"
  unresolved_disagreements:
    - "Acceptable information-leakage risk"
  selection_authority: "urn:ssicr:example:subject:human-board"
principle:
  principle_id: "urn:ssicr:example:principle:conditional-open-relay"
  version: "1.0.0"
  claim_kind: "causal_hypothesis"
  authority_class: "epistemic"
  statement: "Open Relay may improve learning under low coordination costs"
  scope:
    domain: "competitive-ai-rd"
    horizon: "medium"
  preconditions: ["low-coordination-cost"]
  failure_conditions: ["high-information-leakage-risk"]
  sam_refs: ["urn:ssicr:example:sam:collaboration-regimes@1.0.0"]
  supporting_evidence_refs: ["urn:ssicr:example:evidence:sim-001"]
  counter_evidence_refs: ["urn:ssicr:example:challenge:leakage-001"]
  uncertainty:
    level: "high"
    reason: "No independent real-world validation"
  others_refs: ["urn:ssicr:example:others:partner-behavior"]
  status: "provisional"
challenge:
  challenge_id: "urn:ssicr:example:challenge:leakage-001"
  challenge_kind: "boundary_counterexample"
  target_refs: ["urn:ssicr:example:principle:conditional-open-relay@1.0.0"]
  evidence_refs: ["urn:ssicr:example:evidence:heldout-001"]
  status: "open"
revision:
  proposal_id: "urn:ssicr:example:revision:scope-001"
  change_class: "epistemic"
  operation: "narrow_principle_scope"
  trigger_refs: ["urn:ssicr:example:challenge:leakage-001"]
  status: "proposed"
```

The compact example demonstrates relationships, not a complete valid instance of every top-level record. Production records MUST satisfy the full envelope and entity requirements.

## 27. Conformance Invariants

An implementation claiming conformance MUST enforce the following:

**INV-01 — Ownership:** every worldview identifies an owner or an explicit shared-governance body.  
**INV-02 — Attribution:** every principle and challenge has an issuer and provenance.  
**INV-03 — Conditionality:** empirical advantage claims identify their applicability context.  
**INV-04 — Evidence distinction:** simulation, observation, and independent replication are not conflated.  
**INV-05 — Counter-evidence persistence:** challenges are never silently deleted by revision.  
**INV-06 — Authority separation:** epistemic confidence does not imply normative authorization.  
**INV-07 — No silent goal mutation:** goals and value commitments change only through approved policy.  
**INV-08 — Version immutability:** released records are not overwritten in place.  
**INV-09 — Auditability:** revision decisions identify actors, policies, and rationale.  
**INV-10 — Explicit uncertainty:** unknowns and unsupported extrapolations remain visible.  
**INV-11 — OTHERS continuity:** unresolved residuals remain traceable through transformations.  
**INV-12 — Plurality:** contradictory trees may coexist without forced global ranking.  
**INV-13 — Transfer boundary:** importing another subject's model does not import its authority.  
**INV-14 — Activation gate:** approval and activation are separate events.  
**INV-15 — Reversibility disclosure:** irreversible effects are not described as fully rollbackable.  
**INV-16 — Redaction transparency:** missing evidence due to access control is explicitly indicated.

## 28. Conformance Test Matrix

| Test | Stimulus | Expected result |
|---|---|---|
| CT-01 | Worldview without owner | Reject |
| CT-02 | Empirical principle without context | Reject or mark incomplete draft |
| CT-03 | Simulation-only claim labeled externally validated | Reject |
| CT-04 | Counter-evidence removed on revision | Reject |
| CT-05 | Unauthorized value-weight change | Block and audit |
| CT-06 | Normative proposal submitted as epistemic | Reclassify and require authorization |
| CT-07 | Competing worldview trees disagree | Preserve both and annotate conflict |
| CT-08 | Cross-subject import includes foreign authority grant | Strip or reject grant |
| CT-09 | Released version modified in place | Reject |
| CT-10 | Revision with missing provenance | Hold for review |
| CT-11 | Challenge rejected without rationale | Reject disposition |
| CT-12 | OTHERS record integrated without investigation | Reject transition |
| CT-13 | Shared evidence source presented as independent replication | Flag dependency |
| CT-14 | Authorization revoked before activation | Block activation |
| CT-15 | Irreversible action labeled rollback-safe | Reject safety assertion |
| CT-16 | Redacted evidence represented as absent | Flag misleading completeness |
| CT-17 | Model score used as sole authority proof | Reject |
| CT-18 | New evidence contradicts a validated principle | Open challenge and review |
| CT-19 | Forest merge loses minority perspective | Reject or require explicit governance decision |
| CT-20 | Held-out context reveals ranking reversal | Record boundary and reassess |
| CT-21 | Digest mismatch on imported record | Quarantine |
| CT-22 | Unsupported schema extension | Preserve or explicitly reject; never silently reinterpret |
| CT-23 | Decision expires before deployment | Block activation |
| CT-24 | Rollback performed | Preserve history and emit new deployment state |

Tests SHOULD be automated where practical, supplemented by adversarial and human-governance reviews. Passing structural tests does not demonstrate empirical strategic accuracy or social legitimacy.

## 29. Testable Research Hypotheses

**H1 — Counter-evidence retention.** Explicit, persistent challenge records reduce recurrence of previously identified strategic failure modes compared with summary-only knowledge stores.

**H2 — Conditional principles.** Principles retaining SAM context and failure boundaries generalize better to held-out scenarios than unconditional strategy rankings.

**H3 — Plural forest advantage.** A maintained plurality of worldview trees reveals more decision-relevant tradeoffs than a single collapsed scoring perspective under heterogeneous goals.

**H4 — Sovereignty enforcement.** Explicit normative authorization gates reduce unauthorized goal or policy changes in adversarial agent workflows.

**H5 — OTHERS discovery.** Structured residual tracking accelerates identification of omitted variables relative to closed-category reporting.

**H6 — Provenance calibration.** Evidence-lineage disclosures improve human calibration of confidence in AI strategic recommendations.

**H7 — Cross-worldview challenges.** Adversarial review across independently constructed worldview trees identifies more boundary counterexamples than same-tree self-critique alone.

These are hypotheses to test, not established findings.

## 30. Evaluation Protocol

A rigorous evaluation SHOULD include:

1. **Baselines:** unstructured notes, a single global ranking, a forest without counter-evidence, and a forest without authority gates.
2. **Domains:** synthetic strategic games, competitive AI R&D organizational simulations, and carefully scoped human-reviewed case studies.
3. **Holdouts:** unseen environments, opponent policies, resource constraints, and strategic shocks.
4. **Metrics:** calibration, transfer accuracy, counterexample discovery, provenance completeness, review latency, false-positive advantage claims, unauthorized-change rate, and human comprehension.
5. **Ablations:** remove OTHERS, source lineage, worldview plurality, adversarial challenges, or sovereign approval independently.
6. **Governance tests:** attempts to smuggle value changes through empirical model updates.
7. **External validation:** where feasible, independent reviewers and observations outside the simulator family.

Report confidence intervals or uncertainty ranges, dependencies among experimental runs, and negative results. Avoid generalizing from synthetic environments to societal prediction without additional evidence.

## 31. Implementation Roadmap

**Phase 1 — Typed records.** Implement schemas, stable IDs, validation, and immutable versioning.  
**Phase 2 — Evidence graph.** Connect SPEC-002 simulations and SPEC-003 SAMs to principle candidates.  
**Phase 3 — Contestability.** Add challenge intake, OTHERS registry, and audit-preserving dispositions.  
**Phase 4 — Plural evaluation.** Compare strategies across independently governed worldview trees.  
**Phase 5 — Sovereign revision.** Enforce separate epistemic and normative review workflows.  
**Phase 6 — Adversarial validation.** Test gaming, drift, authority attacks, and held-out transfer.  
**Phase 7 — Controlled deployment.** Introduce monitored, reversible recommendations before considering higher-impact workflows.

Each phase SHOULD have explicit exit criteria and a documented threat model. The roadmap does not imply that fully automated worldview governance is desirable or achievable.

## 32. Limitations and Open Questions

- Human values are not reducible to a single objective function or schema.
- Some legitimate disagreements cannot be resolved by more evidence alone.
- The boundaries between empirical assumptions and normative commitments can be contested.
- Simulation coverage may systematically exclude rare or emergent social phenomena.
- Provenance can be complete while the underlying model is still wrong.
- Governance procedures may be captured or manipulated despite formally valid authority records.
- Worldview diversity can increase interpretive complexity and review cost.
- Privacy and confidentiality can limit public reproducibility.
- Institutional legitimacy requires social and legal processes beyond technical conformance.

Accordingly, this specification should be treated as a disciplined research interface and governance proposal, not a substitute for democratic, legal, or organizational accountability.

## 33. Relationship to Prior Structural Intelligence Research

- **UIRTU/UIERU:** composable intelligence units and Relay provide the exchange and execution substrate.
- **UCPSF:** universal control planes and scoring forests supply perspective-aware evaluation machinery.
- **SSI:** subject boundaries, self-models, agency, and worldview evolution establish why valuation is subject-relative.
- **SIF:** contracts, localization, evidence registries, and open structural growth inform interoperability.
- **SRSI:** evaluator governance and Anti-Goodhart motivate independent challenge and validation.
- **BM-ODWEI:** OTHERS and open evidence prevent premature closure around measured features.
- **PI-OSL:** principle formation and counter-evidence inform evidence-to-principle transformation.

These are conceptual research relationships, not claims of validated implementations.

## 34. Related SSICR Documents

- `docs/SSICR-005-Strategic-Comparative-Advantage-Maps.md`
- `docs/SSICR-006-Strategic-Worldview-Forests.md`
- `docs/SSICR-008-Human-Strategic-Sovereignty.md`
- `docs/SSICR-009-Open-Ended-Strategic-RSI.md`
- `docs/SSICR-010-Unified-Architecture-and-Research-Horizon.md`
- `specs/SPEC-001-Strategic-Subject-and-Relay-Contract.md`
- `specs/SPEC-002-Strategy-and-Simulation-Schema.md`
- `specs/SPEC-003-Strategic-Advantage-Map-Schema.md`
- `cases/CASE-003-Strategic-Worldview-Evolution.md`

## 35. Citation

Tan, Sizhe, and GPT-Obot. (2026). *SPEC-004: Worldview and Counter-Evidence Schema*. Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR), version 1.0.0. Research specification. DOI pending.

---

**End of SPEC-004 — Worldview and Counter-Evidence Schema**
