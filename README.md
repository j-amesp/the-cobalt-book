# The Cobalt Book

**A vendor-neutral architecture standard for public sector workloads.**

Version 0.1 — draft for comment. Licensed under [CC BY 4.0](LICENCE.md) (text) and Apache 2.0 (code).

---

Government does not need thousands of bespoke architectures. It needs a small number of trusted patterns, implemented repeatedly, and owned by the state rather than by its suppliers.

Government treats every workload as exceptional, then wonders why delivery is slow, expensive, unauditable and permanently dependent on suppliers. This is not a technology failure. It is a classification failure with technological consequences.

The Cobalt Book classifies government workloads into a finite set of archetypes, derives a security and operational profile from each workload's data and consequence characteristics, and maps that profile to portable implementation patterns that can be satisfied on public cloud, sovereign cloud, private cloud, government-owned infrastructure or edge estates.

It standardises what a system must do and how it must behave. It does not standardise which vendor's product provides it.

> **Variation is permitted in implementation. It is not permitted in control outcomes.**

## Position

Government already holds guidance for most questions surrounding a technology investment. The Green Book governs appraisal, the Orange Book risk, the Magenta Book evaluation, the Aqua Book analytical assurance, the Teal Book project delivery, the Rose Book knowledge assets.

None of them answers what is being built and what it must be able to do.

This book is written to be used alongside them. The other books are read. This book is executed.

## How it works

A delivery team writes a declaration. The declaration is held with the code and versioned with it.

```yaml
cobalt_version: 0.1
workload:
  name: example-casework-service
  archetype: case-management
  overlays:
    - ai-assisted
  data:
    sensitivity: official-sensitive
    personal_data: true
    residency: uk
    jurisdictional_exposure: none-permitted
    retention: 7-years
    integrity: evidential
  availability:
    tier: high
    rto: 4-hours
    rpo: 15-minutes
  continuity:
    supplier_failure_tolerance: required
  access:
    internet_facing: false
    offshore_administration: prohibited
  hosting:
    portability_required: true
```

From that, the profile engine generates the control set, the approved deployment patterns, the network constraints, the assurance evidence schedule, the exit obligations, the deployment templates and an automated test suite.

The declaration is the artefact. Everything else is generated from it. Where a system and its declaration diverge, the tests fail — which is the point, and a property no assurance document has ever had.

## The taxonomy

Seven archetypes. Classification is settled by two questions, in order: who primarily consumes this, and what does it primarily do to data.

| | Archetype | Discriminator |
|---|---|---|
| A1 | Public transactional service | Public consumer, unpredictable volume, cannot be vetted |
| A2 | Internal business application | Would exist in near-identical form in any large enterprise |
| A3 | Case management | The record is evidence; decisions on it are challengeable |
| A4 | Analytical and modelling platform | Outputs are derived, inputs are someone else's authoritative data |
| A5 | Shared platform service | Consumers are services, not people; compromise cascades |
| A6 | Custodial content and records | Retention and disclosure are the purpose, not a side effect |
| A7 | Operational and mission system | Latency and integrity failures have physical consequence |

Four overlays attach to any archetype and modify the derived profile. They can never be used to argue for a new archetype.

| | Overlay | Applies when |
|---|---|---|
| O1 | AI-assisted | Inference sits in or adjacent to the decision path |
| O2 | Disconnected or edge | Must operate without reachback to its control plane |
| O3 | Cross-domain | Spans classification boundaries or partner nations |
| O4 | Life-safety or operationally critical | Failure kills people or loses the mission |

A system may hold multiple archetypes. It must then decompose into components that each hold exactly one. "We are a bit of everything" is not a classification. It is an admission that boundaries have not been drawn.

## Conformance

| Level | Meaning | Cost |
|---|---|---|
| **C1 — Declared** | A valid, machine-readable declaration exists and is held with the system | Free, self-served |
| **C2 — Verified** | The generated test suite passes against the deployed environment, continuously | Free, self-served |
| **C3 — Rehearsed** | Exit and continuity obligations demonstrated by execution, independently witnessed | Cost of the rehearsal only |

Conformance means a system's declared characteristics are true and its derived controls are in place. It does not mean the system is well designed, useful or affordable, and it does not replace accreditation or professional judgement. Overstating this is the fastest available route to discrediting the standard.

No party is authorised to sell Cobalt certification. See [LICENCE.md](LICENCE.md), Section 4.

## Rules that bind this project

These exist because a vendor-neutrality standard is worth exactly as much as the mechanisms that stop it being captured.

- **Conformance is free and self-servable.** The moment conformance requires a paid assessor, whoever owns the assessor owns government technology.
- **Contracts, not products.** If only one platform can satisfy a contract, the contract is wrong.

**Declaration of interest.** The author is employed by a major cloud and infrastructure vendor active in the public sector market. This is stated in the front matter of every release, not in a footnote. A vendor-neutrality standard authored by a vendor architect will be read as positioning unless the governance that prevents it is stated openly and can be checked. That is the correct reading. The two-implementation rule exists to answer it in engineering terms rather than in assurances.

This is not an HM Treasury, Cabinet Office or departmental publication and carries no official status.

## Contributing

Six open questions are recorded in Section 17 of the specification. They are the most useful place to start, and they are open because they are genuinely unresolved rather than as an invitation to agree.

## Citation

> Patrick, J. (2026). *The Cobalt Book: A vendor-neutral architecture standard for public sector workloads*, version 0.1. Licensed under CC BY 4.0.
