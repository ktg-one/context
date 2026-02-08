# CORE — MLDoE Unified Reference

MLDoE = PDL + Experts + CoD. One system, not four concepts.
Each expert IS a CoD iteration targeting a transformer attention layer.
See SKILL.md Parts 4 + 9 for the full mapping.

This file covers only what SKILL.md doesn't: the formal algorithm and cross-domain extraction.

---

## PDL Algorithm (Formal)

```
Input:  Conversation C, target compression ratio r
Output: Compressed context packet P

P_0 ← Initial sparse summary of C
FOR i = 1 to n iterations:
  E_i ← missing entities from C not in P_{i-1}
  R_i ← missing relations from C not in P_{i-1}
  P_i ← Fuse (E_i, R_i) into P_{i-1} without increasing length
  IF density(P_i) ≥ 0.15 ent/tok THEN BREAK
Append meta-cognitive markers (goals, constraints, user profile)
RETURN P_n
```

Unlike summarization ("what are key points?"), PDL asks "what must survive for a fresh instance to continue work?"
Summarization captures L1 only. MLDoE preserves L1-L4 as structured scaffold.

---

## Cross-Domain Preservation

### Formal Constraint
```
D = {d_1, d_2, ..., d_k}  // domains in conversation
∀ r(d_i, d_j) ∈ C WHERE i ≠ j:
  ∃ r'(d_i, d_j) ∈ P
  such that fresh_instance can infer original relationship
THRESHOLD: ≥95% preservation
```

### Detection Signals

**Explicit**: User says "X relates to Y because...", decision references multiple domains, constraint spans domains.

**Implicit**: Same entity in different domain contexts, reasoning chain crosses boundaries, conflict involves different-domain concepts.

**Structural**: Concepts from D_i and D_j in same L2.edge, L1.decision.rationale references multiple domains.

### Extraction Procedure
```
1. IDENTIFY domains — scan C for topic clusters, assign d_1..d_k
2. MAP concepts — assign primary domain per concept, flag multi-domain
3. EXTRACT intra-domain edges — within each d_i, add to L2 with xd=false
4. EXTRACT cross-domain edges (CRITICAL):
   FOR each (c_i, c_j) WHERE domain(c_i) ≠ domain(c_j):
     IF relationship exists → add to L2 with xd=true, NEVER_PRUNE
5. VALIDATE — preserved/original ≥ 0.95, re-scan if fails, max 2 retries
```

### Why Cross-Domain Edges Matter
```
Intra-domain:  recoverable from L1 facts alone
Cross-domain:  encode RELATIONSHIPS that facts don't capture
               Fresh instance needs xdomain to understand WHY decisions connected
```

### Examples
```yaml
# Business requirement → technical choice
- src: 50ms_latency_requirement
  tgt: redis_cache_choice
  rel: requires
  xd: true
  # Next session knows WHY redis, not just THAT redis

# Technique → capability
- src: chain_of_density
  tgt: context_extension
  rel: enables
  xd: true
  # Core insight CEP is built on

# Psychology → strategy
- src: credential_anxiety
  tgt: publication_timing
  rel: delays
  xd: true
  # Next session knows to push publication despite anxiety
```
