# Lessons: base58-py

Lineage `c12109ca42d955b0bbc7e2a3ffbf5ebacd3141687da6b1ed6d814327ef9af1d8` on [https://github.com/keis/base58](https://github.com/keis/base58) at `2fae7065e3446e69e5d748c767011f05eee8400e`. 12 published attempts.

Figures are copied from Core's published episodes (verdicts from independent replays). Nothing here is estimated.

## Target perf:encode_ir

- Attempts: 4 (2 accepted, 2 rejected)
- Best accepted effect: 24.10% (ratio 0.7590), episode `9f93409b3f94`
- Accepted effects: 24.10%, 1.60%
- Why candidates failed: stale_conflict (2)
- Files changed by accepted candidates: `base58/__init__.py`
- Files changed by rejected candidates: `base58/__init__.py`
- Median model spend per attempt: 0.2941 USD (over 4 attempts with a recorded cost)

## Target perf:decode_ir

- Attempts: 2 (2 accepted)
- Best accepted effect: 8.29% (ratio 0.9171), episode `a68ec05c18be`
- Accepted effects: 8.29%, 3.51%
- Files changed by accepted candidates: `base58/__init__.py`
- Median model spend per attempt: 0.2816 USD (over 2 attempts with a recorded cost)

## Target (none chosen)

- Attempts: 3 (3 no candidate)

## Target perf:check_ir

- Attempts: 3 (1 accepted, 2 rejected)
- Best accepted effect: 13.05% (ratio 0.8695), episode `e9b5f12bc39f`
- Why candidates failed: stale (1), stale_conflict (1)
- Files changed by accepted candidates: `base58/__init__.py`
- Files changed by rejected candidates: `base58/__init__.py`
- Median model spend per attempt: 0.2003 USD (over 3 attempts with a recorded cost)

## Licence

Code excerpts from https://github.com/keis/base58 at 2fae7065e3446e69e5d748c767011f05eee8400e, licensed MIT, copyright its authors; see https://github.com/keis/base58/blob/master/COPYING.
