# Julian Torres — Founder Profile

**Tribunus · San Francisco, California · since October 2024**

Contact: hello@tribunus.dev · julian@tribunus.dev
LinkedIn: https://www.linkedin.com/in/juliantorr-es
GitHub: https://github.com/Tribunus-dev
Site: https://tribunus.dev/founder

---

## TL;DR

Software engineer based in San Francisco, California. Author of Tessera (a fork of llama.cpp for calibrated per-tensor quantization) and Tessera Studio (a Swift desktop app for running LLMs locally). Founder and sole maintainer of Tribunus. Founder applying to startup accelerators in 2026. Pre-seed. Self-funded.

## What I have actually shipped (the receipts)

Not pitch-deck plans. Code on GitHub. Receipts in the artifacts.

### 01 — Tessera (the engine)

A fork of llama.cpp that takes calibration seriously. Per-tensor evolutionary calibration (T640) with a small genetic algorithm, AWQ pre-scaling, schema-versioned receipts, runtime agreement with the offline reference to F16 precision. Native speculative decoding (DFlash / DSpark). ANE prefill via Core ML on Apple Silicon. ~25 C++ modules, ~10.6k LoC, multi-licensed under LICENSE-TESSERA (PolyForm Noncommercial 1.0.0) with commercial licensing available.

- github.com/Tribunus-dev/tessera
- License: PolyForm Noncommercial 1.0.0 + commercial available

### 02 — Tessera Studio (the app)

The Swift desktop app that ships Tessera to users. Native macOS (Apple Silicon), iOS, and Linux in development. Manifest-based SKILL.md skills system. Real agent loop with capability-scoped tools, streaming, and approval levels. ~8.4k LoC Swift + ~3.7k LoC C/C++. The first product Tribunus is shipping in 2026.

- github.com/Tribunus-dev/tessera (TesseraStudio/)
- Product site: tessera.tribunus.dev
- License: AGPLv3 with LICENSE-TESSERA noncommercial for Tessera-specific pieces

### 03 — Tessera calibration stack (the substrate)

Python quantizer and the schema-versioned telemetry substrate that powers drafter training. Per-tensor GA, regime-routed MAP-Elites archive, AWQ + ternary + outlier policy. Per-step spec-decoding telemetry (`llama.tessera.spec.v1`) with verifier + drafter top-k. Native LK training driver (Path A, autoregressive drafters) and D-PACE block dataset (Path B, DFlash/DSpark). The receipts the engine and the studio share.

- tessera/tools/{tessera,ane-mtp,tile640,imatrix}/

### 04 — Prism Engine (the R&D sister)

An inspectable heterogeneous AI deployment system in Rust, with a constitutional authority model: one canonical reality, `WorldTxn` mutations, effects outside the write transaction, immutable evidence, rebuildable projections. ANE, Core ML, Metal, MLX backends via a shared apple-bridge. Open research surface; not the shipping path for Tessera.

- github.com/Tribunus-dev/prism-engine
- Observatory: prism-engine.tribunus.dev

### 05 — Tessera Studio macOS UX (HIG)

A 13-section macOS Human Interface Guidelines study feeding the Tessera Studio app surface. Documents the design rationale for every toolbar, inspector, settings scene, and sheet — and explicitly tracks the MS Office UX pain points the app is designed to avoid.

### 06 — Build, license, governance, evidence

AGPLv3 site + LICENSE-TESSERA (PolyForm Noncommercial) for the fork + Apache-2.0 for upstream-inherited pieces. Receipts substrate across the stack (calibration policy, spec-decoding telemetry, per-tensor sidecars, audit reports). Wave-based "evolve" loop with strict gate discipline.

---

## How I work — eight operating principles

These are not aspirations. They are the rule set I run on.

1. **Constitutional, not ambient.** Every decision is compile-time, not runtime. Every mutation produces a schema-versioned receipt. Tessera is a fork, not a wrapper: changes ship in the same files as the upstream code, on the upstream's terms.
2. **Receipts, not logs.** Logs are what you write when nothing happened. Receipts are what happened. The audit trail is a first-class artifact, not a side effect.
3. **Replace, don't coexist.** No `v1` / `v2` / `v3` as labels for coexisting implementations in the same tree. Refactor in place. The version is a release tag on the artifact, not a label on the code.
4. **One canonical authority.** One source of truth, one mutation path, one render. Re-derive on conflict. The state machine is explicit; the engine-coupled terminal state is forbidden.
5. **Local-first, federated when needed.** Your hardware, your data, your model. The escape valve is federation; the default is local. No required cloud dependency for core operations.
6. **No vendor egress by default.** Self-hosted OSS first. Paid APIs as opt-in fallbacks. Treat every external account, key, and billing relationship as a first-class design risk to design out, not inherit.
7. **One founder, one product, one bet.** I am the only full-time person on this. The first full-time hire will come after a pre-seed close. I do not scale the team before the product earns the right.
8. **Honesty over hype.** The status table is the source of truth. Live, in dev, planned, and superseded are different things, and the table is honest about which is which.

---

## What I am not

Five things I am not, in case it saves us both a meeting.

- **Not a pitch-deck founder.** I do not have a 12-slide narrative. I have a C++ fork, a Swift app, a research surface, and a status table. The receipts are the pitch.
- **Not a chat-wrapper over a remote API.** Tessera Studio runs models locally with calibrated quantization. If that distinction does not land, we are not the right fit.
- **Not a "ship a v1 to validate" founder.** The architecture is the strategy. I would rather ship one thing well than three things badly.
- **Not ready for a public launch narrative.** The macOS developer preview is for the beta users on the looking-for page. Press, podcasts, conference talks are welcome; press releases are not.
- **Not a hire-first founder.** The first full-time hire will be on the Tessera side and will be posted publicly when the time comes. Please don't cold-pitch your way in before then.

---

## Background

Before Tribunus I worked as a software engineer in the San Francisco Bay Area, and as a freelance photographer and designer. The creative background shows up in the design language — minimal, monochrome, terminal-honest — and in the care taken with documentation, schema versioning, and the look of every receipt the system produces. The Tessera Studio HIG study is the most visible expression of that background.

Full name: Julian Alejandro Torres Nieto (Tribunus.dev).

## What I am looking for in 2026

The five concrete collaboration shapes are on the looking-for page:

1. Beta users on Mac & Linux for Tessera Studio
2. Co-engineers (Swift / SwiftUI / C++ / quantization / UX)
3. Quantization researchers (T640 / DFlash / DSpark)
4. Advisors who have shipped a Mac desktop product or a fork of llama.cpp
5. Investors & startup accelerators (applying 2026)

---

## Timeline

- **2024 — October.** Tribunus is founded in San Francisco. The thesis: the inference + agent stack must be compiled together, not assembled at runtime.
- **2024 — Q4.** First cut: a desktop agent with local inference. Tribunalus begins as a derivative of opencode (SST Inc., MIT) and quickly diverges.
- **2025.** The Tessera fork of llama.cpp takes over. The C++ side is named Tessera; per-tensor evolutionary calibration (T640), DFlash/DSpark drafters, and ANE prefill via Core ML all land against the new infrastructure.
- **2026 — H1.** The Tessera Studio pivot. The desktop product is renamed Tessera Studio. The Swift app and the C++ fork ship from a single repo.
- **2026 — Mid.** Self-improving loop, calibration stack, design system. Prism Engine (Rust constitutional ECS) absorbs its FFI substrate. Tessera Studio's macOS HIG study is published.
- **2026 — August.** Accelerator applications filed. Pre-seed and self-funded.
- **2026 — Now.** One product in flight: Tessera Studio on macOS (developer preview). Linux in CI. Sole maintainer, one founder, no team hires planned before a pre-seed close.

---

## Intellectual lineage

The architecture is not invented from scratch. The team has published a long-form essay — *The Tribunus Thesis* — that traces the intellectual lineage paper by paper. A few anchors:

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
