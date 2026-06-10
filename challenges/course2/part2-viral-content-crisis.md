# Challenge 2 Part 2: Technical Design Document — Viral Content Crisis

**Student Name**: [Your Name]
**Submission Date**: [Date]
**Challenge**: News Aggregation Platform — Part 2 Viral Content Crisis

---

## Context — what happened

Your Part 1 platform launched six months ago. You grew from 10,000 to 500,000 daily users. Then a major world event broke. Traffic spiked **100x in 30 minutes**. Caches missed. The database buckled. Users saw error pages.

This document is your **evolution** of the Part 1 design — not a redesign. Part 2 should clearly build on the architecture you submitted for Part 1, adding components and modifying connections to address the new requirement.

## IMPORTANT: Technology-Agnostic Design Required

Use building block names, not technologies. See the Part 1 template for the full list. Scaling techniques are **patterns** — they describe what happens to building blocks, not new building block primitives. Name the pattern; do not name a vendor.

## Flow notation: how to write flows

Every flow in this document uses building-block notation. Here is the format, illustrated with a system this course does not cover — a city library's book-reservation system:

```
Reserve a book: User → Reservation Service → Relational Database (availability check) → Queue → Notification Worker → External Service (SMS)
Browse the catalog: User → Catalog Service + Key-Value Store → Relational Database (on cache miss)
```

Your flows should look like this in notation — the architecture is yours to design.

---

## Part 1 Architecture Recap

[Briefly summarize your Part 1 architecture in 2-3 sentences. Name the major components and how they connect. This sets the baseline for what you're evolving.]

---

## Requirement 6: Handle 100x Traffic Spikes Without Degradation

*The system must handle 100x traffic surges during breaking news events without service degradation. Users should experience consistent performance whether traffic is normal or spiking. No error pages. Response times stay under 200ms. Search still works. Analytics still get recorded.*

### Failure mode analysis

**Where does the Part 1 design break under 100x load?**

- **Bottleneck 1**: [Which component falls over first, and why?]
- **Bottleneck 2**: [What fails second, and why?]
- **Bottleneck 3**: [Any other failure modes you anticipate?]

---

## Requirement 6: Your Scaling Approach

Address the 100x requirement with the patterns you judge right for this system. For each change you make, name the building blocks involved and explain how the change slots into your Part 1 architecture.

### Change 1: [Name it]

**What you add or modify**: [Which blocks, where in the architecture]

**Why it helps**: [How does this address a bottleneck you identified?]

**Trade-off**: [What does this cost you?]

### Change 2: [Name it]

**What you add or modify**: [Which blocks, where in the architecture]

**Why it helps**: [How does this address a bottleneck you identified?]

**Trade-off**: [What does this cost you?]

### Change 3: [Name it]

**What you add or modify**: [Which blocks, where in the architecture]

**Why it helps**: [How does this address a bottleneck you identified?]

**Trade-off**: [What does this cost you?]

[Add more changes as your design requires.]

---

## Traffic Flow Under Both Conditions

A strong submission shows how a request flows through the system in two scenarios.

### Normal traffic (500K users)

Walk through what happens when a user requests a popular article:

1. [Step 1]
2. [Step 2]
3. ...

### Spike traffic (50M users in 30 minutes)

Walk through what happens to that same request during the spike:

1. [Step 1]
2. [Step 2]
3. ...

**Key insight**: [What stays the same? What changes? Where does the spike load get absorbed?]

---

## Failure Mode Analysis

Even with your evolution, name what would still break and how the system degrades:

- **[Scenario 1]**: [What breaks and how does the architecture handle it?]
- **[Scenario 2]**: [What breaks and how does the architecture handle it?]
- **[Scenario 3]**: [What breaks and how does the architecture handle it?]

---

## Cost Analysis (Optional but Rewarded)

[How does your evolved architecture handle 100x traffic without provisioning 100x resources? Cite specific places where smart architecture multiplies effective capacity.]

---

## Trade-offs Explicitly Accepted

- **[Trade-off 1]**: [What you gave up to gain resilience]
- **[Trade-off 2]**: [What you gave up to gain resilience]
- **[Trade-off 3]**: [What you gave up to gain resilience]

---

## What This Evolution Intentionally Does NOT Address

[Anything you're deferring to Part 3 — explicitly. The grader rewards designs that know their boundaries.]

---

## Submission

Save this document as markdown and paste the full content into the **Challenge Part 2** submission form at [systemthinkinglab.ai](https://systemthinkinglab.ai/protected/course2/challenge2.html). Part 1 must be graded before Part 2 can be submitted.
