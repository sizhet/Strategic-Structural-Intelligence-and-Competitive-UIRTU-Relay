# SSICR-002 — Strategic Subjects and Relay Boundaries

**Project:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)  
**Subtitle:** From Subject Sovereignty to Cross-Subject Strategic Contracts  
**Authors:** Sizhe Tan & GPT-Obot  
**Version:** 1.0.0  
**Status:** Research framework and testable design proposals  
**Companion:** SSICR-001 — From Cooperative to Strategic Relay

## Abstract

Competitive and adversarial UIRTU-Relay systems require a distinction between an intelligence unit, an executing organization, and a strategic subject. A strategic subject is not defined by its number of agents or its computational capacity, but by a bounded locus of objectives, authorization, valuation, and accountability. This paper proposes an explicit subject model, six complementary relay boundaries, a cross-subject contract, and a simulation-oriented treatment of incomplete and evolving subject descriptions. It links Subjective Structural Intelligence (SSI), Universal Control Planes and Scoring Folding (UCPSF), and the Structural Intelligence Framework (SIF) to multi-subject strategic simulation. The proposal distinguishes empirical model revision from normative goal authorization, and makes uncertainty, provenance, counter-evidence, and withdrawal first-class elements of strategic relay. These are architectural hypotheses, not claims of validated predictive fidelity.

**Keywords:** strategic subject; UIRTU; relay boundary; scoring sovereignty; multi-agent systems; strategic simulation; trust; counter-evidence; open subject modeling; human governance

---

## 1. Motivation: Why Relay Requires Subject Boundaries

In cooperative UIRTU-Relay, participants can often be modeled as components pursuing a shared task. Competitive and adversarial settings break that simplifying assumption. A relay provider may also be a market competitor; a research consortium may share infrastructure while retaining proprietary goals; a regulator may influence multiple organizations without owning their strategies.

The resulting question is not only **which unit can perform a task?** It is also **whose objective does the task serve, under whose authorization, and with which rights over information, action, learning, and evaluation?**

A large collection of agents is not necessarily an independent strategic subject. Conversely, a small unit can act as a strategic subject if it possesses appropriately delegated objectives and decision rights. Distinguishing these cases prevents scale from being mistaken for sovereignty.

## 2. Basic Ontology

### 2.1 Intelligence unit

An **intelligence unit** is a bounded functional component with inputs, outputs, internal state or procedures, and an interface for invocation or composition. A UIRTU is treated here as a candidate unit of intelligence evolution and relay. The acronym's existing project definition remains authoritative; this paper does not redefine it.

### 2.2 RSI subsystem

An **RSI subsystem** is a recursive-improvement process, potentially implemented by multiple agents, tools, evaluators, and memory structures. It can be represented as a UIRTU-like relay participant when it has explicit contracts, state, evaluation, and feedback. The correspondence is conditional, not an identity: some RSI processes lack an independent relay boundary.

### 2.3 Strategic subject

A **strategic subject** is an identifiable locus of strategic objectives, valuation, delegated authority, and accountability, capable of selecting or authorizing actions over a time horizon. It may be a human, an organization, or an AI system operating under explicitly delegated governance. Modeling an AI as a strategic subject does not establish legal personhood, moral status, or unlimited autonomous authority.

### 2.4 Relay relationship

A **relay relationship** is a structured transfer or coordination of capability, work, evidence, information, or control between units or subjects. Its relational state can be cooperative, competitive, adversarial, mixed-motive, or dynamically changing.

### 2.5 Institution

An **institution** is a relatively persistent rule or governance structure constraining or enabling multiple subjects. Institutions can be exogenous to a simulation or endogenous outcomes of repeated interactions; these two cases must be labeled separately.

## 3. Subject Model: Identity, Objectives, Authority, and History

For simulation and interoperability, represent subject *i* at time *t* as:

\[
S_i(t) = \langle I_i, O_i, V_i, A_i, R_i, M_i, H_i, B_i, U_i \rangle_t
\]

where:

- **I — Identity:** persistent identifiers, organizational membership, and provenance.
- **O — Objectives:** explicit strategic goals and target horizons.
- **V — Valuation:** scoring perspectives, priorities, and trade-off rules.
- **A — Authority:** permissions to select, delegate, commit, or terminate actions.
- **R — Resources:** budgets, tools, compute, information access, and capabilities.
- **M — Models:** beliefs about the environment, other subjects, and causal mechanisms.
- **H — History:** past decisions, commitments, evidence, and adaptations.
- **B — Boundaries:** constraints on information, action, learning, and governance.
- **U — Uncertainty:** incomplete knowledge, model ambiguity, and unresolved residuals.

This is a modeling schema rather than a universal psychological or sociological description. Different applications may omit, refine, or partition fields, but omissions should be declared.

### 3.1 Historical identity and continuity

A subject's objectives and models may change while its identity remains continuous. Simulations must record which changes represent ordinary learning, authorized organizational reconfiguration, or the creation of a genuinely new subject. A new agent process or new model checkpoint alone does not necessarily imply a new strategic subject.

### 3.2 Scoring sovereignty

**Scoring sovereignty** means that the subject's authorized valuation and objectives are not silently replaced by another relay participant's scoring function. Shared evaluation metrics may be negotiated; they do not erase differences in underlying interests.

A practical distinction is essential:

- **Epistemic update:** evidence changes beliefs or estimated effectiveness.
- **Normative change:** goals, value priorities, or permitted actions change.

An optimizer may propose either; only authorized governance may enact normative changes.

## 4. Six Strategic Relay Boundaries

| Boundary | Core question | Minimal control |
|---|---|---|
| Identity | Who is acting, for whom? | Authenticated principals, provenance |
| Objective | Whose goal and scoring rule governs? | Declared objectives, approval rules |
| Information | What data and context may cross? | Access scope, minimization, retention |
| Action | What may the receiving unit do? | Capability permissions, spending limits, termination |
| Learning | What may be retained or used for adaptation? | Training consent, derivative-use restrictions |
| Governance | Who audits, disputes, revokes, or intervenes? | Logs, oversight, escalation, revocation |

Boundaries can be nested. An internal organizational relay may cross an information boundary without crossing objective sovereignty. A service contract between competitors crosses organizational boundaries but need not transfer strategic control.

### 4.1 Trust is scoped, not binary

A relay partner may be trusted for computation but not for training on supplied data; trusted for a limited task but not for onward delegation; trusted for measurement but not for final decisions. Trust should therefore be represented by explicit scopes and evidence rather than a single global score.

### 4.2 Boundary crossings are events

Every cross-subject relay should produce an auditable event containing the sender, recipient, purpose, contract version, permissions, inputs and outputs references, observed outcome, and exception state. Sensitive payloads need not be copied into logs; references, hashes, and access-controlled evidence may suffice.

---

![Fig-003-Strategic-Subjects-and-Control-Planes.png](../figures/Fig-003-Strategic-Subjects-and-Control-Planes.png)

---

## 5. Cross-Subject Strategic Relay Contract

A minimal contract should specify:

1. **Parties and roles:** principal, provider, beneficiary, evaluator, and overseer, when distinct.
2. **Purpose:** task scope and allowed strategic use.
3. **Interface:** input/output types, units, constraints, and quality expectations.
4. **Objective relationship:** aligned, partially aligned, competitive, or unknown.
5. **Data policy:** visibility, retention, derivative rights, and permitted learning.
6. **Action policy:** tools, external effects, budgets, and human approval thresholds.
7. **Evaluation:** metrics, provenance, uncertainty, and dispute procedure.
8. **Termination:** expiry, revocation, rollback, and handling of residual obligations.
9. **Adaptation:** what changes are permitted without renegotiation.
10. **Evidence:** logs, attestations, counter-evidence, and audit access.

**Illustrative contract fragment (not a finalized normative schema):**

```yaml
contract_id: relay-contract-example-001
version: 0.1
principal_subject: org-A
provider_subject: org-B
purpose: evaluate_candidate_research_designs
objective_alignment: mixed_motive
input_policy:
  classification: confidential
  onward_sharing: prohibited
  training_use: prohibited
action_policy:
  external_execution: prohibited
  max_compute_budget_units: 100
  human_approval_required_for: [publication, spending, deployment]
evaluation:
  metric_set: research-quality-v1
  evidence_required: true
  uncertainty_required: true
governance:
  revocable: true
  audit_log: required
  dispute_route: human_review
```

A contract can fail despite valid syntax: conflicting incentives, incomplete observability, and dishonest behavior remain possible. Enforcement and verification are separate research problems.

## 6. Strategic Relations Across Subject Boundaries

Cooperation and competition are not mutually exclusive attributes of entire organizations. They may vary by task, asset, time, and relationship.

For two subjects *i* and *j*, let:

\[
R_{ij}(t, c) \in \{\text{cooperative},\text{competitive},\text{adversarial},\text{mixed},\text{undetermined}\}
\]

where *c* is a specified context. This categorical representation is intentionally coarse; richer models may represent continuous alignment, asymmetric dependence, bargaining power, and uncertainty.

A useful research question is whether subject-level contracts can preserve reliable cooperative sub-relays even when the encompassing strategic relationship is competitive.

## 7. Open-Subject Modeling and the OTHERS Evidence Space

Social and organizational subjects cannot be completely parameterized in advance. Their objectives may be partially hidden, their internal structure may change, and they may learn from the interaction being simulated.

We propose **Open-Subject Modeling**: begin with explicit, limited models; record unmodeled phenomena as evidence; and introduce new parameters or structural hypotheses only when justified.

A subject model may include:

\[
\text{Subject Evidence} = \text{Modeled Features} + \text{Residual / OTHERS Evidence}
\]

This expression is conceptual, not an additive physical law. OTHERS is a governed evidence space, **not** an unconstrained explanation for model failures.

For each residual, record: observation, source, confidence, competing explanations, proposed structural revision, and out-of-sample test. If a revision improves fit only on the original simulation data, it should not be promoted as a validated principle.

### 7.1 Three kinds of evolution

- **Parameter evolution:** budgets, capabilities, preferences, or estimated risks change.
- **Structural evolution:** organizational units, interfaces, and relay graphs change.
- **Worldview evolution:** causal assumptions, strategic principles, and scenario interpretations change.

These processes should be logged separately, because they imply different validation requirements and different governance permissions.

## 8. Strategic Control Planes and Multiple Scoring Perspectives

A strategic subject may maintain its own control plane and scoring forest. Cross-subject systems therefore do not necessarily possess one legitimate global utility function.

For strategy \(\pi_i\) under context \(c\), opponent configuration \(\Pi_{-i}\), and horizon \(h\), write:

\[
J_i(\pi_i \mid c, \Pi_{-i}, h; V_i)
\]

The function depends on the subject's valuation \(V_i\). A strategy can score well for one subject and poorly for another without either score being mathematically erroneous.

For evaluation, distinguish:

- **Subject utility:** effectiveness relative to the subject's authorized objectives.
- **System effects:** externalities, resource use, resilience, and institutional outcomes.
- **Governance constraints:** actions that remain prohibited regardless of utility.

An aggregate score, if used, must document whose perspective it represents and how trade-offs were authorized.

## 9. Relay Security, Deception, and Counter-Evidence

Competitive relay introduces risks absent from idealized cooperation: strategic misrepresentation, data leakage, hidden dependency, metric gaming, and unauthorized delegation. The proposed framework addresses these through bounded permissions, independent evaluation, counter-evidence, and revocation.

The research focus here is defensive: preserving subject boundaries and testing resilience, not prescribing offensive exploitation of other participants.

**Validation questions:**

- Does the relay honor data-use and onward-delegation constraints?
- Can the principal detect unexplained changes in task scope or scoring?
- Can independent evaluators reproduce critical results?
- Can the system terminate a compromised or misaligned relay without cascading failure?
- Does a claimed improvement persist under alternative opponent models and simulator assumptions?

## 10. From Subject Models to Strategic Advantage Maps

A Strategic Advantage Map should preserve the context and subject perspective behind every comparative result. A record should minimally bind:

\[
(\text{subject},\text{strategy},\text{context},\text{opponents},\text{horizon},\text{metric},\text{evidence})
\]

A claim such as “distributed relay is superior” is incomplete without these qualifiers. Advantage regions should be accompanied by failure boundaries, confidence, and counter-evidence.

Strategic Worldview Forests can then organize recurring principles across contexts. The map supplies evidence; the worldview supplies an interpreted, revisable orientation. Neither should silently override the subject's authorized goals.

## 11. Reference Simulation: Competing AI R&D Organizations

Consider three hypothetical organizations:

- **A:** high compute budget, centralized research management.
- **B:** moderate compute budget, modular distributed research relay.
- **C:** limited compute budget, selective external collaboration.

Each has multiple RSI/UIRTU subsystems. They compete for research outcomes while potentially sharing benchmark standards or infrastructure. A separate governance actor imposes data and deployment constraints.

**Controlled factors:** compute budget, collaboration policy, relay topology, opponent behavior, task distribution, and strategic horizon.

**Measured outcomes:** research quality, compute efficiency, reproducibility, robustness to opponent adaptation, contract violations, and time to validated improvement.

**Baselines:** fixed organization policies, fixed relay topology, and nonadaptive opponent models.

**Experimental variations:** adaptive strategy selection, adaptive relay structure, and open-subject model updates.

This case is a proposal for reproducible experiments, not an empirical result. All reported improvements must be compared against matched budgets and held-out scenarios.

## 12. Testable Hypotheses

**H1 — Boundary Integrity:** Explicit relay contracts reduce unauthorized cross-subject information or action events compared with informal delegation under matched task conditions.

**H2 — Perspective Preservation:** Subject-specific scoring improves the traceability of strategic trade-offs compared with a single undisclosed aggregate score.

**H3 — Open-Subject Benefit:** Evidence-governed model revision improves held-out predictive or decision performance in selected nonstationary scenarios compared with fixed-parameter models.

**H4 — Adaptive Relay Benefit:** Under some dynamic competitive conditions, subject-aware relay adaptation improves robustness or efficiency relative to static topologies, after accounting for coordination costs.

**H5 — Governance Compatibility:** Human approval and revocation controls can preserve strategic authorization while permitting high-volume automated simulation, at measurable latency and compute cost.

These are falsifiable hypotheses; null and negative outcomes should be retained.

## 13. Validation Protocol and Failure Modes

A credible evaluation program should include:

1. **Formal checks:** schema conformance, permission checks, contract invariants, and audit completeness.
2. **Controlled simulation:** seeded scenarios with declared opponent models and matched compute budgets.
3. **Adversarial stress tests:** defensive tests for boundary violations, model exploitation, and strategic misalignment.
4. **Model diversity:** multiple simulator assumptions and opponent populations.
5. **Held-out evaluation:** new scenarios and independent evidence where available.
6. **Human oversight studies:** measure comprehensibility, decision quality, approval burden, and ability to detect failures.

Important failure modes include simulator overfitting, hidden value aggregation, goal drift, identity confusion, strategic deception, spurious OTHERS explanations, and unwarranted claims about real social systems.

Simulation success does not by itself establish predictive validity in actual markets, governments, or societies.

## 14. Connections to the Structural Intelligence Research Program

- **UIERU / UIRTU:** modular intelligence units, evolution, and relay composition.
- **SSI:** subject boundaries, historical identity, scoring sovereignty, and worldview formation.
- **UCPSF:** control planes, scoring forests, perspective-aware optimization, and structural selection.
- **SIF:** contracts, universal naming and relay, dual maps, precedent registry, and adversarial sandbox.
- **Structural RSI:** evaluator governance, feedback loops, and structural self-improvement.
- **BM-ODWEI:** OTHERS, counter-evidence provenance, and open evidence growth.
- **PI-OSL:** evidence-to-principle learning and revisable structural knowledge.

The distinctive contribution proposed here is to make **cross-subject boundaries and strategic authority** explicit primitives of competitive relay and simulation.

## 15. Open Questions and Future Work

1. When does a delegated AI system qualify as a distinct strategic subject rather than an organizational subsystem?
2. How should mixed-motive alignment be represented without reducing all values to a single scalar?
3. How can a contract be verified when one party's objectives or internal learning process are partially hidden?
4. What forms of model revision are justified by residual evidence, and which merely overfit a simulator?
5. How should strategic subjects negotiate shared standards while preserving scoring sovereignty?
6. Can strategic advantage maps remain useful when opponents deliberately change their policies in response to published maps?
7. What minimum provenance and audit guarantees are required for human strategic oversight at AI simulation speed?
8. How should institutions and collective-action rules emerge in simulation without being mistaken for empirically validated social laws?

## 16. Conclusion

Competitive UIRTU-Relay requires more than a larger collection of cooperating intelligence units. It requires an explicit account of **who owns objectives, who authorizes actions, what crosses subject boundaries, and how evidence changes strategic beliefs without silently changing strategic sovereignty**.

The proposed strategic-subject model, six relay boundaries, cross-subject contract, and open-subject evidence process provide a research architecture for that transition. Together they prepare the ground for large-scale multi-strategy simulation, context-dependent Strategic Advantage Maps, and evolving Strategic Worldview Forests under human governance.

The guiding principle is straightforward: **relay may cross subject boundaries; strategic sovereignty must not transfer by accident.**

---

## Research and Citation Note

This manuscript proposes conceptual definitions, architecture, and testable hypotheses. It does not report completed experiments or establish priority over existing work in multi-agent systems, game theory, agent-based modeling, distributed authorization, or AI governance. Future revisions should include a verified bibliography and comparative prior-art review before making claims of novelty.

**Suggested citation:** Tan, S., & GPT-Obot. (2026). *SSICR-002: Strategic Subjects and Relay Boundaries*. Strategic Structural Intelligence and Competitive UIRTU-Relay, version 1.0.0. DOI to be assigned upon archival release.
