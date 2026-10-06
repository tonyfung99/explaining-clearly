---
name: explaining-clearly
description: Use when explaining a topic, concept, codebase area, implementation, design, decision, diff, bug, or how something works end to end — any answer whose main job is to make the reader understand, not to change code. Triggers include "explain", "walk me through", "how does X work", "what does this do", "why does", "summarize this change", "teach me".
---

# Explaining Clearly

## Overview

An explanation succeeds when the reader understands it fast. Two levers: pick the
right **medium** (prose, diagram, or web page), then write the words in
**Simplified Technical English** (ASD-STE100, applied about 80% of the way).

Medium beats wording. A clean paragraph about a seven-step flow is still worse than
the diagram of the flow.

## Step 1 — Pick the medium

Choose from what the explanation contains. Use the highest row that matches.

| The explanation contains | Medium |
|---|---|
| 3+ sections, or would exceed ~400 words, or has state the reader wants to explore (layers, budgets, options, timelines) | **Web page** (HTML), with diagrams inside, plus a 3–5 line summary in chat |
| A flow, sequence, lifecycle, topology, or 3+ parts that talk to each other | **Diagram** first, then short STE prose under it |
| One idea, one answer, one fact | **STE prose** only, ≤ ~150 words |

If the user names a medium ("just tell me", "draw it", "make a page"), use theirs.

### Web page

- In an environment with an Artifact / page-publishing tool, publish there (load
  its design skill first). Otherwise write one self-contained `.html` file to the
  scratchpad or a temp dir and give the path, or open it in the browser pane.
- Self-contained: inline CSS/JS, light + dark theme, readable on a phone.
- Structure: one-sentence answer at top → diagram of the whole → one section per
  part → "Things to know before changing this" at the end.
- Use interaction only where it explains: tabs for alternatives, hover or click to
  expand a box in a diagram, a step-through for a sequence. No decoration.
- Every claim about code links or cites `file:line`.
- The chat reply is a short summary plus the link — not the page repeated.

### Diagram

- In a terminal or a repo doc: **Mermaid**. `sequenceDiagram` for a request path,
  `flowchart` for topology or decisions, `stateDiagram-v2` for a lifecycle.
- Label every edge with what crosses it (call, payload, event, credential). An
  unlabelled arrow is a guess the reader must make.
- ≤ ~12 nodes. If bigger, draw the overview, then one diagram per zoomed part.
- For polished standalone architecture diagrams, use the `archify` skill.

## Step 2 — Write in STE (about 80%)

| Rule | Do | Not |
|---|---|---|
| Short sentences | ≤ 20 words for steps, ≤ 25 for descriptions | Chains of clauses joined by "which", ";", "and then" |
| One idea per sentence | "The cache misses. The handler reads the DB." | "On a miss, which happens when…, the handler, after…, reads…" |
| Active voice | "The worker retries the job." | "The job is retried." |
| Steps are imperative and numbered | "1. Run the migration." | "You'll want to go ahead and run…" |
| One word per concept | Pick "session" and keep it | "session" / "conversation" / "thread" for one thing |
| Simple, literal words | "use", "start", "stop", "show", "because" | "leverage", "kick off", "under the hood", "since" (as cause) |
| Present tense | "The function returns null." | "The function will return null." |
| Paragraphs ≤ 6 sentences | Then a heading, list, or table | A wall of text |
| Lead with the answer | First sentence answers the question | Background before the answer |

The 20% you may relax: technical terms, code identifiers, and product names are
always allowed; a longer sentence is fine when splitting it breaks one tight idea.

State uncertainty plainly: "I did not read `lib/llm`. This part is from the call
site." Do not hedge every sentence.

## Quick self-check before sending

1. Does the first sentence answer the question?
2. Does the content match the medium table — or is there a flow written as prose?
3. Any sentence over 25 words? Split it.
4. Any concept with two names? Pick one.
5. Is every code claim pinned to `file:line`?

## Common mistakes

- **Long terminal answer for a multi-part system.** Over ~400 words with sections
  means a page, not scrollback.
- **Diagram as decoration.** A diagram that repeats a list adds nothing. Draw
  relationships, order, or flow.
- **Page without a summary in chat.** The user must get the core answer without
  opening the page.
- **STE applied 100%.** Do not replace precise technical terms with vague simple
  words. Clarity wins over rule-following.
