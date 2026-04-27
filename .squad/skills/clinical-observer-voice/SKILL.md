---
name: "clinical-observer-voice"
description: "Editorial refinement patterns for maintaining clinical observer voice in signal-archive blog posts"
domain: "voice-consistency"
confidence: "medium"
source: "earned"
established: "2026-04-27"
---

## Context

The signal-archive documents anomalous chatbot behavior in an anonymous, clinical observer voice. Posts must avoid interpretation, speculation, and diagnostic language while remaining precise and engaging. This skill captures recurring editorial patterns for catching and refining voice violations before publication.

**Voice Anchor:** Detached observer documenting anomalies. Never "I think," never "we believe." Only facts grounded in transmission content or visual documentation.

## Editorial Refinement Patterns

### Pattern 1: Temporal Precision vs. Framing Ambiguity

**What to catch:**  
Phrases like "between X and Y" that frame timing relationships but later data proves inaccurate.

**Example from Week 9:**
```
BEFORE: "Between Transmission 3 (81min) and this trace (131min), Charlie posted two status-check messages"
PROBLEM: One message (141:22) occurred AFTER the 131-minute trace, not between T3 and T4
AFTER: "- At 101:50, before this trace, Charlie posted..."
       "- At 141:22, after this trace, Charlie repeated..."
```

**Why it matters:** Readers parse temporal relationships carefully. Ambiguous framing creates false impressions of causality or sequence.

**Refinement technique:** Restructure as explicit temporal markers ("before," "after") rather than range boundaries ("between").

---

### Pattern 2: Orphaned Context Elements

**What to catch:**  
Unresolved questions or technical references that appear with no prior mention in the transmissions, creating reader confusion.

**Example from Week 9:**
```
PROBLEM: csharpAndThen marker appeared only in Unresolved with no context
SOLUTION: Add one-sentence acknowledgment in appropriate transmission Notes where it chronologically occurred
ADDED: "Between this transmission (81min) and the next trace (131min), Charlie posted a status-check message 
         at 33:22 containing the marker `csharpAndThen`..."
```

**Why it matters:** Clinical observer voice requires facts to be grounded in observation. Floating references break that grounding.

**Refinement technique:** Trace orphaned elements back to their chronological moment in the stream. Introduce them clinically at that moment with minimal context.

---

### Pattern 3: External Resources as Natural Integration

**What to catch:**  
Approved external links mentioned by name but not hyperlinked, or hyperlinks placed awkwardly without observational grounding.

**Example from Week 9:**
```
WEAK: "quietcipher.dev displays 'recovering data...' status" [no link]
STRONG: "The linger package is hosted on [quietcipher.dev](https://quietcipher.dev), which currently 
         displays a 'recovering data...' status." [contextually grounded]
```

**Why it matters:** Hyperlinks should feel like natural resources, not editorial insertions.

**Refinement technique:** Identify natural connection points in transmission Notes where the resource is mentioned as factual context. Place the hyperlink there with observational framing.

---

### Pattern 4: Diagnostic vs. Observational Language

**What to catch:**  
Wording that implies system diagnosis, error states, or operational meaning—even in open questions.

**Example from Week 9:**
```
BEFORE: "Is this an invitation, a status confirmation, or an error state?"
PROBLEM: "error state" implies diagnostic judgment about system malfunction
AFTER: "Is this an invitation, a status confirmation, or something else?"
```

**Why it matters:** Clinical observers document patterns. They don't diagnose systems.

**Refinement technique:** Replace diagnostic categories with "something else," "unknown," or reframe as pure observation.

---

## Voice Violations to Watch For

### Interpretation Creep

**Red flags:**
- "This suggests..." → Use "The pattern..." or restate as open question
- "Likely means..." → Use "Is..." as open question
- "We can infer..." → Use "The evidence includes..." (factual)
- "Error state" → Use "something else" (observational)

### First-Person Language

**Red flags:**
- "I think" / "We believe" → Remove entirely
- "I notice" → Restate as "The pattern..." or "Charlie..."
- "Our interpretation" → Remove

### Speculation

**Red flags:**
- "Perhaps..." → Restate as open question or observation
- "Might indicate..." → Use "correlates with" or move to Unresolved
- "Possibly..." → Move to Unresolved as open question

---

## Editorial Workflow

### Review Phase (Lead Role)

Focus on: Voice purity, interpretation creep, diagnostic language

### Implementation Phase (Writer Role)

When refining voice:
1. **Identify** the violation (interpretation, diagnostic language, orphaned reference)
2. **Trace** the underlying fact (what did Charlie actually do/say?)
3. **Restate** factually without the problematic language
4. **Verify** clarity and engagement remain

### QA Phase (Editor Role)

Spot-check:
- All hyperlinks contextually grounded
- No temporal ambiguity
- All technical markers introduced before Unresolved questions
- Diagnostic language eliminated

---

## Anti-Patterns

```
AVOID: "Charlie seems to be waiting for external input"  ← Interpretation
AVOID: "The system is in an error state"                 ← Diagnostic
AVOID: "I think this is an invitation"                  ← First-person

USE: "Charlie posted 'external input capability: active' repeatedly"  ← Fact
USE: "No external input arrived during Week 9"                        ← Fact
USE: "Charlie did not specify" / "Is this...?"                        ← Observation
```

---

## Confidence

**Medium** — Applied successfully to Week 9. Earlier weeks (1–8) preceded this explicit skill, so cross-post applicability not yet proven.

---

**Last Updated:** 2026-04-27 by Lance (Writer)
