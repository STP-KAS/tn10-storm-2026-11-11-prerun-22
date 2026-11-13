> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value. Counts only.

> **Our own testing.** What this page shows is what our probe read on our own desk node in this run; it is not a claim of how TN10 behaves in general.

# Mempool and template timeline, pre-run 22

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.

## The run

Step is the runner's step at the minute's start (see TIMELINE.md).

| Minute (UTC) | Step | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T11:36 | families | 1 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 1 | 51 |
| 2026-11-13T11:37 | BASE | 3 | 3 | 3 | 0.25 | 0 | 0 | - | - | 0 | 0 / 0 | 3 / 3 | 0 / 0 | 0 / 0 | 0 / 0 | 3 | 124,307 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 3 | 2 |
| 2026-11-13T11:38 | BASE | 3 | 13 | 15 | 1.25 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 498,218 | 0 | 0 | 0 | 2 | 3 | 4 | 4 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T11:39 | BASE | 3 | 9 | 16 | 1.33 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 498,201 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 0 | 106.1 / 104.5 / 101.4 | 2 | 1 |
| 2026-11-13T11:40 | HOLD-1 | 3 | 13 | 16 | 3.47 | 0 | 0 | - | - | 0 | 4 / 4 | 4 / 4 | 4 / 4 | 3 / 3 | 4 / 4 | 6 | 474,252 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 0 | 270.0 / 167.3 / 112.9 | 10 | 1 |
| 2026-11-13T11:41 | HOLD-1 | 3 | 17 | 17 | 2.76 | 0 | 0 | - | - | 0 | 3 / 3 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 474,780 | 1 | 0 | 1 | 0 | 1 | 2 | 4 | 0 | 268.1 / 167.0 / 112.9 | 3 | 0 |
| 2026-11-13T11:42 | HOLD-2 | 2 | 16 | 16 | 4.60 | 0 | 0 | - | - | 0 | 8 / 8 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 497,432 | 1 | 0 | 1 | 1 | 3 | 4 | 4 | 0 | 297.9 / 171.8 / 113.4 | 2 | 8 |
| 2026-11-13T11:43 | HOLD-2 | 3 | 16 | 16 | 2.43 | 0 | 0 | - | - | 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 473,820 | 1 | 0 | 1 | 0 | 3 | 1 | 4 | 0 | 227.8 / 158.4 / 111.9 | 13 | 4 |
| 2026-11-13T11:44 | HOLD-2 | 3 | 12 | 22 | 4.13 | 5 | 5 | - | - | 0 | 6 / 6 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 474,272 | 1 | 0 | 1 | 0 | 1 | 1 | 3 | 0 | 307.7 / 173.1 / 113.5 | 12 | 13 |
| 2026-11-13T11:45 | HOLD-2 | 3 | 29 | 29 | 7.22 | 2 | 2 | 2 | 5,038 | 0 | 11 / 11 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 8 | 432,813 | 1 | 0 | 1 | 0 | 0 | 1 | 3 | 0 | 364.0 / 179.3 / 114.0 | 25 | 5 |
| 2026-11-13T11:46 | HOLD-3 | 3 | 21 | 21 | 3.99 | 0 | 0 | - | - | 0 | 5 / 5 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 473,163 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 0 | 374.1 / 180.1 / 114.1 | 22 | 3 |
| 2026-11-13T11:47 | HOLD-3 | 3 | 8 | 20 | 3.45 | 0 | 0 | - | - | 0 | 5 / 5 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 471,399 | 1 | 0 | 1 | 1 | 0 | 0 | 4 | 0 | 634.0 / 191.2 / 115.0 | 4 | 1 |
| 2026-11-13T11:48 | HOLD-3 | 3 | 9 | 17 | 1.85 | 0 | 0 | - | - | 0 | 1 / 1 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 473,426 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 0 | 346.3 / 177.6 / 113.9 | 17 | 0 |
| 2026-11-13T11:49 | HOLD-3 | 3 | 16 | 16 | 3.58 | 0 | 0 | - | - | 0 | 5 / 5 | 4 / 4 | 3 / 3 | 2 / 2 | 3 / 3 | 6 | 473,031 | 1 | 0 | 1 | 0 | 1 | 1 | 2 | 0 | 1139.9 / 195.8 / 115.3 | 16 | 1 |
| 2026-11-13T11:50 | HOLD-3 | 3 | 13 | 13 | 1.84 | 0 | 0 | - | - | 0 | 1 / 1 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 472,200 | 1 | 0 | 1 | 0 | 0 | 3 | 2 | 0 | 354.6 / 178.4 / 114.0 | 0 | 0 |
| 2026-11-13T11:51 | HOLD-3 | 3 | 18 | 18 | 2.92 | 0 | 0 | - | - | 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 472,704 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 0 | 992.0 / 195.2 / 115.3 | 19 | 1 |
| 2026-11-13T11:52 | HOLD-3 | 3 | 9 | 10 | 2.09 | 0 | 0 | - | - | 0 | 3 / 3 | 4 / 4 | 2 / 2 | 0 / 0 | 0 / 0 | 6 | 470,965 | 1 | 0 | 1 | 3 | 2 | 0 | 0 | 0 | 101.5 / 101.1 / 100.4 | 8 | 4 |
| 2026-11-13T11:53 | HOLD-3 | 3 | 17 | 27 | 2.95 | 7 | 7 | - | - | 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 471,904 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 1 | 172.9 / 140.8 / 109.5 | 7 | 7 |
| 2026-11-13T11:54 | HOLD-3 | 3 | 17 | 17 | 1.32 | 1 | 1 | - | - | 0 | 0 / 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 13 | 491,999 | 0 | 0 | 0 | 0 | 4 | 4 | 4 | 1 | 137.6 / 124.2 / 106.5 | 17 | 1 |
| 2026-11-13T11:55 | HOLD-3 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,469 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 134.8 / 122.6 / 106.2 | 16 | 0 |
| 2026-11-13T11:56 | HOLD-4 | 3 | 4 | 17 | 1.44 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 12 | 450,011 | 0 | 0 | 0 | 1 | 2 | 4 | 4 | 0 | 135.3 / 122.9 / 106.2 | 5 | 2 |
| 2026-11-13T11:57 | HOLD-4 | 3 | 12 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,214 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 134.8 / 122.7 / 106.2 | 1 | 0 |
| 2026-11-13T11:58 | HOLD-4 | 3 | 6 | 16 | 1.30 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 487,992 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 135.2 / 122.8 / 106.2 | 2 | 1 |
| 2026-11-13T11:59 | HOLD-4 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,631 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 137.9 / 124.3 / 106.5 | 3 | 0 |
| 2026-11-13T12:00 | HOLD-4 | 3 | 1 | 1 | 0.01 | 1 | 1 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 2,532 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T12:01 | RETURN | 2 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 1 | 1 |
| 2026-11-13T12:02 | RETURN | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T12:03 | RETURN | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T12:04 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 1 | 1 |
| 2026-11-13T12:05 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T12:06 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | 1 | 5,590 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T12:07 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 1 | 1 |
| 2026-11-13T12:08 | tail | 3 | 0 | 1 | 0.13 | 1 | 1 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T12:09 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 1 | 1 |
