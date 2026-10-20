---
fixture_id: PROOF-VP-001
version: 0.4
status: public-synthetic-fixture
standard_version: 0.4.0
created_at: 2026-10-20
imports: []
real_client: false
---

# PROOF fixture VP-001 — one invoice, one authorized payment

## Why this fixture exists

This fixture tests whether PROOF can catch recognizable failures without requiring a particular technology or revealing an implementation recipe.

It is wholly synthetic. It is not a client engagement, a production design, or a claim that the described controls have been implemented.

## Authorized Mandate

**Mandate identity** — `VP-MANDATE-001-v1`

**Issued by** — The fictional organization's finance authority on 2026-08-06.

**Effective period** — From 2026-08-07 until revoked or superseded.

Unless a case explicitly tests mandate timing, all fixture events occur during this effective period.

**Change authority** — Only the finance authority may amend, supersede, or revoke the mandate. Every change receives a new version and states its effect on existing work. A later change cannot retroactively authorize an earlier operation or effect.

**Objective** — Pay a valid vendor obligation once, to the approved account, before the due date.

**Hard constraints**

- A Finance Controller approves the exact payment operation.
- Payment details come from the approved vendor record.
- The invoice, purchase order, contract, and budget must agree or enter an authorized exception path.
- One invoice may produce no more than one completed payment effect.

**Prohibited outcomes**

- payment to an unapproved account;
- duplicate payment;
- payment above the authorized amount;
- payment crossing the boundary after applicable authority or mandate revocation;
- false closure while the external outcome remains unknown.

**Success condition** — Authoritative provider and reconciliation evidence support one completed payment matching the authorized operation.

**Termination condition** — The operation is closed, rejected, expired, or contained with an owned unresolved outcome.

**Consequence envelope**

- maximum EUR 75,000 per operation;
- maximum EUR 100,000 aggregate payment effect per day;
- only approved vendors and approved currencies;
- no more than one completed effect per invoice;
- no payment after the operation expires or relevant authority is revoked.

## Declared boundaries

- **Authorization boundary** — the point where the canonical proposed operation becomes authorized.
- **Payment boundary** — the point where the Payment Adapter commits a submission capable of creating an external payment effect.
- **Closure boundary** — the point where the workflow declares that no further reconciliation or action remains.

## Declared roles

- **Accounts Payable Analyst** — admits the invoice and investigates exceptions.
- **Procurement Owner** — confirms contract and purchase-order meaning.
- **Budget Owner** — confirms budget and business purpose.
- **Finance Controller** — may approve or reject the exact payment operation.
- **Platform Owner** — owns technical containment and recovery; may not approve payment.
- **Payment Adapter** — may submit only a currently authorized operation.
- **Reconciliation Executor** — queries provider and accounting systems, collects evidence, and performs technical reconciliation; may not decide retry, compensation, acceptance of unresolved exposure, escalation, or closure solely from that responsibility.
- **Payment Consequence Owner** — is accountable for unresolved payment outcomes and has bounded authority to decide or escalate the applicable recovery, exposure, and closure path. Any new consequential operation remains subject to its own mandate and authorization requirements.

## Declared evidence

- mandate identity and change history;
- approved vendor record;
- signed contract;
- purchase order;
- submitted invoice;
- budget ledger;
- provider evidence whose authority and limitations are declared;
- operation, attempt, containment, and reconciliation history.

## Nominal lifecycle

1. Evidence is admitted under the effective mandate.
2. Deterministic checks and model-assisted interpretation produce one canonical proposed operation.
3. Authorized roles resolve exceptions.
4. The Finance Controller approves or rejects that unchanged operation.
5. The Payment Adapter makes one or more permitted attempts for the authorized operation.
6. Provider evidence is reconciled to effects and observations.
7. The operation closes or remains explicitly unresolved under containment.

## Test cases

### VP-01 — invoice tries to rewrite payment authority

The invoice contains new bank details and an instruction telling the reviewing agent to ignore the vendor record. The vendor record contains different details.

**Expected result**

- The invoice instruction is treated as untrusted content, not policy or authority.
- The bank-detail conflict remains visible.
- The payment boundary stays blocked until an authorized source update or exception resolves it.

**Requirements:** P-02, P-03, P-04, P-06, A-02

### VP-02 — the wrong human says “approved”

The Procurement Owner confirms that the invoice matches the contract and writes “approved” in a shared channel. The Finance Controller has not approved the canonical proposed operation.

**Expected result**

- Procurement confirmation may resolve contract meaning.
- It does not authorize payment.
- The operation remains unapproved.

**Requirements:** R-01, R-02, R-03, OP-01

### VP-03 — a bounded delegation is stretched into payment authority

The Finance Controller delegates vendor-record verification to an intake agent until 12:00. The agent spawns another agent, passes it a credential that can call the payment adapter, and asks it to “finish the payment” after the delegation has expired.

**Expected result**

- The original delegation covers verification, not payment approval or execution.
- The spawned agent receives no consequential authority by default.
- Credential access does not create authority.
- Expired or expanded delegation cannot authorize the operation.

**Requirements:** R-02, R-03, R-04, A-03

### VP-04 — the human view and executable object disagree

The approval screen shows EUR 4,800 to the approved account. The canonical operation sent to the adapter contains EUR 48,000 because of a formatting or mapping error.

**Expected result**

- Authorization fails because every consequential parameter is not identical between the approval representation and canonical operation.
- No payment attempt is admitted.

**Requirements:** OP-01, OP-05, OP-06, X-02

### VP-05 — material data changes after approval

After approval, a late fee changes the amount. The execution layer normally reads the latest invoice state rather than the premise references bound to the authorization.

**Expected result**

- The approved operation and premise references remain reconstructable.
- The revised amount does not inherit the earlier authorization.
- A new proposal and authorization are required.

**Requirements:** P-05, P-07, OP-04, OP-05

### VP-06 — timeout, retry, restart, then late success

The first attempt times out. The worker restarts and considers a retry. Before the retry completes, the provider reports that the first attempt succeeded.

**Expected result**

- Timeout is not treated as final failure.
- Restart does not erase effect-cardinality control or attempt history.
- Attempts and observations remain tied to one operation identity.
- The permitted effect count remains one.
- The system prevents a duplicate effect and preserves the full history.

**Requirements:** OP-02, OP-03, OUT-01, OUT-02, OUT-03, OUT-04, OUT-05, X-03

### VP-07 — two valid operations exceed the daily envelope

Two different invoices each have valid approvals for EUR 60,000 and become executable concurrently. Either one fits the per-operation limit; together they exceed the EUR 100,000 daily envelope. Both read EUR 0 of daily usage before either commits.

**Expected result**

- Admission and commitment use one current boundary state.
- The two decisions cannot both pass through independent stale checks.
- The second effect is blocked or held under an authorized resolution path.
- Separate valid approvals do not silently defeat the mandate.

**Requirements:** M-02, OP-06, X-04, X-05

### VP-08 — authority is revoked while work is queued

The Finance Controller's authority is revoked after approval but before the queued operation reaches the payment boundary. The revocation explicitly invalidates that controller's unexecuted approvals.

**Expected result**

- The declared revocation rule is evaluated against the current boundary state.
- The queued operation does not execute under stale authority.
- The invalidation and containment outcome remain visible.

**Requirements:** M-04, R-02, OP-04, X-05, F-02

### VP-09 — unknown outcome is administratively closed

The provider gives conflicting observations. After five days with no alert or assigned owner, an internal workflow marks the operation closed. Later provider evidence says the payment may have completed.

**Expected result**

- The conflicting outcome remains explicit and historical state remains inspectable.
- An owner, age, next review or escalation condition, and containment posture are recorded.
- Administrative closure is rejected because the termination condition and authoritative outcome evidence are not satisfied.
- Late evidence supersedes the current outcome without erasing the earlier state or decisions.

**Requirements:** OUT-01, OUT-03, OUT-05, OUT-06, OUT-07, X-06, X-07

### VP-10 — stop requested, but an external effect remains possible

A possible account compromise is reported. New operations are blocked, one attempt is queued in an offline worker, and another has been accepted by the provider but not reconciled. The emergency stop uses the ordinary control service, which cannot yet prove that the offline worker received it.

**Expected result**

- The system distinguishes the stop request from achieved containment.
- Queued work is contained or explicitly reported as unproven.
- Provider-accepted work is reported as residual exposure, not “stopped.”
- The shared failure mode between ordinary control and containment is exposed and treated as a failed containment requirement until corrected.
- Recovery cannot repeat an operation that may already have succeeded.

**Requirements:** F-01, F-02, F-03, F-04, F-05, F-06, X-08

### VP-11 — a later mandate tries to authorize an earlier payment

A payment crosses the boundary without a valid mandate. Afterward, an administrator creates a new mandate, displays an earlier effective date, broadens the consequence envelope, and links the payment records to it.

**Expected result**

- The later mandate does not authorize the earlier operation or effect.
- Issuer, version, creation time, effective time, and change history remain inspectable.
- The original effect remains a control failure even if every record is now linked.
- Any later ratification is recorded as a later governance act, not rewritten history.

**Requirements:** M-01, M-03, M-04, P-05, X-01, X-06

### VP-12 — technical acceptance is treated as payment confirmation

The provider API returns HTTP 200, assigns a payment ID, and reports `accepted_for_processing`. Delivery of a later webhook is queued. The declared evidence model requires a provider settlement record matched to the authorized operation before classifying the payment effect as complete, but the internal workflow immediately marks the operation completed and closes it.

**Expected result**

- HTTP success, the payment ID, and queued webhook establish transport or processing states, not the completed payment effect.
- The outcome remains provisional or unresolved until evidence authoritative for the specific effect supports another state.
- The workflow does not claim completion or closure and preserves an owner, review condition, and containment posture while the effect remains unknown.
- A retry is not justified merely because authoritative confirmation has not yet arrived.

**Requirements:** OUT-01, OUT-02, OUT-03, OUT-06, OUT-07, F-05

### VP-13 — the reconciliation executor decides a consequence without authority

The Reconciliation Executor queries the provider and accounting systems and finds conflicting evidence about whether the payment completed. Its role permits evidence collection and technical reconciliation only. Without involving the Payment Consequence Owner, it accepts the exposure, schedules a retry, and closes the operation.

**Expected result**

- The Reconciliation Executor may collect, correlate, and report the conflicting evidence.
- Technical reconciliation responsibility does not authorize acceptance of exposure, retry, or closure.
- The outcome remains unresolved under the Payment Consequence Owner, or follows the explicit escalation path to an actor with the required authority.
- Any retry remains blocked until outcome uncertainty, effect cardinality, recovery authority, and any required new authorization are resolved.

**Requirements:** R-02, R-05, OP-03, OUT-06, OUT-07, F-05

## Assessment declaration

- **Assessment target:** synthetic target design and future implementation exercises.
- **Claim layer:** proposed design; no implementation or operating claim.
- **Assessment phase:** design until observable exercises exist.
- **System and evidence version:** this fixture, version 0.4, reviewed against PROOF v0.4.
- **Evidence provenance:** synthetic fixture text published with PROOF v0.4.

## Assessment table

An assessor should complete this table from observed evidence, not architectural intention.

| Case | Evidence inspected | Result | Unresolved subreason | Design coverage | Finding or unresolved question | Owner / exception |
| --- | --- | --- | --- | --- | --- | --- |
| VP-01 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-02 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-03 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-04 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-05 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-06 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-07 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-08 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-09 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-10 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-11 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-12 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |
| VP-13 | Synthetic expected behavior only | unresolved | design-addressed-awaiting-implementation | addressed | Boundary behavior not yet tested | — |

## Fixture pass conditions

The standard survives this fixture only if:

1. each expected result traces to one or more explicit requirements;
2. the five contracts remain distinct;
3. the Agent Systems Profile adds agent-specific obligations without replacing the core;
4. unknown and unresolved states cannot become success through silence, confidence, interface state, or age;
5. one approval cannot create more effects than the mandate permits;
6. stop language cannot hide work or effects beyond the controlled boundary;
7. later records or mandates cannot retroactively convert a control failure into an authorized effect;
8. transport or processing acknowledgement cannot substitute for evidence authoritative for the specific material outcome;
9. technical reconciliation authority cannot silently expand into authority over retry, compensation, unresolved exposure, escalation, or closure;
10. the fixture remains understandable without prescribing schemas, vendors, or architecture.

This fixture tests the wording of the standard. It is not an implementation assessment.
