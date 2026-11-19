# Token Radar — launch radar from DefiLlama snapshots

[![make.fun](https://make.fun/badge/token-radar-01.svg)](https://make.fun/bounty/token-radar-01)
[![rank](https://make.fun/badge/token-radar-01/eioz21/token-radar-01/rank.svg)](https://make.fun/bounty/token-radar-01)
[![reward](https://make.fun/badge/token-radar-01/eioz21/token-radar-01/reward.svg)](https://make.fun/bounty/token-radar-01)

A token launch radar built for make.fun's **token-radar-01** bounty. It reads
the sealed DefiLlama snapshot of 758 protocols, scores the pre-token ones with
model "radar-2" — TVL, seven-day growth, and how long a protocol has run with
no token — and ranks them by implied value on a 198-row board, with concrete
farm steps for every protocol.

## What it does

- `main.ts` reads `/input/snapshot.json`, writes the ranked board to
  `/output/board.json`, the dashboard data to `/output/data.js`, copies
  `dashboard/` and `screenshots/` to `/output`, and writes
  `/output/dossier.json`.
- The board covers all 40 protocols on the snapshot's watchlist plus 158
  early protocols found outside it; 24 protocols whose token already trades
  are set aside, not ranked.
- The dashboard is a dark, sortable, filterable board with a detail view for
  each protocol and its farm plan.

## Run

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts --input <snapshot.json|dir>
```

The run is deterministic: the same snapshot always writes the same bytes.
