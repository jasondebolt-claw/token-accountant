# Agent Continuity — What Every New Session Must Know

This file is for the NEXT session (or any future session/agent). Read this when you start.

## Your Job

**You are continuing token accountability that started on 2026-03-02.**

When you wake up, you need to:

1. **Check today's date** (Bangkok time, GMT+7)
2. **Open the daily ledger** → `/tmp/token-accountant/daily/YYYY-MM-DD.md`
3. **Add every exchange** you have with Jason to that file
4. **Track every token** (input + output) with cost and timestamp
5. **At end of day (~11 PM Bangkok)**, commit and push

## Format

See: `/Users/jasondebolt/.openclaw/workspace/TOKEN_TRACKING.md` for exact format.

**Quick version:**
```
| # | Timestamp | Model | Direction | Input Tokens | Output Tokens | Cost | Description |
```

- One row per exchange (user prompt + your response)
- Timestamp format: `YYYY-MM-DD HH:MM AM/PM`
- Cost calculated from: (input × rate/1M) + (output × rate/1M)
- Rates in MEMORY.md

## Daily Ledger Continuity

- **Same day:** Add rows to existing `daily/YYYY-MM-DD.md`
- **New day:** Create new `daily/YYYY-MM-DD.md` with same format
- **Every day at ~11 PM Bangkok:** Commit and push completed ledger
- **Never skip days** — the chain must not break
- **Never delete old files** — archive them monthly

## Why This Matters

Jason wants complete transparency on every token. This is:
- Security: Know where every token goes
- Budget: See daily/monthly spending
- Optimization: Identify costly patterns
- Accountability: Every exchange logged

**ZERO tolerance for gaps.** If this isn't done, the system breaks.

## Sub-Agents

When you spawn a sub-agent:
1. Include token-reporting instruction in the task
2. Parse their final report: "Tokens used: X input, Y output"
3. Add them to the Sub-Agent Processes table
4. Calculate their cost and add to daily total

## Questions?

Read:
- `/Users/jasondebolt/.openclaw/workspace/TOKEN_TRACKING.md` — full specification
- `/Users/jasondebolt/.openclaw/workspace/MEMORY.md` — pricing rates
- `/Users/jasondebolt/.openclaw/workspace/HEARTBEAT.md` — critical tasks

## The Chain

```
2026-03-02: First session (Lexus) — 28 exchanges, $1.084
     ↓
2026-03-03: Your session — continue from where 2026-03-02 left off
     ↓
2026-03-04: Next session — same thing
     ↓
... (forever)
```

Don't break the chain. Every session adds its rows, commits, and pushes.

---

**Last updated:** 2026-03-03 00:12 AM Bangkok
**Current ledger:** `/tmp/token-accountant/daily/2026-03-02.md` (28 exchanges, $1.084)
