# Julian Torres — Founder Profile

**Tribunus · San Francisco, California · since October 2024**

Contact: hello@tribunus.dev · julian@tribunus.dev
LinkedIn: https://www.linkedin.com/in/juliantorr-es
GitHub: https://github.com/Tribunus-dev
Site: https://tribunus.dev/founder

---

## TL;DR

Software engineer based in San Francisco, California. Author of Tessera (a fork of llama.cpp for calibrated per-tensor quantization) and Tessera Studio (a Swift desktop app for running LLMs locally). Founder and sole maintainer of Tribunus. Raising a pre-seed. Self-funded.

## What I've shipped

All of it is on GitHub. The short version:

### 01 — Tessera (the engine)

A fork of llama.cpp that takes calibration seriously. Per-tensor evolutionary calibration (T640) with a small genetic algorithm, AWQ pre-scaling, schema-versioned policies, runtime agreement with the offline reference to F16 precision. Native speculative decoding (DFlash / DSpark). ANE prefill via Core ML on Apple Silicon. ~25 C++ modules, ~10.6k LoC, multi-licensed under LICENSE-TESSERA (PolyForm Noncommercial 1.0.0) with commercial licensing available.

- github.com/Tribunus-dev/tessera
- License: PolyForm Noncommercial 1.0.0 + commercial available

### 02 — Tessera Studio (the app)

The Swift desktop app that ships Tessera to users. Native macOS (Apple Silicon), iOS, and Linux in development. Manifest-based SKILL.md skills system. Real agent loop with capability-scoped tools, streaming, and approval levels. ~8.4k LoC Swift + ~3.7k LoC C/C++. The first product Tribunus is shipping in 2026.

- github.com/Tribunus-dev/tessera (TesseraStudio/)
- Product site: tessera.tribunus.dev
- License: AGPLv3 with LICENSE-TESSERA noncommercial for Tessera-specific pieces

### 03 — Tessera calibration stack (the substrate)

Python quantizer and the schema-versioned telemetry substrate that powers drafter training. Per-tensor GA, regime-routed MAP-Elites archive, AWQ + ternary + outlier policy. Per-step spec-decoding telemetry (`llama.tessera.spec.v1`) with verifier + drafter top-k. Native LK training driver (Path A, autoregressive drafters) and D-PACE block dataset (Path B, DFlash/DSpark).

- tessera/tools/{tessera,ane-mtp,tile640,imatrix}/

### 04 — Prism Engine (the R&D sister)

An inspectable heterogeneous AI deployment system in Rust, with a constitutional authority model: one canonical reality, `WorldTxn` mutations, effects outside the write transaction, immutable evidence, rebuildable projections. ANE, Core ML, Metal, MLX backends via a shared apple-bridge. Open research surface; not the shipping path for Tessera.

- github.com/Tribunus-dev/prism-engine
- Observatory: prism-engine.tribunus.dev

### 05 — Tessera Studio macOS UX (HIG)

A 13-section macOS Human Interface Guidelines study feeding the Tessera Studio app surface. Documents the design rationale for every toolbar, inspector, settings scene, and sheet — and explicitly tracks the MS Office UX pain points the app is designed to avoid.

### 06 — Build, license, governance, evidence

AGPLv3 site + LICENSE-TESSERA (PolyForm Noncommercial) for the fork + Apache-2.0 for upstream-inherited pieces. Records substrate across the stack (calibration policy, spec-decoding telemetry, per-tensor sidecars, audit reports). Wave-based "evolve" loop with strict gate discipline.

---

## How I work with research

The Tessera stack did not start with a plan. It started with the research.

I run deep-research passes that produce 50+ reference bibliographies, then write 1,000+ line design docs that map the prior art against the open problem. The research spine is the source of truth for the roadmap; the plan docs carry pointers to it, not the other way around. When the research disagrees with a plan doc, the research wins.

What I look for in a paper is the *open problem* — the thing the prior art does not close. For Tessera, the open problem was that every prior search-based quantizer — HAQ, RAMP, FracBits, Q-Palette, QuantEA, EvoPress — searches over discrete bit-widths, and none of them closes the loop against the actual kernel dequant output. Tessera's novelty is not a new quantizer. It is the **composition**: evolutionary search over continuous reconstruction knobs, scored against the real kernel output, conditioned on regime descriptors. The architecture is what closes the loop.

I bring the same discipline to building systems. The first version of any new system is the architecture. The Tile640 kernel exposes a debug mode that emits its actual dequantized weights so calibration is measured against the runtime, not a reference. The kernel-fidelity loop is the differentiating capability *and* the ground-truth evaluator. One pipeline, two levels: the quantizer grounded in kernel output, the capability grounded in world output (tests, builds, commits).

### What this looks like in practice

- **A new system starts as a 1,000+ line design doc.** Six locked design docs on Tessera, each with a *prior art* section, a *locked decisions* section, and a *research source-of-truth* pointer. The architect ratifies the calls. There is no committee.
- **A new system commits at a SHA where the build is green and the outputs are bit-identical.** The architecture gate is monotonic. The ratchet only moves forward. A green test that doesn't match the real build is a broken gate — `test_all.sh` is not a gate; `cmake --build` is.
- **A new system does not improvise correctness under load.** Decisions are frozen before execution. If the kernel dequant changes, the calibration thresholds re-search, and the record carries the new SHA.
- **A new system does not import a new abstraction it does not need.** Match the host project's style. *Match llama.cpp production code style. No new abstraction layers, no virtual dispatch.* The codebase reads like it grew there, not like it was grafted on.
- **A new system does not tolerate parallel implementations.** No `v1` / `v2` / `v3` as labels for coexisting code in the same tree. Refactor in place. The version is a release tag on the artifact, not a label on the code.
- **A new system is allowed to use AI, but not to ship code I cannot explain.** *"AI-generated code is allowed. What is not allowed is shipping code you do not understand. The human owns every line, however it was produced."* The agent drafts; the architect owns.

---

## How I work — eight operating principles

These are not aspirations. They are the rule set I run on.

1. **Constitutional, not ambient.** Every decision is compile-time, not runtime. Every mutation produces a schema-versioned record. Tessera is a fork, not a wrapper: changes ship in the same files as the upstream code, on the upstream's terms.
2. **Records, not logs.** Logs are what you write when nothing happened. Records are what happened. The audit trail is a first-class artifact, not a side effect.
3. **Replace, don't coexist.** No `v1` / `v2` / `v3` as labels for coexisting implementations in the same tree. Refactor in place. The version is a release tag on the artifact, not a label on the code.
4. **One canonical authority.** One source of truth, one mutation path, one render. Re-derive on conflict. The state machine is explicit; the engine-coupled terminal state is forbidden.
5. **Local-first, federated when needed.** Your hardware, your data, your model. The escape valve is federation; the default is local. No required cloud dependency for core operations.
6. **No vendor egress by default.** Self-hosted OSS first. Paid APIs as opt-in fallbacks. Treat every external account, key, and billing relationship as a first-class design risk to design out, not inherit.
7. **One founder, one product, one bet.** I am the only full-time person on this. The first full-time hire will come after a pre-seed close. I do not scale the team before the product earns the right.
8. **Honesty over hype.** The status table is the source of truth. Live, in dev, planned, and superseded are different things, and the table is honest about which is which.

---

## Background

Before Tribunus I worked as a software engineer in the San Francisco Bay Area, and as a freelance photographer and designer. The creative background shows up in the design language — minimal, restrained, monochrome — and in the care taken with documentation, schema versioning, and the look of every record the system produces. The Tessera Studio HIG study is the most visible expression of that background.

Full name: Julian Alejandro Torres Nieto (Tribunus.dev).

## What I am looking for in 2026

The five concrete collaboration shapes are on the looking-for page:

1. Beta users on Mac & Linux for Tessera Studio
2. Co-engineers (Swift / SwiftUI / C++ / quantization / UX)
3. Quantization researchers (T640 / DFlash / DSpark)
4. Advisors who have shipped a Mac desktop product or a fork of llama.cpp
5. Investors — raising a pre-seed (evidence-led, self-funded)

---

## Timeline

- **2024 — October.** Tribunus is founded in San Francisco. The thesis: the inference + agent stack must be compiled together, not assembled at runtime.
- **2024 — Q4.** First cut: a desktop agent with local inference. Tribunus begins as a derivative of opencode (SST Inc., MIT) and quickly diverges.
- **2025.** The Tessera fork of llama.cpp takes over. The C++ side is named Tessera; per-tensor evolutionary calibration (T640), DFlash/DSpark drafters, and ANE prefill via Core ML all land against the new infrastructure.
- **2026 — H1.** The Tessera Studio pivot. The desktop product is renamed Tessera Studio. The Swift app and the C++ fork ship from a single repo.
- **2026 — Mid.** Self-improving loop, calibration stack, design system. Prism Engine (Rust constitutional ECS) absorbs its FFI substrate. Tessera Studio's macOS HIG study is published.
- **2026 — August.** Raising a pre-seed. Self-funded.
- **2026 — Now.** One product in flight: Tessera Studio on macOS (developer preview). Linux in development. Sole maintainer, one founder, no team hires planned before a pre-seed close.

---

## Intellectual lineage

The architecture is not invented from scratch. The research is documented paper by paper. A few anchors:

- **Kwon et al., *PagedAttention* (SOSP 2023).** The reframing of inference as memory orchestration. Tessera's KV-cache handling and per-token plan live here.
- **Mark Miller, *Robust Composition*.** Capability-based security. The plugin runtime, the surface separation between desktop / web / mobile, and the "no ambient authority" rule all derive from this lineage.
- **Kleppmann et al., *Local-First Software*.** The client is the authority for its own data; sync is eventual and conflict-free; offline is not an afterthought. Tessera Studio runs locally first.
- **Lattner et al., *MLIR* (CGO 2021).** The progressive-lowering, dialect-composable compiler architecture. Tessera's calibration pipeline is built on a similar progressive-validate pattern.

---

## License & IP

- All Tribunus-specific work is Copyright © 2024–2026 Julian Torres.
- The site (tribunus.dev) is released under AGPLv3. The site copy is CC-BY-4.0.
- The Tessera fork ships under LICENSE-TESSERA (PolyForm Noncommercial 1.0.0) with commercial licensing available; contact enterprise@tribunus.dev.
- The opencode attribution in NOTICE.md is preserved.
- Tessera software may include technology covered by one or more pending patent applications owned or controlled by Julian Alejandro Torres Nieto, Tribunus.dev. The PolyForm Noncommercial License includes a Patent License.

---

## One line

I build one product, the way the engine itself deserves to be built.
