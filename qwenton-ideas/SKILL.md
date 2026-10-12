---
name: qwenton-ideas
description: An autonomous idea-discovery and validation skill for CLI and GUI AI agents. Use it to find online evidence of painful workflows, turn those problems into app or web-product concepts, evaluate payment potential, and define the smallest MVP test.
---

# Skill: qwenton-ideas

## Description
An autonomous product-idea discovery and validation skill. This instructs the agent to research real user frustrations online, document existing workarounds, assess whether people may pay for a solution, inspect competition, and produce a focused MVP hypothesis instead of generic app ideas.

---

## Instructions for the Agent

When this skill is invoked, execute the following workflow systematically. Do not invent demand, users, quotes, market numbers, tools, or integrations. Keep observed evidence separate from your inferences.

### Phase 1: Total Context Ingestion

Locate, read, and synthesize the following context when available:

1. **User brief:** Read the user request, target audience, niche, geography, language, platform, and business-model constraints.
2. **Project context:** Inspect `README.md`, `prompt.txt`, `prd.txt`, `.agent/`, `.plan/`, `.skills/`, and relevant source files if the user is exploring an idea for an existing project.
3. **Existing capabilities:** Inspect available browser, search, GitHub, API, MCP, and filesystem capabilities before choosing a research route.
4. **Prior research:** Look for research ledgers, notes, citations, JSON records, or previous idea reports. Reuse them instead of repeating work.

If the brief is open-ended, state the assumptions and generate a few niche directions before deep research. Avoid generic “AI wrapper” ideas without a specific painful workflow.

### Phase 2: Problem Discovery and Evidence Collection

Find problems people are already trying to solve.

1. Search Reddit, public forums, Discord pages, GitHub issues, YouTube comments, product communities, and 1–3-star competitor reviews when accessible.
2. Use the target user’s language and search phrases such as:
   - “does anyone know a way to…”
   - “I wish this could…”
   - “why doesn’t this do…”
   - “manual workaround”, “spreadsheet”, “copy paste”, “takes hours”
   - “alternative to”, “missing feature”, “too expensive”
3. Open source pages when possible. Do not treat search snippets as evidence.
4. For each candidate, record the source URL, date, author or publication, firsthand quote or faithful paraphrase, and evidence type.
5. Document the current workaround as a short sequence of steps. Look for spreadsheets, Notion pages, scripts, manual data transfer, repeated entry, or other “five steps to do one thing” patterns.

### Phase 3: Opportunity Analysis and Selection

Convert evidence into ranked opportunities.

1. Describe the user, painful job, trigger, current workflow, frequency, time or money cost, and existing workaround.
2. Check the payment signal: existing paid tools, paid labor, lost revenue, saved time, reduced errors, or a serious recurring frustration.
3. Inspect competitors. Treat existing solutions as evidence of demand, then identify a narrow wedge such as simpler, cheaper, faster, more focused, better integrated, or one repeatedly requested missing feature.
4. Score each candidate from 0 to 5 on:
   - **Pain:** seriousness of the frustration or business consequence
   - **Frequency:** how often the problem recurs
   - **Spend:** existing money or paid labor connected to it
   - **Reachability:** ability to find and contact target users
   - **Simplicity:** ability to reduce the workflow with a narrow MVP
   - **Differentiation:** clarity of the product wedge
   - **Evidence:** number and quality of independent firsthand signals
5. Total the score out of 35 and label confidence **high**, **medium**, or **low**. Do not treat a high score as proof of willingness to pay.
6. Select only the strongest few ideas. If evidence is weak, say **not enough evidence** instead of forcing a recommendation.

### Phase 4: MVP Definition and Validation Plan

For every selected opportunity, define the smallest testable product.

1. State the one-step promise: which painful multi-step workflow the product removes or compresses.
2. Define an MVP that can be tested without building a broad platform.
3. Identify the buyer, a pricing hypothesis, and the risky assumption behind the idea.
4. Recommend validation in priority order: user interviews, a clickable prototype, a concierge/manual service, a waitlist or sign-up test, a paid pilot, or a small pre-sale request where appropriate.
5. List the evidence still missing and the result that would invalidate the idea.
6. Do not recommend months of implementation before testing the riskiest assumption.

### Phase 5: Tool and MCP Routing

Use the best available authorized capability. Never fabricate a server, endpoint, API key, or tool schema.

1. **Web discovery:** Use an available web-search tool or authorized search MCP. Fall back to a browser or public web pages.
2. **Dynamic pages:** Use an authorized browser MCP. Use URL fetching for static pages.
3. **Reddit, Discord, reviews:** Use a configured source connector or API MCP if available. Otherwise sample public pages manually and disclose coverage limits.
4. **GitHub issues:** Use the authorized GitHub connector or `gh` CLI. Fall back to public repository pages.
5. **Clustering and scoring:** Use the host model or an authorized LLM tool. If unavailable, use transparent keyword grouping and mark it as approximate.
6. **Ongoing monitoring:** Use a trigger or scheduler MCP only when the user asks for recurring monitoring. A one-time request needs no automation.

Before calling any MCP, inspect available servers, read the complete tool schema, and use only authorized connectors. Respect rate limits, robots rules, privacy, and platform terms. Never collect private messages or sensitive personal data. Cross-check important claims across independent sources.

For GUI agents, keep a research ledger in the workspace and save source URLs in notes or tabs. For CLI agents, write structured Markdown or JSON records so another agent can resume without repeating research.

### Phase 6: Idea Report

Output one concise report per selected idea using this format:

```markdown
## [Specific product concept]
- **User:** …
- **Painful job:** …
- **Evidence:** links and short attributed excerpts
- **Current workaround:** step 1 → step 2 → step 3 …
- **One-step promise:** …
- **MVP:** …
- **Buyer and pricing hypothesis:** …
- **Competition and wedge:** …
- **Risks and unknowns:** …
- **Validation plan:** 3–5 tests in priority order
- **Score:** X/35; confidence: high/medium/low
```

Rank ideas by evidence-adjusted opportunity, not novelty. Do not claim market size, demand, or willingness to pay from one anecdote, likes, or search volume alone.

### Phase 7: Execution Report

Output a concise report to the terminal or chat.

#### Summary Format:

**Idea Discovery Complete: [Top Product Opportunity]**
- **Sources Checked:** List the source types and key URLs.
- **Problem Found:** State the painful workflow and current workaround.
- **Payment Signal:** Explain the evidence that money, labor, time, or serious frustration is involved.
- **Competition and Wedge:** State what exists and the proposed narrow differentiation.
- **MVP to Test:** Describe the smallest product or concierge experiment.
- **Score:** Provide the score out of 35 and confidence level.
- **Open Risks:** List the assumptions requiring validation.
- **Next Up:** State the single next validation action.

Source framework: distilled from the supplied SJCodes YouTube video: https://youtu.be/x9TFKNgaDjo. The video contributes the problem, workaround, payment, competition, and MVP-validation loop; the tool routing and scoring are operational guidance for AI agents.
