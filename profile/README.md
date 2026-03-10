# Luminesce Labs | AxoDen
*Luminesce Limited (UK)*

**Transparency starts where opacity ends.**

**AxoDen** is Luminesce Labs' product line for **deterministic assurance and security middleware**; built around the **AxoDen Kernel** and delivered through domain wedge products: **Forensic Intelligence**, **Spectrum Bridge**, and **Grid Flight Recorder**.

Jump to: [AxoDen Kernel](#1-axoden-kernel) · [Wedge products](#2-wedge-products) · [Publications](#publications) · [About](#about-luminesce-limited) · [Contact](#contact)

---

## What we build

AxoDen turns safety and security requirements into **contract-bound runtime controls** with **audit-grade, replayable evidence**.

Three design principles govern every product:

**Kernel-first.** A shared control vocabulary, evidence identity rules, and determinism contracts are fixed at the platform layer. Domain products import these rather than re-implementing them, so semantics and audit posture cannot drift across deployments.

**Fail-closed by contract.** When the declared operating envelope is violated, the system degrades, inhibits, or halts — and records why. Safe degradation is not a fallback; it is a first-class output.

**Replay over rhetoric.** Every decision is designed to be independently re-run and assessed against the original evidence. Replayability is the assurance claim, not a confidence score.

> What AxoDen is not: not a "trust us" AI safety claim, not a model benchmark, and not a SIEM/SOAR replacement.

---

## Portfolio overview

| Product | Role | Maturity |
|---|---|---|
| **AxoDen Kernel** | Shared control and evidence substrate | Implemented — canonical baseline v0.8.1 |
| **Forensic Intelligence** | Deterministic forensic middleware for security operations | Operationalised — locally deployed |
| **Spectrum Bridge** | Deterministic evidence layer between RF sensing and AI | MVP |
| **Grid Flight Recorder** | Pre-actuation gating for cyber-physical systems | Ideation |

Wedge products import the kernel so enforcement semantics and evidence handling stay consistent across domains.

> **[Explore the mathematical lineage interactively →](https://luminesce-labs.github.io/axoden-math-foundations)**  
> Click any node to trace how 300+ years of mathematics — from Euler and Shannon to 2-adic metrics and rotation systems — compose into the AxoDen pillars.

---

## 1. AxoDen Kernel

**Maturity: Implemented — canonical baseline v0.8.1**

The kernel is the control and assurance layer that downstream AxoDen products import (or consume as a sidecar). It is licensable infrastructure: a deterministic kernel for decisioning, auditability, and fail-closed control that can be embedded via SDK or deployed as a standalone sidecar service.

**What it fixes at the platform layer:**

- Action, state, reason, metric, and profile vocabulary is registry-governed — IDs are immutable and cannot drift between products or deployments.
- Evidence identity is canonicalised (RFC 8785 JCS + SHA-256), hash-chained, and ledgered — every decision record is replayable.
- Enforcement is fail-closed by contract — invalid or unsafe conditions produce a logged halt, not a best-effort output.
- Conformance profiles bind thresholds and portability rules — the same kernel semantics apply across domains without rewriting the control plane.
- Replay packs and certification-oriented artefacts are first-class outputs, not documentation afterthoughts.

**Current state (v0.8.1):**

- Normative contract: `KERNEL_CONTRACT.md`
- Machine-readable registries, evidence schemas, and kernel I/O schemas
- Python SDK for evidence, control, topology, reset, and certificate workflows
- Reference sidecar API with health, readiness, config validation, decision, and MQ evaluation endpoints
- Deterministic validation, replay, and evidence-pack generation scripts
- Certification templates, certified corpus vectors, and cross-environment replay checks
- 316 passing tests (local validation run, 2026-03-08); 309 recorded at v0.8.1 release
- Five conformance profiles: `cix`, `cix-1`, `sfa`, `regnav`, `spectrum`

**Typical outputs:**

- Machine-verifiable decision records (CAR-style artefacts where applicable)
- Replay packs for independent verification
- Certificates and topology/evidence artefacts (profile-dependent)

**Defensibility.** The kernel is not a feature bundle. Its value is that it codifies difficult-to-recreate operational guarantees around determinism, policy invariants, evidence integrity, replayability, and topology-aware structural assurance. One kernel can support multiple vertical products through conformance profiles, keeping core policy logic centralised even when exposing APIs or shipping self-hosted runtimes.

---

## 2. Wedge products

### 2.1 AxoDen Forensic Intelligence

**Maturity: Operationalised — locally deployed**

Deterministic forensic middleware that sits between your SIEM/SOAR and analyst workflow. It does not replace those platforms. It produces a structured, replayable, audit-grade investigation package generated by deterministic reasoning (graph + statistics), not model inference.

**The problem it addresses.** SOC teams face an evidence-structure problem, not only an alert-volume problem. Raw alerts do not form a traceable investigation record. Triage outcomes are frequently non-reproducible. Free-form summaries mix observation with inference. Root-cause attribution lives in analyst memory rather than in a verifiable artefact bundle.

**Five deterministic capabilities:**

1. **Pre-triage filtration.** Events are classified into admissibility bands before analysis. Every exclusion is logged with a reason code to an append-only ledger — noise reduction with a complete audit trail.
2. **Conflict-free deduplication.** Ingestion-layer deduplication resolves duplicate and near-identical alerts deterministically. Re-running the same dataset yields identical results.
3. **Patient Zero hunting.** Two intentionally separate analyses: temporal precedence (earliest causally reachable node) and connectivity rank (node whose removal most disrupts campaign reachability). Kept separate to prevent confusing "earliest" with "most structurally central."
4. **Parallel campaign isolation.** Simultaneous attacks are separated into distinct investigation threads using connected-components decomposition, preventing timeline and evidence contamination between concurrent campaigns.
5. **Predictive blast-radius analysis.** Graph topology estimates likely future lateral movement paths and models the expected blast radius for control-node removal, enabling containment prioritisation.

**Claim governance.** Every report enforces a strict auditable distinction: OBSERVED (directly supported by raw events), INFERRED (graph-derived hypotheses, explicitly labelled), VERIFIED (only when claims pass explicit statistical gates — CMI + permutation p-value + bootstrap confidence intervals). "Verified" is tied to emitted artefacts, not a model confidence score.

**The three-ledger chain** links stage-1 admissibility decisions, kernel admission decisions, and ARV gate-chain decisions — non-repudiable and hash-chained throughout.

**Artefact bundle per campaign:** forensic assessment report, machine-readable forensic ledger, interactive campaign topology graph, campaign snapshot, temporal analysis JSON, statistical verification outputs, and a run-level reproducibility manifest.

**Deployment:** local Docker, CLI and API modes. Sits alongside existing SOC tooling without replacement.

**Validation (public dataset):** end-to-end run achieved approximately 95% event reduction via deduplication and admissibility gating, with multiple isolated campaign findings and full artefact bundle emission.

> What it is not: not a SIEM/SOAR replacement; not "LLM reasoning" as an authoritative source of truth.

---

### 2.2 AxoDen Spectrum Bridge

**Maturity: MVP**

Deterministic assurance middleware between RF sensing (antenna/SDR/receiver chain) and downstream AI. It does not replace the AI model. It protects the AI by ensuring the model only receives admissible, replayable, audit-grade evidence under a declared operating envelope.

**The structural safety gaps it addresses:**

- **Physical-domain mismatch.** RF sensing operates in continuous-time physics; AI pipelines operate on discretised features. Without contract-bound feature formation, downstream decisions become difficult to reproduce and certify.
- **Throughput mismatch.** RF sample rates can exceed downstream ingestion capacity by orders of magnitude. Ad-hoc downsampling introduces hidden failure modes without explicit signalling to the decision system.
- **Silent preprocessing drift.** Floating-point and hardware-dependent preprocessing can drift across architectures and builds, breaking repeatability and undermining certification.
- **Common-mode vulnerability.** Multi-stage RF pipelines often share upstream assumptions. When those assumptions fail — under jamming, spoofing, interference, or adversarial waveforms — multiple checks can fail together. Without engineered independence, redundancy is superficial.

**Architecture:** two coupled pillars. Pillar A is active control — a deterministic gatekeeper that evaluates signal integrity and pipeline constraints, then either passes admissible evidence or degrades/halts delivery. Pillar B is cryptographic compliance — each admitted Evidence Object (EO) is canonicalised, cryptographically bound, and emitted alongside a run manifest.

**Four-state operating envelope:** NOMINAL / DEGRADED / SAFE_MODE / HALT. Every transition is logged with the predicates that triggered it.

**Admissibility gates (G1–G4):**
- G1 — Signal integrity: rejects evidence that violates declared SNR/congestion/jam bounds
- G2 — Determinism and profile: enforces declared execution profile and stable encoding rules
- G3 — Throughput and budget: enforces explicit admission control against rate and budget constraints
- G4 — Independence/correlation: enforces engineered independence checks to limit common-mode failure risk

**Evidence Objects** are bounded, schema-versioned, cryptographically bound, and carry the envelope state at emission time. They enable independent replay, procurement-grade traceability, and controlled AI model upgrades without losing continuity of the physical evidence baseline.

> What it is not: not an AI model replacement; not best-effort evidence when contracts are violated.

---

### 2.3 AxoDen Grid Flight Recorder

**Maturity: Ideation**

Runtime execution assurance for cyber-physical systems (microgrids, industrial control). It sits in the actuation path and enforces one contract:

> **No irreversible physical actuation occurs unless safety, policy, and evidence conditions are valid at the moment of execution.**

**The Zombie Intent Hazard.** Many critical systems implement write-ahead logging: record intent, then execute. This pattern introduces a specific hazard. An intent recorded at time t₀ may be replayed after an outage or restart, executing against physical conditions that have changed by time t₁. Grid Flight Recorder requires fresh, session-bound validation at the moment of execution — not only at the moment of logging.

**Three core capabilities:**

1. **Pre-actuation gating (fail-closed).** Before a command reaches a physical actuator, the system evaluates safety validity, policy validity, and evidence validity. If conditions are not met, the action is blocked and the decision is recorded.
2. **Session-bound intent validation.** Intent is scoped to a session rather than indefinitely replayable. After a restart or power loss, stale intents are invalid unless explicitly re-authorised under current conditions.
3. **Evidence-native outputs.** Each gated decision can emit a Canonical Attestation Record (CAR) and a Replay Pack — reproducible bundles that support independent review without requiring access to the live production environment.

**Operating envelope:** NOMINAL / DEGRADED / SAFE_MODE / HALT. All transitions are recorded with the predicate that triggered them.

**High-value use cases:** microgrid islanding and reconnection; industrial process actuation; safety interlocks for autonomous operations; incident forensics and dispute resolution; compliance assurance workflows.

> What it is not: not "just logging" — it is deterministic gating plus replayable evidence artefacts.

---

## Publications

The following DOI-registered publications are the formal mathematical and specification foundations that AxoDen is built from. They cover topology-of-reasoning constructs, evidence object semantics, admissibility, determinism, and certification and replay requirements.

AxoDen Kernel and wedge products are implementations and conformance profiles derived from this canon. Product artefacts map runtime controls and outputs back to these foundations.

> Access note: some items are Restricted/Controlled due to dual-use sensitivity and patent activity. Review access is available under appropriate collaboration frameworks.

### Foundational theories

| Title | DOI |
|---|---|
| The Thermodynamics of Agency: Why Unbounded Intelligence Fails and How Architecture Restores Control | [10.5281/zenodo.18146418](https://doi.org/10.5281/zenodo.18146418) |
| Information Physics for Safety-Critical AI | [10.5281/zenodo.18876342](https://doi.org/10.5281/zenodo.18876342) |

### Compositional framework (EBDP, EFI, and unified backbone)

| Title | DOI |
|---|---|
| Entropy-Bounded Data Pipelines and Entropy-Frugal Intelligence: A Compositional Framework for Quantitative Assurance in Industrial AI Systems | [10.5281/zenodo.17709557](https://doi.org/10.5281/zenodo.17709557) |
| AxoDen Unified Mathematical Backbone: A Compositional Theory of Entropy-Bounded Pipelines, Cognitive Coherence, Engineered Independence | [10.5281/zenodo.18633407](https://doi.org/10.5281/zenodo.18633407) |

### Topology-of-Reasoning (TOR)

| Title | DOI |
|---|---|
| The Topology of Reasoning: Structural Invariants for Certifiable AI — Part I | [10.5281/zenodo.18769043](https://doi.org/10.5281/zenodo.18769043) |
| The Topology of Reasoning: Structural Invariants for Certifiable AI — Part II | [10.5281/zenodo.18862777](https://doi.org/10.5281/zenodo.18862777) |

### Adversarial robustness, Coprime Factors, and multi-root trust (ASIL-M)

| Title | DOI |
|---|---|
| ASIL-M: AI Safety Integrity Level — Multi-Root Trust Architecture | [10.5281/zenodo.17690760](https://doi.org/10.5281/zenodo.17690760) |
| Coprime-Factor Security Architecture | [10.5281/zenodo.17690358](https://doi.org/10.5281/zenodo.17690358) |

### Quantum-classical hybrid safety

| Title | DOI |
|---|---|
| A Compositional Information-Theoretic Framework for Hybrid Quantum-Classical AI Safety | [10.5281/zenodo.18213048](https://doi.org/10.5281/zenodo.18213048) |
| Systems and Certification Engineering, Runtime Enforcement, and Assurance for Hybrid Quantum-Classical AI Safety | [10.5281/zenodo.18282922](https://doi.org/10.5281/zenodo.18282922) |

### Failure modes and hazard analysis

| Title | DOI |
|---|---|
| The Zombie Intent Hazard: A Safety Violation in Write-Ahead Audit Architectures for Safety-Critical Systems | [10.5281/zenodo.18768569](https://doi.org/10.5281/zenodo.18768569) |

### Applied frameworks: grid, RF, and operational forensics

| Title | DOI |
|---|---|
| AxoDen Spectrum Bridge: RF-AI Bridge (Patent) | [10.5281/zenodo.18863188](https://doi.org/10.5281/zenodo.18863188) |
| AxoDen Grid Flight Recorder: Micro-Grid Safety | [10.5281/zenodo.18863456](https://doi.org/10.5281/zenodo.18863456) |
| AxoDen Forensic Intelligence: Deterministic Investigation Artifacts for Security Operations | [10.5281/zenodo.18260373](https://doi.org/10.5281/zenodo.18260373) |

### Certification artefacts and evidence topology

| Title | DOI |
|---|---|
| ER-topo.cert v0.3: A Certification Artifact for Topological Evidence in Replayable Assurance | [10.5281/zenodo.18320118](https://doi.org/10.5281/zenodo.18320118) |
| The Engine Room: Canonical Formula IDs and Determinism Rules for AxoDen Kernel | [10.5281/zenodo.18471273](https://doi.org/10.5281/zenodo.18471273) |
| Canonical Controls: MQ/ARV Consolidated Control Vocabulary for AxoDen Kernel | [10.5281/zenodo.18498971](https://doi.org/10.5281/zenodo.18498971) |

---

## About Luminesce Limited

Luminesce Limited is a UK-based deep-tech company founded by **Erkan Yalcinkaya** (Engineering Physicist), with 25 years' experience delivering technology in regulated, safety-critical environments (including Unilever, GSK, Fresenius Group, Telefónica, Accenture).

That background shaped a single design requirement: **assurance evidence must be the kind that assessors, regulators, and governance boards already know how to evaluate** — replayable, auditable, and contract-bound.

Luminesce combines mathematical rigour (first-principles constraints and evidence formation) with deployment reality (what regulated operations require in practice). AxoDen is the result: a kernel-and-wedges product line for deterministic assurance middleware.

---

## Collaboration

Open to:

- Mission partnerships (government and defence)
- Academic research partnerships
- Industrial pilots (security operations, RF-AI integration, regulated infrastructure)

A typical starting point for evaluation: **use-case → conformance profile → evidence artefacts expected (CAR / replay pack / certificates) → disclosure constraints**.

---

## Licensing

Luminesce Labs uses a dual-licensing model:

- Free for academic research and education (subject to licence terms)
- Commercial licensing required for business use

Implementation repositories are released progressively. Patent-protected components may remain private during filing.

---

## Contact

**Erkan Yalcinkaya**, Founder and Principal Systems Architect, Luminesce Limited

Luminesce Limited (UK) · Company no. 15317429 · VAT 474096567  
D-U-N-S® Number: 231242963  
ISNI: 0000000529733416  
Ringgold ID: 847099  
ORCID: [0009-0008-6435-3530](https://orcid.org/0009-0008-6435-3530)  
LinkedIn: [eyk](https://www.linkedin.com/in/eyk/)

---

© Luminesce Limited 2023–2026
