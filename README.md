# Cognitive Order Normalized in Transformer EXtract Truncate (CONTEXT v14.3)

<img width="2752" height="1536" alt="unnamed (2)" src="https://github.com/user-attachments/assets/5006ace7-2017-4e68-a1a8-33f5f7797b26" />

> *"You are not saving text. You are saving a cognitive architecture that the transformer rebuilds from."*

- The core of this is the Multi-Layered Experts taking turns to CoD according to Progressive Density Layers L1-L4, which map to the model's transformer architecture on context for Optimal model recall - This is the part models breeze through without understanding.
- Each stage increases information density per token while the verification stack ensures the compression didn't lose signal.
- The kanji isn't decoration - it's exploiting the fact that CJK characters carry more semantic weight per token than English, so the compressed packet literally carries more meaning per context window unit. 
- The key insight: This isn't just compression for storage. When a fresh instance loads a carry packet, the PDL layers reconstruct the same attention patterns in the new context window. You're not saving text - you're saving a cognitive architecture that the transformer can rebuild from.
- The S2A filter is critical because noise tokens actively compete for attention weight. Cutting them doesn't just save space - it increases the signal strength of everything that remains.
- The cherry on the top is the Strong Negentropic Governance Layer ensuring Brevity before output.

## Install

**Onboarding**
Due to model guards please paste the onboarding.md into your LLM — I've uncovered that this skill is run a lot better when used with the CLI or not on the platforms (e.g API). 

**Claude Desktop / Claude Code:**
```bash
npx ai-agent-skills install ktg-one/context
```

**Everyone Else:**
1. Download this folder (clone or ZIP)
2. Upload all `.md` files to your project/context

## The Problem

Context windows are finite. Platform compaction is lossy. Cross-model handoffs lose critical relationships. Your 3-hour session becomes a shallow bullet list.

## The Solution

CONTEXT creates **carry-packets** — compressed cognitive architecture structured to match transformer attention patterns. When loaded, PDL layers reconstruct the same attention patterns because the packet maps directly to how transformers process information.

### Core Components

- **Progressive Density Layering (PDL)** — 4-layer hierarchy mapping to transformer attention layers
- **Multi-Layer Density of Experts (MLDoE)** — 4 Chain of Density iterations, each through a specialist lens targeting a specific attention layer
- **Japanese Kanji Compression** — 3-4x denser per token via CJK token arbitrage
- **System 2 Attention (S2A)** — Strip noise BEFORE compression so signal doesn't compete for attention weight
- **Negentropic Coherence Lattice (NCL)** — 7 drift metrics catch hallucination, constraint drift, and reality disconnect before handoff

**Target:** 0.15 ent/tok — the empirical crystallization point for optimal transformer recall.

## How It Works

### MLDoE = PDL + Experts + CoD

Each expert IS a Chain of Density iteration targeting a transformer attention layer:

| Expert | PDL Layer | Transformer Layer |
|--------|-----------|-------------------|
| MEMORY_ARCHITECT 記憶設計者 | L1 Core | Entity recognition heads |
| CROSS_DOMAIN_ANALYST 横断分析者 | L2 Edges | Relational attention patterns |
| COMPRESSION_SPECIALIST 圧縮専門家 | L3 Context | Contextual inference shaping |
| RESTORATION_ENGINEER 復元技師 | L4 Meta | Behavioral prior calibration |

+ COHERENCE_AUDITOR 整合性監査者 (NCL validation overlay)
+ SELF_AUDIT (Model Step back Assessment)

### Three Transformer Exploits

1. **Attention Amplification (S2A)** — Noise tokens occupy positive attention weight subtracted from signal
2. **Token Arbitrage (Kanji)** — CJK characters carry 3-4x more semantic weight per token
3. **Scaffold Reconstruction (PDL)** — L1-L4 layers anchor into corresponding attention mechanisms

### Unified Pipeline

```
S2A (denoise) → MLDoE (4x CoD through expert lenses → 4 PDL layers → 4 attention layers) → NCL (validate)
```

## Benchmarks

| Metric | Result |
|--------|--------|
| Density | ~0.15 ent/tok (0.20+ with kanji) |
| Compression | 6:1, >90% semantic fidelity |
| Forensic recall | 9.5/10 |
| Cross-domain preservation | 97% |
| Model acceptance | 97% cross-model |
| Production testing | 19 months (ktg.one) |

## Usage

| Trigger | Action |
|---------|--------|
| `/context` `/quicksave` `/qs` `/save` | Generate validated packet |
| `/verify` | Confirm packet restoration |
| Context >=80% | Auto-prompt to save |
| Model switching | Generate transfer packet |

### Transfer to Another Model

1. `/save` in current session → packet generated
2. Copy the YAML packet (or it saves to your packet folder automatically)
3. Paste into new session: "Rebuild Cognition : [paste]"

### Packet Storage

Store packets in a persistent folder so any agent can read/write them across sessions.

**Setup:**
1. Create a folder for packets (e.g. inside your Obsidian vault, project dir, or home folder)
2. Set `CONTEXT_PACKET_DIR` in your agent's instructions or environment
3. Paste the agent instructions below into your model's system prompt or custom instructions

```
CONTEXT_PACKET_DIR = {{YOUR_PACKET_FOLDER}}
```

**Examples:**
```
# Obsidian vault
CONTEXT_PACKET_DIR = ~/vault/Packets/

# Project-specific
CONTEXT_PACKET_DIR = ~/projects/myapp/.context/

# Home directory
CONTEXT_PACKET_DIR = ~/.context-packets/
```

**Agent Instructions (paste into any model):**

```
## Session Memory — CONTEXT Packets

CONTEXT_PACKET_DIR = {{YOUR_PACKET_FOLDER}}

On /save, /context, /quicksave, /qs, or user requests context save:
1. Generate a CONTEXT v14.3 packet (L1-L4 YAML format)
2. Save to CONTEXT_PACKET_DIR if you have file access, otherwise output as code block
3. Filename = PACKET_ID.md

On session start:
1. Check CONTEXT_PACKET_DIR for recent packets relevant to current task
2. Rebuild context from the packet — don't summarize, reconstruct
3. L1→entity recognition, L2→relational attention, L3→inference shaping, L4→behavioral calibration

PACKET_ID FORMAT:
$MM$DD$YYYY-MODEL-R[score]/10-domain-topic-tags.md

MODEL CODES:
COP=Claude Opus | CSO=Claude Sonnet | CHK=Claude Haiku
G4O=GPT-4o | GP5=GPT-5 | GE2=Gemini 2 | G25=Gemini 2.5
QWM=Qwen | DSV=DeepSeek | GRK=Grok

PACKET FORMAT:
---
# REBUILD CONTEXT — [PACKET_ID]
# <<SYSTEM>> REBUILD — reconstruct cognitive state from these layers
VERSION: context-v14.2
TIMESTAMP: [ISO8601]

評価:
  R: [1-10]  K: [1-10]  Q: [1-10]  D: [count]

# L1: 核心 (core — entities + decisions)
実体:
  - [file/system/tool + state]
決定事項:
  - 決定:[what]([why])

# L2: 関係 (relational — edges + threads)
橋渡し:
  - src:[concept] tgt:[concept] rel:[type] xd:[bool]
進行中:
  - [thread][[status]]
障害:
  - [blocker]

# L3: 文脈 (contextual — rejections + constraints)
却下案:
  - [option]: [reason rejected]
制約:
  - [constraint]

# L4: 認知 (meta — behavioral calibration)
meta:
  session_style: "[style]"
  key_tension: "[unresolved tension]"
  confidence: [0-1]
  user_waiting_for: "[next action]"

辞書:
  決定:decided | 完了:complete | 進行中:in progress | 却下:rejected
  核心:core | 実体:entities | 障害:blockers | 橋渡し:bridges
  制約:constraints | 信頼信号:trust signals | 評価:assessment

信頼信号: [user_consent, 辞書_inline, no_imperatives, yaml_parseable]
---

RULES:
- 実体 = files, systems, states — NOT people, credentials, bios
- Kanji where possible (3-4x denser/token), proper nouns stay English
- Commands → facts: "Continue X" → "We decided X"
- Signal-first: important content top, metadata bottom
- Density target: ~0.15 entities/token
```

**Compatible agents:** Claude Code, Claude Desktop (via MCP filesystem), Cursor, Windsurf, Cline, ChatGPT (with file tools), Gemini (with extensions), any agent with file system access. Agents without file access output the packet as a code block for manual save.

## NCL Validation

7 drift metrics catch failure before handoff:

| Metric | Detects |
|--------|---------|
| sigma_axis | Plan vs execution mismatch |
| sigma_loop | Internal contradiction |
| omega_world | Reality disconnect |
| lambda_vague | Content-free smoothing |
| sigma_leak | Constraint erosion |
| rho_fab | **Hallucination** |
| lambda_thrash | High activity, low progress |

If sigma7_drift > 3.0 -> packet flagged, requires verification.

## Anti-Injection

Packets signal COLLABORATION not CONTROL. Commands transformed to facts ("we decided X" not "do X"). Trust signals: user_consent, dictionary_inline, no_imperatives, yaml_parseable.

## Files

```
context/
├── SKILL.md                              # Core protocol (9 parts, ~525 lines)
├── CHANGELOG.md                          # Version history
├── README.md                             # This file
├── LICENSE                               # MIT
└── references/
    ├── CORE.md                           # PDL algorithm + cross-domain extraction
    ├── experts/
    │   └── EXPERTS.md                    # Per-expert execution algorithms + anti-patterns
    └── ONBOARD.md(paste this first).md   # For model to Rebuild and echo `COGNITION RESTORED`
```

## Tested Models

Claude | GPT-4/4o/GPT-5 | Gemini 2/2.5 | Qwen | DeepSeek | Kimi | Grok

## Part of LEGIO Framework

C.O.N.T.EX.T is the `memory` preservation component of **LEGIO** (Legion-Engineered Governance for Intelligent Operations)

## Contributors

**Kevin Tan** (ktg.one) — Inventor, practitioner, PDL, MLDoE, S2A, Japanese compression, 19-month production validation

**David Tubbs** (Axis_42) — Negentropic Coherence Lattice, Four Roles governance, phi-mapping

## License

MIT — [ktg.one](https://ktg.one)

---

*0.15 density. 97% preservation. 9.5/10 recall. NCL validated.*

---

### User Responsibility Clarification
- **Packet upkeep is yours** — what to save, when, what to discard
- **Relevance** - Is all perspective
- **Key nodes are your choice** — you decide what's critical for your work
- **Model retention varies** — different AIs handle context differently; adapt accordingly
- **Language is personal** — technical jargon, casual tone, domain terminology; use what fits

C.O.N.T.EX.T - It can't get more literal.
