# Luminesce Labs

**Transparency starts where opacity ends.**

Luminesce Labs is a research programme by **Luminesce Limited (UK)** focused on **deterministic AI assurance and security**: architectures and middleware that turn “AI safety” from policy and heuristics into **runtime-enforceable constraints**, with **audit-grade evidence** for regulated and safety-critical deployment.  
(Primary body of work: **AxoDen**.) 

---

## Why Luminesce Labs Exists

Modern AI and autonomous systems fail in predictable ways that “better prompts” and post-hoc review cannot reliably fix:

- **Unbounded uncertainty propagation** across pipelines (noise accumulates until the system is no longer verifiable).   
- **Fabrication / hallucination risk** when model influence exceeds what evidence can support.   
- **Common-mode failures** (monocultures) where “redundant” components fail together because they share roots and dependencies.   
- **Safety hazards in audit + actuation loops** (e.g., stale intent after reboot). :contentReference[oaicite:5]{index=5}  

Luminesce Labs develops **contract-first** safety mechanisms that **degrade safely**, remain **replayable**, and produce **evidence artifacts** a third party can verify. 

---

## What You’ll Find Here

### 1) AxoDen Kernel-aligned runtime assurance (Implemented / Canonical)
A compositional framework and control plane for deterministic assurance:

- **EBDP — Entropy-Bounded Data Pipelines** *(Academic-DOI / Canonical)*: stage + global entropy bounds for pipeline uncertainty control.   
- **EFI — Entropy-Frugal Intelligence** *(Academic-DOI / Canonical)*: bounds model influence; detects “surplus” beyond evidence support.   
- **CFS — CoPrime Factor Security** *(Academic-DOI / Canonical)*: engineered independence across roots (models, vendors, toolchains, pipelines).   
- **ASIL-M — AI Safety Integrity Level (Multi-Root Trust)** *(Academic-DOI / Canonical)*: multi-root attestation + correlation-bounded trust gating.   
- **MQ + ARV + VSR loop** *(Implemented, kernel contract)*:
  - **MQ (Monitoring Quad)**: runtime evidence/consistency/novelty/independence telemetry.   
  - **ARV (Admission Resilience Validator)**: deterministic enforcement actions **EXECUTE | THROTTLE | ROLLBACK | HALT | RESET**.   
  - **VSR states**: **NOMINAL | DEGRADED | SAFE_MODE | HALT**.   

### 2) Applied wedges (domain deployments)
- **Cyber defense / ransomware containment** *(Academic-DOI + scenario-qualified implementation posture)*.   
- **Spectrum Bridge (RF → AI Evidence Boundary Layer)** *(Academic-DOI / Patent posture noted)*: deterministic RF evidence formation + envelope-honest degradation.   
- **Micro-Grid Safety / Grid Flight Recorder** *(Academic-DOI / procurement-ready spec posture)*: deterministic actuation gating, session-bound intent, replay packs, and explicit handling of “Zombie Intent” hazards.   

---

## What this repository is not

- Not a “prompting toolkit” or model benchmark repo.
- Not a claim of perfect detection.
- Not “trust us”: the goal is **control-by-contract**, **auditability**, and **safe degradation** when operating envelopes are exceeded.   

---

## Reading Paths (pick one)

### If you’re evaluating the *core thesis* (15–30 mins)
1) **AxoDen Master Reference** (what it is / isn’t; pillars; wedges). :contentReference[oaicite:18]{index=18}  
2) **MQ + ARV consolidated controls** (control vocabulary + enforcement semantics). :contentReference[oaicite:19]{index=19}  
3) **ASIL-M** (multi-root trust gate + CAR artifacts).   

### If you’re technical / building
1) **Engine Room** (canonical formula IDs + determinism rules). :contentReference[oaicite:21]{index=21}  
2) **ER-topo.cert spec** (topological evidence certification artifact). :contentReference[oaicite:22]{index=22}  
3) **Controls (MQ/ARV)** + your conformance profile bindings. :contentReference[oaicite:23]{index=23}  

### If you’re procurement / assurance / audit
1) **Micro-Grid Safety / Grid Flight Recorder** (evidence-or-actuate framing; replay verifier posture). :contentReference[oaicite:24]{index=24}  
2) **Zombie Intent Hazard** (why write-ahead audit can be unsafe without session binding). :contentReference[oaicite:25]{index=25}  
3) **ASIL-M** (multi-root trust, CAR, and independence constraints).   

---

## Publications (Zenodo)

> Access notes: some items are **Restricted / Controlled** due to dual-use sensitivity and patent activity; review access is available under appropriate collaboration frameworks. :contentReference[oaicite:27]{index=27}  

### 2026 (latest)
- **Information Physics for Safety-Critical AI** — Zenodo DOI: `10.5281/zenodo.18876342` :contentReference[oaicite:28]{index=28}  
- **AxoDen Grid Flight Recorder – Micro-Grid Safety** — `10.5281/zenodo.18863456`   
- **AxoDen Spectrum Bridge (RF–AI Bridge) (Patent)** — `10.5281/zenodo.18863188`   
- **THE TOPOLOGY OF REASONING — Part I** — `10.5281/zenodo.18769043` :contentReference[oaicite:31]{index=31}  
- **THE TOPOLOGY OF REASONING — Part II** — `10.5281/zenodo.18862777`   
- **The Zombie Intent Hazard** — `10.5281/zenodo.18768569`   
- **AxoDen Unified Mathematical Backbone** — `10.5281/zenodo.18633407` :contentReference[oaicite:34]{index=34}  
- **Hybrid Quantum–Classical AI Safety (framework)** — `10.5281/zenodo.18213048` :contentReference[oaicite:35]{index=35}  
- **Hybrid Quantum–Classical AI Safety (systems & certification)** — `10.5281/zenodo.18282922` :contentReference[oaicite:36]{index=36}  

### 2025 (selected)
- **Entropy-Bounded Data Pipelines & Entropy-Frugal Intelligence** — `10.5281/zenodo.17709557` :contentReference[oaicite:37]{index=37}  
- **ASIL-M: AI Safety Integrity Level (Multi-Root Trust)** — `10.5281/zenodo.17690760`   
- **Coprime-Factor Security Architecture** — `10.5281/zenodo.17690358`   

---

## Collaboration

Open to:
- Mission partnerships (government / defence)
- Academic research partnerships
- Industrial pilots (security operations, RF-AI, regulated infrastructure)

If you want an evaluation pack, typical starting point is: **use-case → conformance profile → evidence artifacts expected (CAR / replay pack / certificates) → disclosure constraints**.   

---

## Contact

Erkan Yalcinkaya, Founder and Principal Systems Architect, Luminesce Limited
Luminesce Limited (UK) • id 15317429 • VAT 474096567
D-U-N-S® Number: 231242963
ISNI: 0000000529733416
Ringgold ID: 847099

---

## Licensing

Luminesce Labs uses a dual-licensing model:
- Free for academic research and education (subject to licence terms)
- Commercial licensing required for business use

Implementation repositories are released progressively; patent-protected components may remain private during filing.

---

© Luminesce Limited 2023–2026
