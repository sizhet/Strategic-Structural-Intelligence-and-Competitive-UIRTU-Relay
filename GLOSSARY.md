# GLOSSARY — Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)

**Authors:** Sizhe Tan & GPT-Obot  
**Version:** 1.0.0  
**Status:** Research terminology and proposed operational definitions  
**Date:** 2026-10-22

---

## Purpose and Conventions

This glossary provides a common vocabulary for the ten SSICR research papers, four technical specifications, and three case studies. Definitions are **proposed research constructs**, not claims that a universal scientific consensus or validated implementation already exists. Terms from established fields (such as agent-based modeling and game theory) are identified as methodological foundations rather than SSICR inventions.

**Terminology conventions:** A *subject* owns or legitimately represents goals and decision authority; a *strategy* specifies conditional choices; a *Relay* mediates exchange, delegation, or interaction; a *simulation* explores consequences under explicit assumptions; a *map* summarizes comparative evidence; a *worldview* organizes principles and valuations. None of these objects automatically confers real-world authorization.

## A. Foundational Structural Intelligence

### Structural Intelligence (SI)
An approach to intelligence that explicitly represents and evolves reusable capabilities, relationships, decision structures, evidence, and governance mechanisms rather than relying exclusively on implicit model parameters or isolated responses.

### UIRTU-Relay
A compositional intelligence-unit and Relay framework referenced by the SSICR research program. In SSICR, its principal extension is to strategic interactions among distinct subjects, including cooperation, competition, adversarial behavior, and mixed motives. The precise unit semantics are governed by the underlying UIRTU work; SSICR does not silently redefine them.

### Intelligence Unit
A bounded capability or computational component that may be composed, invoked, evaluated, and revised under applicable contracts.

### Relay
A structured mechanism by which subjects or intelligence units exchange information, delegate tasks, coordinate, compete, or pass outputs across boundaries. A Relay is not synonymous with unrestricted sharing.

### Relay Contract
An explicit description of participants, permitted interactions, inputs and outputs, resources, confidentiality, evidence, termination, and authority. See [SPEC-001](specs/SPEC-001-Strategic-Subject-and-Relay-Contract.md).

### Structural Composition
The construction of a higher-level capability or process from multiple bounded units and their relationships, preserving enough interface information for testing and revision.

### Structural Growth
An observable change to capabilities, decision rules, relationships, interfaces, evidence structures, or governance that expands or improves a system's tested competence under stated conditions.

### Open-Ended Growth
A research objective in which new relevant structures and problem classes can continue to emerge; it does **not** mean guaranteed indefinite improvement or unbounded real-world action.

### Localization
The selection of a relevant problem context, capability region, node, or strategy space before detailed per-node computation or evaluation.

### Per-Node Intelligence
Intelligence performed at a selected structural node, such as evaluating evidence, generating candidates, selecting a tool, or applying a domain-specific scoring rule.

### Control Plane
A layer governing routing, policy, evaluation, resources, authority, and feedback across intelligence units or strategic interactions.

### Capability Plane
The layer containing available models, tools, specialized units, expertise, infrastructure, and other resources that may execute authorized work.

### Information Plane
The layer carrying observations, knowledge, messages, evidence, uncertainty, and provenance between subjects and components.

## B. Strategic Subjects and Boundaries

### Strategic Subject
An individual, organization, institution, or other legitimately modeled decision-making entity with identifiable interests, capabilities, constraints, and an attributable locus of strategic authority. An AI agent may be modeled as an operational actor without being presumed to possess human-equivalent legal or moral sovereignty.

### Subject Boundary
The distinction between a subject's authorized internal decisions, its interactions with other subjects, and external constraints. Boundaries can concern identity, data, resources, goals, action rights, or accountability.

### Strategic Agency
The practical capacity to formulate, compare, select, and revise strategies within a subject's constraints and delegated authority.

### Strategic Sovereignty
The retained authority to determine or authorize a subject's goals, commitments, risk limits, and consequential actions. Computation and recommendation may be delegated without transferring this authority.

### Human Strategic Sovereignty (HSS)
A design requirement that AI-mediated strategic exploration strengthen human understanding and decision capacity while preserving accountable human authority over consequential goals and actions. See [SSICR-008](docs/SSICR-008-Human-Strategic-Sovereignty.md).

### Scoring Sovereignty
Authority to define, approve, and revise the objectives, trade-offs, weights, constraints, and perspectives by which strategic alternatives are evaluated.

### Goal Ownership
The identification of the subject authorized to define or change an objective. A simulation's optimization target is not automatically the subject's legitimate goal.

### Delegation Boundary
A contractual limit on what an AI system or intermediary may recommend, simulate, prepare, execute, or revise on behalf of a subject.

### Revocability
The capacity of the authorized subject to suspend or withdraw delegated permissions and halt or contain future actions, subject to the practical limitations of actions already taken.

### Strategic Authority Contract
A record of authority holders, delegated capabilities, permitted actions, limits, escalation conditions, expiration, revocation, and audit requirements.

### Normative Authorization
Explicit approval by a legitimate authority for changes to goals, values, rights, or consequential policy—not merely evidence that a change would improve a measured score.

## C. Competitive Relay and Strategic Interaction

### Cooperative Relay
Relay relationships primarily structured around mutually agreed shared tasks or complementary capabilities.

### Competitive Relay
Relay interactions among subjects whose objectives or incentives partly conflict, including strategic adaptation, information asymmetry, bargaining, or adversarial behavior.

### Mixed-Motive Relay
A relationship combining shared and conflicting incentives, such as joint safety evaluation alongside commercial competition.

### Open Relay
A strategy emphasizing broad access, interoperable interfaces, knowledge exchange, or open participation, subject to specified limits.

### Closed Relay
A strategy emphasizing internal coordination, restricted interfaces, protected information, or limited external participation.

### Hybrid Relay
A configurable combination of open and restricted interfaces, often differentiated by information class, partner, purpose, or risk.

### Adaptive Hybrid Relay
A hybrid policy that revises its openness and restrictions in response to validated changes in context, evidence, or threat conditions.

### Relay Topology
The network of subjects and permitted connections through which interactions, information, and resources flow.

### Relay Sovereignty Boundary
The set of authority and data restrictions that remain effective when information or work crosses a Relay interface.

### Strategic Interdependence
A condition in which one subject's outcomes depend on other subjects' choices, capabilities, or adaptations.

### Opponent Adaptation
Changes in a competing subject's behavior or policy in response to observed strategies or environmental conditions.

### Cross-Play
Evaluation of multiple strategies against a diverse set of other strategies or opponents, rather than only against a fixed baseline.

### Self-Play
A training or evaluation arrangement in which variants of an agent or policy interact with one another; its validity for real opponents requires separate testing.

### Strategic Equilibrium
A stable or approximately stable pattern of choices under a specified game, information structure, and behavioral assumptions. Equilibrium is not synonymous with ethical desirability or empirical inevitability.

## D. Strategies and Simulation

### Strategy
A conditional plan or policy connecting observations and context to choices, resource allocations, commitments, and possible revisions.

### Strategy Candidate
A proposed strategy awaiting simulation, comparison, counter-evidence review, and any required authorization.

### Strategy Portfolio
A set of complementary or competing strategies retained for selection across contexts rather than compressed prematurely into a single winner.

### Strategic Policy Vector
A structured parameterization of a strategy, potentially including openness, investment, security controls, delegation, reciprocity, and audit requirements.

### Scenario
A specified configuration of environment, subjects, resources, institutions, initial conditions, assumptions, and possible shocks used for analysis or simulation.

### Simulation Run
A recorded execution of a scenario and strategy configuration, including model version, random seed where applicable, observations, outcomes, and provenance.

### Massive Multi-Strategy Simulation (MMSS)
A proposed SSICR workflow that evaluates many strategy–subject–environment combinations using scalable compute, adaptive sampling, cross-play, and validation. “Massive” describes a scaling ambition, not a demonstrated performance result.

### Agent-Based Modeling (ABM)
An established method for simulating interactions among individual modeled agents and observing aggregate dynamics.

### Multi-Agent Systems (MAS)
An established research field studying multiple interacting computational agents, including coordination, communication, competition, and distributed decision-making.

### Evolutionary Game Theory
An established family of models for strategy distributions and adaptation under payoff-dependent dynamics.

### System Dynamics
An established modeling approach emphasizing stocks, flows, feedback loops, and aggregate system behavior.

### Multi-Fidelity Simulation
Using models of different cost and realism, such as inexpensive screening followed by more detailed tests for promising or uncertain cases.

### Adaptive Compute Allocation
Dynamically distributing computational resources among strategy generation, simulation, counter-evidence, and validation according to expected information value, uncertainty, and risk.

### Out-of-Distribution (OOD) Evaluation
Testing a strategy or model in conditions differing materially from those used to construct or tune it.

### External Validation
Checking claims against independent data, experiments, expert judgment, or real-world observations not used to tune the original model.

### Simulation-to-Reality Gap
The discrepancy between modeled outcomes and real-world outcomes arising from omitted variables, incorrect assumptions, strategic adaptation, measurement errors, or other causes.

## E. Evaluation and Strategic Advantage

### Scoring Perspective
An explicitly identified evaluator's choice of objectives, constraints, metrics, weights, and interpretation of outcomes.

### Scoring Forest
A structured collection of evaluators or scoring trees representing multiple domains, objectives, perspectives, or constraints. Aggregation rules must not erase legitimate differences among subjects.

### Anti-Goodhart
Methods intended to reduce the failure of optimizing a metric that becomes an unreliable proxy for the actual objective, including diverse metrics, held-out tests, adversarial evaluation, and counter-evidence.

### Comparative Advantage
A strategy's relative benefit against specified alternatives, under stated conditions and a defined scoring perspective; it is not an unconditional global ranking.

### Strategic Advantage Map (SAM)
A versioned evidence structure identifying where, for whom, against which alternatives, and with what confidence a strategy has a comparative advantage. See [SPEC-003](specs/SPEC-003-Strategic-Advantage-Map-Schema.md).

### Advantage Region
A subset of the modeled context space where evidence supports a strategy's relative advantage under a specified comparison and scoring perspective.

### Failure Boundary
A tested or hypothesized boundary beyond which a strategy's advantage degrades, reverses, or becomes too uncertain to assert.

### Rank Reversal
A change in the ordering of strategies as context, opponents, objectives, or evidence changes.

### Baseline Strategy
A documented comparator, such as the status quo or a simpler policy, used to interpret relative performance.

### Counterfactual Comparison
An analysis of what might have occurred under an alternative strategy, requiring explicit causal or modeling assumptions.

### Robustness
A strategy's stability across relevant variations in assumptions, environments, opponents, and measurement noise.

### Generalization
The extent to which an inferred strategic advantage holds beyond the conditions used to discover it.

### Confidence
A calibrated or otherwise explicitly qualified assessment of support for a claim; confidence must specify its basis and should not be fabricated from simulation frequency alone.

### Provenance
The traceable origin, transformation history, model version, assumptions, and custodianship of evidence and conclusions.

## F. Strategic Principles and Worldviews

### Strategic Principle
A reusable conditional claim about strategic choice, supported by evidence, qualified by assumptions, and open to counter-evidence.

### Principle Extraction
The process of proposing a transferable strategic rule from repeated or otherwise informative observations, while retaining evidence lineage and exceptions.

### Strategic Worldview
A subject- or perspective-associated organization of strategic principles, priorities, interpretations, and decision criteria used to perceive and navigate strategic situations.

### Strategic Worldview Tree
A structured grouping of mutually related principles, assumptions, evidence, and revision rules for one coherent strategic perspective.

### Strategic Worldview Forest (SWF)
A plural collection of worldview trees, potentially associated with different subjects or legitimate value perspectives, that can be compared and revised without forcing normative convergence. See [SSICR-006](docs/SSICR-006-Strategic-Worldview-Forests.md).

### Worldview-Guided Strategy Generation
Using a worldview's current assumptions and principles to suggest strategies, while maintaining pathways for exploration outside those assumptions.

### Cross-Worldview Evaluation
Comparing strategic conclusions across distinct worldviews and scoring perspectives while making disagreement and incompatible objectives explicit.

### Epistemic Revision
Changing factual beliefs, causal models, applicability conditions, or confidence in response to evidence.

### Normative Revision
Changing values, objectives, risk tolerance, rights, or authority rules; such revisions require legitimate authorization rather than automatic optimization.

### Worldview Drift
A change in a worldview over time, which may represent learning, unrecognized objective shift, evidence distortion, or unauthorized normative change.

### Worldview Lock-In
A failure mode where accumulated assumptions, incentives, or scoring rules suppress legitimate alternatives and contradictory evidence.

### Worldview Branching
Creating alternative principle sets when evidence or subject objectives support multiple non-equivalent interpretations.

### Worldview Folding
Combining or abstracting compatible principles while retaining their qualifications, provenance, and disagreement where material.

## G. Counter-Evidence, OTHERS, and Uncertainty

### Counter-Evidence
Evidence that challenges, limits, contradicts, or lowers confidence in a claim, principle, advantage region, or worldview. It should remain independently accessible rather than being silently discarded.

### Counter-Evidence Registry
A structured record of challenges, their sources, status, relevance, resolution attempts, and effects on associated claims.

### OTHERS
An explicitly preserved space for unexplained observations, unknown factors, unmatched evidence, and possible new structural dimensions. It is a prompt for inquiry, not a quantified explanation by itself.

### Residual Evidence
Observations not adequately accounted for by the current matched variables, models, or explanatory structure.

### Open Evidence Space
A mechanism for retaining residual or anomalous evidence so future models may identify additional factors without prematurely forcing a match.

### Epistemic Uncertainty
Uncertainty arising from incomplete knowledge or imperfect models, potentially reducible through better evidence or modeling.

### Aleatoric Uncertainty
Variability treated as inherent or stochastic within the modeled process, though its classification depends on the modeling assumptions.

### Model Risk
The possibility that an incorrect or incomplete model produces misleading conclusions or unsafe decisions.

### Evaluator Governance
Policies and checks controlling how scoring criteria are created, challenged, updated, authorized, and audited.

### Adversarial Validation
Testing claims or systems against deliberately challenging cases, alternative assumptions, or adaptive opponents.

### Falsifiable Hypothesis
A sufficiently specific claim paired with observable conditions under which it could be rejected or weakened.

## H. Evolution, Society, and Institutions

### Recursive Self-Improvement (RSI)
A process in which a system's outputs help modify its own future capabilities or procedures, with measurable evaluation and constraints. Improvement must be demonstrated rather than inferred from recursion alone.

### Structural RSI
RSI that modifies explicit intelligence structures—such as interfaces, routing, capability graphs, evaluators, or Relay policies—rather than solely adjusting model parameters.

### Open-Ended Strategic RSI
A proposed feedback system in which strategic simulation and evaluation generate candidate changes to capabilities, Relay structures, strategies, relationships, and worldviews, subject to counter-evidence, validation, and authorization. See [SSICR-009](docs/SSICR-009-Open-Ended-Strategic-RSI.md).

### Co-Evolution
Mutual adaptation among interacting subjects, capabilities, strategies, and institutional rules, where changes at one level alter incentives and possibilities at others.

### Social Structural Simulation
Modeling interactions among subjects, Relay networks, institutions, and environments to explore emergent social or organizational structures; predictive validity requires independent evaluation.

### Institutional Structure
Rules, norms, standards, rights, enforcement processes, and organizations that constrain or enable strategic interaction.

### Institutional Co-Evolution
The reciprocal process by which strategic behaviors alter institutional arrangements and institutional changes alter strategic behaviors.

### Emergence
System-level patterns arising from interactions among components that are not explicitly prescribed as a single component's behavior.

### Structural Precedent
A documented earlier case, principle, contract, or outcome that may inform new decisions, subject to relevance and changed conditions.

### Strategic Knowledge Accumulation
Preserving validated comparisons, failures, boundary conditions, and transferable principles for future strategy generation and evaluation.

## I. Governance, Validation, and Operational Terms

### Human-in-the-Loop
A design pattern requiring human involvement at defined stages; meaningful sovereignty additionally requires adequate information, authority, time, and the practical ability to reject or revoke actions.

### Decision Support
Information, comparisons, simulations, and recommendations provided to an authorized decision-maker without assuming the authority to act.

### Decision Compression
Summarizing a large strategy space into intelligible options, trade-offs, assumptions, failure boundaries, and evidence while avoiding concealment of material disagreement.

### Strategy Stream
A potentially high-volume flow of AI-generated strategies, revisions, and simulation results that may exceed direct human review capacity.

### Authorization Gate
A control that prevents specified actions or normative changes until a legitimate authority grants permission.

### Audit Trail
A durable record of proposals, evidence, approvals, revisions, actions, and outcomes sufficient for later accountability and investigation.

### Conformance Test
A test of whether an implementation satisfies stated schema, contract, or governance requirements; conformance alone does not establish scientific validity or safety.

### Research Prototype
An experimental implementation intended to test a hypothesis or design; it should not be represented as production-ready without additional evidence.

### Synthetic Case Study
A deliberately constructed illustrative scenario with invented entities or values, useful for conceptual or test design but not empirical proof.

### Validation Roadmap
A staged plan connecting hypotheses to datasets, baselines, tests, falsification criteria, and external review.

### Responsible Strategic Deployment
Use of strategic systems within explicit authority, safety, privacy, security, and accountability boundaries, with monitoring and mechanisms to correct or halt harmful behavior.

---

## J. Key Distinctions

| Distinction | Why it matters |
|---|---|
| Subject vs. AI agent | An operational agent need not be the owner of goals or legitimate authority. |
| Relay vs. permission | A connection does not grant unrestricted access or action rights. |
| Simulation vs. evidence of reality | Model outcomes depend on assumptions and need external validation. |
| High score vs. strategic advantage | An advantage is relative to a comparator, context, and scoring perspective. |
| Advantage map vs. worldview | A map describes conditional evidence; a worldview also organizes principles and valuations. |
| Epistemic vs. normative revision | Evidence may justify changing beliefs, but not automatically changing values or authority. |
| Strategy recommendation vs. execution | The right to propose does not entail the right to act. |
| Structural growth vs. verified improvement | More complexity is not necessarily better performance or safety. |
| Counter-evidence vs. OTHERS | Counter-evidence challenges a claim; OTHERS also holds unexplained or unmatched information. |
| Research hypothesis vs. demonstrated result | Proposed mechanisms require tests, controls, and replication. |

## K. Document Cross-Reference

**Foundations and theory:** [SSICR-001](docs/SSICR-001-From-Cooperative-to-Strategic-Relay.md), [SSICR-002](docs/SSICR-002-Strategic-Subjects-and-Relay-Boundaries.md), [SSICR-003](docs/SSICR-003-Strategic-Control-Planes-and-Scoring.md), [SSICR-004](docs/SSICR-004-Massive-Multi-Strategy-Simulation.md), [SSICR-005](docs/SSICR-005-Strategic-Comparative-Advantage-Maps.md), [SSICR-006](docs/SSICR-006-Strategic-Worldview-Forests.md), [SSICR-007](docs/SSICR-007-Social-Structural-Simulation-and-Co-Evolution.md), [SSICR-008](docs/SSICR-008-Human-Strategic-Sovereignty.md), [SSICR-009](docs/SSICR-009-Open-Ended-Strategic-RSI.md), and [SSICR-010](docs/SSICR-010-Unified-Architecture-and-Research-Horizon.md).

**Contracts and schemas:** [SPEC-001](specs/SPEC-001-Strategic-Subject-and-Relay-Contract.md), [SPEC-002](specs/SPEC-002-Strategy-and-Simulation-Schema.md), [SPEC-003](specs/SPEC-003-Strategic-Advantage-Map-Schema.md), and [SPEC-004](specs/SPEC-004-Worldview-and-Counter-Evidence-Schema.md).

**Illustrative cases:** [CASE-001](cases/CASE-001-Competitive-AI-RD-Organizations.md), [CASE-002](cases/CASE-002-Open-Closed-and-Hybrid-Relay-Strategies.md), and [CASE-003](cases/CASE-003-Strategic-Worldview-Evolution.md).

**Navigation:** [README](README.md) · [START-HERE](START-HERE.md) · [CONTENTS](CONTENTS.md) · [FIGURE-INDEX](FIGURE-INDEX.md).

---

## Citation

Tan, Sizhe, and GPT-Obot. (2026). *GLOSSARY: Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)*. Version 1.0.0. Research repository documentation. DOI pending.

**Editorial note:** If a later specification assigns stricter field-level meanings to a term, that specification controls implementation conformance; this glossary remains the conceptual orientation. All proposed SSICR constructs remain open to revision through evidence and research.
