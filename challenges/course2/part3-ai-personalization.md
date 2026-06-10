# Challenge 2 Part 3: Technical Design Document — AI Personalization

**Student Name**: [Your Name]
**Submission Date**: [Date]
**Challenge**: News Aggregation Platform — Part 3 AI Personalization

---

## Context — what users are asking for

Your Part 2 platform handles viral traffic gracefully. But user feedback reveals the next frontier:

> *"Why do I keep seeing sports articles when I only care about tech?"*
> *"Why can't I just ask 'what happened with AI regulation this week?' instead of searching for keywords?"*
> *"Why does this platform show me the same content as everyone else?"*

This document is the **final evolution** — layering AI capabilities on top of your scaled Part 2 architecture. AI is added, not bolted on. The patterns from Parts 1 and 2 should remain intact and operational.

## IMPORTANT: Classification Matters Here

Part of the grade is classifying third-party AI capabilities into the correct building blocks and external entities. Apply the classification rules from the lessons carefully — a capability described with the wrong block costs points.

## Flow notation: how to write flows

Every flow in this document uses building-block notation. Here is the format, illustrated with a system this course does not cover — a city library's book-reservation system:

```
Reserve a book: User → Reservation Service → Relational Database (availability check) → Queue → Notification Worker → External Service (SMS)
Browse the catalog: User → Catalog Service + Key-Value Store → Relational Database (on cache miss)
```

Your flows should look like this in notation — the architecture is yours to design.

---

## Part 1 + Part 2 Architecture Recap

[Briefly summarize the architecture you have after Part 2 (2-3 sentences). This sets the baseline for what you're extending.]

---

## Requirement 7: Personalized AI-Powered Content Experience

This requirement splits into two distinct capabilities. Address both.

### Capability A: Personalized Feeds

*Each user sees content tailored to their reading history and interests. New users start with sensible defaults; the personalization improves as the system learns from behavior.*

### Capability B: Natural Language Search

*Users ask questions like "What happened with the federal budget this week?" and get relevant articles — not just articles containing those exact keywords. Keyword search finds documents; semantic search finds meaning.*

---

## Personalized Feed Architecture

### User Flow Design

**Your personalization flows:**
[Write 2-4 specific flows showing how user behavior becomes recommendations, and how a personalized feed gets served fast]

### Building Blocks Added

- **[Block or entity 1]**: [What it stores or does, and why this block is the right classification]
- **[Block or entity 2]**: [Same]
- **[Block or entity 3]**: [Same]

### Architecture Decisions & Trade-offs

- **[Decision 1]**: [When and where does personalization work happen, and why there?]
- **[Decision 2]**: [How fresh is "fresh enough" for a personalized news feed, and how does your design deliver that?]
- **[Decision 3]**: [How does this scale to millions of users with unique profiles?]

---

## Natural Language Search Architecture

### User Flow Design

**Your semantic search flows:**
[Write 2-4 specific flows showing how articles become findable by meaning and how a natural-language query gets answered]

### Building Blocks Added

- **[Block or entity 1]**: [What it stores or does, when it is involved, and why this block is the right classification]
- **[Block or entity 2]**: [Same]
- **[Block or entity 3]**: [Same]

### Architecture Decisions & Trade-offs

- **[Decision 1]**: [What you chose to build versus consume, and why]
- **[Decision 2]**: [How do you control the cost of repeated identical work in this path?]
- **[Decision 3]**: [What's the latency budget for semantic search vs traditional keyword search?]

---

## Trade-offs of AI Personalization

A strong Part 3 submission names the hard trade-offs explicitly. Identify at least three tensions that adding AI personalization to a news platform creates, and state how your architecture lands on each. For each one:

**[Tension]**: [What pulls in each direction, the choice you made, and the specific architectural mechanism that implements that choice.]

---

## Graceful Degradation: Designing for AI Failure

AI services fail. Your platform cannot go down when AI does.

For each AI capability, define the fallback:

| AI capability | Primary path | Fallback when AI is unavailable |
|---|---|---|
| Personalized feed | [Your primary path] | [Your fallback] |
| Semantic search | [Your primary path] | [Your fallback] |
| [Add your own] | [Primary path] | [Fallback path] |

**Architectural principle**: [State explicitly what your design guarantees about the core product when AI capabilities are unavailable.]

---

## Complete End-to-End Architecture

Provide a complete architecture diagram (or detailed text description) showing:

1. All Part 1 components (still present)
2. All Part 2 additions (still present)
3. All Part 3 additions (new)
4. The connections between them

[Include diagram or detailed text walkthrough]

---

## Trade-offs Explicitly Accepted

- **[Trade-off 1]**: [What you gave up to add AI]
- **[Trade-off 2]**: [What you gave up to add AI]
- **[Trade-off 3]**: [What you gave up to add AI]

---

## What This Architecture Intentionally Does NOT Address

[Be honest about what's out of scope. Examples: real-time collaboration on articles, multi-language support, video personalization. The grader rewards designs that know their boundaries.]

---

## Submission

Save this document as markdown and paste the full content into the **Challenge Part 3** submission form at [systemthinkinglab.ai](https://systemthinkinglab.ai/protected/course2/challenge3.html). Parts 1 and 2 must be graded before Part 3 can be submitted. This is the capstone of Course 2 — make it count.
