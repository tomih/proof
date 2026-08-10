# The PROOF Standard for Consequential Agent Systems

**Human approval is not human control.**

PROOF is an open, implementation-neutral standard for describing and reviewing the control chain around consequential agent operations. It was created by **Hodl** and is used in **[Hodl Advisory's](https://hodl.org)** approach to reviewing and designing consequential agent systems.

PROOF stands for five contracts:

1. Premise — what the system may treat as true enough to act on.
2. Role — who or what may decide and do what.
3. Operation — what exact authorized object may cross a consequential boundary.
4. Outcome — what evidence establishes what happened.
5. Failsafe — what contains further action and governs recovery.

## Why PROOF exists

Important standards and frameworks already address AI governance, management, security, and adversarial risk:

- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) helps organizations manage risks and trustworthiness across AI systems.
- [ISO/IEC 42001](https://www.iso.org/standard/42001) defines requirements for an AI management system.
- [OWASP Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) identifies critical security risks in agentic systems.
- [MITRE ATLAS](https://atlas.mitre.org/) catalogs adversarial tactics and techniques targeting AI-enabled systems.

In [Hodl Advisory's](https://hodl.org) architecture work, we needed an additional, compact way to test one specific problem: whether a consequential agent operation remains bound to admissible premises, current authority, one canonical operation, authoritative outcome evidence, and a credible failsafe.

We did not find an existing framework that provided this exact consequential-operation lifecycle test. PROOF addresses that specific gap while complementing broader governance and security frameworks.

## What PROOF does

PROOF provides stable requirements and evidence obligations for tracing control from mandate and premise through authority, operation, outcome, and containment. It can support design and assessment, but it does not itself certify a system or replace system-specific security, legal, regulatory, or operational validation.

The distinction matters: documentation can show that a control is designed; only attributable evidence can show that it operates. PROOF keeps those claims separate.

## Release contents

- `proof-standard-v0.3.md` — normative standard and guidance.
- `proof-field-guide-v0.3.md` — concise human-readable guide.
- `fixtures/vendor-payment/fixture-vp-001-v0.3.md` — synthetic fixture.
- `LICENSE` and `NOTICE.md` — one CC BY 4.0 license and attribution terms.
- `CITATION.cff` — citation metadata.
- `CHANGELOG.md`, `GOVERNANCE.md`, and `CONTRIBUTING.md` — version and contribution rules.
- `release-manifest-v0.3.json` and `SHA256SUMS-v0.3` — versioned release provenance.

The vendor-payment fixture contains 11 synthetic cases that trace expected results to applicable requirements within the 55-ID v0.3 requirement set. It tests the wording and application of the standard without prescribing an implementation.

## Authorship and license

Created by **Hodl** and used in **[Hodl Advisory's](https://hodl.org)** approach to reviewing and designing consequential agent systems. The release materials are licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/). Attribution is required. See `NOTICE.md` for the preferred form.

The license covers the released material. Attribution does not imply Hodl's endorsement of a modified work.
