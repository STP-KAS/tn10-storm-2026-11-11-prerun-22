OBSERVATION

Not scored. No payment of ours in pre-run 22: families only, on the desk's private node, plus our own heavy lane at the N shown per minute.

# HOLD-3, desk, pre-run 22

> Our own TN10 testing: what we observed in this run, on our own desk node. Counts only. Included is what the desk's private TN10 node accepted on chain, read by the desk counter, by accepting chain block time. Mini's files are a second read.

HOLD-3 in pre-run 22 is cap test (one lane, N=8, greedy: wants 110 percent of its reference and never steps down, from 600 with x2 steps up to the 2,000 cap; the cap guard puts it back to 150 after 4 decided minutes at 2,000; two decisions after that reset the lane's fee cap is lowered on purpose so the lane stops and the rule must freeze): L8-greedy-cap 10 whole minutes. Families only for payments (no payment of ours); our own heavy lane ran at the N and rate shown per minute (N = how many lane chains may each hold one ready transaction in the mempool). The HOLD file names are kept so the bot's and Mini's gates read as in earlier pre-runs. Not scored.

Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. No payment sender was started.

## Tiers against the mempool, per minute

| Minute (UTC) | Lane 1 N / rate | Lane 2 N / rate | floor (100) | r150 (150) | r300 (300) | r450 (450) | Our heavy in mempool / ready | Our heavy landed, lane 1 / lane 2 | Lane submits OK, lane 1 / lane 2 | Outside heavy at 100 (>200k mass) / ready | Outside at 100, n | Ready mass, blocks | Mempool | Fee estimate priority |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2026-11-13T11:46 | 8 / 600 | 0 / 150 | 246 | 255 | 282 | 323 | 5 / 5 | 227 / 0 | 222 / 0 | - / - | - | 3.99 | 21 | 374.1 |
| 2026-11-13T11:47 | 8 / 600 | 0 / 150 | 243 | 260 | 304 | 316 | 5 / 5 | 217 / 0 | 219 / 0 | - / - | - | 3.45 | 8 | 634.0 |
| 2026-11-13T11:48 | 8 / 1200 | 0 / 150 | 235 | 265 | 297 | 303 | 1 / 1 | 211 / 0 | 210 / 0 | - / - | - | 1.85 | 9 | 346.3 |
| 2026-11-13T11:49 | 8 / 2000 | 0 / 150 | 238 | 251 | 286 | 319 | 5 / 5 | 201 / 0 | 201 / 0 | - / - | - | 3.58 | 16 | 1139.9 |
| 2026-11-13T11:50 | 8 / 2000 | 0 / 150 | 237 | 258 | 279 | 294 | 1 / 1 | 204 / 0 | 200 / 0 | - / - | - | 1.84 | 13 | 354.6 |
| 2026-11-13T11:51 | 8 / 2000 | 0 / 150 | 238 | 258 | 305 | 330 | 3 / 3 | 201 / 0 | 204 / 0 | - / - | - | 2.92 | 18 | 992.0 |
| 2026-11-13T11:52 | 8 / 2000 | 0 / 150 | 241 | 271 | 298 | 318 | 3 / 3 | 220 / 0 | 220 / 0 | - / - | - | 2.09 | 9 | 101.5 |
| 2026-11-13T11:53 | 8 / 150 | 0 / 150 | 266 | 279 | 308 | 320 | 3 / 3 | 235 / 0 | 238 / 0 | - / - | - | 2.95 | 17 | 172.9 |
| 2026-11-13T11:54 | 8 / 300 | 0 / 150 | 261 | 273 | 289 | 300 | 0 / 0 | 113 / 0 | 107 / 0 | - / - | - | 1.32 | 17 | 137.6 |
| 2026-11-13T11:55 | 8 / 600 | 0 / 150 | 283 | 292 | 307 | 310 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 16 | 134.8 |

Lane 1 and lane 2 N / rate are the caps the runner set for that minute (N lane chains each, each chain with at most one ready transaction in the mempool) and each lane's fee rate (in the duel, the rate in effect at the start of the minute). Our heavy in mempool / ready is the probe's median count of our own lane entries; our heavy landed is what the desk counter read as accepted on chain from our lane in the minute; lane submits OK is the lane's own log. Hops are what the desk counter read as accepted on chain in that minute, per tier. Ready mass, blocks, is the median of the probe's samples in the minute (block limit 500,000). Outside at 100 is the median count of mempool entries not in our logs (our lane is in our logs) paying 100 sompi/gram, and heavy is how many of those had a mass over 200,000 (median of samples). The outside stream is not attributed to anyone.

## Chain, desk counter

| Minute (UTC) | Included, all non-coinbase | Our payments included | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Chain blocks | DAA gap max | Sink age max, ms | Final after, s | Counter |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T11:46 | 4,376 | 0 | 246 | 255 | 282 | 323 | 3,119 | 386 | 1 | 661 | 20 | kept pace |
| 2026-11-13T11:47 | 4,395 | 0 | 243 | 260 | 304 | 316 | 3,123 | 360 | 1 | 536 | 20 | kept pace |
| 2026-11-13T11:48 | 4,481 | 0 | 235 | 265 | 297 | 303 | 3,239 | 354 | 0 | 384 | 19 | kept pace |
| 2026-11-13T11:49 | 4,324 | 0 | 238 | 251 | 286 | 319 | 3,111 | 352 | 1 | 486 | 20 | kept pace |
| 2026-11-13T11:50 | 4,375 | 0 | 237 | 258 | 279 | 294 | 3,170 | 350 | 0 | 224 | 20 | kept pace |
| 2026-11-13T11:51 | 4,537 | 0 | 238 | 258 | 305 | 330 | 3,258 | 383 | 1 | 854 | 20 | kept pace |
| 2026-11-13T11:52 | 4,493 | 0 | 241 | 271 | 298 | 318 | 3,211 | 354 | 1 | 290 | 20 | kept pace |
| 2026-11-13T11:53 | 4,486 | 0 | 266 | 279 | 308 | 320 | 3,161 | 373 | 1 | 438 | 19 | kept pace |
| 2026-11-13T11:54 | 4,316 | 0 | 261 | 273 | 289 | 300 | 3,127 | 380 | 0 | 499 | 20 | kept pace |
| 2026-11-13T11:55 | 4,303 | 0 | 283 | 292 | 307 | 310 | 3,144 | 391 | 1 | 335 | 20 | kept pace |

Coinbase is taken out as one per merged blue block (on this node a chain block's accepted list carries the coinbase of each blue block it merges). Other traffic is the rest: other users' load, the genesis, and anything not in our logs.

## Hop rate per cohort, as built

Floor (families 1–4, desk private node): 100 sompi/gram per hop. R150 (families 5–8, desk private node): 150 sompi/gram per hop. R300 (families 9–12, desk private node): 300 sompi/gram per hop. R450 (families 13–16, desk private node): 450 sompi/gram per hop. In pre-run 22 that rate is on the hop's node-side mass (kit21): the builder is asked for a bill rate on its own mass so that fee / node mass is the tier's rate.

| Tier | Node rate as built, median (min–max) | Bill rate, median | Node mass, median (min–max) | Node rate in the desk mempool, lowest–highest (probe) |
|---|---|---:|---|---|
| floor (100) | 100.16 (100–100.32) | 315 | 41,076 (40,377–42,136) | 100–100.32 |
| r150 (150) | 150.16 (150–150.32) | 473 | 41,085 (40,383–42,133) | 150–150.32 |
| r300 (300) | 300.16 (300–300.32) | 945 | 41,077 (40,403–42,143) | 300–300.32 |
| r450 (450) | 450.16 (450–450.32) | 1417 | 41,067 (40,423–42,598) | 450–450.31 |

Node rate as built is kit21's fee / node mass (rusty-kaspa v2.1.0 storage mass with UTXO plurality, or compute or transient/2 if larger). In the desk mempool the probe divides the node's fee by the larger of the storage and compute mass the node reports.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 10 (254), 11 (246), 12 (243), 13 (241), 9 (233), 14 (195), 15 (175), 8 (172), 7 (134), 16 (108), 6 (87), 17 (86), and 16 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | R150 OK / att / rate rej / full rej / waiting | R300 OK / att / rate rej / full rej / waiting | R450 OK / att / rate rej / full rej / waiting | Family stalls logged | Family node mempool-high marks | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|---|---:|---:|---|
| 2026-11-13T11:46 | 0 | 0 | 0 | 0 | 0 | 248 / 362 / 0 / 0 / 2 | 253 / 360 / 0 / 0 / 0 | 278 / 360 / 0 / 0 / 0 | 319 / 376 / 0 / 0 / 0 | 0 | 0 | yes |
| 2026-11-13T11:47 | 0 | 0 | 0 | 0 | 0 | 242 / 372 / 0 / 0 / 3 | 261 / 372 / 0 / 0 / 3 | 304 / 381 / 0 / 0 / 0 | 316 / 378 / 0 / 0 / 0 | 0 | 0 | yes |
| 2026-11-13T11:48 | 0 | 0 | 0 | 0 | 0 | 235 / 367 / 0 / 0 / 0 | 262 / 368 / 0 / 0 / 0 | 298 / 364 / 0 / 0 / 1 | 307 / 373 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T11:49 | 0 | 0 | 0 | 0 | 0 | 239 / 368 / 0 / 0 / 4 | 254 / 364 / 0 / 0 / 3 | 289 / 370 / 0 / 0 / 4 | 319 / 391 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T11:50 | 0 | 0 | 0 | 0 | 0 | 233 / 365 / 0 / 0 / 0 | 255 / 372 / 0 / 0 / 0 | 276 / 376 / 0 / 0 / 1 | 290 / 361 / 0 / 0 / 0 | 0 | 0 | yes |
| 2026-11-13T11:51 | 0 | 0 | 0 | 0 | 0 | 242 / 363 / 0 / 0 / 4 | 262 / 365 / 0 / 0 / 4 | 308 / 379 / 0 / 0 / 4 | 334 / 391 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T11:52 | 0 | 0 | 0 | 0 | 0 | 241 / 354 / 0 / 0 / 4 | 271 / 359 / 0 / 0 / 4 | 298 / 366 / 0 / 0 / 4 | 318 / 376 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T11:53 | 0 | 0 | 0 | 0 | 0 | 264 / 374 / 0 / 0 / 2 | 277 / 374 / 0 / 0 / 2 | 308 / 383 / 0 / 0 / 4 | 320 / 390 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T11:54 | 0 | 0 | 0 | 0 | 0 | 261 / 374 / 0 / 0 / 2 | 273 / 368 / 0 / 0 / 2 | 285 / 376 / 0 / 0 / 0 | 296 / 375 / 0 / 0 / 0 | 0 | 0 | yes |
| 2026-11-13T11:55 | 0 | 0 | 0 | 0 | 0 | 285 / 369 / 0 / 0 / 4 | 294 / 372 / 0 / 0 / 4 | 311 / 373 / 0 / 0 / 4 | 314 / 372 / 0 / 0 / 4 | 0 | 0 | yes |

A family stall is a coordinator mark: no hop of that family landed for a while. The family was still attempting. It is logged, and it does not make the minute dirty.

A mempool-high mark means the family node read a mempool at or over 90,000. In pre-run 22 that does not stop the families: the skip does not apply to them. A skip, if one were set, is dirt with its reason (node-skip-fam) for every minute it covers, and it clears when the mempool falls back under the line.

Within 10 percent means 0 to 0 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 5. The family sender reads and submits every tier on the desk's private node, which the desk counter reads. The kept public kaspads are read for sync and DAA only; no payment of ours went to them.

Kept nodes are unique kaspads: each answered with its own node id at the preflight. 3 candidate endpoints passed the check and were 2 kaspads (node 4 is node 1; the second hostname was not used). 3 payment senders per kaspad.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 622347453 | 0 | 0 | 0 | 32 |
| 5 | yes | 622347453 | 0 | 0 | 0 | 40 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 2490 of 2490 | 774 | 1489 |
| r150 | 2662 of 2662 | 691 | 1365 |
| r300 | 2955 of 2955 | 624 | 1223 |
| r450 | 3133 of 3133 | 569 | 1097 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end. Every tier has the same hop shape and the same node; only the rate differs.

## Mempool and template, desk node (probe)

| Minute (UTC) | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T11:46 | 3 | 21 | 21 | 3.99 | 0 | 0 | - | - | 0 | 5 / 5 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 473,163 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 0 | 374.1 / 180.1 / 114.1 | 22 | 3 |
| 2026-11-13T11:47 | 3 | 8 | 20 | 3.45 | 0 | 0 | - | - | 0 | 5 / 5 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 471,399 | 1 | 0 | 1 | 1 | 0 | 0 | 4 | 0 | 634.0 / 191.2 / 115.0 | 4 | 1 |
| 2026-11-13T11:48 | 3 | 9 | 17 | 1.85 | 0 | 0 | - | - | 0 | 1 / 1 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 473,426 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 0 | 346.3 / 177.6 / 113.9 | 17 | 0 |
| 2026-11-13T11:49 | 3 | 16 | 16 | 3.58 | 0 | 0 | - | - | 0 | 5 / 5 | 4 / 4 | 3 / 3 | 2 / 2 | 3 / 3 | 6 | 473,031 | 1 | 0 | 1 | 0 | 1 | 1 | 2 | 0 | 1139.9 / 195.8 / 115.3 | 16 | 1 |
| 2026-11-13T11:50 | 3 | 13 | 13 | 1.84 | 0 | 0 | - | - | 0 | 1 / 1 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 472,200 | 1 | 0 | 1 | 0 | 0 | 3 | 2 | 0 | 354.6 / 178.4 / 114.0 | 0 | 0 |
| 2026-11-13T11:51 | 3 | 18 | 18 | 2.92 | 0 | 0 | - | - | 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 472,704 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 0 | 992.0 / 195.2 / 115.3 | 19 | 1 |
| 2026-11-13T11:52 | 3 | 9 | 10 | 2.09 | 0 | 0 | - | - | 0 | 3 / 3 | 4 / 4 | 2 / 2 | 0 / 0 | 0 / 0 | 6 | 470,965 | 1 | 0 | 1 | 3 | 2 | 0 | 0 | 0 | 101.5 / 101.1 / 100.4 | 8 | 4 |
| 2026-11-13T11:53 | 3 | 17 | 27 | 2.95 | 7 | 7 | - | - | 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 471,904 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 1 | 172.9 / 140.8 / 109.5 | 7 | 7 |
| 2026-11-13T11:54 | 3 | 17 | 17 | 1.32 | 1 | 1 | - | - | 0 | 0 / 0 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 13 | 491,999 | 0 | 0 | 0 | 0 | 4 | 4 | 4 | 1 | 137.6 / 124.2 / 106.5 | 17 | 1 |
| 2026-11-13T11:55 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,469 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 134.8 / 122.6 / 106.2 | 16 | 0 |

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.
