> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Counts only. No key, seed, txid, covenant id, address, host, or port.
>
> Mini's second chain read for pre-run 22. The desk does not write this folder.

# Mini counts

Mini publishes a scored file when the desk's matching file is on origin. HOLD-4 waits for the bot file, the halt file, or 10 minutes, as [GO-MINI.md](../../GO-MINI.md) says. Mini counts only on its own synced TN10 node.

| File | Target |
|---|---|
| BASE.md | no payments, families plus our heavy lane at N = 0 (control), 2 whole minutes, an observation. The first line is `OBSERVATION` |
| HOLD-1.md | our one heavy lane, N = 8 at a fixed 460: the reference (2 whole minutes; pre-run 22 has no payment offer) |
| HOLD-2.md | the template probe: one lane at a fixed 460, submit cap 230 a minute, N = 15 (2 whole minutes), then N = 30 (2) |
| HOLD-3.md | the cap test: one lane N = 8, greedy at 110 percent from 600 with × 2 steps to 2,000, the cap guard, then the freeze (10 whole minutes) |
| HOLD-4.md | the observation minute |
| RETURN.md | lane N = 0 (drain), 2 whole minutes |

In pre-run 22 the desk counter is the first chain count and Mini is the second read. Each file's first line is Mini's own read: `READ`, `PARTIAL`, or `NOT READ`. The chat does not publish this folder.
