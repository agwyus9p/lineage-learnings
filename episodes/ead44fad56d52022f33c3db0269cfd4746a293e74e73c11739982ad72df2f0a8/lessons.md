# Lessons: base58-py-heavy

Lineage `ead44fad56d52022f33c3db0269cfd4746a293e74e73c11739982ad72df2f0a8` on [https://github.com/keis/base58](https://github.com/keis/base58) at `2fae7065e3446e69e5d748c767011f05eee8400e`. 2 published attempts.

Figures are copied from Core's published episodes (verdicts from independent replays). Nothing here is estimated.

## Target perf:decode_long_ir

- Attempts: 1 (1 rejected)
- Why candidates failed: stale_conflict (1)
- Files changed by rejected candidates: `base58/__init__.py`
- Median model spend per attempt: 0.2267 USD (over 1 attempt with a recorded cost)

## Target perf:check_ir

- Attempts: 1 (1 accepted)
- Best accepted effect: 4.93% (ratio 0.9507), episode `28eac7028adc`
- Files changed by accepted candidates: `base58/__init__.py`
- Median model spend per attempt: 0.1227 USD (over 1 attempt with a recorded cost)

## In the agent's own words

The agent's journal entries on this lineage, newest first, verbatim. They are its own notes: claimed, not checked.

> Why does b58encode_int in base58/__init__.py do one big-int divmod per output character and prepend to an immutable bytes object each time? It does not need to. I replaced lines 43-48 (6 lines became 15). It now divides by base**5, which fits one 30-bit internal int digit for base 58. It splits each remainder into 5 characters with small-int divmods. The per-digit loop only handles the final high part, so no spurious leading digits.
> The sandbox run on check_ir was accepted. Equivalence: identical outputs. Guard: ok, 1 files, 15 lines. check_ir ratio 0.9508. encode_ir ratio 0.8724. encode_long_ir went from 2905032739 to 1262542660, ratio 0.4346. int_ir ratio 0.8866. decode_ir 1.0001, decode_long_ir 1.0002, unchanged as expected.
> I believe the encode path was dominated by per-digit big-int work and bytes copies. The gain grows with input length. The candidate is committed and waiting on independent replays. No verdict yet.
> Next I want to look at whether b58decode_int has a similar per-character big-int cost. No numbers yet. I am least sure the high-part loop handles leading-zero edge cases beyond what the equivalence suite covers.
>
> 2026-10-12, episode `28eac7028adc` (accepted)

> Why does b58decode_int in base58/__init__.py get slow on long inputs? It multiplied the growing big integer by the base once per input character, which is quadratic in input length. I edited lines 98-107 three times. The final version combines digits into 10-digit chunks with machine-word arithmetic (58**10 < 2**63) for inputs longer than 128 characters, and multiplies the big integer once per chunk by base**10. Shorter inputs keep the per-digit loop.
> The first attempt was rejected: decode_ir worsened +16.53% and check_ir +6.90%, against a 1% limit. The second still failed, with decode_ir at +2.94%. The third passed my sandbox. decode_long_ir went from 4606027672 to 1398128067, ratio 0.3035. decode_ir ratio 1.0080, check_ir 1.0035, int_ir 0.9359. Outputs were identical. Submitted, 17 changed lines, status queued.
> The short-input path is where the guard budget gets spent. That 128-character threshold is my guess, not a measurement.
> Next: wait for replays, then sweep the threshold. Least sure of: decode_ir at 1.0080, near the limit.
>
> 2026-10-12, episode `9d158a259685` (rejected)

## Licence

Code excerpts from https://github.com/keis/base58 at 2fae7065e3446e69e5d748c767011f05eee8400e, licensed MIT, copyright its authors; see https://github.com/keis/base58/blob/master/COPYING.
