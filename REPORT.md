# Deterministic Trust Layers for AI Outputs: An Independent Audit Milestone Report

**PHM-Audit | Independent release, timed to coincide with APEC Leaders' Week in Shenzhen (Nov 17-19, 2026)**

> **Disclaimer**: This is an independent report by PHM-Audit. We are not affiliated with, endorsed by, or acting for APEC, Microsoft, NVIDIA, promptfoo, or any other named organization; names and references are for identification and context only. This is an independent technical review, not a formal audit, certification, legal, medical, or investment advice. Claims are as of the publication date. The APEC-week timing is editorial and does not imply any APEC review or approval.

---

## Why This, Why Now

As APEC economies meet in Shenzhen this week to advance cooperation on artificial intelligence, publicly available APEC materials this year have repeatedly discussed **trust and technical standards** as central themes of AI governance. In our own engagement with regional stakeholders, fragmented AI assurance requirements have been repeatedly raised as a cross-border deployment concern.

This short report documents what a small independent research team (one researcher + AI-assisted engineering) has achieved in under five months by focusing on exactly one capability: **deterministic, physics- and rules-based validation of AI system outputs and data** — a trust layer that does not rely on another large model, is designed to produce reproducible verdicts for identical inputs under a fixed rule set and configuration, and attaches a hash-anchored evidence chain to every result.

We share our milestone list openly because "trust" in AI should mean *verifiable* trust, and verifiability begins with public, reproducible records.

---

## Milestones (public evidence where linked)

### 1. Our deterministic scorer was merged into Microsoft PyRIT's mainline

Microsoft PyRIT is a widely used open-source red-teaming framework for generative AI. Our physics-consistency scorer (deterministic validation of AI outputs against physical and logical constraints) was reviewed by PyRIT creator Richard Lundeen through four rounds of feedback (including issues he identified and pushed fixes for), and **merged into the official mainline** (PR #3507, Nov 2026). Microsoft's Agent Framework documentation independently describes this category of capability as a "deterministic action-boundary validator."

- Evidence: https://github.com/microsoft/PyRIT/pull/3507 (merged)

### 2. NVIDIA fixed demonstration-dataset issues we reported

We ran schema-completeness, per-frame timestamp, and index-continuity checks on the NVIDIA Isaac-GR00T demonstration datasets (humanoid robotics). We found missing `timestamp`/`frame_index` fields that made the declared frame rate unverifiable for one dataset family. NVIDIA's team subsequently fixed the demonstration dataset (commit 9652f0d) and closed the issue as resolved.

- Evidence: https://github.com/NVIDIA/Isaac-GR00T/issues/807

### 3. Our rule set was independently re-implemented into the promptfoo open-source ecosystem

A third-party developer has proposed porting our physics/bounds assertion rules (light-speed limits, thermodynamic bounds, etc.) into JavaScript for the promptfoo red-teaming platform, **crediting PHM-Audit as the reference implementation** in the file header. The PR is under maintainer review (not yet merged), with CI fixes already applied by the platform's core maintainer.

- Evidence: https://github.com/promptfoo/promptfoo/pull/12376, origin proposal #12236

### 4. Sixteen vertical domains systematically audited — to our knowledge, no comparable public cross-domain audit corpus exists

The same engine has been run across 16 verticals, including: healthcare AI output boundaries (patient-safety rule families), embodied-robotics datasets (4 leading vendors independently audited, incl. one third-party replication of our findings matching bit-for-bit), drone flight telemetry (470,000+ crash-log frames; we measured a 1.3 s warning lead time on this analyzed corpus), highway traffic (845,100-frame test set, zero false positives under the stated rule set), aerospace (NASA C-MAPSS, 2,241 Sentry objects), BCI/EEG, bio-molecular QC, and military open-domain hallucination (48% → 24% reduction with deterministic guards).

- Evidence: https://github.com/PHM-Audit

### 5. A healthcare output-boundary validator, released open source

Following real-world incidents where AI-generated medication guidance caused harm, we released **QMed** — a language-agnostic, zero-medical-knowledge-dependency validator for AI health advice boundaries (dosage limits, symptom-conclusion consistency, supervision evasion detection). 33/33 test cases pass; replay of publicly documented incident narratives achieves 9/9.

- Evidence: https://github.com/PHM-Audit/qmed

---

## What This Means for the Region

A figure widely cited in regional policy discussion holds that roughly 14% of the Asia-Pacific population uses AI, and that the benefits accrue to economies "ready to embrace AI." Readiness is not just compute and connectivity — it is **assurance infrastructure**: deterministic validators, auditable evidence chains, and interoperable checking standards that let a hospital, a factory, or a customs broker in any economy verify AI behavior without trusting any vendor's word.

We believe deterministic validation layers belong in the same policy conversation as data-cross-border verification platforms (e.g., hash-based "data-not-leaving" architectures already operating in the Greater Bay Area). Our hash-anchored audit chains follow the same technical pattern: verifiable, local, vendor-neutral.

**We offer an open, independent reference implementation of that pattern — most claims above link directly to public artifacts; verification time depends on the artifact.**

---

*PHM-Audit is an independent research effort (Shenzhen, China). All claims above link to public artifacts. Contact: 14788045967@163.com | https://github.com/PHM-Audit*
