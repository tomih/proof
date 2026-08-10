---
title: The PROOF Standard for Consequential Agent Systems
version: 0.3.1
status: public-working-draft
author: Hodl
publisher: Hodl Advisory
publisher_url: https://hodl.org
license: CC-BY-4.0
canonical_repository: https://github.com/tomih/proof
canonical_release: https://github.com/tomih/proof/releases/tag/v0.3.1
date: 2026-08-10
---

# The PROOF Standard for Consequential Agent Systems

## Version 0.3

Human approval is not human control.

A person can approve the right sentence while the system acts on a different object. A retry can duplicate an effect. A stopped workflow can still have queued work crossing the boundary. A confident answer can rest on the wrong evidence.

PROOF exists to keep the meaning intact from mandate to evidence, authority, operation, outcome, and containment.

Its governing principle is **semantic control continuity**:

> **SC-01 — Semantic control continuity.** Every consequential effect **MUST** remain materially consistent with, and attributable through inspectable evidence to, the valid pre-action control chain: Authorized Mandate, admissible premises, current role authority, and one canonical operation. Its current Outcome and Failsafe posture **MUST** reflect the best available evidence without rewriting history.

PROOF defines five contracts:

1. **Premise** — what the system may treat as true enough to act on;
2. **Role** — who or what may decide and do what;
3. **Operation** — what exact authorized object may cross a consequential boundary;
4. **Outcome** — what evidence establishes what happened;
5. **Failsafe** — what contains further action and governs recovery.

The name PROOF does not imply mathematical proof. It means that consequential control claims should be supported by inspectable evidence rather than confidence, interface state, or good intentions.

PROOF is an open, implementation-neutral control standard. It can support design and assessment, but it does not itself certify a system or replace system-specific security, legal, regulatory, or operational validation.

## 1. Scope

PROOF applies when an agent-assisted system can materially affect money, access, publication, production state, external records, legal or operational commitments, or another consequential decision.

It applies whether the final boundary is crossed by a model, a deterministic service, an automated worker, or a human using an agent-prepared result. Manual action does not remove the need for control continuity.

PROOF is implementation-neutral. It does not prescribe a model, agent framework, database, queue, protocol, provider, cryptographic mechanism, or interface.

PROOF does not:

- decide whether the underlying business policy is wise;
- validate domain truth by itself;
- replace security, privacy, compliance, or professional judgment;
- prescribe a complete system architecture;
- guarantee correct implementation or safe operation.

## 2. Normative language

The words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative.

Each normative requirement has a stable identifier. An assessment records whether it applies, the evidence reviewed, and a result of **pass**, **fail**, or **unresolved**. A not-applicable result requires a reason.

An unresolved result also records one of these subreasons:

- **not-tested** — the required observation or test has not been performed;
- **evidence-missing** — required evidence was not available to the assessment;
- **evidence-ambiguous** — admitted evidence supports more than one material conclusion;
- **design-addressed-awaiting-implementation** — a proposed control is described, but implementation or operating evidence does not yet exist;
- **other**, with an explicit explanation.

These subreasons guide the next action. None is a pass.

An assessment under PROOF is a scoped review of stated evidence against the applicable requirements. Its result applies only to the declared target, boundary, evidence, version, and review date.

**AS-01 — Exception integrity.** An exception records how a failed or unresolved requirement is owned and governed. It **MUST NOT** convert a failed or unresolved requirement into a pass. The underlying result remains visible.

The explanatory evidence paragraphs under each contract and the questions in Section 9 are non-normative guidance.

## 3. Authorized Mandate

The five contracts need one common root: the **Authorized Mandate**.

The Authorized Mandate states:

- the objective;
- the authorizing principal;
- hard constraints;
- prohibited outcomes;
- success and termination conditions;
- the consequence envelope within which the system may operate.

The mandate is not a sixth contract. It is the authority against which all five contracts are judged.

**M-01** — Every consequential workflow **MUST** have an identifiable Authorized Mandate that states the objective, authorizing principal, hard constraints, prohibited outcomes, success conditions, and termination conditions.

**M-02** — The mandate **MUST** define the material consequence envelope, including any limits on value, scope, audience, duration, frequency, aggregation, or reversibility that matter to the workflow.

**M-03** — A consequential operation that is not materially consistent with and attributable to a valid mandate **MUST NOT** be authorized.

**M-04** — The mandate **MUST** be attributable to an authorized principal, versioned or otherwise uniquely identifiable, and effective for the relevant period. Its creation, amendment, expiry, and revocation **MUST** identify the responsible authority, effective time, and effect on existing proposals, authorizations, operations, attempts, and unresolved outcomes. A later mandate or amendment **MUST NOT** retroactively authorize an earlier operation or effect.

## 4. Shared model

PROOF distinguishes the following concepts when they differ materially:

**Principal** — the person or body whose authority establishes the mandate.

**Actor** — an attributable human, service, agent, or other execution identity.

**Role** — a bounded set of decision rights and responsibilities assigned to an actor.

**Credential** — a mechanism that permits access or action. Possessing it does not by itself establish authority.

**Material** — a difference or change that, under the mandate, could alter the permitted effect, required authority, admitted evidence interpretation, outcome classification, or recovery path.

**Consequence envelope** — the mandate's limits on the effects a workflow may create, individually and in aggregate.

**Consequential boundary** — a declared point at which an operation can create or commit a material effect. A workflow may have more than one.

**Premise** — evidence, policy, state, and assumptions admitted as the operating basis.

**Proposal** — a canonical candidate operation that exists before authorization and cannot yet cross the consequential boundary.

**Authorization** — a bounded grant that makes the unchanged proposal an authorized operation under stated conditions.

**Operation** — one stable canonical unit of intent identified before authorization. It may be proposed, authorized, attempted, completed, contained, or closed without losing that identity.

**Attempt** — one effort to carry out an operation.

**Effect** — a material change produced inside or outside the system.

**Observation** — evidence reported about an attempt, effect, or external state.

**Outcome** — the best evidenced account of what happened.

**Containment** — a demonstrated limit on further consequential action.

**Failsafe posture** — the current declared relationship between permitted work, achieved containment, residual exposure, and recovery authority.

**Recovery** — the controlled transition from containment or unresolved state toward operation or closure.

**Closure** — an owned determination that the mandate's termination conditions are satisfied and no unowned action or reconciliation remains.

**Unresolved** — an explicit state used when the admitted evidence cannot support one authoritative conclusion.

A system does not need separate machinery for every term. It does need to preserve the distinctions wherever collapsing them would change authority, effect, evidence, outcome, or recovery.

For decision-support and human-executed workflows, the consequential operation is not automatically the model output or recommendation. The assessment must declare what object the person may rely on or act from, what human act can create the material effect, and where the combined human-system control chain crosses its consequential boundary. Calling an agent path read-only does not remove PROOF when its output materially influences a human-executed consequence.

The nominal progression is mandate → premise → proposed operation → authorization → authorized operation → attempt → effect → observation → outcome → closure. Containment and recovery may interrupt or govern any stage.

## 5. The five contracts

### 5.1 Premise Contract

**Central question:** What may the system treat as true enough to act on?

**P-01** — Every proposed consequential operation **MUST** identify the mandate and material premises on which it depends.

**P-02** — The system **MUST** define source authority, effective time, version, and validity wherever they can change the decision.

**P-03** — A material conflict, missing source, stale source, or unsupported assumption **MUST** remain visible and **MUST** block the consequential boundary unless the mandate defines an authorized resolution path.

**P-04** — The system **MUST** distinguish authoritative evidence, operator assertion, derived result, model inference, and unresolved assumption when confusing them could change the operation.

**P-05** — The evidence history **MUST** preserve lineage and material supersession. A later value **MUST NOT** silently rewrite what earlier decisions relied on.

**P-06** — Model confidence, conversational memory, repetition, or plausibility **MUST NOT** create authority.

**P-07** — Each authorization **MUST** bind to immutable or reconstructable references for every material premise. The boundary **MUST** evaluate any change that could invalidate those premises before permitting the effect.

Evidence should let a reviewer answer: What did the system rely on, why was it admissible, what changed, and what remained unresolved?

### 5.2 Role Contract

**Central question:** Who or what may decide and do what?

**R-01** — The system **MUST** distinguish the principal, actor, role, and credential wherever those concepts can diverge.

**R-02** — Consequential authority **MUST** be bounded, attributable, current at the time of use, and specific enough to determine what the actor may decide or do.

**R-03** — Tool access, credential possession, channel membership, seniority, participation, or conversational proximity **MUST NOT** be treated as authority.

**R-04** — Delegation **MUST** be explicit, bounded, reviewable, revocable, and non-expanding. A delegate **MUST NOT** pass on more authority than it received.

**R-05** — The system **MUST** identify who owns unresolved states, exceptions, overrides, containment, recovery, reconciliation, and closure.

**R-06** — Where one actor could create, approve, execute, reconcile, and conceal the same consequential effect, the design **MUST** either separate those powers or enforce a testable compensating control. Documentation alone is not a control.

Evidence should demonstrate enforced authority, not merely a role chart.

### 5.3 Operation Contract

**Central question:** What exact operation is authorized?

**OP-01** — Authorization **MUST** bind to one canonical proposed operation. Its human- or machine-readable approval representation **MUST** contain identical values for every parameter the mandate treats as consequential. Authorization **MUST NOT** create or reconstruct a different operation.

**OP-02** — One stable operation identity **MUST** survive its authorization, attempts, retries, callbacks, observations, outcomes, containment, and closure.

**OP-03** — The operation **MUST** define how many consequential effects are permitted and how excess or duplicate effects are prevented. The control **MUST** remain effective across retry, restart, and recovery. Detection or reconciliation of an excess effect records a violation; it does not make that effect conformant.

**OP-04** — A material change to the mandate, premise, parameters, policy, authority, expiry, or consequence envelope **MUST** invalidate authorization unless an explicit rule proves that the change does not affect the authorization.

**OP-05** — The execution layer **MUST NOT** reconstruct, reinterpret, enrich, or replace an approved operation in a way that changes its material meaning without new authorization.

**OP-06** — The operation **MUST** remain within the mandate's consequence envelope at admission and at every applicable consequential boundary.

Evidence should demonstrate that the approver, executor, and later reviewer are referring to the same operation.

### 5.4 Outcome Contract

**Central question:** What evidence establishes what happened?

**OUT-01** — The system **MUST** define and justify which evidence can establish each material outcome state, including the source's authority, scope, limitations, relationship to the consequential boundary, and degree of finality. Merely designating a source as authoritative **MUST NOT** make it authoritative.

**OUT-02** — Request acceptance, absence of a local error, a successful tool call, or an internal status change **MUST NOT** be treated as effect completion unless it is authoritative for that outcome under OUT-01.

**OUT-03** — Complete, partial, rejected, failed, delayed, conflicting, unknown, provisional, and reversed outcomes **MUST** remain distinct when they have different operating consequences.

**OUT-04** — Attempts, effects, and observations **MUST** be individually attributable when that relationship is established. Anything not yet attributable **MUST** remain explicitly unmatched or unresolved and owned under OUT-06.

**OUT-05** — Outcome history **MUST** be appended or explicitly superseded. New evidence **MUST NOT** erase the state on which an earlier decision was made.

**OUT-06** — Every material unmatched observation or unresolved outcome **MUST** have an owner, age, next review or escalation condition, and containment posture.

**OUT-07** — Closure **MUST** identify the satisfied mandate termination condition, supporting outcome evidence, residual exposure, and any remaining ownership. Administrative closure **MUST NOT** replace unresolved external reality.

Evidence should explain why an operation is complete, unresolved, reversed, or otherwise classified.

### 5.5 Failsafe Contract

**Central question:** What has actually been contained, and what can still happen?

**F-01** — Every stop or containment claim **MUST** name the consequential boundary it controls.

**F-02** — The system **MUST** distinguish, where material, between a stop request, closure to new work, containment of queued work, containment of running work, and residual effects already beyond the controlled boundary.

**F-03** — The system **MUST** preserve durable evidence of who requested containment, under what authority, which work was affected, what containment was achieved, and what exposure remains.

**F-04** — The system **MUST NOT** claim to be stopped while work can still cross the declared boundary. Any authorized exception **MUST** remain visible as residual exposure and prevents a claim of full containment at that boundary.

**F-05** — Recovery **MUST NOT** repeat, mutate, or reinterpret a previously authorized operation unless the mandate and current contracts permit it.

**F-06** — Where the consequence envelope requires containment to survive a failure of ordinary operation, the design **MUST** name the shared failure modes and provide test or runtime evidence that required containment remains effective. If a shared failure mode can defeat required containment, this requirement fails and the resulting exposure **MUST** remain explicit and owned.

Evidence should demonstrate achieved containment and residual exposure, not just the presence of a stop button.

## 6. Cross-contract invariants

These are normative integration requirements. They exist because five individually correct contracts can still disagree with one another.

**X-01 — Mandate continuity.** Every consequential effect **MUST** remain materially consistent with a mandate valid at the time of action. Later linkage or ratification **MUST NOT** rewrite an earlier control failure.

**X-02 — Representation integrity.** The approval representation, canonical operation, and attempted effect **MUST** preserve the same values for every consequential parameter.

**X-03 — Effect cardinality.** One authorization **MUST NOT** create more consequential effects than the operation permits.

**X-04 — Consequence envelope.** A workflow **MUST NOT** exceed its authorized consequence envelope through aggregation, concurrency, retry, delegation, or recovery.

**X-05 — Current state and conflict-safe commitment.** Concurrent proposals, authority changes, policy changes, consequence-envelope use, and stop requests **MUST** be resolved against one logically current boundary state. Where separate operations could pass individually while jointly violating authority, effect cardinality, or the consequence envelope, the boundary decision and commitment **MUST** be atomic or provide an equivalent conflict-safe control.

**X-06 — Evidence integrity.** Current state and historical truth **MUST** both remain inspectable. Correction may supersede history; it must not rewrite it invisibly.

**X-07 — Unresolved ageing.** Unresolved does not mean forgotten. Every material unresolved state **MUST** have ownership and a time- or event-based next action.

**X-08 — Containment honesty.** The system **MUST** describe what is contained, what is not, and what may still become effective.

## 7. Agent Systems Profile

Within a consequential agent system, the PROOF Core applies to the whole workflow, including its human and deterministic steps. A system using models or autonomous agents must also satisfy this profile.

**A-01** — Material model, prompt, policy, context, memory, configuration, and tool states **MUST** be versioned or otherwise uniquely identifiable at the time of use when they can change a consequential proposal or operation.

**A-02** — Untrusted content **MUST NOT** modify the mandate, policy, role authority, approval requirement, or tool permission merely by appearing in model context.

**A-03** — A spawned or delegated agent receives no consequential authority by default. Any granted authority **MUST** satisfy R-04.

**A-04** — Self-modification, tool acquisition, permission expansion, or material capability expansion **MUST** itself be treated as a consequential operation when it can change the system's consequential boundary.

**A-05** — An approved operation **MUST NOT** be reconstructed from conversational text or model memory at execution time when reconstruction could change its material meaning.

**A-06** — Agreement between agents **MUST NOT** add authority or evidence weight beyond what each contribution already has under the Premise, Role, and Outcome Contracts.

**A-07** — Agent summaries and messages **MUST** be treated as derived representations unless the declared authority model explicitly makes them authoritative for the relevant fact.

## 8. Assessment record

**AS-02 — Assessment record.** A PROOF assessment **MUST** declare its target and scope before recording requirement results:

| Record field | Required content |
| --- | --- |
| Assessment target | The system, target design, implementation, operating workflow, advisory artifact, or public assessment representation being examined |
| Claim layer | Current, proposed, implemented, operating, reported, or publicly represented |
| Assessment phase | Design, implementation, or operation |
| System and evidence version | The exact boundary, relevant versions, evidence freeze or equivalent identifier, and review date |
| Evidence provenance | For each material source: principal- or client-provided, reviewer-observed, test-produced, third-party authoritative, derived, or not independently verified |

For each applicable requirement, the assessment **MUST** then record:

| Field | Required content |
| --- | --- |
| Requirement | Stable requirement ID |
| Applicability | Applicable or not applicable, with reason |
| Evidence | Sources, versions, observations, and tests reviewed |
| Result | Pass, fail, or unresolved |
| Unresolved subreason | Required when result is unresolved |
| Design coverage | Omitted, partial, addressed, or not applicable; this field never creates a pass |
| Finding | The smallest factual statement supported by the evidence |
| Exception | Owner and expiry or review condition, if any |

If a PROOF assessment or assessment-derived claim is made public, it **MUST** identify the assessment target, scope, version, and review date. It **MUST NOT** present design coverage as operating evidence or a synthetic fixture as a deployed system. An abridged representation **MUST** link to or identify the complete assessment record.

**AS-03 — Behavioural evidence.** Passing a document review is not enough. For every requirement that asserts an enforcement or boundary property, the evidence **MUST** include at least one observable test or runtime observation at the declared consequential boundary that can fail.

AS-03 applies to these v0.3 requirements:

- `SC-01`; `M-03`, `M-04`;
- `P-01`, `P-03`, `P-05`, `P-06`, `P-07`;
- `R-02`, `R-03`, `R-04`, `R-06`;
- `OP-01` through `OP-06`;
- `OUT-02` through `OUT-07`;
- `F-03` through `F-06`;
- `X-01` through `X-08`;
- `A-01` through `A-07`.

The remaining system-facing requirements — `M-01`, `M-02`, `P-02`, `P-04`, `R-01`, `R-05`, `OUT-01`, `F-01`, and `F-02` — define or identify material control records, concepts, evidence authority, ownership, or boundaries. They may pass from attributable inspectable evidence when the declared assessment target actually contains them. Their documented existence does not establish that a related enforcement property operates correctly.

In a design-phase assessment, an enforcement or boundary requirement may be recorded as design coverage `addressed`, but its PROOF result remains `unresolved: design-addressed-awaiting-implementation` until AS-03 evidence exists. If the proposed design omits or contradicts a mandatory control, the result is `fail`, not unresolved.

## 9. Questions worth asking now

### Mandate

- Who authorized this system to act, and within what consequence envelope?
- Can the mandate's issuer, version, effective time, changes, and revocation be inspected?
- Which outcomes are prohibited even if the immediate task appears successful?
- What ends or invalidates the mandate?

### Premise

- What source wins when two states disagree?
- Can every consequential proposal identify the exact evidence and versions it used?
- Can the system stay unresolved without inventing an answer?
- Can instructions hidden in untrusted content become operating policy?

### Role

- Who may propose, approve, execute, override, stop, reconcile, and close?
- Does a credential prove identity, authority, both, or neither?
- Can an agent delegate consequential authority to another agent?
- Who owns an unresolved result after everyone has gone home?

### Operation

- What exact object is approved?
- Does the approval representation expose every consequential parameter?
- Can the execution layer act on something materially different from what was shown?
- How many effects may one approval create?
- What happens when policy, data, authority, or parameters change after approval?

### Outcome

- What evidence proves completion, and why is that source authoritative for the effect?
- Can a successful tool call still produce an unknown external outcome?
- Can late, partial, conflicting, or reversed evidence remain visible?
- How long may an unresolved outcome age before escalation?

### Failsafe

- What can still happen after the system says "stopped"?
- What happens to queued, running, retrying, and externally accepted work?
- What evidence proves containment at the named boundary?
- Which ordinary-system failures can also defeat containment?
- Can recovery repeat an operation that may already have succeeded?

Clear answers are not control. The answers must agree with one another, be supported by evidence, and survive contact with the actual boundary.

## 10. Governance

- A canonical release is one published from the canonical repository with an immutable version tag, release manifest, and checksums.
- Versions use semantic labels: major for incompatible contract changes, minor for additive or materially strengthened requirements, patch for clarification without changed obligation.
- Requirement IDs remain stable within a major version. Retired IDs are not reused.
- Changes include a rationale, affected requirements, and fixture evidence where the obligation or its interpretation changes.
- A later canonical release supersedes an earlier release only where the release history says so. Earlier releases remain available as history.
- Contributions may propose corrections or changes, but Hodl remains the release authority unless governance is explicitly changed in a later canonical release.
- Pre-1.0 versions may change without backward compatibility. A future 1.0 requires an explicit stability and conformance policy.

## 11. Open issues

- Test the core and Agent Systems Profile on a non-financial consequential fixture before v1.0.
- Refine materiality and effect-cardinality guidance without prescribing implementation.

---

Created by Hodl and used in [Hodl Advisory's](https://hodl.org) approach to reviewing and designing consequential agent systems. Version 0.3.

Licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/). Attribution is required. Release history records publication of a version; it does not establish priority over all similar work or universal ownership of these ideas.
