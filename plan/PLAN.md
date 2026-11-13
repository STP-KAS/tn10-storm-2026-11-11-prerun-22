> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md) · This page does not start a machine. Pre-run 22. Not Wednesday. Not Tuesday. Not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, or 21.

# Targets

There is no T0. There is no public clock. There is no latest minute. Nothing in pre-run 22 is scored: every step is an observation of whole minutes.

The hash file comes first and does not wait for the open. Nothing else in this page starts until the gates are true: Mini's TN10 node is synced with DAA moving; the desk's private TN10 node is up from its own data (PowerShell 7, no wipe) and synced; no Tuesday, Wednesday, or pre-run 1 to 21 runner is up; the operator has armed (no paste; see the README); our heavy lane's calibration on the node passed; and this repo's `logs/PRE-RUN-OPEN.md` is on origin.

## Order

1. **Nodes live.** Both TN10 nodes synced, DAA moving. No wipe.
2. **Calibration.** One lane transaction, read back from the desk mempool: node storage mass within 1 percent of our SDK's, fee rate 99–101. Otherwise the lane does not run and that is recorded.
3. **Hashes first.** [hashes/SIXTEEN.md](../hashes/README.md): sixteen rows, family label, tier, sha256 of the lowercase hex covenant id, and an On origin line.
4. **Families.** The sixteen covenant families start on the desk's private node, 1.2 hop/s offered. No payment sender of ours is started.
5. **Our one heavy lane** starts at N = 0 and follows one timeline of whole minutes set by the runner (lane 2 stays at N = 0 throughout):

| Order | File | The lane | Length |
|---:|---|---|---|
| 1 | BASE | 0 (control) | 2 whole minutes |
| 2 | HOLD-1 (the reference) | 8 at a fixed 460, no submit cap | 2 whole minutes |
| 3 | HOLD-2 (the template probe) | 15, then 30, at a fixed 460, submit cap 230 a minute (paced) | 2 + 2 whole minutes |
| 4 | HOLD-3 (the cap test) | 8, greedy at 110 percent, never down, from 600, × 2 steps, cap 2,000; cap guard; then the fee cap lowered on purpose | 10 whole minutes |
| 5 | drain, HOLD-4 | 0 | the pinned minute; the bot sends only on a free third public kaspad, or files `NO SEND` |
| 6 | RETURN (after-run control) | 0 | 2 whole minutes |
| 7 | tail | families and lane stopped, the counter reads on | 5 minutes |

The lane's N changes on the minute boundary, on a timeline fixed when the lane starts. The minutes between HOLD-3's end and the pinned minute are the start of the drain; they are in `counts/chain/TIMELINE.md`. The run is sized on the coins we hold (key 0 about 760 usable tKAS a family minute, 8,000 over the 18,000 line at the end): 30 planned family minutes.

## Cohorts (families, node rates): the bystanders

| Cohort | Families | Rate, sompi/gram of node mass | Weight against the outside stream at 100, (rate/100)^3 |
|---|---|---:|---:|
| floor | 1–4 | 100, fixed | 1.00 |
| r150 | 5–8 | 150, fixed | 3.38 |
| r300 | 9–12 | 300, fixed | 27.0 |
| r450 | 13–16 | 450, fixed | 91.1 |

A hop is about 41,100–41,700 node mass (storage mass; compute 9,123), a lane transaction about 266,700. kit24 is pre-run 17's, unchanged; no family reads a live rate in this run.

## The cap test (HOLD-3)

Once a minute, at 22 seconds past the minute or later (the counter's line for the minute just closed is final about 20 seconds after it ends), the desk runner reads that minute and moves the lane's rate:

| What it is | Metric | Reference |
|---|---|---|
| the lane, 8 chains | lane transactions landed in the minute | the lane's landings in HOLD-1's second minute (at 460) |

- **greedy at 110 percent:** metric under 110 percent of the reference: rate × 2, rounded, at most 2,000; it never steps down; otherwise unchanged. It starts at 600;
- the first minute of the cap test is not decided (the minute before it was HOLD-2's); an unread, partial or lagging minute holds the rate;
- **cap guard:** 4 decided minutes in a row at 2,000 → `CAP_REACHED`, back to 150, counters cleared; the same rule goes on deciding;
- **freeze, on purpose:** two decisions after that reset, `FROZEN_ARM` lowers the lane's fee cap to its fees so far plus 20 tKAS; the lane stops at that cap (`LANE_CAP`), the next decision logs `FROZEN` once, and no rate is moved after it.

The new rate takes effect about 22 seconds into the next minute. The per-minute snapshot of the rate and every decision are in `logs/duel.log` (lane 2 shows 150 and never moves; it is off).

## The template probe (HOLD-1 and HOLD-2)

The lane at a fixed 460 (no rule): 2 minutes with N = 8 and no submit cap (HOLD-1), then 2 minutes each with N = 15 and N = 30 under a submit cap of 230 a minute, paced evenly (about 3.8 a second). `tools/desk/tplwatch20.mjs` (read-only, unchanged) asks the desk node for a block template every 3 s (never submitted) and records its transaction count, its mass, how many transactions over 200,000 mass it holds, the mass of the rest, and the node's ready count and ready mass. The mempool probe reads how many of ours are in the desk mempool every few seconds.

## Connectivity guard (new in pre-run 22)

Pre-run 21 lost its network for about 8 minutes and its minute checks waited behind stuck pushes. The desk runner now checks every 10 s, on its own timer, the last minute that closed at least 25 s ago. While the plan has the lane at N > 0 and the lane has not stopped (a cap) and is not held, the minute is dark if the lane logged no minute, got no submit accepted, or none of ours landed on the desk counter (a counter row not there yet counts neither way). Two dark minutes in a row: `fail()` stops every sender (no sends), writes `FAILED` locally and publishes it with retries.

## Prediction, written before the run

- **The cap test.** Our offline check (`tools/sim/sim21.py`: the runner's rule re-typed, each decided minute drawing the lane's landings from pre-run 20's five minutes of 8 chains at 460, 225–244, and the reference from the same five; the largest ratio is 108 percent, under the 110 percent target) gives one path in every draw: **600 → 1,200 → 2,000, four decided minutes at 2,000, `CAP_REACHED` (about 6 minutes in), 150 → 300 → 600, `FROZEN_ARM`, `FROZEN`** about 9 minutes in. We expect the live run to follow it unless the landings at 2,000 rise more than 10 percent over the reference (we do not expect that: with 8 chains each chain waits for its last transaction to leave the mempool, which caps the lane near 240 a minute). We expect it to climb again after the reset as fast as before.
- **Cost.** About 1.23 tKAS a lane transaction at 460 and 5.34 at 2,000. About 560 tKAS for the reference, about 1,130 for the template probe, about 6,400 for the cap test: about 8,000–8,500 in all, under the 9,500 cap.
- **Bystanders at 2,000 with 8 chains.** If pre-run 20's reading holds (few of ours ready leave the template full), the tiers should lose only a little at 2,000 with 8 chains: we guess the floor at about 85–95 percent of BASE, r450 near 100. If the floor falls far lower at 2,000 than at 460 with the same 8 chains, the rate matters by itself and our reading was incomplete.
- **The template probe.** Paced at 230 a minute, our transactions should leave the mempool about as fast as they come, so with 15 or 30 chains only a few of ours should be waiting at once, about as with 8. **Our best guess (about 60 percent): the template stays about as full with 15 and 30 chains as with 8 (about 470,000), because what matters is how many of ours are ready, not how many chains we run or how many land.** If the template shrinks with 30 chains even at 230 a minute, the chain count matters by itself. If the paced lane still keeps many of ours waiting, the probe will read it, and we report that the two could not be told apart this way.
- **Other users** at up to about the lane's rate lose more the higher it goes; at 2,000 almost all of them pay less than our lane.

## Our heavy lane
## Our heavy lane

- **Shape.** One input (the chain's own coin, from the payment key), two plain pay-to-key outputs: 0.0375 tKAS to a dedicated sink key of ours, and the change back into the chain. Storage mass about 266,670 (KIP-9: 10^12 / 3,750,000 sompi for the small output, the change and input terms nearly cancel). Compute mass about 2,000. Fee rate × mass: about 0.40 tKAS at 150, 2.67 at 1,000 and 5.34 at the 2,000 cap.
- **Why this shape.** Our SDK counts every output at UTXO plurality 1 (pre-run 12's source check); plain outputs have plurality 1 on the node too, so the two agree. A covenant output (plurality 2) would be under-read by the SDK by a factor of four.
- **One lane, pre-run 20's process.** The lane uses chain slots 1–100 of pre-run 18's two-lane process (one node connection, one key-16 pile, its own N, rate and submit bucket: 1,200 a minute, 20 a second, or under a submit cap from `control/LANE-PERMIN` that many a minute, paced evenly); lane 2 (slots 101–200) stays at N = 0 all run, so the counter's lane-2 column (hv2) should read 0.
- **Ready count.** A chain's next transaction goes out only after the previous one has left the desk mempool. So each lane has at most N entries in the mempool and all are ready. About one 267,000-mass transaction fits a 500,000 block, so at about 10 blocks a second the chain takes at most about 600 heavy transactions a minute, shared with any outside heavy. In pre-run 20, 8 chains landed 225–244 a minute at 460 and 30 chains about 520.
- **Money.** Only from the payment key (key 16: 679 coins, 13,447 tKAS after pre-run 21, before this run's refill of key 0, which moved 130 of them, 2,630 tKAS; 549 coins, 10,811 tKAS, after). Each chain takes one pile coin and runs it down to under 2 tKAS, then takes the next. The family lane (key 0) is not touched by the heavy lane. The operator said tKAS is not a limit; the caps stay as guards, and the spend is logged.
- **Caps.** 1,200 lane submits a minute; pause above N + 2 lane entries for three probe samples; hold at mempool 90,000 or ready mass over 80 blocks; rate at most **2,000**; stop at **9,500** tKAS of fees (or the lower cap the runner sets on purpose in the cap test) or **10,000** tKAS moved, or the pile estimate under **1,000** tKAS (pre-run 20: 12,000 / 13,000 / 3,000); stop on any rejection that is not a timing one, or if the node's rate or mass on our own entries drifts from the calibration.
- **Swept before this run.** Pre-run 20's 0.0375 tKAS sink outputs (11,476, 430.35 tKAS) were swept back into the payment key before this repo was opened (12.90 tKAS of fees). This run's outputs stay on the sink key until a later, logged sweep.

## Why this shape

- The cap test needs a target the lane cannot meet, so the rule climbs every minute; 8 chains land about the same at any rate, and 110 percent is over their spread. 8 chains also keep the cost at 2,000 about half of 30's.
- The template probe keeps the rate (460) and holds the landings near 8 chains' while it raises the chain count, so a full template with 30 chains would mean pre-run 20's shrink came with many of ours waiting at once, not with the chain count or the landings alone.
- HOLD-1 gives the lane its reference at 460 and the template probe its N = 8; BASE gives the bystanders' reference.
- No payments: the only load is the families, our lane and whatever other TN10 traffic is there.

## What we read

For each minute: the lane's N and rate and every decision (`logs/duel.log`); the lane landed (counter); the desk node's template every 3 s (`tplwatch20.mjs`); hops per tier and each tier's node rate (as built and as the probe read it in the mempool) (desk counter, accepted on chain); our heavy in the mempool and ready (probe), our heavy landed (counter), lane submits (the lane's log); outside heavy at 100 (probe, entries not in our logs); the ready mass in blocks of 500,000 (from the full mempool read up to 10,000 entries, from the node's own figures above); the mempool size and the fee estimate. Mini is a second read of the hops.

## Selection rule

The desk node and the public kaspads answered serverVersion 2.1.0. In rusty-kaspa tag v2.1.0 (commit 01b532e8b553523216471682649693af92f0fd16), `mining/src/mempool/model/frontier.rs` takes every ready transaction best-first while the ready set's mass fits one block, and otherwise samples at random with weight (fee/mass)^3 (`ALPHA = 3`). Only a transaction with no parent in the mempool is ready, so a chained hop is not a candidate until its parent is out of the mempool. A higher fee raises the odds of being drawn; it does not buy a place in a queue. This is the source's rule, read from the code; the run reads the desk node's own template, not a miner's.

Abort line **18,000 usable tKAS** (key 0 coins over 3 tKAS, less 3 tKAS each). The coin count is logged, not a gate (pre-run 13 tripped on change fragments). Key 0 was consolidated and refilled before the open (sized on use; the runner's `BUDGET_CHECK`). Do not lower it.
