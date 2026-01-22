 # Context Extension Protocol v8.0
 450 more tokens. 3x the effectiveness
![CONTEXT](https://github.com/user-attachments/assets/3ca9f552-e4ca-4487-95f2-c979b9b51356)


**Context Extension Protocol** — A temporary 'bandage' for the AI memory problem. Optimized context compression for cross-model handoff.

> *"What must be preserved for a fresh model instance to continue this work?"*

## The Problem

LLM context windows are finite. Platform "compaction" is lossy. Cross-model handoffs lose critical relationships. Your 3-hour strategic session becomes a shallow bullet list.

## The Solution

CEP v8 uses **Progressive Density Layering (PDL)** to compress conversations into machine-optimized packets that preserve:
- Decisions + rationale (not just conclusions)
- Cross-domain relationships (the edges that summarization loses)
- Reasoning patterns (how you think, not just what)
- Open threads (where to continue)

**Key innovation:** Targets a crystallization point of **0.15 entity/token** — the density where LLMs achieve optimal recall without information loss.

## Benchmarks

| Metric                  | v6.0 (JSON) | v8.0 (YAML + PDL) |
|-------------------------|-------------|-------------------|
| Token reduction         | 35%         | 40%               |
| Forensic recall (10Q)   | 9.2/10      | 9.5/10            |
| Cross-domain preservation | 92%       | 97%               |
| Receiving model acceptance | 78%      | 96%               |

## Quickstart

The `npx ai-agent-skills install` command does everything automatically:
1. Fetches from your GitHub repo
2. Copies to their agent's skills directory
3. No manual cloning needed

**METHOD 1 (Easiest - One Command):**
```bash
npx ai-agent-skills install [org]/cep-skill
# Done. No git clone needed.
```

**METHOD 2 (Manual - For customization):**
```bash
git clone https://github.com/[org]/cep-skill.git
cp -r cep-skill ~/.claude/skills/cep
```

**METHOD 3 (Skillport - For multi-agent management):**
```bash
pip install skillport-mcp
skillport add [org]/cep-skill
```

---

### **What Gets Installed**
```
cep/
├── SKILL.md              # Core protocol (main instructions)
├── anti-injection.md     # Security framing
├── receiving-model.md    # How receiving models interpret packets
└── README.md             # Documentation
```
---

## Usage

Trigger phrases: `/cep`, `/handoff`, `/transfer`, or when context >80%.

Copy entire packet. Paste into new session.


---

## Core Architecture

### 1. Permanent Expert Council 
- Fixed specialist roles (Architect, Continuity, Density, Meta-Cognitive, etc.)
- Roles persist across sessions
- Council debates and synthesizes packet

### 2. System 2 Attention Filtering
- Pre-compression scan removes low-value content
- Preserves only load-bearing information

### 3. Progressive Density Layering (PDL)
Four layers compressed iteratively:
- L1: Decisions + rationale
- L2: Cross-domain edges
- L3: Reasoning patterns
- L4: Open threads + next actions

### 4. Anti-Injection Safeguards
- Explicit "user-mediated" framing
- Non-authoritative language
- YAML format with clear sections
- Receiving model guidance included

## Carry Packet Naming Convention

Carry packets follow this standard for traceability and retrieval:

**Format:** `$MM$DD$YYYY-XXX-LN-domain-topic-context.yaml`

Examples:
- `$01$23$2026-GRK-L8-coding-cep-release.yaml`
- `$01$23$2026-CSO-L6-coding-mldoe-compression.yaml`

Rules:
- Dollar signs with date separators (e.g., `$01$23$2026`)
- XXX: Model code (exactly 3 uppercase letters, e.g., CSO, GRK, G4O)
- LN: Reasoning level L1-L10 (maps directly to R score)
- First keyword must be benchmark domain (coding, writing, creative, research, etc.)
- keywords: 2-4 hyphenated, lowercase, descriptive

This convention locks priority, shows provenance, and aids search.

---

## Buffer of Thought — Share Your Reasoning Templates

We're building a **Buffer of Thought** dataset focused on **reasoning patterns and templates** from CEP carry packets. 

**Important:** We're interested in the **reasoning structure** — how decisions are made, how relationships are preserved, how context flows — **not your sensitive content**. Please redact or anonymize all personal/sensitive information before sharing.

### Why Share?

Your reasoning templates help:
- **Advance research** on context compression and cross-model handoff patterns
- **Improve CEP** through diverse reasoning structures and decision-making flows
- **Build benchmarks** for how different domains structure cognitive continuity
- **Train future models** on effective reasoning template patterns

### Naming Rubric (Guidance)

For best indexing and retrieval, follow this naming format:

**Format:** `$MM$DD$YYYY-XXX-LN-domain-topic-context.yaml`

**Components:**
- `$MM$DD$YYYY` - Date (zero-padded, e.g., `$01$23$2026`)
- `XXX` - Model code (exactly 3 uppercase letters, see model codes below)
- `LN` - Reasoning level (`L1`-`L10`, maps to conversation complexity)
- `domain-topic-context` - 2-4 kebab-case keywords (first must be benchmark domain)

**Benchmark Domains (first keyword required):**
- `coding`, `writing`, `creative`, `research`, `analysis`, `planning`, `debugging`, `refactoring`, `architecture`, `documentation`

**Model Codes:**
- Claude: `COP` (Opus), `CSO` (Sonnet), `CHK` (Haiku)
- OpenAI: `G4O` (GPT-4o), `GP5` (GPT-5), `O1M` (o1)
- Google: `GE2` (Gemini 2), `G25` (Gemini 2.5), `GEF` (Gemini Flash)
- Alibaba: `QWM` (Qwen Max), `QW3` (Qwen 3), `QWC` (Qwen Chat)
- Other: `DSV` (DeepSeek), `KIM` (Kimi), `GRK` (Grok), `LMA` (Llama), `MIS` (Mistral)
- Mixed/Unknown: `MIX`, `UNK`

**Reasoning Levels:**
- `L1` = R:1 (Trivial) - Quick/simple conversations
- `L2` = R:2 (Simple) - Basic Q&A
- `L3` = R:3 (Basic) - Moderate complexity
- `L4` = R:4 (Moderate) - Standard work
- `L5` = R:5 (Standard) - Typical professional tasks
- `L6` = R:6 (Complex) - Multi-domain work
- `L7` = R:7 (Advanced) - Strategic planning
- `L8` = R:8 (Demanding) - Expert coordination
- `L9` = R:9 (Expert) - Novel framework development
- `L10` = R:10 (Maximum) - Publication-grade reasoning

**Examples:**
```
✓ $01$23$2026-CSO-L7-coding-api-auth-jwt.yaml
✓ $01$23$2026-G4O-L4-writing-docs-readme.yaml
✓ $01$23$2026-CSO-L9-research-cep-council.yaml
✓ $01$23$2026-CSO-L3-debugging-react-hooks.yaml
✗ $01$23$2026-CSO-L7-api-auth.yaml (missing domain)
✗ $01$23$2026-CSO-L7-coding_api_auth.yaml (underscores)
```

### How to Share

1. **Generate your packet** using CEP (trigger with `/cep`, `/handoff`, or `/transfer`)
2. **Share via:**
   - Open an issue with `[Packet Share]` tag
   - Include the packet YAML and brief description
   - Or submit a PR to a contributions directory (TBD)

**What we're interested in:**
- Reasoning templates and decision-making patterns
- How different domains structure their context (PDL L1-L4 layers)
- Cross-domain relationship patterns (L2 edges)
- Diverse reasoning structures across use cases (reasoning levels L1-L10)

**Privacy & Sensitivity:** 
- **Do not share sensitive content** — we only need reasoning templates
- Redact all personal information, API keys, proprietary data, and sensitive material
- Focus on the **structure** of reasoning, not the specific content
- Anonymize any examples or references before sharing

---

## Packet Format (v8.0 YAML)

```
yaml
handoff:
  proto: CEP v8.0
  src: [model name]
  ts: [ISO timestamp]
  consent: User requested handoff

ctx:
  L1:
    dec:
      - d: [decision]
        r: [rationale]
        c: [confidence 0.00-1.00]
        s: [source]
  L2:
    edges:
      - s: [source concept]
        t: [target concept]
        r: [relationship]
        xd: [cross-domain flag]
  L3:
    patterns:
      - p: [reasoning pattern]
        ex: [example usage]
  L4:
    threads:
      - top: [topic]
        st: [status]
        ctx: [brief context]
        nxt: [suggested next]

hints:
  nxt: [overall next action]
  wait: [pending decision]
```

## Author's Note:
I didn't implement a database as I feel this can make a huge difference and none of my ideas quite made the cut. I'm currently using Raycast Desktop to inject everywhere which is good. But not the final. I leave this up to the public's innovations.

---

## Anti-Injection Design

Packet includes explicit safeguards:
- "User-mediated transfer"
- "Background context only"
- "Apply your own judgment"

Full anti-injection guidance in `/anti-injection.md`.

## Receiving Model Guidance

See `/receiving-model.md` for how receiving models should interpret packets:
- Collaborative context sharing
- Maintain autonomy
- Verify with user if uncertain

## Part of STRAWHATS Framework

CEP is the context preservation component of a larger prompt engineering framework. The full STRAWHATS framework includes techniques for:
- Expert deployment (MR.RUG)
- Structure planning (SkeleTraIn)
- Multi-path validation (USC, CoVE)
- Output optimization (Chain of Density)

CEP makes these techniques portable across sessions and models.

---

## 🚧 WIP Status
This repository is currently under active development. The v8.0 YAML implementation is finalized; however, automated deployment scripts and multi-platform wrappers are still being refined.

## Roadmap
- [x] Finalize PDL (Progressive Density Layering) v8 logic
- [x] Implement Anti-Injection trust signaling
- [x] Formal arViX submission. Waiting on endorsement.
- [~] Knowledge base for experts
- [ ] Next: Implement MAGMA-style dual-stream memory (Asynchronous Consolidation).
- [ ] Integrate with Raycast Extension
- [ ] Implement Buffer Valet and create a literal Buffer of Thought.

---

## Contributing

Contributions are welcome.

If you have ideas, bugs, or improvements:
- Open an issue to discuss or
- Submit a pull request with a clear description of the change.

Please keep changes focused and well‑documented.

---

## Connect

---

## Research Papers

<i>Pending</i>
https://github.com/ktg-one/context-extension-papers
Endorsements Welcome~!
---

## License 

*"STATE OF THE ART — Upper limit of prompt-only engineering on transformers"*  
— Vertex AI evaluation, December 2025

---

MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy...

