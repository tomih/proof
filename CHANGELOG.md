# Changelog

All public changes to PROOF are recorded here.

## 0.4.0 — 2026-10-20

- Clarified that technical reconciliation and authority over its business or operational consequences are distinct responsibilities, even when one actor is explicitly authorized to hold both.
- Clarified that transport or processing acknowledgement does not establish an intended effect unless the evidence is authoritative for that specific outcome.
- Made the authority boundary fail-capable under AS-03 and added synthetic negative cases for acknowledgement without authoritative confirmation and reconciliation without consequence authority.
- This release incorporates an architectural gap originally identified by **Jeffrey Low** during an independent review of PROOF. We thank Jeffrey for his contribution. See [issue #1](https://github.com/tomih/proof/issues/1) and [PR #2](https://github.com/tomih/proof/pull/2).
- Supersedes v0.3.1 as the current canonical release. Earlier releases remain available as immutable history.

## 0.3.1 — 2026-08-10

- Added the missing Hodl.org link to authorship, publisher, and attribution surfaces.
- Updated patch-release metadata and provenance; normative requirements and fixture cases are unchanged.

## 0.3.0 — 2026-08-10

- Initial public release.
- Defined Premise, Role, Operation, Outcome, and Failsafe contracts under one Authorized Mandate.
- Published 55 stable normative requirements, a shared lifecycle model, cross-contract invariants, and the Agent Systems Profile.
- Separated design coverage from implementation and operating evidence.
- Added assessment targets, claim layers, evidence provenance, unresolved subreasons, and fail-capable behavioral-evidence requirements.
- Added an 11-case synthetic vendor-payment fixture.
