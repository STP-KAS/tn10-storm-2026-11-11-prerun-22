> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value. Counts only.

# Chain timeline, pre-run 22

Every minute the desk counter read, from its start to the end of the 5-minute tail after RETURN. Read on the desk's private TN10 node, by accepting chain block header time. Submit-OK is the desk sender log for scored minutes (a dash where the runner did not score the minute). A minute marked LAGGING, partial, or not final is what the node had accepted at that point, not a network figure. Nothing is filled in.

| Minute (UTC) | Step (lane) | Scored | Pay submit-OK | Our payments included | Our heavy landed | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Included, all non-coinbase | Chain blocks | DAA gap max | Sink age max, ms | Counter |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T11:36 | families (pre) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 329 | 329 | 39 | 0 | 317 | partial |
| 2026-11-13T11:37 | BASE (pre) |  | - | 0 | 0 | 192 | 220 | 225 | 220 | 3,201 | 4,035 | 374 | 1 | 428 | kept pace |
| 2026-11-13T11:38 | BASE (N0-control) | yes | 0 | 0 | 0 | 268 | 289 | 304 | 308 | 3,104 | 4,232 | 385 | 2 | 617 | kept pace |
| 2026-11-13T11:39 | BASE (N0-control) | yes | 0 | 0 | 0 | 275 | 309 | 325 | 320 | 3,373 | 4,558 | 381 | 1 | 300 | kept pace |
| 2026-11-13T11:40 | HOLD-1 (L8-r460-ref) | yes | 0 | 0 | 235 | 233 | 256 | 293 | 306 | 3,153 | 4,417 | 387 | 1 | 405 | kept pace |
| 2026-11-13T11:41 | HOLD-1 (L8-r460-ref) | yes | 0 | 0 | 239 | 231 | 259 | 287 | 289 | 3,177 | 4,419 | 389 | 2 | 354 | kept pace |
| 2026-11-13T11:42 | HOLD-2 (L15-r460-cap230) | yes | 0 | 0 | 230 | 236 | 247 | 295 | 326 | 3,160 | 4,432 | 356 | 1 | 344 | kept pace |
| 2026-11-13T11:43 | HOLD-2 (L15-r460-cap230) | yes | 0 | 0 | 230 | 242 | 272 | 298 | 316 | 3,099 | 4,360 | 379 | 2 | 489 | kept pace |
| 2026-11-13T11:44 | HOLD-2 (L30-r460-cap230) | yes | 0 | 0 | 230 | 228 | 242 | 271 | 299 | 3,170 | 4,371 | 382 | 2 | 541 | kept pace |
| 2026-11-13T11:45 | HOLD-2 (L30-r460-cap230) | yes | 0 | 0 | 230 | 197 | 223 | 259 | 293 | 3,163 | 4,331 | 377 | 1 | 279 | kept pace |
| 2026-11-13T11:46 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 227 | 246 | 255 | 282 | 323 | 3,119 | 4,376 | 386 | 1 | 661 | kept pace |
| 2026-11-13T11:47 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 217 | 243 | 260 | 304 | 316 | 3,123 | 4,395 | 360 | 1 | 536 | kept pace |
| 2026-11-13T11:48 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 211 | 235 | 265 | 297 | 303 | 3,239 | 4,481 | 354 | 0 | 384 | kept pace |
| 2026-11-13T11:49 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 201 | 238 | 251 | 286 | 319 | 3,111 | 4,324 | 352 | 1 | 486 | kept pace |
| 2026-11-13T11:50 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 204 | 237 | 258 | 279 | 294 | 3,170 | 4,375 | 350 | 0 | 224 | kept pace |
| 2026-11-13T11:51 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 201 | 238 | 258 | 305 | 330 | 3,258 | 4,537 | 383 | 1 | 854 | kept pace |
| 2026-11-13T11:52 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 220 | 241 | 271 | 298 | 318 | 3,211 | 4,493 | 354 | 1 | 290 | kept pace |
| 2026-11-13T11:53 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 235 | 266 | 279 | 308 | 320 | 3,161 | 4,486 | 373 | 1 | 438 | kept pace |
| 2026-11-13T11:54 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 113 | 261 | 273 | 289 | 300 | 3,127 | 4,316 | 380 | 0 | 499 | kept pace |
| 2026-11-13T11:55 | HOLD-3 (L8-greedy-cap) | yes | 0 | 0 | 0 | 283 | 292 | 307 | 310 | 3,144 | 4,303 | 391 | 1 | 335 | kept pace |
| 2026-11-13T11:56 | HOLD-4 (N0-drain) |  | - | 0 | 0 | 288 | 303 | 313 | 311 | 3,168 | 4,334 | 402 | 0 | 536 | kept pace |
| 2026-11-13T11:57 | HOLD-4 (N0-drain) |  | - | 0 | 0 | 268 | 296 | 327 | 318 | 3,138 | 4,316 | 383 | 1 | 376 | kept pace |
| 2026-11-13T11:58 | HOLD-4 (N0-drain) |  | - | 0 | 0 | 279 | 304 | 315 | 317 | 3,188 | 4,382 | 392 | 0 | 442 | kept pace |
| 2026-11-13T11:59 | HOLD-4 (N0-drain) |  | - | 0 | 0 | 253 | 283 | 291 | 295 | 3,116 | 4,194 | 352 | 0 | 384 | kept pace |
| 2026-11-13T12:00 | HOLD-4 (N0-drain) | yes | 0 | 0 | 0 | 4 | 3 | 4 | 1 | 3,189 | 3,201 | 373 | 1 | 414 | kept pace |
| 2026-11-13T12:01 | RETURN (N0-drain) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 3,126 | 3,126 | 362 | 1 | 677 | kept pace |
| 2026-11-13T12:02 | RETURN (N0-drain) | yes | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 3,195 | 3,195 | 394 | 1 | 470 | kept pace |
| 2026-11-13T12:03 | RETURN (N0-drain) | yes | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 3,301 | 3,301 | 380 | 1 | 456 | kept pace |
| 2026-11-13T12:04 | tail (N0-drain) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 3,280 | 3,280 | 376 | 0 | 469 | kept pace |
| 2026-11-13T12:05 | tail (N0-drain) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 3,124 | 3,124 | 391 | 2 | 581 | kept pace |
| 2026-11-13T12:06 | tail (N0-drain) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 3,121 | 3,121 | 343 | 1 | 464 | kept pace |
| 2026-11-13T12:07 | tail (N0-drain) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 3,192 | 3,192 | 400 | 2 | 643 | kept pace |
| 2026-11-13T12:08 | tail (N0-drain) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 3,185 | 3,185 | 390 | 1 | 408 | kept pace |
| 2026-11-13T12:09 | tail (N0-drain) |  | - | 0 | 0 | 0 | 0 | 0 | 0 | 2,744 | 2,744 | 334 | 0 | 595 | not final |

Whole run, as read: our payments submit-OK 0, of which included by the end of the tail 0 (- percent). Family hops included: floor 5,682, r150 6,168, r300 6,762, r450 7,052. Our heavy-lane transactions included: 3,223.
