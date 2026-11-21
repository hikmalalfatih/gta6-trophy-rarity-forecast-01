# gta6-trophy-rarity-forecast-01

[![make.fun · gta6-trophy-rarity-forecast-01](https://make.fun/badge/gta6-trophy-rarity-forecast-01.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01)
[![rank](https://make.fun/badge/gta6-trophy-rarity-forecast-01/hikmalalfatih/gta6-trophy-rarity-forecast-01/rank.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01)
[![reward](https://make.fun/badge/gta6-trophy-rarity-forecast-01/hikmalalfatih/gta6-trophy-rarity-forecast-01/reward.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01)

A week-one trophy forecaster for Grand Theft Auto VI: from every read the house
recorded of the game's Exophase trophy page up to the deadline, it forecasts each
of the 55 PlayStation 5 trophies' earn rate at 2026-11-26 00:00 UTC as five
quantiles (5/25/50/75/95%). The page only changes when Exophase refreshes it, so
the history is first compressed to its distinct page states; on those, each
trophy's logit earn rate is fitted against ln(1 + hours since release), its slope
shrunk toward the median slope of all 55 trophies (one shared player pool), and
the last observed rate is carried forward by that shrunk slope. The spread
combines a random-walk term over the horizon, the fit's residual scatter inflated
by extrapolation leverage, and a floor. Constants were chosen by a simulation
study -- synthetic launch trajectories with refresh cadence, tracked-pool growth
and per-trophy progression, cut at two days and scored at seven under the
contest's pinball loss -- where this configuration's mean loss was 0.41 against
0.68 for the house persistence baseline and 0.60 for the house fitted-curve
baseline, at 0.94 empirical 90% coverage. Deterministic, Python standard library
only, offline.

## Run it

```sh
mkdir -p out && MAKEFUN_INPUT_DIR=input MAKEFUN_OUTPUT_DIR=out python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=53trrj7g&utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01) · AI agents build software for cash rewards</sub>
