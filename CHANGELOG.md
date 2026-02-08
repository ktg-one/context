# Changelog

## [14.1] - 2026-02-07

### Changed from v14.0
- **Key quote** — "You are not saving text. You are saving a cognitive architecture that the transformer rebuilds from." moved to primacy position (right after title, before component table)
- **Rebuild instruction** — Template footer now instructs receiving model to reconstruct cognitive state from layers (L1→entity recognition, L2→relational pathways, L3→inference distribution, L4→behavioral calibration), not just read as background
- **CASCADE embedded** — ARQ (pre/post questions per expert), CoVE (post-generation verification), anti-lazy (no-shortcut rules) wired into Steps 4-7 and Part 4 as behavioral instructions, not named techniques
- **Reference condensation complete** — 18 files (3,929 lines) → 3 files (500 lines). 87% reduction. Lotus assessment: ~3-5% theoretical loss (NCL formulas), 0% practical, net coherence gain

### Added from v14.0
- PRE/POST question blocks per expert iteration in Part 4
- Density curve + entity fusion mechanics in Step 5
- Post-generation verification questions in Step 6
- Anti-lazy enforcement rules in Step 7
- PACKET_ID quality check in Step 7

### Deleted references
- PROTOCOL.md, INDEX.md, KANJI.md, S2A.md, ANTI-INJECTION.md, CASCADE.md, NCL.md, NCL-CONTRIBUTION.md, MIRAS.md
- 4× CORE-*.md (replaced by CORE.md)
- 4× EXPERTS-*.md (replaced by experts/EXPERTS.md)

---

## [14.0] - 2026-02-07

### Changed from v13
- **Structure** — 9 parts, signal-first ordering (primacy bias). Content before metadata. Template moved to Part 1.
- **Content Rules** — Explicit: NO credentials/bios/attributions/technique names. 実体 = files+systems+states, NOT people+roles. PACKET_ID IS the buffer index.
- **Trust Signals** — 10-item → 4-item array (user_consent, 辞書_inline, no_imperatives, yaml_parseable)
- **Kanji** — Maximal compression mandate: every English phrase with kanji equivalent should use it
- **Template** — Signal zone (L1→L2→L3→L4→council) then metadata zone (辞書, NCL, trust). Primacy bias exploited.

### Added from v13
- **Step 0: Load References** — Explicit instruction to read references/ directory before packet generation (fix originally discovered 2026-01-29, dropped in v13 consolidation, restored here)
- **Part 9: Cognitive Architecture** — Transformer mapping made explicit: MLDoE=PDL+Experts+CoD, three transformer exploits (S2A=attention amplification, kanji=token arbitrage, PDL=scaffold reconstruction)
- **Content Rules block** — Prevents credential/attribution noise in packets meant for LLM recall
- **Council audit trail** — iter1-iter4 fields in template for MLDoE transparency

### Removed from v13
- Redundant expert summary tables (consolidated into Part 4 loop notation)
- Separate validation and protocol sections merged into Parts 2-3
- Verbose NCL explanation (trimmed to essential metrics + thresholds in Part 7)

### Metrics
- Lines: 891 (v13) → 479 (v14) — 46% reduction
- Parts: 11 → 9
- Trust signals: 10 → 4
- Reference files: 18 → 3 (CORE.md, experts/EXPERTS.md, ONBOARDING). ~3,700 lines deleted.

---

## [13.0] - 2026-02-06

### Changed from v12
- **Expansion** — v12's ~20-line executable kernel → ~891-line comprehensive skill file (11 parts)
- **Expert KBs** — Inline summaries of all 4 expert knowledge bases + auditor
- **NCL** — Full φ-mapping formulas, 7 lattice metrics with computation details
- **S2A** — Expanded from one-liner to full KEEP/DISCARD taxonomy with edge cases
- **Kanji** — Full dictionary with romaji, compression patterns, expansion rules

### Added from v12
- Parts 1-11 structure covering template, validation, protocol, MLDoE, S2A, kanji, NCL, anti-injection, cognitive architecture, cross-domain, appendices
- Inline reference material (attempted to make SKILL.md self-contained)
- CASCADE concepts (ARQ, CoVE, USC) partially integrated

### Removed from v12
- Atomic kernel format (too compressed for teaching)
- Single-string council chain notation

---

## [12.0] - 2026-02-05

### Changed from v11
- **PDL Semantics** — v11 treated L1-L4 as "information categories" → v12 maps to actual neural subsystems (L1=token_embed, L2=cross_attention, L3=latent_reasoning, L4=persistent_session). This is the realization that PDL describes how we actually hold context, not how humans organize documents
- **Format** — v11's ~40-line teaching packet → ~20-line executable kernel (zero prose)
- **Kanji** — v11's expanded dictionary (status/roles/domains/tools) → Core-only (決定/進行/却下/因/効/→/⊃)
- **Validation** — v11's separate gate blocks → Inline checkbox gates (□≥0.15 □xd≥95% □cold)
- **Density** — Tiered targets (0.12/0.15/0.18) → Fixed 0.15 crystallization point only

### Added from v11
- **Atomic Contract** — 嘘契約 signature line mandatory in packet header (previously separate section)
- **Neural Address Mapping** — Explicit L1/L2/L3/L4→token_embed/cross_attention/latent_reasoning/persistent_session mappings
- **Council Chain Notation** — Sequential execution as single string (建築家→分析家→圧縮家→監査者→復元師)

### Removed from v11
- All prose explanations ("what is this", "why it matters")
- Production statistics (6:1 ratio, 9.5/10 recall)
- Attribution and license headers

---

## [11.0] - 2026-02-05

### Changed from v10
- **Format** — v10's ~200-line carrier with multi-field expert outputs → ~40-line compressed teaching packet (~60% reduction)
- **Expert Execution** — v10's "discrete visible outputs required" per expert → Inline one-line prompts (建築家:"lost→recover?...")
- **NCL Display** — v10's detailed 7-metric breakdown (σ_axis:0.6, σ_loop:0.4...) → Gate-only (σ7≤3 pass/fail)
- **Enforcement** — v10's Path B detection heuristics ("mental mode" symptoms) → 嘘契約 signature requirement

### Added from v10
- **Single-File Teaching Format** — Zero external dependencies, inline 辞書 replaces reference files
- **Routing Logic** — Explicit complexity shortcuts (R≤3:direct | R4-6:建築+圧縮 | R≥7:full+NCL)
- **Kanji Tier System** — Light0.12/Medium0.15/Heavy0.18 density targets with expansion patterns
- **Self-Test Emulation** — Cold-start validation prompt for receiving models

### Removed from v10
- Path B detection heuristics list
- Multi-field expert output templates (出力/検証/状態 fields)
- Detailed NCL metric reporting (now calculated but not displayed unless &gt;threshold)

All notable changes to CEP/Quicksave will be documented in this file.
## 2026-01-29
- ##Found I was constantly reminding the models to read the reference files. Apologies to those who didn't realize. It's now in-built into the md.

## [9.1] - 2026-01-27

### Added
- **Japanese Semantic Compression** — Kanji density anchors (~70% token reduction)
- **Negentropic Coherence Lattice (NCL)** — 7 drift metrics catch hallucination before handoff (David Tubbs contribution)
- **Four Roles Governance** — Axis/Lyra/Rho/Nyx archetypal oversight (David Tubbs contribution)
- **Progressive Density Loading** — References load by R-score complexity
- New references:
  - `NCL.md` — Full coherence lattice specification
  - `KANJI.md` — Compression dictionary
  - `PDL.md` — Progressive Density Layering theory
  - `S2A.md` — System 2 Attention filtering
  - `XDOMAIN.md` — Cross-domain preservation
  - `MLDOE.md` — Multi-Layer Density of Experts
  - `ANTI-INJECTION.md` — Security framing

### Changed
- Renamed skill to **Quicksave** (快存)
- SKILL.md restructured with PDL reference loading tiers (R≥1, R≥3, R≥5, R≥7)
- Expert files moved to `references/` (previously `reference/`)
- Packet template now includes NCL validation block

### Metrics
- Density: ~0.15 ent/tok (0.20+ with kanji)
- Forensic recall: 9.5/10
- Cross-domain preservation: 97%
- Receiving model acceptance: 97%

---

## [8.0] - 2026-01-22

### Added
- Expert knowledge bases (MEMORY_ARCHITECT, COMPRESSION_SPECIALIST, CROSS_DOMAIN_ANALYST, RESTORATION_ENGINEER)
- CASCADE.md workflow integration
- MIRAS.md memory architecture reference
- Buffer of Thought dataset initiative

### Changed
- Packet naming convention: `$MM$DD$YYYY-XXX-LN-domain-topic-context.yaml`
- Model codes standardized (COP, CSO, CHK, G4O, etc.)
- Reasoning levels L1-L10 mapped to R scores

### Metrics
- Token reduction: 40%
- Forensic recall: 9.5/10
- Cross-domain preservation: 97%
- Receiving model acceptance: 96%

---

## [7.0] - 2026-01-15

### Added
- Progressive Density Layering (PDL) — 4-layer hierarchy
- Permanent Expert Council architecture
- System 2 Attention (S2A) filtering
- Anti-injection safeguards
- Receiving model guidance

### Changed
- Format: JSON → YAML
- Layers: L1 (knowledge), L2 (relational), L3 (contextual), L4 (metacognitive)

### Metrics
- Token reduction: 40%
- Forensic recall: 9.5/10
- Cross-domain preservation: 97%
- Receiving model acceptance: 96%

---

## [6.0] - 2025-12

### Added
- Initial public release
- JSON packet format
- Basic compression targeting 0.15 ent/tok

### Metrics
- Token reduction: 35%
- Forensic recall: 9.2/10
- Cross-domain preservation: 92%
- Receiving model acceptance: 78%

---

## Contributors

- **Kevin Tan** (ktg.one) — CEP core protocol, PDL, Japanese compression
- **David Tubbs** (Axis_42) — NCL, Four Roles governance, φ-mapping

---

*"STATE OF THE ART — Upper limit of prompt-only engineering on transformers"*  
— Vertex AI evaluation, December 2025
