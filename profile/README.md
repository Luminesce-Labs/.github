
# Luminesce Labs (Luminesce Limited)

**Transparency starts where opacity ends.**
---

**AxoDen** is Luminesce Labs’ product line for deterministic assurance and security middleware — starting with **AxoDen Kernel** and delivered through wedge products (Forensic Intelligence, Spectrum Bridge, Grid Flight Recorder).  

Jump to: [AxoDen Kernel](#1-axoden-kernel-implemented--canonical-baseline-v081) · [Wedges](#2-axoden-forensic-intelligence-operationalised--locally-deployed)

---

## Portfolio Overview (Kernel → Wedges)

AxoDen is structured as:
1) **AxoDen Kernel** (shared control + evidence substrate)
2) **Domain wedges** that import the kernel so semantics, evidence handling, and enforcement **don’t drift per product**. 

---

## 1) AxoDen Kernel (Implemented / Canonical baseline v0.8.1)

### What it is
A **deterministic control and assurance layer** that downstream AxoDen products import (or consume as a sidecar) so:
- action/state/reason/metric vocabulary is registry-governed and immutable
- evidence identity is canonicalized and ledgered
- enforcement is **fail-closed by contract**
- conformance profiles bind thresholds and portability across domains
- replay + certification-oriented artifacts are first-class outputs 

### What exists at v0.8.1 (product surface)
- normative contract + machine-readable registries / schemas
- Python SDK (evidence, control, topology, reset, certificate workflows)
- reference API-only sidecar (decision + MQ evaluation endpoints)
- deterministic validation + replay tooling + evidence-pack generation
- certification templates and cross-environment replay checks 

### What it is not
- Not “trust us”: the point is **control-by-contract** + **replayable evidence**
- Not a model benchmark repo or prompting toolkit
- Not a feature bundle: it’s the substrate that makes multiple products easier to trust and certify 

---

## 2) AxoDen Forensic Intelligence (Operationalised / Locally Deployed)

### What it is
Forensic middleware that sits **between your SIEM/SOAR and analyst workflow**. It produces a structured, replayable, audit-grade investigation package via **deterministic reasoning (graph + statistics)**—not model inference. 

Key properties (customer-safe):
- deterministic, reproducible outputs (identical inputs → identical artefacts)
- local deploy (Docker) with CLI + API modes
- explicit admissibility + deduplication with logged reason codes 

### What it is not
- Not a SIEM/SOAR replacement (it sits alongside them)
- Not “LLM reasoning”: if an LLM is used, it is **non-authoritative** and cannot change claim labels, ledgers, or statistical outputs 

---

## 3) AxoDen Spectrum Bridge (MVP)

### What it is
A deterministic assurance layer between **RF sensing (antenna/SDR/receiver chain)** and downstream AI. It ensures the model only receives **admissible, replayable, audit-grade Evidence Objects (EOs)** under a declared operating envelope. 

Core contract behaviors (customer-safe):
- profile-bound determinism for evidence formation and replayability
- explicit envelope states: **NOMINAL / DEGRADED / SAFE_MODE / HALT**
- deterministic gates (integrity, determinism/profile, throughput/budget, independence/correlation) 

### What it is not
- Not an AI model replacement
- Not “best-effort evidence”: when the contract is violated, it **degrades, inhibits delivery, or halts** with an auditable record 

---

## 4) AxoDen Grid Flight Recorder (Ideation)

### What it is
A runtime execution assurance layer for critical cyber-physical systems (e.g., microgrids / industrial control) that sits in the actuation path and enforces:

> **No irreversible physical actuation occurs unless safety, policy, and evidence conditions are valid at the moment of execution.** :contentReference[oaicite:20]{index=20}

It addresses the **Zombie Intent Hazard** by making intent session-scoped and requiring fresh validation after restart/outage before actuation. :contentReference[oaicite:21]{index=21}

Outputs (customer-safe):
- machine-verifiable decision record (**CAR**) and a reproducible **Replay Pack** for independent review 

### What it is not
- Not “just logging”: it combines deterministic gating with evidence artifacts for third-party replay :contentReference[oaicite:23]{index=23}

---

## Reading Paths (pick one)

### If you’re evaluating the core thesis (15–30 mins)
1) AxoDen Master Reference (what it is / isn’t; pillars; wedges)
2) MQ + ARV consolidated controls (control vocabulary + enforcement semantics)
3) ASIL-M (multi-root trust gate + CAR artifacts) 

### If you’re technical / building
1) Engine Room (canonical formula IDs + determinism rules)
2) ER-topo.cert spec (topological evidence certification artifact)
3) Controls (MQ/ARV) + your conformance profile bindings 

### If you’re procurement / assurance / audit
1) Micro-Grid Safety / Grid Flight Recorder (evidence-or-actuate framing; replay verifier posture)
2) Zombie Intent Hazard (why write-ahead audit can be unsafe without session binding)
3) ASIL-M (multi-root trust, CAR, and independence constraints) 

---

## Publications (Zenodo)

> Access notes: some items are Restricted / Controlled due to dual-use sensitivity and patent activity; review access is available under appropriate collaboration frameworks. 

(See the existing list below—kept as-is.)

---

## Collaboration

Open to:
- Mission partnerships (government / defence)
- Academic research partnerships
- Industrial pilots (security operations, RF-AI, regulated infrastructure)

Evaluation pack starting point:
**use-case → conformance profile → evidence artifacts expected (CAR / replay pack / certificates) → disclosure constraints** 

---

## Licensing

Luminesce Labs uses a dual-licensing model:
- Free for academic research and education (subject to licence terms)
- Commercial licensing required for business use

Implementation repos are released progressively; patent-protected components may remain private during filing. 

---

## Contact

Erkan Yalcinkaya, Founder and Principal Systems Architect, Luminesce Limited  
Luminesce Limited (UK) • id 15317429 • VAT 474096567  
D-U-N-S® Number: 231242963 • ISNI: 0000000529733416 • Ringgold ID: 847099 

---

© Luminesce Limited 2023–2026
