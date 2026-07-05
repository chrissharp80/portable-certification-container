# Portable Certification Container (PCC)

**A formal specification for deterministic JSON certification in distributed systems.**

PCC defines a complete, deterministic pipeline from raw input bytes to a byte-identical certification report — so that *any* conforming implementation, on any platform, produces the same result down to the byte.

> **Status:** Version 4.0 · Commercially licensable
> This repository is a public **overview**. The full normative specification and whitepaper are available under commercial license — see [Licensing](#licensing).

---

## The problem

The same data can be serialized in many valid ways — key ordering, number formatting, whitespace, Unicode escaping — so two systems can produce "identical" data with different bytes, and therefore different hashes. There is no standard for *proving* that two systems produced byte-identical results from the same input. Without that guarantee, certification and audit trails are meaningless.

## The approach

PCC specifies a **nine-phase pipeline** — raw bytes through parsing, validation, normalization, and hashing to a final certification report — anchored by a single **SHA-256 manifest hash** that binds every normative artifact into a Merkle-like integrity chain. Verification needs no network, no certificate authority, and no trusted third party.

Authority is deliberately split between a human-readable prose specification and machine-verifiable JSON artifacts; where the two conflict, the artifacts prevail. Determinism is enforced by hard constraints rather than convention:

- **Integer-only numbers** — no floating-point ambiguity
- **A strict parse gate** with deterministic error precedence
- **A profiled JSON Schema Draft 2020-12 subset**
- **Conformance defined as byte-identical output** across a shared test-vector suite

## The guarantee

Given identical inputs and identical normative artifacts, any conforming implementation produces a **byte-identical report**. The guarantee is absolute within its defined scope.

## By the numbers

| | |
| --- | --- |
| **27** | JSON schemas |
| **4** | certification tiers |
| **50+** | audit cycles |
| **10+** | system designs built on the same methodology |

## Methodology

PCC was produced through an automated iterative audit process: designs submitted to independent AI auditors in blind sessions, findings resolved without feature creep, repeated until convergence. The same methodology has since been applied across 10+ system designs.

## Licensing

The full specification, JSON Schema artifacts, test-vector suite, and whitepaper are available under commercial license.

**Contact:** chris@chrissharp.dev · [chrissharp.dev](https://chrissharp.dev)

---

© 2026 Chris Sharp. This overview may be read and shared freely. The normative specification and its artifacts are licensed separately and are not included in this repository.
