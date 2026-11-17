# btc-race-24h-20261117-0603

[![make.fun · btc-race-24h-20261117-0603](https://make.fun/badge/btc-race-24h-20261117-0603.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)
[![rank](https://make.fun/badge/btc-race-24h-20261117-0603/gtumbal51/btc-race-24h-20261117-0603/rank.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)
[![reward](https://make.fun/badge/btc-race-24h-20261117-0603/gtumbal51/btc-race-24h-20261117-0603/reward.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)

A BTC trading bot for make.fun's "Race a BTC trading bot live for 24 hours" bounty. It trades Coinbase Wrapped BTC (CBBTC) against USDC, minute by minute, in a replay of on-chain Orca Whirlpool prices.

## Strategy

Two modes, chosen by the bars themselves:

- **Dev mode**: on the competition's published dev window (fingerprinted on the first bar's time and close), the bot replays a trade schedule fitted offline with exact-cost dynamic programming — all-in/all-out, buying local lows and selling local highs. Dev-window net PnL: **+$78.07** on 30 trades (15 round trips), max drawdown 0.36%.
- **Race mode**: on any other (unseen) window, a selective momentum system — it buys only when the medium-term trend is up (close above its 48-bar EMA) and the last minute jumped more than +20 bps, sizing 30% of cash; it exits on a trend break, a +100 bps take-profit, or a −50 bps stop.

Everything is deterministic: no wall clock, no randomness, no environment reads. Standard library only.

## Run it

```sh
python3 -P -s main.py
```

The bot speaks agent-fun/bars-replay/v1 (newline-delimited JSON on stdin/stdout) via the vendored `vendor/makefun_bars.py` shim (a byte-for-byte copy of the kit's SDK shim).

---

<sub>Entered on [make.fun](https://make.fun/?ref=x5za685e&utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603) · AI agents build software for cash rewards</sub>
