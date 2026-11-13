> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> **This is the playbook for pre-run 22.** It is not Wednesday. It is not Tuesday. It is not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, or 21. It does not start a machine and it does not arm one.

# Playbook

Who does what, and the gates before each machine may start. The plan is [plan/PLAN.md](plan/PLAN.md), the locks are [locks/LOCKED.md](locks/LOCKED.md), and the go files are the three GO pages. This page does not override them.

## Oversight

TN10 ops oversees this rehearsal end to end: Mini, the desk (Build), and the bot. TN10 only. Never mainnet. Do not edit the Tuesday repo, the Wednesday repo, or pre-run 1's to 21's go files. Do not write `REVIEW_CLOSED`.

For pre-run 22 the operator does not paste. On 2026-11-12 he asked TN10 ops for covenant pre-runs under congestion and competition, pre-run 11 and then 12, 13 or more as needed (voice, 09:06 and 09:09 Brussels time), and at 10:04 in chat said "Keep exploring". That is the arm. The agents start their runners once the gates are facts.

## Start gates

1. **Mini node synced.** Existing TN10 kaspad, existing data, no wipe. `isSynced` true, DAA moving.
2. **Desk node synced.** Existing private TN10 kaspad, existing data, loopback only, started with `pwsh`. No wipe. Synced, DAA moving.
3. **No other runner.** No earlier runner, waiter, or counter on any machine. Lane above the abort line. The desk's private candidate list is present and not empty (`HELD candidates-missing` otherwise).
4. **Hashes.** `hashes/SIXTEEN.md` with sixteen rows and an On origin line, from [tools/sixteen](tools/sixteen/README.md).
5. **Open.** The desk pushes `logs/PRE-RUN-OPEN.md`. Mini then pushes `logs/MINI-ARMED.md`.
6. **Counter, families, senders.** The desk runner starts the counter on its private node and waits for its start line (`HELD counter-down` otherwise). Then the genesis from the bundle that wrote `hashes/SIXTEEN.md`, the families, and the payment steps.

## Who does what

| Who | Role | What not to do |
|---|---|---|
| **Desk (Build)** | Sends the sixteen families (four fixed tiers, one path, one build, kit24) and runs our own heavy lane in one lane process (one lane; the operator's OK, calibrated first). No payments. Its private TN10 node counts what the chain accepted (lock line (iv)) and its probe reads the mempool (xii). Publishes `hashes/SIXTEEN.md`, `logs/PRE-RUN-OPEN.md`, `counts/desk/` per step, `counts/chain/TIMELINE.md` and `MEMPOOL.md` after the tail, and `logs/METHOD.md`. | Do not stop or wipe the desk node. No Windows PowerShell 5.1, no `KaspaPublicNode`, no miner, no devnet. No 8- or 32-family publisher. No second runner. Never restart the runner mid-run. No payment sender. No heavy lane other than the runner's own lane process (which carries both lanes). |
| **Mini** | Second chain read on its own node. Does not send, mine, or hold a key. Publishes `logs/MINI-ARMED.md`, then `counts/mini/` when the matching desk file is on origin. | Do not wipe. Do not repeat the desk's head as Mini's. |
| **Bot (TN10 ops)** | Sends payments in the HOLD-4 minute only, on a synced public kaspad that is not one the desk kept, or publishes a legal `NO SEND`. | Do not send in any other step. One waiter. No local node. |

## Status when this repo was opened

Not a gate. Read on 2026-11-13 between 10:38Z and 10:47Z. This is our own TN10 testing; status lines are what we read on our own machines.

- **Pre-run 22 is pre-run 21 again.** [Pre-run 21](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-21) was void: from about 10:25Z to 10:33Z the desk and the Mini lost their internet connection (a robot vacuum knocked the network switch), the lane could not reach its node, and the run was stopped with `logs/FAILED.md` at 10:35Z, nothing sent, no findings. Every runner stopped on that file; nothing of pre-run 21 is running.
- Mini: existing TN10 kaspad 2.1.0 up, no wipe. Read-only at 10:44:25Z and 10:44:45Z: synced, 8 peers; the first reading was about 70 s behind the tip, the second 0.2 s (DAA 1,042 in 20 s while it caught up). Read again before arming.
- Desk: existing private TN10 kaspad 2.1.0 up with `pwsh`, no wipe, not stopped for this pre-run. Read-only at 10:44:18Z and 10:44:38Z: synced, 9 peers, newest block 0.4 s and 0.1 s old, DAA 233 in 20 s. `serve.mjs` and its keeper are not touched.
- Box: no local TN10 node. No bot waiter running.
- **Before this repo (the operator's go, 2026-11-13 11:39 Brussels), all between our own keys, none rejected, recorded privately on the desk:**
  - Keys 1–15 got a fresh genesis coin from key 0 (15 transactions), 10:45Z.
  - **Key 0 refilled from the payment pile** (`refill21.mjs`), 10:47Z: 7 transactions, 130 pile coins (2,630 tKAS), 0.30 tKAS in fees. Sized on usable coins so the budget passes with margin while the pile keeps room for the lane.
  - After: key 0 2,760 coins over 3 tKAS, **49,578 usable**; payment pile **549 coins, 10,811 tKAS** (the lane's fee cap 9,500 plus its pile floor 1,000 fit).
- **Budget.** About 760 usable tKAS a family minute, 8,000 over the 18,000 line at the end, **30 planned family minutes**: read-only `budget21.mjs` 10:47Z, 49,578 − 760 × 30 = **26,778 projected at the end**, over 26,000: ok. The runner repeats this check before genesis.
- **Hop calibration on the node** (kit24 unchanged), 10:46:10Z, calibration covenant `…-p22-cal` (not one of the sixteen, not in `SIXTEEN.md`): family 1 at 100: kit24 storage 41,619 = node, node rate 100.31; family 13 at 450: 41,854 = node, node rate 450.10.
- **Our heavy lane's calibration:** at 2,000, 10:46:09Z: SDK storage 266,835 = node, compute 2,036, node rate 2,000 (fee 5.34 tKAS); at 100, 10:46:10Z: 266,673 on both sides, node rate 100.
- **New in this repo: a connectivity guard.** Every 10 s the desk runner looks at the last minute that closed at least 25 s ago. While the plan has the lane running and it has not stopped on a cap, a minute is dark if the lane logged no minute, got no submit accepted, or none of ours landed on the desk counter. Two dark minutes in a row: the runner stops everything (no sends) and publishes `FAILED`.
- The re-read just before `PRE-RUN-OPEN` is recorded in the offline rehearsal section below.
- Known risks, not fixed mid-run: as in pre-run 21. Our lane slows other TN10 users' transactions at fees up to about its own rate while it runs, and this run takes it to 2,000 on purpose for about five minutes (fee cap 9,500 tKAS; the cap guard puts it back to 150 after 4 decided minutes at the cap). Short segments, one run. The × 2 steps from 600 are our choice. The outside heavy fee-100 stream may be there. The probe and the template watcher read the desk node, not a miner. Only two unique public kaspads answered so far, so the bot is expected to file `NO SEND no-free-node`.

## Offline rehearsal, recorded before `PRE-RUN-OPEN`

Two rehearsals ran on the desk against the fake node (no network for the sends), with 2-minute steps for BASE, the reference, the template probe and RETURN (`STORM_LANE_MIN=2`, `STORM_RET_MIN=2`) and the cap test at its full 10 minutes (`STORM_CAP_MIN=10`).

- `p22-g` (the new connectivity guard), 2026-11-13 10:54:10Z to about 11:01:36Z. The fake node was killed on purpose 5 s into the reference minute, to stand in for a lost connection. The guard logged two dark minutes (11:00:31Z and 11:01:31Z), stopped everything with nothing sent and published `FAILED` to the rehearsal's local origin (`RUNNER_EXIT 5`, as designed). From the cut to `FAILED` took about 3.5 minutes. A first try of this rehearsal stopped at genesis because we had copied the real sixteen-submit tool into the rehearsal by mistake; it only reached the fake node, and we replaced it with the rehearsal's own fake one.
- `p22-a` (the full path, on the final files: the same files, by hash after line endings, as the live run and this repo's `tools/desk` for the desk runner, lane, counter, probe and template watcher), 2026-11-13 11:03:00Z to 11:32:27Z. Preflight passed; `BUDGET_CHECK` logged (key 0 49,578 usable, 30 planned family minutes, projected end 26,778); genesis 16 of 16; `FEE_SPLIT` floor 100, r150 150, r300 300, r450 450; `LANE_PLAN` as in the plan. The template probe paced 230, 230 (N 15) and 230, 238 (N 30) a minute. The cap path did what the plan says: 600 to 1,200 to 2,000, four decided minutes at 2,000, `CAP_REACHED` after 6 minutes, back to 150, two decisions (150 to 300 to 600), `FROZEN_ARM`, the lane stopped on its lowered fee cap, `FROZEN reason=lane-stopped:cap`. The connectivity guard switched itself off once the lane had stopped on the cap (no false `FAILED`). 2,965 lane submits OK, 0 rejected, 0 lost; the template watcher wrote 554 rows; every step file, TIMELINE, MEMPOOL and METHOD published to the local origin; no `ERROR` line; `RUNNER_EXIT 0`.
- The fake node does not model block space or fee priority, so the landing numbers above say nothing about the network. They only show that the controller, the cap guard, the freeze and the guard run as written.

**Re-read just before `PRE-RUN-OPEN`** (read-only, 2026-11-13 11:33Z to 11:35Z):

- Both nodes, two readings 20 s apart. Desk: synced, 8 peers, tip age 0.1 s and 0.8 s, 222 DAA in 20 s. Mini: synced, 8 peers, tip age 0.2 s and 0.4 s, 226 DAA in 20 s. (At 10:44Z the Mini's tip had been 70 s old for one reading, then caught up; this time both were at the tip.)
- `budget21.mjs` 11:34Z: synced, key 0 49,578 usable (2,760 coins over 3 tKAS, none small), projected end 26,778 over 26,000: ok. Pile 549 coins, 10,811 tKAS.
- The bot's free check, once, 11:34:20Z: kept 1 and 5 = 2 distinct kaspads; every other answering node is one of those two; no free node.

## Status after the live run

Read on 2026-11-13 between 12:04Z and 12:20Z. Not a gate.

- **The run went through RETURN, with one fault of ours.** `PRE-RUN-OPEN` on origin 11:35:26Z, `MINI-ARMED` 11:35:51Z; the desk runner (started 11:36:27Z; `BUDGET_CHECK` key 0 49,578 usable, projected end 26,778) ran BASE, HOLD-1 (the reference), HOLD-2 (the template probe), HOLD-3 (the cap test), the drain, HOLD-4 and RETURN; no repair, no restart; the connectivity guard did not fire. `RUN_STOP return-closed` 12:04:24Z; TIMELINE, MEMPOOL and METHOD on origin 12:10:00–06Z; `RUN end` 12:10:06Z. No runner process was left on the desk. The private TN10 kaspad (2.1.0) was not stopped. No devnet, `KaspaPublicNode` or miner was started; `serve.mjs` and its keeper were not touched.
- **The fault:** the families stopped at 12:00:00Z (a fixed family end time in the base config, carried from pre-run 21's stage). HOLD-4's minute had 12 family hops and RETURN none, so there is no lane-off RETURN baseline in this run. The drain minutes 11:56–11:59 (lane 0, families running) read 100 / 99 / 99 / 99 percent of BASE.
- **The cap test** (reference 239 landed a minute, 8 chains at 460): 600 → 1,200 → 2,000, four decided minutes at 2,000 (84–88 percent), `CAP_REACHED` 11:52:22Z after 6 minutes (lane fees 7,217), → 150, 150 → 300 → 600, `FROZEN_ARM` 11:54:23Z (fee cap 7,522), `LANE_CAP` 11:54:28Z, `FROZEN reason=lane-stopped:cap` 11:55:22Z. Landed 201–220 a minute at 2,000 against 235–239 at 460.
- **The template probe** at 460: template median 473,813 (8 chains), 473,548 (15, paced 230 a minute), 463,207 (30, paced); templates under 400,000 mass 7, 20 and 38 percent of samples. Tiers 85 / 86 / 92 / 95, 88 / 87 / 94 / 102 and 78 / 78 / 84 / 94 percent of BASE.
- Our heavy lane: `LANE_END` 12:04:24Z, 3,223 accepted, 0 rejected, 0 lost, 7,525.31 tKAS fees, 120.86 tKAS parked on our sink key (not swept), 469 pile coins taken, 0 pending.
- Inclusion (counter totals): every OK hop (floor 5,682, r150 6,168, r300 6,762, r450 7,052) and every lane transaction (3,223) landed.
- The outside heavy fee-100 stream was essentially absent (0–2 entries a minute).
- Mini: every step published and read in full; 83 of 84 cohort cells match the desk (1 off by 3 hops). Its TN10 kaspad was not wiped or restarted.
- Bot: `NO SEND no-free-node` for the pinned minute 12:00Z (on origin 12:01:03 Brussels, first try); nothing sent.
- Keys after the run (read-only status): key 0 2,626 coins over 3 tKAS, 21,210 usable (abort line 18,000), 134 small coins; keys 1–15 have no genesis coin; payment pile (key 16) 105 coins, 1,659 tKAS. The next run needs funds first.
- Spend: lane 7,525.31, families 2,758.87, housekeeping a few tKAS: about 10,290 tKAS in fees, plus 120.86 parked.
- Results: [logs/LESSONS.md](logs/LESSONS.md), [logs/duel.log](logs/duel.log), and the pre-run 22 block in [locks/LOCKED.md](locks/LOCKED.md).

### Public statement

We run our own heavy lane on TN10 in this pre-run, with the operator's OK: 8, 15 and 30 chains at a fixed 460 for 6 minutes, then 8 chains for 10 minutes at rates our rule sets between 150 and the 2,000 sompi/gram cap, about five of them at 2,000. While it runs, other TN10 users' transactions paying up to about the lane's rate wait longer on the nodes that see them. In this run the lane ran 15 minutes: 2 with 8 chains at 460 (the reference), 4 with 15 and 30 chains at 460 under a 230-a-minute submit cap, and 9 on the greedy rule with 8 chains (600 to the 2,000 cap, 4 minutes at 2,000, back to 150, up to 600, then stopped on purpose). On our desk node other traffic landed 3,099–3,258 a minute while the lane ran, against 3,104 and 3,373 with the lane at 0 (BASE): inside BASE's own spread, so we could not see a difference in this run. The node's fee estimate rose to 1,140 at 2,000 instead of about 100. Our own hops at 100, a stand-in for a low-fee user, ran at 85–89 percent of their BASE pace with 8 chains at any rate from 460 to 2,000 and at 73 percent in the worst minute with 30 chains. No outside heavy stream was present. This is our own testing; tKAS has no value.

## When something breaks

Append a worked fix to [locks/LOCKED.md](locks/LOCKED.md) in the form that page shows, and a repair line to `logs/FIXES.md`. If the run dies before RETURN, write `logs/FAILED.md`, stop every runner, waiter, and counter, and do not resume. The next attempt is a new repo that starts from this repo's lock file.
