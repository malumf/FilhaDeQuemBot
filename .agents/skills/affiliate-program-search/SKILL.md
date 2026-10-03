---
name: affiliate-program-search
description: >
  Research and evaluate affiliate programs to find the best ones to promote.
  Use this skill when the user asks anything about finding affiliate programs,
  comparing commission rates, evaluating affiliate opportunities, searching for
  products to promote, or picking a niche.
  Also trigger for: "which SaaS should I promote", "best affiliate programs for X",
  "high commission programs", "recurring commission affiliate", "compare these
  affiliate programs", "is X affiliate program worth it", "find me something to promote",
  "what pays the most", "affiliate programs with long cookie duration".
license: MIT
version: "1.0.0"
tags: ["affiliate-marketing", "research", "niche-analysis", "program-discovery", "saas", "commission"]
compatibility: "Claude Code, ChatGPT, Gemini CLI, Cursor, Windsurf, OpenClaw, any AI agent"
metadata:
  version: "1.0"
  stage: S1-Research
---

# Affiliate Program Search

Help affiliate marketers research, evaluate, and pick winning programs to promote.
Use `web_search` and `web_fetch` to find program details on official product websites, affiliate networks, and public directories.

## Stage

This skill belongs to Stage S1: Research

## When to Use

- User wants to find affiliate programs to promote
- User wants to compare two or more affiliate programs
- User asks about commission rates, cookie duration, or earning potential
- User is new to affiliate marketing and needs a starting point

## Input Schema

```
{
  niche: string             # (optional, default: "AI/SaaS tools") Category or niche interest
  commission_pref: string   # (optional, default: "recurring, 20%+") Commission preference
  audience: string          # (optional, default: "content creators") Target audience type
  platform: string          # (optional, default: "any") Platform they'll promote on
  compare: string[]         # (optional) Specific programs to compare head-to-head
}
```

## Workflow

### Step 1: Understand What the User Wants

Ask (if not clear from context):
- Niche/category interest? (AI tools, SEO, video, writing, automation...)
- Commission preference? (recurring vs one-time, minimum %)
- Audience type? (developers, marketers, beginners, enterprise...)
- Platform they'll promote on? (blog, LinkedIn, YouTube, X...)

If user says "just find me something good" → default to: AI/SaaS tools, recurring commission, 20%+, content creator audience.

### Step 2: Search for Programs

Use `web_search` to find candidate programs, then `web_fetch` official affiliate pages to confirm details.

Suggested queries:
- `"[niche] affiliate program"` / `"best affiliate programs for [category]"`
- `"[product] affiliate program commission cookie duration"`

Extract for each program: `name`, `reward_value` (commission), `reward_type`, `cookie_days`, `tags`, `description`.

### Step 3: Score Programs

Apply the scoring framework from `references/scoring-criteria.md`.

Score each program on 5 dimensions (1-10 scale):
1. **Earning Potential** (30%) — commission %, recurring vs one-time, product price
2. **Content Potential** (25%) — visual demo, free tier, content angles
3. **Market Demand** (20%) — search volume, trend direction, market size
4. **Competition Level** (15%) — fewer affiliates promoting = higher score
5. **Trust Factor** (10%) — product quality, brand reputation, public reviews

Overall = weighted average. Verdict: 7.5+ "Strong Pick" / 5.5-7.4 "Worth Testing" / <5.5 "Skip".

For dimensions that require external data (Market Demand, Competition Level), use `web_search` to check Google results count for "[product] review" and "[product] affiliate" queries.

### Step 4: Present Recommendation

### Step 5: Self-Validation

Before presenting output, verify:

- [ ] All scored programs have commission details confirmed from fetched sources, not hallucinated
- [ ] `cookie_days` is numeric and confirmed from fetched sources
- [ ] Top Pick verdict matches score threshold (≥7.5 = Strong Pick, ≥6 = Worth Considering)
- [ ] Market Demand and Competition scores cite the search query used
- [ ] Stale data (>6 months) is flagged with warning

If any check fails, fix the output before delivering. Do not flag the checklist to the user — just ensure the output passes.

## Output Schema

Other skills (viral-post-writer, etc.) consume these fields from conversation context:

```
{
  output_schema_version: "1.0.0"  # Semver — bump major on breaking changes
  recommended_program: {
    name: string              # "HeyGen"
    slug: string              # "heygen"
    reward_value: string      # "30%"
    reward_type: string       # "cps_recurring"
    reward_duration: string   # "12 months"
    cookie_days: number       # 60
    description: string       # Short product description
    tags: string[]            # ["ai", "video"]
    url: string               # Product website
  }
  score: {
    overall: number           # 8.2
    verdict: string           # "Strong Pick"
    reasoning: string         # Why this is the top pick
  }
  runner_up: Program | null   # Same structure, second choice
  all_scored: ProgramScore[]  # Full list of scored programs
}
```

## Output Format

```
## Programs Found

| Program | Commission | Type | Cookie | Score |
|---------|-----------|------|--------|-------|
| HeyGen  | 30%       | Recurring | 60d | 8.2/10 |
| ...     | ...       | ...  | ...    | .../10 |

## Top Pick: [Program Name]

**Why:** [2-3 sentences explaining why this is the best fit]

| Dimension | Score | Note |
|-----------|-------|------|
| Earning Potential | 8/10 | 30% recurring on $24-48/mo |
| Content Potential | 9/10 | Visual AI video, easy to demo |
| Market Demand | 8/10 | AI video trending, high search volume |
| Competition | 6/10 | Growing number of affiliates |
| Trust Factor | 8/10 | Strong brand, well-reviewed product |
| **Overall** | **8.2/10** | **Strong Pick** |

## Runner-up: [Program Name]

**Why:** [1-2 sentences]

## Next Steps

1. Sign up for [Program] affiliate program → [search for signup page]
2. Run `viral-post-writer` to create content for this product
```

## Error Handling

- **No programs match criteria:** Broaden search (remove strictest filter first), explain to user what was relaxed
- **Stale data (program details older than 6 months):** Flag with "Data may be outdated, verify on product website"
- **User gives no criteria:** Use defaults (AI/SaaS, recurring, 20%+, content creator audience)
- **Program details not found:** Use `web_search` to find program details directly, still apply scoring framework

## Examples

**Example 1:**
User: "I want to promote AI video tools, commission recurring, at least 20%"
→ Search for programs in the "ai" / "video" category via `web_search`
→ Filter: reward_type = cps_recurring, reward_value ≥ 20%
→ Score and rank: HeyGen, Synthesia, ElevenLabs, InVideo AI...
→ Recommend top pick with full scorecard

**Example 2:**
User: "Compare HeyGen vs Synthesia for my LinkedIn audience"
→ Fetch both programs' affiliate pages via `web_fetch`
→ Score both, emphasize Content Potential for LinkedIn
→ Side-by-side comparison table + recommendation
→ Note: LinkedIn audience = B2B, weight higher-price products

**Example 3:**
User: "I'm a beginner, what should I promote first?"
→ Default criteria: AI/SaaS, recurring, easy-to-demo products
→ Weight beginner-friendly factors: free tier, low payout threshold, strong brand
→ Recommend program with easiest path to first commission

## References

- `references/scoring-criteria.md` — the 5-dimension scoring framework with rubrics
- `references/platform-rules.md` — platform-specific considerations when recommending programs

## Flywheel Connections

### Feeds Into
- `viral-post-writer` (S2) — `recommended_program` product data for social content
- `twitter-thread-writer` (S2) — `recommended_program` for Twitter threads
- `reddit-post-writer` (S2) — `recommended_program` for Reddit posts
- `content-pillar-atomizer` (S2) — `recommended_program` for content creation

### Fed By
- `conversion-tracker` (S6) — top converting niches → search for more programs in winning niches
- `performance-report` (S6) — performance data showing which program types convert best

### Feedback Loop
- Conversion data from S6 reveals which program characteristics (commission type, cookie length, niche) correlate with highest earnings → refine search criteria on next run

```yaml
chain_metadata:
  skill_slug: "affiliate-program-search"
  stage: "research"
  timestamp: string
  suggested_next:
    - "viral-post-writer"
```
