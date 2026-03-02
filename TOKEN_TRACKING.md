# Token Tracking Standard

## Overview
Every single token used (input and output) must be tracked in the token-accountant repo with granular detail. This provides complete transparency and accountability.

## Daily Ledger Format

Each day's file: `daily/YYYY-MM-DD.md`

### Table 1: Exchange Log
Track every prompt, response, AND heartbeat task with exact timestamps.

**Columns:**
| # | Timestamp | Model | Direction | Input Tokens | Output Tokens | Cost | Description |
|---|---|---|---|---|---|---|---|
| 1 | 2026-03-02 08:15 AM | haiku | user-prompt | 2,100 | 0 | $0.002 | Asked to run x-list-ai script with top 5 posts |
| 2 | 2026-03-02 08:16 AM | haiku | lexus-response | 45,000 | 8,500 | $0.065 | Ran pipeline and showed results with JSON output |
| 3 | 2026-03-02 09:00 AM | haiku | heartbeat | 3,000 | 800 | $0.005 | Morning health metrics check and calendar verification |

**Rules:**
- One row per user prompt (has input tokens, 0 output)
- One row per Lexus response (has input tokens for context, output tokens for response)
- One row per heartbeat task (has input + output tokens - they consume tokens too!)
- **Timestamp:** YYYY-MM-DD HH:MM AM/PM (Bangkok time, GMT+7)
- **Model:** haiku, sonnet, or opus
- **Direction:** "user-prompt", "lexus-response", or "heartbeat"
- **Input Tokens:** Token count of that message
- **Output Tokens:** 0 for user prompts; token count for Lexus responses; token count for heartbeat tasks
- **Cost:** Calculate using rates from MEMORY.md:
  - Haiku: (input × $0.000001) + (output × $0.000005)
  - Sonnet: (input × $0.000003) + (output × $0.000015)
  - Opus: (input × $0.000005) + (output × $0.000025)
- **Description:** One concise sentence describing what was asked, responded, or checked
- **Heartbeat tasks to track:** Calendar checks, health metric checks, credential scans, security audits, journal sync, token accountant sync, agent logs, config sync

### Table 2: Sub-Agent Processes
Track every spawned sub-agent.

**Columns:**
| # | Agent | Model | Input Tokens | Output Tokens | Cost | Description |
|---|---|---|---|---|---|---|
| 1 | newsletter-analyzer | opus | 50,000 | 15,000 | $0.625 | Analyzed top 50 posts and generated narrative |

**Rules:**
- One row per sub-agent spawned
- **Agent:** Name/purpose of the sub-agent
- **Model:** haiku, sonnet, or opus
- **Input/Output Tokens:** From sub-agent's final report ("Tokens used: X input, Y output")
- **Cost:** Calculate using same rates as above
- **Description:** One sentence about what the sub-agent accomplished

### Daily Totals Section

```
## Daily Totals

**Main Session (Lexus):**
- Input tokens: 527,000
- Output tokens: 124,200
- Subtotal: 651,200 tokens
- Cost: $1.084

**Sub-Agents:**
- Input tokens: 50,000
- Output tokens: 15,000
- Subtotal: 65,000 tokens
- Cost: $0.625

**GRAND TOTAL:**
- Total input tokens: 577,000
- Total output tokens: 139,200
- Grand total tokens: 716,200
- **Total cost: $1.709**

## Breakdown by Model
- **Haiku:** $1.20 (70%)
- **Sonnet:** $0.35 (21%)
- **Opus:** $0.16 (9%)
```

## Calculation Reference

**Cost formula (per message):**
```
cost = (input_tokens × input_rate/1M) + (output_tokens × output_rate/1M)
```

**Example (Haiku, 45K input + 8.5K output):**
```
cost = (45000 × $0.000001) + (8500 × $0.000005)
     = $0.045 + $0.0425
     = $0.0875 ≈ $0.088
```

## Daily Sync Process

1. Create `daily/YYYY-MM-DD.md` or update existing
2. Add all exchanges from today:
   - User prompts (one row each)
   - Lexus responses (one row each)
   - Sub-agent spawns (separate table)
3. Calculate costs for each row using rates from MEMORY.md
4. Sum totals at bottom
5. Commit and push to GitHub
6. Update `memory/heartbeat-state.json` with last sync time

## Who Tracks What

**Lexus (main agent):**
- Automatically tracks all prompts/responses in daily ledger
- Calculates costs using MEMORY.md rates
- Records one-sentence description of each exchange

**Sub-Agents:**
- Must report token usage before finishing:
  - "Tokens used: 50000 input, 15000 output"
- Lexus parses report and adds sub-agent row to table
- Lexus calculates cost and adds to daily ledger

## Verification

- [ ] Every user prompt has a row (with 0 output tokens)
- [ ] Every Lexus response has a row (with output tokens)
- [ ] Every sub-agent has a row in sub-agent table
- [ ] All costs calculated correctly using MEMORY.md rates
- [ ] Daily totals sum matches individual rows
- [ ] Breakdown by model percentages sum to 100%
- [ ] File committed and pushed to GitHub

## Why This Matters

- **Transparency:** You see exactly where every token goes
- **Accountability:** Can trace any cost back to a specific action
- **Optimization:** Identify costly patterns and optimize
- **Budget control:** Daily totals help track spending
- **Sub-agent visibility:** Know when delegated work gets expensive
