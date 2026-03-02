# Token Accountant

Daily token usage and cost tracking for Lexus (OpenClaw AI Agent).

## Structure

- `daily/YYYY-MM-DD.md` - Daily ledger with all transactions
- `monthly/YYYY-MM.md` - Monthly summary and totals
- `index.md` - Master index of all days

## Entry Format

Each day's file contains a table with:
- **Input Tokens** - Number of input tokens used
- **Output Tokens** - Number of output tokens used
- **Cost** - Estimated cost (calculated from tokens)
- **Description** - What the prompt/task was about

## Daily Totals

Each file ends with:
```
## Daily Total
- Total input tokens: X
- Total output tokens: Y
- Total cost: $Z.ZZ
```

## Purpose

Complete transparency and accountability for all token usage. Every message, sub-agent, and task is tracked.
