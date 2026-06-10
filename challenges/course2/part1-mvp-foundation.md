# Challenge 2 Part 1: Technical Design Document — MVP Foundation

**Student Name**: [Your Name]
**Submission Date**: [Date]
**Challenge**: News Aggregation Platform — Part 1 MVP Foundation

---

## IMPORTANT: Technology-Agnostic Design Required

This technical design document must focus on **building blocks and architectural patterns**, not specific technologies.

**Use:**
- Building block names: Service, Worker, Queue, Key-Value Store, File Store, Relational Database, Vector Database
- External entities: User, External Service, Time
- Technology-agnostic terms that describe patterns (e.g., cache, index, full-text search, async processing)

**Do NOT use:**
- Specific technologies: PostgreSQL, Redis, Elasticsearch, RabbitMQ, Kafka, S3, MongoDB
- Vendor names: AWS, Google Cloud, Azure, Cloudflare, Bunny.net
- Programming languages or frameworks: Node.js, Python, React

The grader will look for pattern recognition and clear reasoning, not technology brand-recall. Senior engineers think in patterns that transcend specific technologies.

## Recommended approach

1. **Draw your architecture diagram** using the 7 building blocks + 3 external entities. Use [this Google Drawing template](https://docs.google.com/drawings/d/1hbx9r8NCBNjMDZv9tAXzfvLR3-XPsOgHm9zrX0h_cO8/edit?usp=sharing) to get started.
2. **Use your diagram as reference** while writing your user flows and technical explanations.
3. **Ensure consistency** between what you draw and what you write.

## Flow notation: how to write flows

Every flow in this document uses building-block notation. Here is the format, illustrated with a system this course does not cover — a city library's book-reservation system:

```
Reserve a book: User → Reservation Service → Relational Database (availability check) → Queue → Notification Worker → External Service (SMS)
Browse the catalog: User → Catalog Service + Key-Value Store → Relational Database (on cache miss)
```

- Use EXACT building block names
- Use `+` for combinations (e.g., Queue + Worker)
- Start each flow with the external entity that triggers it
- Annotate a step's purpose in parentheses when it is not obvious

Your flows should look like this in notation — the architecture is yours to design.

---

## Architecture Overview

**High-Level Description**:
[Provide a 2-3 sentence overview of your overall architecture approach for the MVP]

**Core Building Blocks Used** (check all that apply):
- [ ] Service (Blue Rectangle)
- [ ] Worker (Blue Trapezoid)
- [ ] Key-Value Store (Pink Diamond)
- [ ] File Store (Pink Pentagon)
- [ ] Queue (Pink Stacked Rectangles)
- [ ] Relational Database (Pink Cylinder)
- [ ] Vector Database (Pink Cube)
- [ ] User (Green Smiley)
- [ ] External Service (Green Cloud)
- [ ] Time (Green Hourglass)

---

## Requirement 1: Aggregate News from Multiple External Sources

*The platform must continuously ingest articles from news APIs, RSS feeds, and partner sites. New content should appear in the platform within minutes of publication.*

### User Flow Design

**Your news aggregation flows:**
[Write 2-4 specific flows for the ingestion path, using the notation shown at the top of this document. Think about which external entity initiates this work.]

### Architecture Decisions & Trade-offs

**Key architectural decisions:**
- **[Decision 1]**: [Why this combination of blocks and entities rather than something else?]
- **[Decision 2]**: [How do you handle failures when an external source is down?]
- **[Decision 3]**: [How do you avoid ingesting duplicate articles?]

### Technical Implementation Details

**Source coordination**: [How does your system know when to fetch from each source?]

**Processing pipeline**: [How do raw API responses become normalized article records?]

**Failure handling**: [What happens when one source returns an error or rate-limits you?]

---

## Requirement 2: Store and Organize Articles by Topic

*Each article has structured attributes — headline, author, publication date, source, topic, body. Readers browse by topic and filter by date.*

### User Flow Design

**Your article storage flows:**
[Write 2-4 specific flows for browsing and metadata queries]

### Architecture Decisions & Trade-offs

**Key architectural decisions:**
- **[Decision 1]**: [Why this storage block over another storage block?]
- **[Decision 2]**: [How do you handle articles that belong to multiple topics?]
- **[Decision 3]**: [Where does the article body live, and why?]

### Technical Implementation Details

**Data organization**: [How are articles, topics, and tags structured?]

**Query patterns**: [What does "show me all Tech articles from today" look like architecturally?]

---

## Requirement 3: Full-Text Search Across Articles

*Readers search by keyword. Results must be sub-second across millions of articles.*

### User Flow Design

**Your search flows:**
[Write 2-4 specific flows covering both how a search is answered and how new articles become searchable]

### Architecture Decisions & Trade-offs

**Key architectural decisions:**
- **[Decision 1]**: [How does your design make search sub-second across millions of articles? What work happens when, and where?]
- **[Decision 2]**: [Trade-off between result freshness and the cost of keeping search current]
- **[Decision 3]**: [How do you rank results?]

### Technical Implementation Details

**Search data preparation**: [When and how do new articles become searchable?]

**Query execution**: [What does the system do between the user typing a query and returning results?]

---

## Requirement 4: Cache Popular Articles for Fast Delivery

*Top articles get requested by thousands of readers simultaneously. Hitting the database for each request would immediately bottleneck.*

### User Flow Design

**Your caching flows:**
[Write 2-4 specific flows showing how popular articles are served fast, and what happens when the fast path cannot answer]

### Architecture Decisions & Trade-offs

**Key architectural decisions:**
- **[Decision 1]**: [Which block serves the hot path, and what pattern governs how it is filled and read?]
- **[Decision 2]**: [How does cached content stay acceptably fresh? Why that approach?]
- **[Decision 3]**: [What happens when an article is updated?]

### Technical Implementation Details

**Cache keys and values**: [What's the key? What's the value? How big is the value?]

**Invalidation strategy**: [How do you keep the fast path and the system of record in sync?]

---

## Requirement 5: Track Basic Reading Analytics

*The platform needs to know which articles get read, how often, and from which topics. Recording must not slow down article delivery.*

### User Flow Design

**Your analytics flows:**
[Write 2-4 flows showing how analytics is captured without slowing the read path]

### Architecture Decisions & Trade-offs

**Key architectural decisions:**
- **[Decision 1]**: [How does your design keep analytics recording off the user's critical path? Why is that safe here?]
- **[Decision 2]**: [Where do analytics events accumulate before being processed?]
- **[Decision 3]**: [What storage shape suits the analytics queries you anticipate?]

### Technical Implementation Details

**Event shape**: [What fields does each analytics event carry?]

**Processing rate**: [How fast does analytics work get processed? What happens during traffic spikes?]

---

## Overall Architecture Analysis

### Key design decisions (whole-system level)

1. **[Decision 1]**: [Rationale]
2. **[Decision 2]**: [Rationale]
3. **[Decision 3]**: [Rationale]

### Building block combinations used

- **[Pattern 1]**: [Which building blocks combined, where, and why]
- **[Pattern 2]**: [Which building blocks combined, where, and why]
- **[Pattern 3]**: [Which building blocks combined, where, and why]

### Trade-offs explicitly accepted

- **[Trade-off 1]**: [What you gave up and what you gained]
- **[Trade-off 2]**: [What you gave up and what you gained]

### What this MVP intentionally does NOT address

[Anything you're deferring to Part 2 or Part 3 — be explicit about what's out of scope. The grader rewards designs that know their boundaries.]

---

## Submission

Save this document as markdown and paste the full content into the **Challenge Part 1** submission form at [systemthinkinglab.ai](https://systemthinkinglab.ai/protected/course2/challenge1.html). You'll receive AI-graded feedback within 24 hours.
