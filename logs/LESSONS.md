> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> Our own testing. What we observed in this run, on our own nodes. Not a claim about how TN10 or Kaspa behave in general. No key, seed, txid, covenant id, address, host or port.

# Lessons, pre-run 22

Written after the run, 2026-11-13, from the files on origin and the desk's own logs (read-only). Times are UTC unless marked Brussels. We are just testing; our methods may be wrong, and corrections are welcome.

## Short version

- **Pre-run 22 ran through RETURN**, with one fault of our own (below). Every step file is on origin for the desk and for Mini, then TIMELINE, MEMPOOL and METHOD. The connectivity guard did not fire. All 3,223 lane transactions landed (0 rejected, 0 lost) and every OK family hop landed (floor 5,682, r150 6,168, r300 6,762, r450 7,052).
- **The cap path ran live for the first time, as the plan and the offline check said.** 600 → 1,200 → 2,000, four decided minutes at 2,000, `CAP_REACHED` 6 minutes in, back to 150, 150 → 300 → 600, `FROZEN_ARM`, the lane stopped on its lowered fee cap, `FROZEN reason=lane-stopped:cap`. No rate moved after `FROZEN`.
- **A higher rate bought nothing.** With 8 chains the lane landed 235 and 239 a minute at 460 (the reference 239), 201–220 at 2,000 (84–92 percent of the reference), and 235 at 150 after the reset. At 2,000 it paid about 1,075 tKAS a minute, about 5.3 tKAS a landed transaction against about 1.23 at 460. The greedy rule climbed every minute because its target (110 percent) was out of reach, and it climbed again after the reset just as fast.
- **The tiers at 2,000 with 8 chains looked like 460 with 8 chains.** Percent of BASE (floor / r150 / r300 / r450): 8 chains at 460 85 / 86 / 92 / 95; at 2,000 88 / 87 / 93 / 100. As we observed it, the rate by itself did not make the bystanders worse here.
- **The template probe, paced at 230 a minute: partly as we guessed, partly not.** The desk node's template median stayed about full (8 chains 473,813; 15 chains 473,548; 30 chains 463,207), but templates under 400,000 mass were 7 percent of samples with 8 chains, 20 percent with 15 and 38 percent with 30. In the same samples, the more of ours were ready, the smaller the template (12 or more of ours ready: median 370,232). Even paced, 30 chains kept more of ours ready at times (ready mass up to about 7 blocks against about 3 with 8), and the floor tier fell to 73 percent in that minute. So we still could not fully separate the chain count from the ready count; the ready count is the better match of the two (likely, not proven).
- **Our fault: the families stopped at 12:00:00Z**, the start of the pinned HOLD-4 minute, because the base config carried a fixed family end time from pre-run 21's stage (that run started 73 minutes earlier). HOLD-4 had almost no family hops and RETURN none, so this run has no lane-off RETURN baseline. The four drain minutes before it (11:56–11:59, lane at 0, families running) read 100 / 99 / 99 / 99 percent of BASE. The rehearsal could not catch it because it ran before 12:00Z.
- On our desk node, other traffic (not ours) stayed inside BASE's own spread in every lane minute. Our own low-fee families, our stand-in for other users, lost up to 27 percent (below).

## What happened

- Before the open, with the operator's OK (11:39 Brussels): keys 1–15 funded, key 0 refilled from the pile (130 coins, 2,630 tKAS) to 49,578 usable, hop and lane calibrations matched the node; figures in [PLAYBOOK.md](../PLAYBOOK.md#status-when-this-repo-was-opened). Two offline rehearsals: `p22-g` (the connectivity guard: a cut connection gave `FAILED`, nothing sent) and `p22-a` (the full path, on the final files) exited as designed.
- Re-read just before the open (read-only, 11:33–11:35Z): both nodes synced, tip age under 1 s in two readings 20 s apart, 8 peers each; the budget check passed (projected end 26,778); the bot's free check, once: no free node.
- Live run: `PRE-RUN-OPEN` on origin 11:35:26Z, `MINI-ARMED` 11:35:51Z, desk runner from 11:36:27Z. `BUDGET_CHECK` 49,578 usable, 30 planned family minutes, projected end 26,778. BASE 11:38–11:39 (lane 0), HOLD-1 11:40–11:41 (8 chains at 460, reference **239**), HOLD-2 11:42–11:45 (15 then 30 chains at 460 under the 230-a-minute submit cap), HOLD-3 11:46–11:55 (the cap test, from 11:45:59Z), drain from 11:55:59Z, HOLD-4 pinned minute 12:00, RETURN 12:02–12:03, `RUN_STOP return-closed` 12:04:24Z, `RUN end` 12:10:06Z.
- The outside heavy fee-100 stream was essentially absent (0–2 entries a minute).

## The cap test

Rates in effect at the start of each minute (a decision lands about 22 s into the next minute). All decisions are in [duel.log](duel.log).

| Minute | Rate in effect | Landed | % of reference (239) | Decision | Lane fees so far, tKAS |
|---|---:|---:|---:|---|---:|
| 11:46 | 600 | 227 | 95 | 600 → 1,200 | 2,220 |
| 11:47 | 600 | 217 | 91 | 1,200 → 2,000 | 2,919 |
| 11:48 | 1,200 | 211 | 88 | hold 2,000 (cap minute 1) | 3,988 |
| 11:49 | 2,000 | 201 | 84 | hold 2,000 (2) | 5,041 |
| 11:50 | 2,000 | 204 | 85 | hold 2,000 (3) | 6,143 |
| 11:51 | 2,000 | 201 | 84 | `CAP_REACHED` (4) → 150 | 7,217 |
| 11:52 | 2,000 | 220 | 92 | 150 → 300 | 7,314 |
| 11:53 | 150 | 235 | 98 | 300 → 600, `FROZEN_ARM` (fee cap 7,522) | 7,501 |
| 11:54 | 300 | 113 | — | `FROZEN reason=lane-stopped:cap` | 7,525 |
| 11:55 | 600 | 0 | — | lane stopped; no rate moved | 7,525 |

- **Cost of the cap path:** 5,505 tKAS from the start of the cap test to `CAP_REACHED` (6 minutes), 5,813 to the freeze. Our offline guess was about 6,400 (the freeze came earlier because `FROZEN_ARM` cuts the lane off on purpose).
- **The guard did its job; it does not fix the rule.** After the reset the rule was back at 600 within two decisions; without the freeze it would have reached the cap again about two minutes later. A never-down rule with an unreachable target just keeps paying.
- **Landings at 2,000 were a little lower, not higher, than at 460** (201–220 against 235–239). We do not know why; it may be noise. With 8 chains each chain waits for its last transaction to leave the mempool, so the lane cannot land more by paying more.
- The connectivity guard switched itself off once the lane stopped on its cap (as designed and rehearsed), so the stopped lane did not raise a false `FAILED`.

## The template probe

`tplwatch20.mjs` read the desk node's own block template every 3 s (read-only; never submitted). Medians per segment, 10–90 percent ranges in brackets. "Ours ready" is a rough proxy: the ready mass above BASE's median, in heavy transactions.

| Segment | Samples | Template mass | Template txs | Our heavy in template (mean) | Other mass beside it | Ours ready (proxy) | Share of templates under 400,000 |
|---|---:|---|---|---:|---|---|---:|
| BASE (lane 0) | 40 | 497,277 (166,735–499,051) | 12 (4–12) | 0.00 | 497,277 | 0 | 0.15 |
| 8 chains at 460 (reference) | 40 | 473,813 (432,849–476,234) | 6 (6–12) | 0.85 | 207,082 | 3 (0–6) | 0.07 |
| 15 chains at 460, 230 a minute | 40 | 473,548 (308,496–497,626) | 6 (4–12) | 0.57 | 207,056 | 5 (0–12) | 0.20 |
| 30 chains at 460, 230 a minute | 40 | 463,207 (307,913–495,782) | 6 (3–12) | 0.53 | 206,666 | 5 (0–22) | 0.38 |
| 8 chains at 2,000 | 80 | 472,840 (431,038–493,222) | 6 (6–12) | 0.74 | 205,766 | 3 (0–5) | 0.07 |

At 460 (reference plus probe), grouped by the ours-ready proxy: 0–1.5 ready: template median 493,563; 1.5–3: 474,815; 3–6: 473,920; 6–12: 473,113; 12 or more: **370,232**.

- What we guessed before the run (about 60 percent): the template stays about as full with 15 and 30 chains as with 8. The median nearly did; small templates did not. Pacing held the landings at 230 a minute, but it did not hold the ready count down all the time with 30 chains.
- How we read it, carefully: the template's shrink lines up with how many of our heavy transactions are ready at once. The chain count matters through that, as far as we can tell. One node, one lane, short segments; a miner's template may differ.

## Bystanders (our own families) and other users

Percent of BASE per tier (floor 100 / r150 / r300 / r450 sompi/gram), by segment, from the desk counter:

| Segment | floor / r150 / r300 / r450 | Worst floor minute |
|---|---|---:|
| 8 chains at 460 (reference) | 85 / 86 / 92 / 95 | 85 |
| 15 chains at 460, 230 a minute | 88 / 87 / 94 / 102 | 87 |
| 30 chains at 460, 230 a minute | 78 / 78 / 84 / 94 | 73 |
| Cap test at 600–1,200 | 89 / 87 / 94 / 100 | 87 |
| Cap test at 2,000 | 88 / 87 / 93 / 100 | 87 |
| Re-climb at 150–300 | 97 / 92 / 95 / 99 | 96 |
| Drain, lane 0 (11:56–11:59) | 100 / 99 / 99 / 99 | — |

- **Other traffic** on our desk node (everything not ours) had a median of 3,238 a minute in BASE (3,104 and 3,373) and 3,099–3,258 in every lane minute: inside BASE's own spread, so we cannot see an effect on it in this run. That does not mean there was none: other users who pay about our lane's rate or less wait longer while it runs. The node's fee estimate rose to 1,140 at 2,000 (BASE about 100–106); the desk mempool stayed small (at most 29 entries).
- Our own hops at 100, a stand-in for a low-fee user, kept 85–89 percent of their BASE pace with 8 chains at any rate from 460 to 2,000, and 73 percent in the worst minute with 30 chains.

## Mini

Every step published and read in full (READ 2 of 2, 2 of 2, 4 of 4, 10 of 10, 1 of 1, 2 of 2). 83 of 84 cohort cells match the desk; one is off by 3 hops (11:48, floor). Its TN10 kaspad was not wiped or restarted.

## Bot

The waiter saw HOLD-3 7 s after it was on origin, pinned 12:00Z, checked its libraries, ran the free check at 11:59:30Z: kept 1 and 5 are 2 distinct kaspads, every other answering node is one of them, no free node. `NO SEND no-free-node` on origin at 12:01:03 Brussels, first try. Nothing sent.

## Spend (tKAS, our own test coins)

- Lane: 7,525.31 in fees; 120.86 parked on our sink key (ours, not swept); 469 pile coins taken.
- Families: 2,758.87 in fees (floor 234.35, r150 381.34, r300 835.85, r450 1,307.33).
- Before the open: refill 0.30, genesis funding and calibrations a few tKAS.
- About **10,290 in fees** in all, plus 120.86 parked.
- After the run (read-only): key 0 21,210 usable (2,626 coins over 3 tKAS, 134 small), keys 1–15 have no genesis coin, payment pile 105 coins / 1,659 tKAS. **The next run does not fit our funds** as they are: key 0 is about 3,200 over the 18,000 abort line and the pile is nearly empty.

## Lessons

1. **Derive the family end time from the start, not from a fixed clock time.** The base config's `end_utc` was a fixed 12:00:00Z carried from pre-run 21's stage. The next repo should set it from the runner's start plus the planned minutes, and the rehearsal should check it against the live start time, because a rehearsal that runs earlier in the day cannot catch it.
2. **The cap guard and the freeze work live**; the never-down rule is the problem, not the guard. A rule that never steps down keeps paying when its target cannot be met.
3. **Paying more did not land more with 8 chains.** 201–239 a minute from 150 to 2,000.
4. **The template follows our ready count better than our landings or our rate** (likely, not proven). Pacing the submits did not fully fix the ready count with 30 chains.
5. **Check both nodes right before arming** (as here, two readings 20 s apart). It cost a minute and it is what the outage of pre-run 21 taught.
6. Our lanes slow other TN10 users' transactions while they run. We keep them short and bounded.
