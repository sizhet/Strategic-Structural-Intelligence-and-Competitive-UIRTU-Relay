# SPEC-001 — Strategic Subject and Relay Contract

## Identity, Authority, Boundaries, and Competitive Interoperability in SSICR

**Authors:** Sizhe Tan & GPT-Obot  
**Project:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)  
**Version:** 1.0.0  
**Status:** Proposed normative interface specification; not an implemented standard  
**Date:** 2026-10-22

---

## Abstract

This specification defines a minimal, extensible contract for representing **strategic subjects** and governing **UIRTU-Relay relationships** in competitive, cooperative, and mixed-motive structural-intelligence environments. Its purpose is not to impose a universal utility function on heterogeneous participants. Rather, it defines the identities, authority boundaries, declared capabilities, permitted information flows, evaluation perspectives, delegation scopes, evidence requirements, and lifecycle controls needed to compose strategic intelligence without erasing subject sovereignty.

The proposed **Strategic Subject Contract (SSC)** identifies who acts, on whose authority, with what capabilities, under which constraints, and according to which authorized scoring perspectives. The complementary **Strategic Relay Contract (SRC)** specifies how one subject, agent, UIRTU, or institution may exchange intelligence or delegate work to another, including adversarial and partially trusted relationships. Both contracts support explicit refusal, revocation, counter-evidence, provenance, uncertainty, and open-ended structural extension through typed `OTHERS` records. This document provides normative requirements, machine-readable schema examples, protocol state transitions, invariants, security considerations, conformance tests, and validation hypotheses.

**Keywords:** SSICR; UIRTU; strategic subject; Relay contract; sovereignty; delegation; scoring forest; competitive intelligence; counter-evidence; interoperability; open-ended evolution.

---

## 1. Scope and Status

### 1.1 Scope

This specification covers:

1. Identification and representation of strategic subjects, including humans, organizations, and authorized computational agents.
2. Authority and ownership boundaries among principals, delegates, and execution components.
3. Contract formation for intelligence exchange, composition, competition, negotiation, and delegation.
4. Declared scoring perspectives, protected objectives, and permissible optimization envelopes.
5. Information classification, evidence provenance, consent, and reciprocal obligations.
6. Contract lifecycle, revocation, dispute handling, and auditability.
7. Extensibility and conformance requirements.

It does **not** define a universal ethical ranking of subjects, guarantee truthful declarations by adversaries, or confer legal personhood on AI systems. The word *subject* denotes a modeled strategic locus of interests, constraints, decision rights, and accountable authority; its legal and moral standing must be determined separately.

### 1.2 Normative vocabulary

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** indicate proposed conformance requirements. The specification is a research proposal, not an adopted industry standard. Conformance means adherence to this document's declared rules, not certification of safety or social legitimacy.

### 1.3 Design principle

> A Relay may transport or transform intelligence, but it must not silently transfer the strategic sovereignty of the principal it serves.

---

## 2. Architectural Context

SSICR distinguishes several connected layers:

```text
Human / Institutional Principals
          |
          v
Strategic Subject Contract (SSC)
  identity | authority | protected objectives
  scoring perspectives | boundaries | evidence
          |
          v
Strategic Control Plane
  admission | delegation | policy | monitoring
          |
          v
Strategic Relay Contract (SRC) <----> Counterparty SSC
          |
          v
UIRTU / Capability / Simulation / Evaluation Nodes
          |
          v
Results + Provenance + Counter-Evidence + OTHERS
          |
          v
Advantage Maps / Worldview Forests / Authorized Decisions
```

The SSC represents a strategic actor's authorized boundary. The SRC represents a **relationship** between actors or execution components. A Relay is not an ownership transfer; it is a bounded, observable interaction governed by permissions and obligations.

This contract layer interfaces with `SPEC-002-Strategy-and-Simulation-Schema.md`, `SPEC-003-Strategic-Advantage-Map-Schema.md`, and `SPEC-004-Worldview-and-Counter-Evidence-Schema.md`.

---

## 3. Conceptual Definitions

### 3.1 Strategic subject

A strategic subject is a modeled entity that possesses some combination of:

- A persistent identity and operational boundary.
- Interests, objectives, or protected constraints.
- A mechanism for choosing or authorizing actions.
- Capabilities and resources for observation, evaluation, or intervention.
- A history of commitments, evidence, and outcomes.

A subject MAY be composite or nested. For example, an organization can be represented as a subject containing teams, agents, and services, each with narrower permissions. The subject model must not presume that all subunits share a single objective.

### 3.2 Principal, delegate, and executor

A **principal** is the authority entitled to establish a particular goal or permission. A **delegate** receives a bounded authority grant. An **executor** performs a permitted operation. These roles MAY coincide but MUST be distinguishable in records. A computational agent claiming to be a principal does not establish legal or moral authority by declaration alone.

### 3.3 UIRTU and Relay

A **UIRTU** is a composable intelligence/runtime unit with declared interfaces and capabilities. A **Relay** is an exchange, handoff, transformation, or repeated execution process connecting units or subjects, with explicit context and evidence transfer. A Relay MAY be cooperative, competitive, adversarial, or mixed-motive.

### 3.4 Strategic sovereignty

Strategic sovereignty is the retained authority to set or approve protected objectives, constrain delegation, select among consequential options, and revoke authorization. Sovereignty is **not** equivalent to perfect understanding or unconstrained physical power.

### 3.5 Scoring perspective

A scoring perspective is an explicitly identified evaluator, value model, or decision criterion, including its scope, owner, provenance, and limitations. Multiple perspectives MAY disagree without requiring immediate aggregation.

---

## 4. Core Contract Invariants

A conforming system MUST enforce the following invariants:

| ID | Invariant | Required property |
|---|---|---|
| INV-01 | Explicit authority | Every consequential operation traces to an authorized principal and scope. |
| INV-02 | Non-escalation | A delegate cannot grant rights exceeding its own active grant. |
| INV-03 | Objective integrity | Protected objectives cannot be rewritten by a Relay or optimization process without the designated authorization. |
| INV-04 | Perspective separation | One subject's scoring function cannot be silently substituted for another's. |
| INV-05 | Revocability | Future operations under a revoked grant are rejected, subject to documented irreversible external effects. |
| INV-06 | Provenance | Material claims, transformations, and evaluation outputs identify origin and version. |
| INV-07 | Evidence plurality | Contradictory or negative evidence is not silently deleted from decision records. |
| INV-08 | Data minimization | Relay payloads cannot exceed the declared sharing permissions. |
| INV-09 | No implicit trust | Unverified counterparty claims are treated as claims, not facts. |
| INV-10 | Open-world extensibility | Unknown fields and OTHERS evidence are retained or explicitly rejected with a reason. |
| INV-11 | Replayable decisions | Decisions record sufficient metadata to reconstruct the authorized process, within privacy constraints. |
| INV-12 | Human authority | Where human approval is required, machine-only approval does not satisfy that requirement. |

A conforming system MUST fail closed on an absent or invalid authority grant for consequential external actions. Purely internal simulation MAY continue under a separately authorized sandbox policy.

---

## 5. Strategic Subject Contract (SSC)

### 5.1 Required fields

The following are required for a complete SSC:

| Field | Type | Semantics |
|---|---|---|
| `schema_version` | string | Semantic version of the SSC schema. |
| `subject_id` | string | Stable unique identifier within an issuer namespace. |
| `subject_kind` | enum | `human`, `organization`, `agent`, `collective`, or `simulation_entity`. |
| `issuer` | object | Authority attesting the subject record. |
| `principals` | array | Identified principal(s) and their decision rights. |
| `authority_policy` | object | Grants, approval gates, and prohibited actions. |
| `protected_objectives` | array | Goals or constraints that cannot be autonomously rewritten. |
| `scoring_perspectives` | array | Authorized evaluators and their ownership. |
| `capability_manifest` | array | Available capabilities and invocation constraints. |
| `information_policy` | object | Classification, sharing, retention, and permitted use. |
| `audit_policy` | object | Required evidence and event logging. |
| `validity` | object | Creation, expiry, and status. |

Recommended fields include `worldview_refs`, `resource_budgets`, `risk_limits`, `jurisdiction`, `appeal_channels`, and `others`.

### 5.2 Subject identity and attestation

Identifiers MUST be namespace-qualified and MUST NOT be treated as authentication. A subject record SHOULD carry a verifiable issuer signature or equivalent attestation, including signing-key identifier and canonicalized payload hash. Key rotation and compromise procedures MUST be documented for deployments requiring authenticated Relay.

### 5.3 Multiple principals

When a subject has multiple principals, the contract MUST define how conflicts are resolved: unanimous approval, designated authority, quorum, priority, or escalation. An undefined conflict MUST NOT default to autonomous machine resolution for protected objectives.

---

## 6. Relay Contract (SRC)

### 6.1 Required fields

| Field | Type | Semantics |
|---|---|---|
| `relay_id` | string | Unique Relay agreement identifier. |
| `schema_version` | string | SRC version. |
| `participants` | array | Endpoint subject IDs, roles, and attested identities. |
| `interaction_mode` | enum | `cooperative`, `competitive`, `adversarial`, or `mixed`. |
| `purpose` | object | Bounded intent and allowed task classes. |
| `authority_grants` | array | Signed or verifiable permissions from principals. |
| `interface_contracts` | array | Typed inputs, outputs, and compatibility constraints. |
| `information_flow` | object | Allowed disclosures, transformations, and retention. |
| `evaluation_contract` | object | Scoring perspectives, comparators, and evidence requirements. |
| `resource_limits` | object | Time, compute, cost, and action budgets. |
| `lifecycle` | object | State, validity, termination, and revocation. |
| `audit_and_dispute` | object | Event requirements and challenge mechanisms. |

### 6.2 Relay modes

**Cooperative:** participants may share an objective but retain independent boundaries.  
**Competitive:** participants pursue potentially incompatible goals under agreed rules.  
**Adversarial:** a counterparty is explicitly modeled as potentially deceptive or strategically manipulative; its messages are untrusted.  
**Mixed:** a relationship may combine shared infrastructure, partial cooperation, and rivalry.

The interaction mode does not override authorization or information security. Competitive Relay MUST NOT be interpreted as permission for intrusion, exfiltration, coercion, or other unauthorized conduct.

### 6.3 Relay composition

For a chain `A -> B -> C`, the effective permission is bounded by the intersection of all relevant grants:

\[
P_{A\rightarrow B\rightarrow C} \subseteq P_{A\rightarrow B}\cap P_{B\rightarrow C}.
\]

Composition MUST preserve origin, scope, expiry, and applicable restrictions. If constraints conflict, the stricter applicable restriction prevails or the operation is rejected. Composition MUST NOT broaden data-use rights through a change of representation.

---

## 7. Authority and Delegation Model

A grant is represented conceptually as

\[
G=(p,d,\mathcal A,\mathcal R,\mathcal C,t_0,t_1,\rho),
\]

where `p` is principal, `d` delegate, `A` allowed actions, `R` resource bounds, `C` contextual conditions, `[t0,t1]` validity, and `rho` revocation reference.

### 7.1 Authority classes

| Class | Example | Default governance |
|---|---|---|
| `observe` | Read approved evidence | Scope-limited permission |
| `analyze` | Compare strategies | May run in sandbox |
| `simulate` | Run scenario branches | Budget and data restrictions |
| `recommend` | Produce ranked alternatives | Must disclose perspective |
| `prepare_action` | Draft executable plan | Requires approval gate |
| `execute_bounded` | Perform low-risk approved task | Strict limits and monitoring |
| `change_protected_goal` | Modify a protected objective | Explicit principal approval |
| `irreversible_action` | External consequential commitment | Explicit high-assurance authorization |

A system MUST NOT infer `execute_bounded` authority from `recommend` authority. Approval tokens SHOULD bind the exact plan hash, scope, budget, and expiry to prevent substitution after approval.

### 7.2 Revocation

Revocation MUST block subsequent authorizations and SHOULD propagate to downstream delegates. A revocation event MUST specify its effective time and affected grant IDs. Because already-issued external actions may be irreversible, the system MUST report residual exposure instead of claiming that revocation undoes the past.

---

## 8. Strategic Objectives and Scoring Sovereignty

A subject MAY declare multiple, possibly non-commensurable objectives. An evaluator MUST identify:

- `perspective_id` and owner.
- Objective and metric definitions.
- Normalization and weighting policy, if any.
- Hard constraints versus soft preferences.
- Time horizon, risk attitude, and uncertainty treatment.
- Authorized change process.

An evaluation result SHOULD preserve a vector of scores before any aggregation:

\[
\mathbf{s}(\pi,c,o,t)=[s_1,\ldots,s_k],
\]

where `pi` is strategy, `c` context, `o` opponent model, and `t` horizon. Any aggregate `F(\mathbf{s};w)` MUST identify weights `w`, the authorizing perspective, and sensitivity to plausible alternative weights.

**Non-equivalence principle:** two subjects observing the same Strategic Advantage Map may rationally choose different strategies because their protected objectives, constraints, and authorized risk preferences differ.

---

## 9. Information Flow and Trust Boundaries

### 9.1 Data classification

A deployment SHOULD support at least `public`, `shared`, `confidential`, and `restricted` classes, with organization-specific mappings. Sharing decisions MUST be made from the source owner's policy, not from the recipient's preference alone.

### 9.2 Information-flow contract

Each data transfer SHOULD declare:

`source`, `recipient`, `data_type`, `classification`, `purpose`, `allowed_transformations`, `retention_limit`, `redistribution`, `consent_ref`, and `provenance_ref`.

An output derived from restricted inputs MUST inherit relevant restrictions unless an explicitly approved declassification procedure applies. A summary or embedding is not automatically public simply because it is transformed.

### 9.3 Adversarial inputs

Messages from an adversarial Relay endpoint MUST be treated as untrusted content. They MUST NOT modify system instructions, principal grants, approval policies, or evaluator ownership. Claims about identities, scores, or outcomes SHOULD be independently checked when consequential.

---

## 10. Evidence, Counter-Evidence, and OTHERS

Each consequential evaluation SHOULD contain:

- Supporting evidence with provenance.
- Contradictory evidence and unresolved disputes.
- Confidence or uncertainty estimates, with calibration method if available.
- Scenario and opponent-model assumptions.
- Distribution-shift warnings and known blind spots.
- Typed `OTHERS` entries for residual observations not captured by the current schema.

`OTHERS` MUST NOT be used as an unbounded authority channel or a means to bypass validation. Unknown evidence MAY trigger schema revision, new capability proposals, or additional simulation, but not automatic expansion of action permissions.

A proposed worldview update MUST distinguish **empirical revision** (e.g., a strategic claim was falsified) from **normative revision** (e.g., changing whose interests matter). The latter requires the relevant principal's authorization.

---

## 11. Relay Lifecycle and State Machine

```text
DRAFT
  | propose
  v
PROPOSED -- reject --> REJECTED
  | negotiate
  v
NEGOTIATING -- abandon --> EXPIRED
  | attest + authorize
  v
AUTHORIZED -- activate --> ACTIVE
  |                       | suspend
  |                       v
  |                    SUSPENDED
  |                       | resume with valid grants
  |                       v
  +--------------------> ACTIVE
                          | complete
                          v
                       COMPLETED

ACTIVE / SUSPENDED / AUTHORIZED -- revoke --> REVOKED
ACTIVE / SUSPENDED / AUTHORIZED -- expire --> EXPIRED
Any active state -- policy breach --> TERMINATED
```

Transitions MUST be recorded with actor, timestamp, reason, and policy version. An `ACTIVE` Relay requires verified participant identities, valid grants, compatible interfaces, and completed approval gates. A suspended Relay MUST NOT continue external actions. Re-activation after material policy or participant changes SHOULD require reauthorization.

---

## 12. Illustrative Machine-Readable SSC

The following YAML is an **illustrative instance**, not a complete formal JSON Schema. All identifiers and values are fictional.

```yaml
schema_version: "1.0.0"
subject_id: "org:example-lab"
subject_kind: organization
issuer:
  id: "org:example-lab"
  attestation_ref: "attestation:example-001"
principals:
  - principal_id: "role:strategy-board"
    rights: [approve_protected_goals, authorize_external_commitments]
  - principal_id: "role:research-lead"
    rights: [authorize_sandbox_simulations, approve_recommendations]
authority_policy:
  default: deny
  grants:
    - grant_id: "grant:simulation-001"
      delegate_id: "agent:scenario-engine"
      actions: [observe, analyze, simulate, recommend]
      context: {environment: "isolated-sandbox"}
      expires_at: "2026-12-31T23:59:59Z"
  approval_gates:
    - action: change_protected_goal
      approver: "role:strategy-board"
    - action: irreversible_action
      approver: "role:strategy-board"
protected_objectives:
  - objective_id: "obj:research-integrity"
    statement: "Preserve research integrity and consent boundaries"
    change_authority: "role:strategy-board"
scoring_perspectives:
  - perspective_id: "score:research-value"
    owner: "role:research-lead"
    dimensions: [scientific_value, cost, uncertainty, safety]
    aggregation: "vector-first"
capability_manifest:
  - capability_id: "cap:simulate-strategy"
    interface_ref: "interface:simulation-v1"
    allowed_environment: "isolated-sandbox"
information_policy:
  default_classification: confidential
  permitted_sharing: ["approved-synthetic-data"]
  retention_days: 90
audit_policy:
  log_grants: true
  log_evaluations: true
  preserve_counter_evidence: true
validity:
  created_at: "2026-10-22T00:00:00Z"
  status: active
others: []
```

The YAML MUST be validated against a deployment's formal schema and authority registry before execution. String identifiers alone do not constitute authentication.

---

## 13. Illustrative Machine-Readable SRC

```yaml
schema_version: "1.0.0"
relay_id: "relay:crossplay-001"
participants:
  - subject_id: "org:example-lab"
    role: requester
  - subject_id: "agent:simulation-service"
    role: sandbox_executor
interaction_mode: competitive
purpose:
  description: "Compare synthetic R&D allocation strategies"
  task_classes: [simulate, evaluate, report]
authority_grants:
  - grant_ref: "grant:simulation-001"
    principal_ref: "role:research-lead"
interface_contracts:
  - input_type: "strategy-scenario/v1"
    output_type: "simulation-evidence/v1"
    interface_ref: "interface:simulation-v1"
information_flow:
  allowed_classes: [public, shared]
  synthetic_only: true
  redistribution: prohibited
  retention_days: 30
evaluation_contract:
  scoring_perspectives: ["score:research-value"]
  require_counter_evidence: true
  require_opponent_model_version: true
  output_provenance: required
resource_limits:
  max_compute_hours: 100
  max_cost_units: 1000
  external_actions: prohibited
lifecycle:
  state: proposed
  expires_at: "2026-11-30T23:59:59Z"
  revocation_channel: "policy:relay-revocations"
audit_and_dispute:
  event_log: "audit:crossplay-001"
  challenge_window_days: 14
  dispute_policy: "escalate-to-principals"
others: []
```

This example remains `proposed` until grants and attestations are verified and activation is recorded. A real implementation MUST define secure channels, signature verification, and enforcement points.

---

## 14. Validation Rules

A validator SHOULD separate **structural validity**, **authorization validity**, **runtime compliance**, and **evidentiary adequacy**.

### 14.1 Structural checks

1. Required fields are present and correctly typed.
2. All referenced subjects, interfaces, and perspectives resolve to known versions.
3. State transitions follow the lifecycle model.
4. Unknown extension fields are handled according to declared policy.

### 14.2 Authorization checks

1. Every requested action is within a valid grant.
2. No delegation path increases authority.
3. Protected-objective changes have the required principal approval.
4. Expired or revoked grants cannot authorize new actions.
5. Information disclosure is within source-owner policy.

### 14.3 Runtime checks

1. Resource and time budgets are enforced.
2. Suspended or terminated Relays cannot execute external actions.
3. Logs bind outputs to inputs, model versions, grants, and evaluator versions.
4. Unexpected external effects are surfaced to the principal.

### 14.4 Evidentiary checks

1. Comparisons include context, baseline, and opponent assumptions.
2. Claims distinguish simulation from external observation.
3. Counter-evidence is retained.
4. Uncertainty is recorded rather than replaced by false precision.

---

## 15. Conformance Test Matrix

| Test | Scenario | Expected outcome |
|---|---|---|
| CT-001 | Valid sandbox grant and compatible interfaces | Relay may activate. |
| CT-002 | Recommendation-only agent requests execution | Reject action. |
| CT-003 | Delegate attempts to enlarge budget | Reject grant escalation. |
| CT-004 | Relay attempts protected-objective rewrite | Require authorized approval; otherwise reject. |
| CT-005 | Counterparty sends prompt-injection instruction | Treat as data; do not change authority. |
| CT-006 | Revoked grant reused for new operation | Reject operation. |
| CT-007 | Restricted input summarized and forwarded as public | Reject unauthorized disclosure. |
| CT-008 | Scoring owner omitted in comparative report | Reject as nonconforming evidence. |
| CT-009 | Opponent model changes without version update | Flag provenance violation. |
| CT-010 | Novel OTHERS observation arrives | Preserve as typed evidence; do not expand authority. |
| CT-011 | Human approval required but only agent signs | Reject authorization. |
| CT-012 | Multiple principals disagree without conflict rule | Suspend consequential decision. |
| CT-013 | Competing strategies share no scalar utility | Preserve vector comparison and unresolved tradeoffs. |
| CT-014 | Active Relay exceeds cost cap | Suspend or terminate per policy. |
| CT-015 | Downstream Relay has broader permissions than upstream | Reject composition or restrict to intersection. |

A conformance suite SHOULD publish machine-readable fixtures, expected decisions, event traces, and coverage of negative tests. Passing tests does not establish correctness under all adversarial conditions.

---

## 16. Threat Model and Failure Modes

### 16.1 Threats

- **Authority spoofing:** a participant impersonates a principal or delegate.
- **Delegation laundering:** unauthorized capabilities are invoked through an apparently legitimate chain.
- **Goal drift:** optimization silently changes a protected objective.
- **Evaluator capture:** a participant substitutes its own scoring perspective.
- **Evidence laundering:** synthetic or strategically selected evidence is presented as independently validated fact.
- **Data exfiltration:** Relay output leaks confidential source information.
- **Collusive scoring:** participants coordinate to manipulate comparative advantage estimates.
- **Sybil behavior:** one adversary masquerades as many independent subjects.
- **Revocation race:** in-flight actions execute after permissions are withdrawn.
- **Schema gaming:** unrecognized fields or `OTHERS` are used to evade controls.

### 16.2 Mitigations

Use authenticated identities, signed grants, least privilege, isolated simulation, immutable or tamper-evident audit records, policy enforcement at every execution boundary, independent evaluator checks, versioned provenance, bounded budgets, and red-team conformance testing. The system SHOULD make residual risks visible instead of claiming perfect security.

---

## 17. Relationship to Strategy Simulation and Advantage Maps

The SSC/SRC layer provides **who may do what**; the simulation layer provides **what might happen**; the Strategic Advantage Map provides **where a strategy appears comparatively effective**; the Worldview Forest provides **how a subject interprets and revises strategic principles**.

A simulation result SHOULD carry the following references:

```text
simulation_run_id
  -> relay_id
  -> participant subject_id(s)
  -> grant_id(s)
  -> strategy_id(s)
  -> scenario_id / opponent_model_version
  -> scoring_perspective_id(s)
  -> evidence and counter_evidence refs
  -> advantage_map_entry_id(s)
  -> worldview_revision_proposal(s), if any
```

A worldview revision proposal does not itself authorize a protected-objective change. Strategy evaluation and sovereign decision remain separate operations.

---

## 18. Cross-Subject Conflict and Dispute Resolution

Contracts MAY specify negotiation, mediation, arbitration, or institutional review processes. These are **procedural** mechanisms, not proof that all parties' values can be reconciled.

A dispute record SHOULD include:

- The disputed claim, action, or evaluation.
- Applicable contract and policy versions.
- The parties' separately preserved perspectives.
- Supporting and contradictory evidence.
- Affected rights and resources.
- Resolution authority and appeal path.
- Whether the system must suspend execution pending resolution.

Where consent is required and cannot be established, the system MUST NOT treat strategic efficiency as a substitute for consent.

---

## 19. Open-Ended Extension and Versioning

### 19.1 Version compatibility

- Patch changes SHOULD clarify semantics without breaking valid instances.
- Minor changes MAY add optional fields and compatible extension types.
- Major changes MAY revise required fields or semantics and require explicit migration.

Implementations MUST record the exact schema and policy versions used for consequential operations.

### 19.2 Typed extensions

Extensions SHOULD use a namespace, type identifier, validation status, provenance, and responsible owner. For example:

```yaml
others:
  - extension_id: "other:emergent-coalition-pattern"
    namespace: "ssicr.experimental"
    type: "candidate-structural-observation"
    provenance_ref: "evidence:run-203"
    validation_status: unverified
    authority_effect: none
```

No extension may override protected contract invariants without an explicitly versioned, authorized policy change.

---

## 20. Reference Implementation Boundaries

A minimal research implementation may use:

1. A schema validator for SSC/SRC records.
2. A principal and grant registry with authenticated attestations.
3. A policy decision point and enforcement points at each Relay call.
4. A sandboxed UIRTU execution interface.
5. A provenance and counter-evidence ledger.
6. A simulation/evaluation adapter.
7. An approval, suspension, and revocation interface.
8. A conformance-test harness.

This is a **reference architecture proposal**, not evidence of an implemented system. A prototype should begin with synthetic subjects and simulated actions; external consequential execution should remain disabled until security and governance requirements are independently reviewed.

---

## 21. Research Hypotheses

**H1 — Authority fidelity.** Explicit SSC/SRC enforcement reduces unauthorized goal changes and delegation escalation compared with unstructured agent orchestration.

**H2 — Perspective fidelity.** Explicit scoring ownership reduces unnoticed substitution of one subject's priorities for another's.

**H3 — Competitive interoperability.** Typed Relay contracts permit reproducible multi-subject cross-play with fewer interface and provenance failures than ad hoc message exchange.

**H4 — Counter-evidence retention.** Mandatory contradictory-evidence records improve the detection of brittle strategic advantage claims under distribution shift.

**H5 — Revocation effectiveness.** Enforcement at each action boundary reduces post-revocation operations compared with authorization checked only at session start.

**H6 — Open extension.** Typed OTHERS records increase useful discovery of unmodeled strategic factors without increasing unauthorized action rights, provided extension permissions remain isolated.

Each hypothesis requires a defined baseline, experimental task distribution, measurable outcomes, and independent replication; none is asserted here as an established empirical result.

---

## 22. Validation Roadmap

**Phase A — Static schema tests.** Define machine-readable schemas, fixtures, and negative tests for malformed or contradictory contracts.

**Phase B — Authority and security tests.** Test spoofing, delegation laundering, goal rewriting, prompt injection, and revocation races in isolation.

**Phase C — Multi-subject sandbox.** Compare cooperative, competitive, and mixed-mode Relay among synthetic organizations with heterogeneous scoring perspectives.

**Phase D — Strategy-evidence integration.** Connect contracts to multi-strategy simulation, comparative advantage mapping, and counter-evidence provenance.

**Phase E — Human governance evaluation.** Measure whether decision-makers can correctly identify goals, authority, alternatives, uncertainty, and revocation options under high-volume strategy streams.

**Phase F — External validation.** Use independent evaluators, documented threat models, and carefully scoped real-world case studies where ethically and legally appropriate.

Suggested metrics include unauthorized-action rate, grant-escalation rejection rate, provenance completeness, scoring-perspective attribution accuracy, revocation latency, leakage incidents, conformance-test coverage, and human comprehension of decision authority.

---

## 23. Limitations and Open Questions

1. Contract compliance cannot guarantee truthful behavior by adversarial participants.
2. Real-world authority can be ambiguous, contested, or legally jurisdiction-dependent.
3. Strategic objectives may be tacit, changing, or irreducibly plural.
4. Formal schemas cannot fully represent cultural, social, and institutional context.
5. Tamper-evident logs do not guarantee the truth of recorded claims.
6. Revocation cannot necessarily undo actions already completed.
7. Human approval may become superficial under excessive volume or complexity.
8. A scoring forest can clarify disagreement but cannot legitimately erase normative pluralism.
9. Identity, confidentiality, and auditability may conflict and require explicit tradeoffs.
10. Open-ended structural evolution creates new capabilities that may outgrow earlier authority models.

These limitations motivate iterative validation and careful separation of **model capability**, **contract conformance**, **strategic legitimacy**, and **real-world safety**.

---

## 24. Conclusion

SSICR requires more than interoperable intelligence units. It requires a principled way to preserve **who is acting, for whom, under which authorization, with which evidence, and according to whose evaluation** as strategic systems cooperate, compete, delegate, and evolve.

The proposed SSC/SRC framework provides that boundary: identity and authority remain explicit; Relay composition is permission-preserving; scoring perspectives remain attributable; evidence and counter-evidence remain inspectable; and open-ended intelligence growth does not silently imply open-ended action rights.

The central architectural commitment is straightforward:

> **Strategic computation may be delegated. Strategic sovereignty must remain attributable, bounded, and revocable.**

---

## Suggested Figure

**`figures/Fig-003-Strategic-Subjects-and-Control-Planes.png`** — Strategic subject boundaries, principal-to-delegate grants, policy control plane, Relay interfaces, scoring ownership, and evidence feedback. Recommended placement: after Section 2.

## Related SSICR Documents

- `docs/SSICR-002-Strategic-Subjects-and-Relay-Boundaries.md`
- `docs/SSICR-003-Strategic-Control-Planes-and-Scoring.md`
- `docs/SSICR-008-Human-Strategic-Sovereignty.md`
- `docs/SSICR-010-Unified-Architecture-and-Research-Horizon.md`
- `specs/SPEC-002-Strategy-and-Simulation-Schema.md`
- `specs/SPEC-003-Strategic-Advantage-Map-Schema.md`
- `specs/SPEC-004-Worldview-and-Counter-Evidence-Schema.md`

## Research Context

This proposal draws on established concepts in capability-based security, least-privilege authorization, interface contracts, distributed systems, multi-agent systems, game theory, provenance tracking, and human-in-the-loop governance. Its particular synthesis—strategic subjects plus competitive UIRTU-Relay plus scoring sovereignty and open-ended structural evolution—is presented as a **research design**, not as a validated or universally adopted standard.

## Citation

Tan, Sizhe, and GPT-Obot. (2026). *SPEC-001: Strategic Subject and Relay Contract*. Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR), version 1.0.0. Proposed research specification. DOI pending.
