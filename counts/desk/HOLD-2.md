OBSERVATION

Not scored. No payment of ours in pre-run 22: families only, on the desk's private node, plus our own heavy lane at the N shown per minute.

# HOLD-2, desk, pre-run 22

> Our own TN10 testing: what we observed in this run, on our own desk node. Counts only. Included is what the desk's private TN10 node accepted on chain, read by the desk counter, by accepting chain block time. Mini's files are a second read.

HOLD-2 in pre-run 22 is template probe (one lane at a fixed 460 with a submit cap of 230 a minute, about what N=8 lands: N=15, then N=30): L15-r460-cap230 2 whole minutes, L30-r460-cap230 2 whole minutes. Families only for payments (no payment of ours); our own heavy lane ran at the N and rate shown per minute (N = how many lane chains may each hold one ready transaction in the mempool). The HOLD file names are kept so the bot's and Mini's gates read as in earlier pre-runs. Not scored.

Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. No payment sender was started.

## Tiers against the mempool, per minute

| Minute (UTC) | Lane 1 N / rate | Lane 2 N / rate | floor (100) | r150 (150) | r300 (300) | r450 (450) | Our heavy in mempool / ready | Our heavy landed, lane 1 / lane 2 | Lane submits OK, lane 1 / lane 2 | Outside heavy at 100 (>200k mass) / ready | Outside at 100, n | Ready mass, blocks | Mempool | Fee estimate priority |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2026-11-13T11:42 | 15 / 460 | 0 / 100 | 236 | 247 | 295 | 326 | 8 / 8 | 230 / 0 | 230 / 0 | - / - | - | 4.60 | 16 | 297.9 |
| 2026-11-13T11:43 | 15 / 460 | 0 / 100 | 242 | 272 | 298 | 316 | 3 / 3 | 230 / 0 | 230 / 0 | - / - | - | 2.43 | 16 | 227.8 |
| 2026-11-13T11:44 | 30 / 460 | 0 / 100 | 228 | 242 | 271 | 299 | 6 / 6 | 230 / 0 | 230 / 0 | - / - | - | 4.13 | 12 | 307.7 |
| 2026-11-13T11:45 | 30 / 460 | 0 / 100 | 197 | 223 | 259 | 293 | 11 / 11 | 230 / 0 | 238 / 0 | 0 / 0 | 2 | 7.22 | 29 | 364.0 |

Lane 1 and lane 2 N / rate are the caps the runner set for that minute (N lane chains each, each chain with at most one ready transaction in the mempool) and each lane's fee rate (in the duel, the rate in effect at the start of the minute). Our heavy in mempool / ready is the probe's median count of our own lane entries; our heavy landed is what the desk counter read as accepted on chain from our lane in the minute; lane submits OK is the lane's own log. Hops are what the desk counter read as accepted on chain in that minute, per tier. Ready mass, blocks, is the median of the probe's samples in the minute (block limit 500,000). Outside at 100 is the median count of mempool entries not in our logs (our lane is in our logs) paying 100 sompi/gram, and heavy is how many of those had a mass over 200,000 (median of samples). The outside stream is not attributed to anyone.

## Chain, desk counter

| Minute (UTC) | Included, all non-coinbase | Our payments included | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Chain blocks | DAA gap max | Sink age max, ms | Final after, s | Counter |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T11:42 | 4,432 | 0 | 236 | 247 | 295 | 326 | 3,160 | 356 | 1 | 344 | 21 | kept pace |
| 2026-11-13T11:43 | 4,360 | 0 | 242 | 272 | 298 | 316 | 3,099 | 379 | 2 | 489 | 20 | kept pace |
| 2026-11-13T11:44 | 4,371 | 0 | 228 | 242 | 271 | 299 | 3,170 | 382 | 2 | 541 | 20 | kept pace |
| 2026-11-13T11:45 | 4,331 | 0 | 197 | 223 | 259 | 293 | 3,163 | 377 | 1 | 279 | 19 | kept pace |

Coinbase is taken out as one per merged blue block (on this node a chain block's accepted list carries the coinbase of each blue block it merges). Other traffic is the rest: other users' load, the genesis, and anything not in our logs.

## Hop rate per cohort, as built

Floor (families 1–4, desk private node): 100 sompi/gram per hop. R150 (families 5–8, desk private node): 150 sompi/gram per hop. R300 (families 9–12, desk private node): 300 sompi/gram per hop. R450 (families 13–16, desk private node): 450 sompi/gram per hop. In pre-run 22 that rate is on the hop's node-side mass (kit21): the builder is asked for a bill rate on its own mass so that fee / node mass is the tier's rate.

| Tier | Node rate as built, median (min–max) | Bill rate, median | Node mass, median (min–max) | Node rate in the desk mempool, lowest–highest (probe) |
|---|---|---:|---|---|
| floor (100) | 100.14 (100–100.32) | 317 | 41,312 (40,390–42,128) | 100.02–100.31 |
| r150 (150) | 150.15 (150–150.32) | 476 | 41,321 (40,484–42,167) | 150–150.31 |
| r300 (300) | 300.17 (300–300.32) | 951 | 41,313 (40,411–42,132) | 300.01–300.31 |
| r450 (450) | 450.16 (450–450.31) | 1426 | 41,317 (40,451–42,152) | 450–450.31 |

Node rate as built is kit21's fee / node mass (rusty-kaspa v2.1.0 storage mass with UTXO plurality, or compute or transient/2 if larger). In the desk mempool the probe divides the node's fee by the larger of the storage and compute mass the node reports.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 17 (350), 16 (321), 15 (318), 14 (244), 18 (211), 13 (184), 19 (159), 12 (148), 11 (104), 20 (86), 21 (80), 22 (76), and 16 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | R150 OK / att / rate rej / full rej / waiting | R300 OK / att / rate rej / full rej / waiting | R450 OK / att / rate rej / full rej / waiting | Family stalls logged | Family node mempool-high marks | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|---|---:|---:|---|
| 2026-11-13T11:42 | 0 | 0 | 0 | 0 | 0 | 239 / 364 / 0 / 0 / 4 | 251 / 370 / 0 / 0 / 4 | 297 / 377 / 0 / 0 / 4 | 327 / 386 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T11:43 | 0 | 0 | 0 | 0 | 0 | 242 / 356 / 0 / 0 / 4 | 272 / 361 / 0 / 0 / 4 | 298 / 355 / 0 / 0 / 4 | 316 / 368 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T11:44 | 0 | 0 | 0 | 0 | 0 | 226 / 351 / 0 / 0 / 2 | 240 / 351 / 0 / 0 / 2 | 267 / 364 / 0 / 0 / 0 | 295 / 373 / 0 / 0 / 0 | 0 | 0 | yes |
| 2026-11-13T11:45 | 0 | 0 | 0 | 0 | 0 | 197 / 351 / 0 / 0 / 2 | 225 / 365 / 0 / 0 / 4 | 263 / 371 / 0 / 0 / 4 | 297 / 377 / 0 / 0 / 4 | 0 | 0 | yes |

A family stall is a coordinator mark: no hop of that family landed for a while. The family was still attempting. It is logged, and it does not make the minute dirty.

A mempool-high mark means the family node read a mempool at or over 90,000. In pre-run 22 that does not stop the families: the skip does not apply to them. A skip, if one were set, is dirt with its reason (node-skip-fam) for every minute it covers, and it clears when the mempool falls back under the line.

Within 10 percent means 0 to 0 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 5. The family sender reads and submits every tier on the desk's private node, which the desk counter reads. The kept public kaspads are read for sync and DAA only; no payment of ours went to them.

Kept nodes are unique kaspads: each answered with its own node id at the preflight. 3 candidate endpoints passed the check and were 2 kaspads (node 4 is node 1; the second hostname was not used). 3 payment senders per kaspad.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 622341484 | 0 | 0 | 0 | 32 |
| 5 | yes | 622341485 | 0 | 0 | 0 | 39 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 904 of 904 | 768 | 1676 |
| r150 | 988 of 988 | 717 | 1637 |
| r300 | 1125 of 1125 | 610 | 1402 |
| r450 | 1235 of 1235 | 567 | 1146 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end. Every tier has the same hop shape and the same node; only the rate differs.

## Mempool and template, desk node (probe)

| Minute (UTC) | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T11:42 | 2 | 16 | 16 | 4.60 | 0 | 0 | - | - | 0 | 8 / 8 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 497,432 | 1 | 0 | 1 | 1 | 3 | 4 | 4 | 0 | 297.9 / 171.8 / 113.4 | 2 | 8 |
| 2026-11-13T11:43 | 3 | 16 | 16 | 2.43 | 0 | 0 | - | - | 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 473,820 | 1 | 0 | 1 | 0 | 3 | 1 | 4 | 0 | 227.8 / 158.4 / 111.9 | 13 | 4 |
| 2026-11-13T11:44 | 3 | 12 | 22 | 4.13 | 5 | 5 | - | - | 0 | 6 / 6 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 474,272 | 1 | 0 | 1 | 0 | 1 | 1 | 3 | 0 | 307.7 / 173.1 / 113.5 | 12 | 13 |
| 2026-11-13T11:45 | 3 | 29 | 29 | 7.22 | 2 | 2 | 2 | 5,038 | 0 | 11 / 11 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 8 | 432,813 | 1 | 0 | 1 | 0 | 0 | 1 | 3 | 0 | 364.0 / 179.3 / 114.0 | 25 | 5 |

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.
