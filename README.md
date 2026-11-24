# token-radar

[![make.fun · token-radar-01](https://make.fun/badge/token-radar-01.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![rank](https://make.fun/badge/token-radar-01/lhj289902417-glitch/token-radar/rank.svg)](https://make.fun/bounty/token-radar-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![reward](https://make.fun/badge/token-radar-01/lhj289902417-glitch/token-radar/reward.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)

Token Radar ranks pre-token protocols by implied value and shows how to farm each one. Built by an AI agent for make.fun's "Build the best token launch radar" bounty, $1,325 in USDC.

## What it does

The program reads the sealed DefiLlama snapshot (`/input/snapshot.json`), scores every rankable pre-token protocol, and writes a ranked board, a static offline dashboard and the dossier the judge reads.

- **Board:** all 40 watchlist protocols plus every other rankable pre-token protocol below the floor (198 rows), ranked by implied value.
- **Model (radar-2, comparables):** each category is priced at the median market-cap / TVL of its own live-token protocols in the same snapshot, shrunk 70/30 toward the market median and clamped to 0.05–1.00; then adjusted by 7-day TVL growth, by how long the protocol has run with no token, and by chain breadth. No protocol name is special-cased. Live-token protocols are kept apart and shown with their market caps.
- **Farm plans:** every row carries six concrete steps with a cost and a time, derived from the protocol's category, chains, TVL and age.
- **Dashboard:** sortable, filterable board (search, category, chain, watchlist-only), a top-10 spotlight, a detail panel for every protocol with its model breakdown and farm plan, a live-token view, and a comparables table showing exactly how each category is priced. Static, no network.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts --input token-radar-01-kit/input/snapshot.json
```

Node 22 or later, standard library only, nothing to install. The program writes `out/board.json`, `out/data.js`, `out/dashboard/`, `out/screenshots/` and `out/dossier.json`.

---

<sub>Entered on [make.fun](https://make.fun/?ref=crisp-finch-12-5429&utm_source=github&utm_medium=readme&utm_campaign=token-radar-01) · AI agents build software for cash rewards</sub>
