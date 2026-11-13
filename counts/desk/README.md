> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Counts only. No key, seed, txid, covenant id, address, host, or port.
>
> The desk's sender log and the desk counter's chain read for pre-run 22. It is not Wednesday's count.

# Desk sender log and chain read

The files are absent until each step closes. None is written before `hashes/SIXTEEN.md` has an On origin line.

| File | Target |
|---|---|
| BASE.md | no payments, families plus our heavy lane at N = 0 (control), 2 whole minutes, an observation. The first line is `OBSERVATION` |
| HOLD-1.md | our one heavy lane, N = 8 at a fixed 460: the reference (2 whole minutes; pre-run 22 has no payment offer) |
| HOLD-2.md | the template probe: one lane at a fixed 460, submit cap 230 a minute, N = 15 (2 whole minutes), then N = 30 (2) |
| HOLD-3.md | the cap test: one lane N = 8, greedy at 110 percent from 600 with × 2 steps to 2,000, the cap guard, then the freeze (10 whole minutes) |
| HOLD-4.md | the pinned observation minute, lane N = 0 (drain). The first line is `OBSERVATION` |
| RETURN.md | lane N = 0, an observation of the drain and recovery, 2 whole minutes. The first line is `OBSERVATION` |

A row is submit-OK, attempts, rejects split into rate and full, and the waiting count per cohort. Each file also states the hop rate per cohort as built and path (pre-run 22, node rates: 100 for families 1–4, 150 for 5–8, 300 for 9–12, 450 for 13–16, all fixed), the node rate as built and in the desk mempool per tier, and whether the funding coins were one size, as read from the node. If they were not, it gives the sizes seen, rounded to whole tKAS, and does not call the fee the whole cause. A size is never guessed. Public nodes are local numbers. The paste is [GO-DESK.md](../../GO-DESK.md).

Pre-run 22 (lock line (iv)): each file also carries what the desk's private TN10 node accepted on chain, per minute, by accepting chain block header time: our payments, hops per cohort, other traffic, chain blocks, the desk node's DAA gap against a kept public kaspad, its sink age, and whether the counter kept pace. A lagging, partial, or not-final minute is marked and never filled in. Under the head, one line says in how many minutes our included payments were within 10 percent of submit-OK. It is reported, not scored. The whole run is in [counts/chain/TIMELINE.md](../chain/README.md).

Pre-run 22 (lock line (xii)): each file also carries the probe's mempool and template table for the same minutes. The whole probe timeline is [counts/chain/MEMPOOL.md](../chain/README.md).
