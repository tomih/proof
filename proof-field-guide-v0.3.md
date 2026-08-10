# Human approval is not human control

## A field guide to the PROOF Standard for Consequential Agent Systems

Version 0.3 · Hodl · [Hodl Advisory](https://hodl.org) · CC BY 4.0

A person can approve the right sentence while the system acts on a different object. A retry can duplicate an effect. A stopped workflow can still have queued work crossing the boundary. A confident answer can rest on the wrong evidence.

PROOF is an open standard for examining that gap. It asks whether control meaning survives from mandate to evidence, authority, operation, outcome, and containment.

It does this through five contracts:

1. **Premise** — what may the system treat as true enough to act on?
2. **Role** — who or what may decide and do what?
3. **Operation** — what exact authorized object may cross the consequential boundary?
4. **Outcome** — what evidence establishes what happened?
5. **Failsafe** — what has actually been contained, and what can still happen?

The contracts share one root: an **Authorized Mandate** that states the objective, authorizing principal, hard constraints, prohibited outcomes, termination conditions, and consequence envelope.

## When to use it

Use PROOF when an agent-assisted workflow can materially affect money, access, publication, production state, external records, commitments, or another consequential decision.

It applies whether the final action is taken by a model, deterministic service, automated worker, or human using agent-prepared work. A manual click does not repair a broken control chain.

For decision-support workflows, name both the agent-produced object a person may rely on and the human act that creates the consequence. “Read-only” describes a technical permission, not whether the workflow is consequential.

PROOF is implementation-neutral. It does not prescribe a model, agent framework, database, queue, protocol, provider, cryptographic mechanism, or interface.

## The shortest useful review

### 1. Name the mandate and boundary

Write down who authorized the workflow, what it is allowed to achieve, what it must never do, and where a material effect can become real.

If the consequential boundary is vague, every later answer can sound correct while referring to a different system.

### 2. Trace the premise

List the sources, versions, effective times, assumptions, and conflicts that can change the action. Separate authoritative evidence from operator statements, derived results, model inferences, and unresolved assumptions.

Ask whether a stale, missing, or conflicting source blocks the boundary or quietly becomes somebody else's problem.

### 3. Trace the authority

Separate principal, actor, role, and credential. Tool access is not authority. Participation is not authority. Agent agreement is not authority.

Name who may propose, approve, execute, override, stop, reconcile, recover, and close—and who owns an unresolved result after everyone has gone home.

### 4. Bind the exact operation

Identify one canonical proposed operation before approval. Make every consequential parameter visible in the approval representation. Preserve the same operation identity through attempts, retries, callbacks, outcomes, containment, and closure.

Ask what invalidates approval and how duplicate or excess effects are prevented across retry, restart, concurrency, and recovery.

### 5. Define outcome evidence

Decide which evidence can establish completion, failure, rejection, partial effect, reversal, or an unresolved state—and justify why that source is authoritative for the real boundary.

A successful request, tool call, or local status change may still leave the external outcome unknown.

### 6. Test the failsafe

Name the boundary a stop controls. Distinguish refusing new work from containing queued work, running work, retries, callbacks, and effects already beyond the boundary.

Test a failure mode that could defeat both ordinary operation and containment. A stop button is not evidence that the system stopped.

### 7. Reconcile the contracts

The five contracts can each look reasonable and still disagree. Check that:

- the mandate was valid at the time of action;
- approval, operation, and attempted effect preserve the same consequential values;
- one authorization cannot create more effects than permitted;
- concurrent actions cannot jointly exceed the consequence envelope;
- corrections preserve history;
- unresolved states have owners and next actions;
- containment claims state what remains exposed.

## Questions for a team

- Which source wins when two states disagree?
- What exact object did the approver authorize?
- Can the executor act on something materially different from what was shown?
- Does a credential prove identity, authority, both, or neither?
- How many effects may one approval create?
- What evidence proves the external effect happened?
- What remains possible after the system says “stopped”?
- Who owns an unresolved result, and when must it escalate?
- Can a later policy, approval, or observation silently rewrite what happened earlier?
- Can two individually permitted operations jointly violate the mandate?

Clear answers are not control. The answers must agree, be supported by evidence, and survive contact with the actual boundary.

## What an assessment means

A PROOF assessment first declares what it is evaluating: a target design, implementation, operating workflow, advisory artifact, or public representation; whether each claim is proposed, implemented, operating, reported, or publicly represented; and the exact boundary, versions, evidence provenance, and review date.

It then records applicability, evidence, result, finding, design coverage, and any exception for each relevant requirement. Results are pass, fail, unresolved, or not applicable with a reason. An unresolved result says whether the control was not tested, evidence is missing or ambiguous, or a design is addressed but still awaits implementation. None of those states is a pass.

The assessment applies only to its declared target, boundary, evidence, version, and review date. A failed or unresolved requirement cannot be converted into a pass by documenting an exception.

A design review can therefore be useful without pretending paper controls operate. It may show that a requirement is addressed in the target design while keeping the PROOF result unresolved until a fail-capable test or runtime observation exists. An omitted or contradictory mandatory control fails at design time.

If an assessment or excerpt is published, it should identify the target, scope, version, and review date. It must not present design coverage as operating evidence or a synthetic fixture as a deployed system.

## A synthetic example

The v0.3 fixture uses a fictional vendor-payment workflow because it exposes the control chain clearly:

- a payment proposal depends on admitted invoice and vendor evidence;
- distinct roles propose and approve;
- approval binds to one exact payment operation;
- retries must not create duplicate payment effects;
- bank or ledger evidence determines the outcome;
- stopping the workflow must account for queued, running, accepted, and unresolved work.

Its job is to make the standard fail visibly when the contracts do not hold.

## How to use it

PROOF makes the control problem legible. It does not decide whether a particular architecture satisfies the requirements without examining that architecture and its evidence.

Use the field guide to find the questions. Use the normative standard to assess the requirements. Use system-specific evidence to determine what is designed, what operates, what fails, and what remains unresolved.

Created by **Hodl** and used in **[Hodl Advisory's](https://hodl.org)** approach to reviewing and designing consequential agent systems.
