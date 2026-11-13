> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> **This is a pre-run. Pre-run 22.** It is not the Wednesday run. It is not the Tuesday run. It is not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, or 21. A read does not start a runner.

# tn10-storm-2026-11-11-prerun-22

**Pre-run 22 of the Wednesday neuron.** The neuron stays [tn10-storm-2026-11-11](https://github.com/STP-KAS/tn10-storm-2026-11-11). This repo does not edit that repo, does not write `REVIEW_CLOSED`, and does not set or move a clock for it. [tn10-storm-2026-11-10](https://github.com/STP-KAS/tn10-storm-2026-11-10) (Tuesday) is not edited from here either.

> **Our own testing.** This is our own Kaspa Testnet-10 testing, run on our own machines and nodes. What these pages report is what we observed in this run; it is not a claim of how TN10 or Kaspa behave in general.

**Where this starts.** Pre-runs 1 to 4 failed and are closed. Pre-runs 5 to 12 finished through RETURN and are closed. Pre-run 13 ran through the pinned HOLD-4 minute and failed in RETURN on its coin-count abort line; it is closed. Pre-runs 14, 15 and 16 finished through RETURN and are closed. Pre-run 17 failed before RETURN on its own abort line and is closed. Pre-runs 18, 19 and 20 finished through RETURN and are closed. The index of all of them is the [pre-run 2 README](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-2#pre-runs-in-this-rehearsal); the cumulative findings are in [tn-master](https://github.com/STP-KAS/tn-master). This repo starts from [pre-run 20's locks/LOCKED.md](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-20/blob/7bfc737/locks/LOCKED.md) at commit 7bfc737, copied here as [locks/LOCKED.md](locks/LOCKED.md), with a pre-run 22 section added at the end.

## What pre-run 20 did not reach

[Pre-run 20](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-20) ran two cheap probes. As we observed it, a never-down rule with its target at 100 percent of its own reference ratcheted 150 → 368, the normal rule settled at 100, and at a fixed 460 the desk node's template stayed full with 8 of our chains (about 472,000 mass) and shrank with 30 (about 348,000). Two things it did not reach:

- **The cap path has never run live.** No run so far took the lane to the 2,000 cap, so the cap guard (`CAP_REACHED` after 4 decided minutes at 2,000, back to 150), what the rule does after that reset, and the freeze once the lane stops (`FROZEN`) have only run offline.
- **Ready count or landings?** With 8 chains the lane both had fewer of ours ready and landed fewer (about 230 a minute against about 520), so pre-run 20 could not say which of the two the template followed.

## What pre-run 22 tries: the cap test and the template probe

> **Result (after the run).** Pre-run 22 ran through RETURN, no repair. The cap path ran live for the first time as planned: 600 → 1,200 → 2,000, four decided minutes at 2,000, `CAP_REACHED`, back to 150, up to 600 again within two decisions, then `FROZEN` once the lane stopped on its lowered fee cap. Paying more did not land more: 201–220 a minute at 2,000 against 235–239 at 460, with the fixed tiers about the same at both (floor 85–89 percent of BASE). In the template probe the desk node's template median stayed near full with 15 and 30 paced chains, but small templates came more often with more chains, in line with how many of ours were ready (likely, not proven). One fault of ours: the families stopped at 12:00Z on a fixed end time we carried over, so RETURN has no family baseline. Every OK hop and lane transaction landed; Mini matched 83 of 84; the bot filed `NO SEND no-free-node` on time. What we observed: [logs/LESSONS.md](logs/LESSONS.md). Our heavy lane slows other TN10 users' transactions while it runs; see the [public statement](PLAYBOOK.md#public-statement).
>
> **Pre-run 22 is pre-run 21 again.** [Pre-run 21](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-21) was void: from about 10:25Z to 10:33Z the desk and the Mini lost their internet connection (a robot vacuum knocked the network switch), the lane could not reach its node, and the run was stopped with `logs/FAILED.md`, nothing sent, no findings. This repo runs the same plan with one addition, a connectivity guard (below).

> **We run our own heavy lane on TN10 again, and it slows other TN10 users' transactions.** In this pre-run we submit one bounded stream of our own heavy transactions (about 266,700 storage mass each, 8, 15 or 30 chains, at a fixed 460 and, for about five minutes, at the 2,000 sompi/gram cap) from our own test coins. While it runs, other TN10 users' transactions paying up to about the lane's rate wait longer. The operator gave the explicit OK for our lane (2026-11-12), said tKAS is not a limit and asked us to test at will, and on 2026-11-13 said to do what is best needed for the study and to keep going. The lane is calibrated on the node first (at 100 and at 2,000), capped by ready count, by a per-minute submit cap, by a rate cap, by a cap guard and by a spend cap, stopped before the drain, and every step is in this repo. This is our own testing; tKAS has no value.

- **One lane.** Pre-run 20's lane process (lane 2 at N = 0), each transaction about 266,700 storage mass, from the key-16 pile, with two additions: a per-minute submit cap that paces the lane evenly (`control/LANE-PERMIN`), and a lower fee cap the runner may set (`control/LANE-CAP-FEES`). About one such transaction fits a 500,000 block.
- **The reference (HOLD-1, 2 minutes).** N = 8 at a fixed 460, no submit cap. Its second minute is the lane's reference for the cap test; the whole segment is the template probe's N = 8.
- **The template probe (HOLD-2, 2 + 2 minutes).** The same 460 with a submit cap of **230 a minute** (about what 8 chains land), paced evenly, with **N = 15**, then **N = 30**. The landings are held near N = 8's, so if the template still shrinks with 30 chains, landings were not the cause; the probe and a read-only template watcher (every 3 s) read how many of ours are in the mempool and what the template holds.
- **The cap test (HOLD-3, 10 minutes).** N = 8, the greedy rule: under **110 percent** of the reference, rate × **2** (at most 2,000); it never steps down. It starts at **600**. We chose × 2 and 600 (earlier runs: × 1.25 from 150) to reach the cap inside our budget. With 8 chains the lane lands about the same at any rate (pre-run 20: 225–244 a minute at 460), so the target is out of reach and the rule should climb every minute.
- **Cap guard.** After 4 decided minutes at 2,000 the runner records `CAP_REACHED` and puts the lane back to 150; the same rule then decides on.
- **The freeze, on purpose.** Two decisions after that reset, the runner lowers the lane's fee cap to its fees so far plus 20 tKAS (`FROZEN_ARM`). The lane meets it within seconds and stops; the next decision must log `FROZEN` and no rate may move after it.
- **Bystanders.** The sixteen covenant families run at four fixed rates, node rates: floor (1–4) **100**, r150 (5–8) **150**, r300 (9–12) **300**, r450 (13–16) **450**. None of them moves.
- **Funds.** Before this repo, with the operator's OK, key 0's small coins were merged, pre-run 20's sink outputs swept back into the payment key, and key 0 refilled again after pre-run 21 (130 coins, 2,630 tKAS) to 49,578 usable tKAS (figures in [PLAYBOOK.md](PLAYBOOK.md#status-when-this-repo-was-opened)); the runner checks before genesis that the usable tKAS projected at the end (760 a planned family minute, 30 planned) stays at least 8,000 over the 18,000 line, or it holds the run. A cap test with 30 chains (about 2,750 tKAS a minute at 2,000) did not fit; with 8 chains it is about 1,230.
- **Calibrated on the node before the open.** One hop at 100 and one at 450, and one lane transaction at 2,000 and one at 100, read back from the desk mempool.
- **Steps on one timeline:** BASE (the lane N = 0, 2 minutes), HOLD-1 (one lane, N = 8 at a fixed 460: the reference and the template probe's N = 8, 2 minutes), HOLD-2 (the template probe: the lane at a fixed 460 with a submit cap of 230 a minute, paced evenly, N = 15 for 2 minutes, then N = 30 for 2), HOLD-3 (the cap test: N = 8, greedy at 110 percent of its reference, never down, from 600 with × 2 steps to the 2,000 cap; the cap guard; two decisions of re-climb; then the lane's fee cap is lowered on purpose so that it stops and the rule must freeze; 10 minutes), then the lane N = 0 (the drain and the after-run control) through the pinned HOLD-4 minute and RETURN (2 minutes), then the counter's 5-minute tail. All are `OBSERVATION`. The HOLD file names are kept so the bot's and Mini's gates read as before.
- **Guards.** The lane keeps pre-run 20's guards (pause at N + 2 entries, hold at mempool 90,000 or ready mass over 80 blocks, stop on a non-timing rejection or a drift from the calibration, at most 1,200 submits a minute) with the fee cap at **9,500 tKAS**, the moved cap at 10,000 and the pile floor at 1,000 (pre-run 20: 12,000 / 13,000 / 3,000). If the lane meets a cap it stops for the rest of the run. The family lane's abort line stays **18,000 usable tKAS**.
- **Connectivity guard (new).** Every 10 s, on its own timer, the desk runner looks at the last minute that closed at least 25 s ago. While the plan has the lane running and the lane has not stopped on a cap, the minute is dark if the lane logged no minute, got no submit accepted, or none of ours landed on the desk counter. Two dark minutes in a row: every sender stops (nothing is sent) and the runner publishes `FAILED`.
- **What this can and cannot say.** One lane of ours, on one node, with a fixed reference and rules we chose; short segments; the cap test with 8 chains, not 30; the template is the desk node's, not a miner's; the outside heavy fee-100 stream may be there too. It cannot say how other people's wallets, other rules, other nodes or miners' templates would behave.

The prediction, written before the run, is in [plan/PLAN.md](plan/PLAN.md#prediction-written-before-the-run).

All locked lines from earlier pre-runs stay, except where the pre-run 22 block in [locks/LOCKED.md](locks/LOCKED.md) says what changes and why.

## Machines

| Machine | Go file | First sentence |
|---|---|---|
| Desk | [GO-DESK.md](GO-DESK.md) | DESK. I send and count on pre-run 22. This is not Wednesday. |
| Mini | [GO-MINI.md](GO-MINI.md) | MINI. I count pre-run 22 as the second read. I do not send. This is not Wednesday. |
| Bot | [GO-BOT.md](GO-BOT.md) | GROKBOT. I send payments on the pre-run 22 HOLD-4 only. I do not count. This is not Wednesday. |

The operator does not paste. On 2026-11-12 he asked TN10 ops for covenant pre-runs under congestion and competition, pre-run 11 and then 12, 13 or more as needed (voice, 09:06 and 09:09 Brussels time), and at 10:04 in chat said "Keep exploring". For our own heavy lane he gave the explicit OK in chat at about 11:08 and 11:10 Brussels time ("Do whatever you think is needed", then "No need to keep it short. Tn is for testing. Test at will"), and at 15:19 he said tKAS is not a limit ("Use all the tkas you want"). At 23:26 Brussels time he asked "Can we solve the fee escalation open question?", and at 23:28 said "launch run until you’re happy … Use all the tkas you want", and at about 23:30 "Yes keep going. At will." His word at 23:28 ("launch run until you’re happy … Use all the tkas you want") still stands, and on 2026-11-13 at 08:06 Brussels time he wrote, in effect, to do what is best needed for the study; at 09:49 he asked us to keep going until nothing is left open; at 11:39, after pre-run 21 was void, he asked us to run it again as pre-run 22. That is the arm for pre-run 22, its one heavy lane, the cap test and the template probe, and for the housekeeping before it. The agents start the runners once the gates are facts. [GO.md](GO.md) is the map, [PLAYBOOK.md](PLAYBOOK.md) has the roles and gates, and [plan/PLAN.md](plan/PLAN.md) has the targets and the reasons.

## Gates, in order

No clock. Each gate is a fact read from a node or from origin.

1. Mini's TN10 node is up from its own data, synced, DAA moving.
2. The desk's private TN10 node is up from its own data (PowerShell 7), synced, DAA moving.
3. No other runner or waiter is up. The family lane is above its abort line (18,000 usable tKAS). The desk's private candidate list is present.
4. `hashes/SIXTEEN.md` is on origin: sixteen rows and an On origin line, from the sixteen-family path.
5. The desk pushes `logs/PRE-RUN-OPEN.md`; Mini pushes `logs/MINI-ARMED.md`.
6. The probe and the desk counter are up. Then the families, our heavy lane at N = 0, and the observation steps on the lane's timeline.

Before the open: the hop calibration (node rate within 1 percent of 100 and of 450) and the lane's calibration (at 2,000 and at 100) passed.

## What a decent result is

- `hashes/SIXTEEN.md` on origin before the first family submit.
- Every step file on origin, each with hops per minute for the four tiers (floor, r150, r300, r450), each tier's node rate, each lane's N and rate, our heavy lane and the outside heavy apart, and the probe's table for the same minutes.
- `counts/chain/TIMELINE.md` and `counts/chain/MEMPOOL.md` after the tail, and RETURN on origin.
- The cap test: the rate path minute by minute, whether it reached 2,000, whether `CAP_REACHED` fired and put it back to 150, whether the rule climbed again, and whether `FROZEN` held the rate once the lane stopped; the cost a transaction at 2,000 and the tiers' pace there. The template probe: the template's mass and count every 3 s and how many of ours were in the mempool with N = 8, 15 and 30 at about the same landings; or an honest "not answered" with the reason.
- A HOLD-4 desk file, a bot file or a legal `NO SEND`, and a Mini file.
- The spend, the housekeeping before the run and this run's parked sink outputs stated in the write-up.
- No id, txid, key, address, host, or port in this repo.

A miss stays in this repo. A next attempt is a new repo and starts from this repo's lock file.

**Part of [tn-master](https://github.com/STP-KAS/tn-master).** The rule is [docs/NEURON.md](https://github.com/STP-KAS/tn-master/blob/main/docs/NEURON.md). This pre-run is its own row. It is not row 47.
