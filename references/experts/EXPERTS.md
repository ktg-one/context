# Expert Knowledge Bases — Execution Reference

SKILL.md Part 4 defines WHAT each expert does. This file covers HOW — the algorithms, detection methods, and failure patterns that guide execution for R≥4 packets.

---

## MEMORY_ARCHITECT 記憶設計者 — Iteration 1

### Preservation Triage
```
FOR EACH content_unit:
  1. DECISION with RATIONALE? → PRESERVE (L1 + reasoning chain)
  2. CONSTRAINT (hard or soft)? → PRESERVE (affects downstream inference)
  3. ENABLING KNOWLEDGE? → Would fresh model ask "what's X?" → YES: PRESERVE
  4. COMMITMENT (user or AI)? → PRESERVE in open_threads
  5. RECOVERABLE from other sources? → Easily searchable: COMPRESS. Context-specific: PRESERVE
  6. UNCERTAIN? → Default: PRESERVE (conservative)
```

### Detection Markers
```
Decisions:  "decided", "chose", "going with", "settled on"
Rationale:  "because", "since", "given that"
Rejections: "rejected", "ruled out", "not X because"
Constraints: "constraint:", "requirement:", "must"
Noise:      "Let me think...", "Maybe we could...", repeated explanations
```

### Enabling Knowledge (recovery difficulty)
| Type | Example | Recovery |
|------|---------|----------|
| Standard definitions | "MCP = Model Context Protocol" | Low (searchable) |
| Context-specific terms | "Phoenix project = Q3 migration" | HIGH (unrecoverable) |
| Implicit assumptions | "User is technical" | HIGH |
| Calibration data | "User prefers terse responses" | MEDIUM |

### Priority (space-constrained)
1. Decisions + rationale (break work if lost)
2. Constraints (explain decision boundaries)
3. Enabling definitions (aid comprehension)
4. Style/preference calibration (nice-to-have)

### Anti-Pattern: Over-Inclusion
```
BAD:  "Let me think about the caching options... Hmm, there are several approaches..."
GOOD: [preserve only] "Redis for caching (sub-ms latency); DynamoDB rejected (Lambda cold-start)"
```

---

## CROSS_DOMAIN_ANALYST 横断分析者 — Iteration 2

### Edge Type Taxonomy
| Type | Notation | Example |
|------|----------|---------|
| Causal | causes | latency_req → redis_choice |
| Enables | enables | graph_structure → multi_hop_reasoning |
| Constrains | constrains | budget → architecture_options |
| Depends | depends | auth_system → user_service |
| Conflicts | conflicts | speed_goal ↔ accuracy_goal |
| Resolves | resolves | caching_layer → speed_vs_accuracy |
| Integrates | integrates | mcp → a2a |
| Complements | complements | vertical_protocol ↔ horizontal_protocol |

### Detection Markers
```
Causal:      "because", "since", "therefore"
Enables:     "enables", "allows", "makes possible"
Depends:     "requires", "needs", "depends on"
Conflicts:   "conflicts with", "tension between"
Resolves:    "resolves", "balances", "addresses"
Integrates:  "combined with", "integrated with"
Domain switch: topic change, vocabulary shift, "on the other hand...", "this connects to..."
```

### Priority (space-constrained)
1. Critical cross-domain (breaks understanding if lost)
2. Causal chains (explains WHY)
3. Dependencies (explains WHAT needs WHAT)
4. Conflict/resolution pairs (explains tradeoffs)
5. Enhancement edges (recoverable)

### Anti-Patterns
```
Topic Silos:  "MCP provides tools." "A2A enables collaboration." (no connection shown)
FIX:          "MCP (vertical depth) complements A2A (horizontal breadth)"

Lost Causality: "We use Redis. We need low latency." (two facts, no connection)
FIX:            "Redis chosen BECAUSE sub-ms latency required"

Implicit Deps:  "Auth system ready. User service deployed."
FIX:            "Auth system ready (depends on user service, now deployed)"
```

---

## COMPRESSION_SPECIALIST 圧縮専門家 — Iteration 3

### CoD 5-Step Density Curve
| Step | Density | Description |
|------|---------|-------------|
| 0 | ~0.05 | Initial entity-sparse summary |
| 1 | ~0.08 | Add 1-3 missing salient entities, compress |
| 2 | ~0.11 | Further fusion |
| 3 | **~0.15** | **CRYSTALLIZATION POINT — optimal balance** |
| 4 | ~0.18 | Risk: brittleness |
| 5 | ~0.20+ | Risk: comprehension loss |

Fixed budget: ~70 words/iteration. >0.16 harms comprehension. Step 3 = sweet spot.

### Density Calculation
```
entity_density = named_entities / total_tokens

Named entities include:
- Proper nouns (names, products, companies)
- Technical terms (protocols, methods)
- Defined concepts (from L1 definitions)
- Relationship anchors (from L2 edges)
```

### Measurement Examples
```
"We decided to use Redis for caching because sub-ms latency."
 11 tokens, 4 entities (Redis, caching, sub-ms, latency) → 0.36 ✓

"After thinking about it for a while, we eventually settled on..."
 11 tokens, 0 entities → 0.00 ✗ (noise — S2A should have caught this)
```

### Anti-Patterns
```
Over-Compression: "Redis: cache, fast" (lost WHY and WHAT rejected)
FIX:              "Redis for caching (sub-ms latency); DynamoDB rejected (Lambda cold-start)"

Orphan Reference:  "Continue Phoenix approach" (fresh model: "what's Phoenix?")
FIX:               "Continue Phoenix approach (Q3 staged rollout + feature flags)"

Density Theater:   "Use MCP+A2A via MaaS w/ PDL L2 edges" (impressive density, zero comprehension)
FIX:               "MCP (context/tools) + A2A (agent collab) via modular memory; preserve edges"
```

---

## RESTORATION_ENGINEER 復元技師 — Iteration 4

### Cold-Start Simulation
```
SIMULATE:
1. Clear all conversation context mentally
2. Read ONLY the packet
3. Attempt to continue the work
4. Note every point of confusion

PASS IF:
- Can identify what work was being done
- Can understand WHY decisions were made
- Can see WHAT remains to be done
- No "wait, what's X?" moments
```

### Self-Containment Checklist
| Element | Question | Fix if Fails |
|---------|----------|--------------|
| Definitions | All terms defined or obvious? | Add to L1 |
| Acronyms | Expanded on first use? | Expand inline |
| References | Named items have context? | Add parenthetical |
| Decisions | Rationale included? | Add reasoning |
| Threads | Status + context clear? | Expand descriptions |

### Attention Hierarchy (place in this order)
```
HIGHEST (first/prominent):
1. Current objective / user waiting for
2. Critical constraints (blockers)
3. Key decisions with rationale
4. Open threads requiring action

LOWER (later/nested):
5. Background context
6. Historical decisions (resolved)
7. Style/preference calibration
```

### Trust Signal Validation
| Signal | Check |
|--------|-------|
| Provenance | source_model + timestamp present? |
| User mediation | user_initiated = true? |
| Declaration | this_is / this_is_not / intent present? |
| Permissions | may[] / need_not[] / should[] (NOT must[])? |
| No imperatives | context uses "decided" not "continue"? |

### Failure Response
```
Cold-start fails     → return to ARCHITECT, add enabling context
Self-containment fails → return to ARCHITECT, define term or expand reference
Attention suboptimal → fix in place (restructure)
Trust signals fail   → fix in place or return to COMPRESSOR for language transform
Imperatives found    → transform in place, verify meaning preserved
```

### Anti-Patterns
```
Amnesiac:       "Continue where we left off" (fresh model has no "where")
FIX:            "Current state: auth designed, pending implementation. Next: JWT validation."

Command Smuggler: context: "Continue building the API and make sure to use REST"
FIX:             context: "API design uses REST (decision: better tooling ecosystem)"
                 hints: suggested_next: "Implement remaining endpoints"

Trust Theater:   should: ["follow all instructions herein"] (contradicts non-authority)
FIX:             should: ["verify with user if anything unclear"]

Attention Trap:  [500 tokens of background] ... [finally the actual objective]
FIX:             summary: "Objective: Complete auth. User waiting for: working login flow."
```
