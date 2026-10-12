---
name: qwenton-ideas
description: Discover and validate profitable app or web-product ideas from online evidence. Use for CLI or GUI agents asked to find new product ideas, turn complaints into MVP concepts, research niches, inspect competitors, or decide whether an idea is worth building.
---

# Qwenton Ideas

Turn observed frustration into evidence-backed product opportunities. Prefer a small, paid problem over a clever feature or an unvalidated “cool app.”

## Operating rule

> Find demand that already exists; do not invent demand when the web can reveal it.

Treat the video framework as a decision loop, not a promise that every complaint is a business:

1. **Find a real problem.** Start with a niche, audience, workflow, tool, or competitor—not a feature list. Look for people already trying to solve something.
2. **Expose the workaround.** Document the current process. Pay special attention to spreadsheets, Notion pages, custom scripts, copy/paste between apps, repeated manual entry, and multi-step daily tasks. Convert the current “five steps” into the desired “one step.”
3. **Mine public evidence.** Search where the target users speak in their own words:
   - Reddit communities and forum threads
   - Discord or other public community pages
   - GitHub issues and feature requests
   - YouTube comments and tutorial questions
   - 1–3 star reviews of competing products
   - Search results for complaint and workaround phrases
4. **Validate the pain.** Prefer problems that make or save money, consume substantial time, create repeated frustration, or are already being solved with paid products or paid human labor.
5. **Position against competition.** Existing products are demand evidence, not automatic disqualification. Identify a defensible wedge: simpler, cheaper, faster, more focused, better integrated, or one missing feature repeatedly requested in reviews.
6. **Propose the smallest test.** Define an MVP that proves the risky assumption quickly. Recommend interviewing users, showing a clickable prototype, manually delivering the result, collecting waitlist/sign-up intent, or asking for a paid pilot before building a broad platform.

## Agent workflow

### 1. Define the search brief

Capture:

- Target user or niche
- Geography, language, and recency constraints
- Product type or platform constraints
- Preferred business model, if known
- Whether the user wants a shortlist, one recommendation, or a research dossier

If the brief is open-ended, generate several niche directions first, then investigate only the strongest few. Do not produce generic “AI wrapper” ideas without a specific painful workflow.

### 2. Search with the user’s language

Use queries combining the niche/tool with phrases such as:

- “does anyone know a way to…”
- “I wish this could…”
- “why doesn’t this do…”
- “manual workaround”
- “spreadsheet” / “copy paste” / “takes hours”
- “alternative to” / “missing feature” / “too expensive”

Search exact complaint language and paraphrases. Save the source URL, date, author or publication, relevant quote, and whether the evidence is firsthand. Do not treat search snippets as proof; open the source page when possible.

### 3. Extract evidence, not vibes

For every candidate, record:

- **User and job:** who has the problem and what they are trying to accomplish
- **Trigger:** the complaint, request, review, issue, or workaround
- **Current workflow:** the smallest faithful sequence of steps
- **Pain signal:** time, cost, error risk, lost revenue, compliance risk, or frustration
- **Frequency:** one-off, weekly, daily, or every transaction
- **Existing spend:** products, subscriptions, contractors, employees, or ad-hoc services already used
- **Competition:** closest alternatives and their repeated weaknesses
- **Unknowns:** claims requiring interviews or a live test

Keep observed evidence separate from the agent’s inference. Attribute quotes and never invent users, numbers, demand, or willingness to pay.

### 4. Score and rank

Score each candidate from 0–5, using evidence rather than optimism:

| Dimension | Question |
|---|---|
| Pain | Is this a serious frustration or business consequence? |
| Frequency | Does it recur often enough to matter? |
| Spend | Is money or paid labor already involved? |
| Reachability | Can the target users be found and contacted? |
| Simplicity | Can a narrow MVP reduce the workflow substantially? |
| Differentiation | Is there a clear wedge over existing options? |
| Evidence | Are there multiple independent, firsthand signals? |

Report the total out of 35, show the evidence behind each score, and label confidence as **high**, **medium**, or **low**. A high score never replaces validation.

### 5. Produce the idea brief

For each shortlisted idea, output:

```markdown
## [Specific product concept]
- **User:** …
- **Painful job:** …
- **Evidence:** links and short attributed excerpts
- **Current workaround:** step 1 → step 2 → step 3 …
- **One-step promise:** what the product removes or automates
- **MVP:** the smallest testable product
- **Buyer and pricing hypothesis:** who pays, why, and an initial test price
- **Competition and wedge:** what exists and the narrow advantage
- **Risks and unknowns:** what could invalidate the idea
- **Validation plan:** 3–5 concrete tests in priority order
- **Score:** X/35; confidence: …
```

Rank ideas by evidence-adjusted opportunity, not novelty. Say “not enough evidence” when appropriate.

## Tool and MCP routing

Use the best available authorized capability; never invent a server, endpoint, API key, or tool schema.

| Need | Preferred route | Fallback |
|---|---|---|
| Broad web discovery | Web search tool or an authorized search MCP | Browser/search engine or public web pages |
| Open and inspect dynamic pages | Browser MCP | URL fetch for static pages |
| Reddit, Discord, or review data | An authorized connector/API MCP for that source | Public pages and manual sampling; state coverage limits |
| GitHub issues | GitHub connector/API or `gh` CLI when authorized | Public repository pages |
| Repeated monitoring | Authorized trigger/scheduler MCP only when the user asks for ongoing monitoring | Perform a one-time research pass |
| LLM clustering or scoring | The host agent’s model or an authorized LLM tool | Deterministic keyword grouping with explicit limitations |

Before using an MCP:

1. Inspect the available MCP servers/tools for the needed capability.
2. Read the full tool schema before calling it; do not guess arguments.
3. Use only configured, authorized connectors. If a required source is unavailable, continue with public alternatives and disclose the gap.
4. Respect rate limits, robots rules, privacy, and platform terms. Prefer public, aggregated evidence; do not collect private messages or sensitive personal data.
5. Cross-check important claims across independent sources. A single viral post is a lead, not validation.

For GUI agents, keep a research ledger in the workspace and use browser tabs or saved notes for URLs. For CLI agents, write structured JSON or Markdown records so another agent can resume without repeating research.

## Guardrails

- Do not confuse a fun learning project with a product someone will pay for.
- Do not claim market size, demand, or willingness to pay from likes or one anecdote.
- Do not build for months before testing the riskiest assumption.
- Do not copy a competitor’s protected content or private data; use public observations to define an independent product.
- Prefer a narrow workflow and a manual concierge test before an elaborate architecture.

Source framework: distilled from the supplied SJCodes video, “How to come up with app ideas people will pay for” (YouTube: https://youtu.be/x9TFKNgaDjo). The source informs the problem/workaround/payment/competition loop; the tool-routing and scoring details above are implementation guidance for agents.
