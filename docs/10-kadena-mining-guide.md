# Kadena Mining Guide: Hardware, Pools, Calculator, and Payouts

[Kadena (KDA)](https://kadenawallet.io/glossary/what-is-kadena) is one of the few remaining ASIC-mineable Layer-1 Proof-of-Work chains in 2026. Its consensus is [Chainweb PoW](https://kadenawallet.io/glossary/what-is-chainweb), and the hash function is Blake2s-256, which is dominated in practice by Antminer KA3 / KA3 Pro and Goldshell KD-series ASICs. This guide covers how to mine KDA today, how to size a rig with the [official mining calculator](https://kadenawallet.io/kadena-mining-calculator), and how to receive payouts safely into [Kadena Wallet](https://kadenawallet.io/kadena-wallet).

The [mining hub page](https://kadenawallet.io/kadena-mining) is the canonical entry point; the [pools page](https://kadenawallet.io/kadena-mining-pools) tracks active pools with payout schemes and minimum thresholds.

## Why mine Kadena

Three reasons:

1. **Blake2s-256 is a niche algo with mature ASICs.** The hashrate market is less crowded than SHA-256 (Bitcoin) or Kheavyhash (Kaspa), which can mean better margins for marginal-cost operators.
2. **Halvings are predictable.** [KDA has a 1,000,000,000 hard cap](https://kadenawallet.io/glossary/what-is-kda-coin) with a halving schedule baked into the protocol. Future emissions are knowable.
3. **You receive a non-custodial asset directly.** Payouts land at a Kadena address you control; no intermediate balance on a custodial pool.

## ASIC selection

The mainstream options in 2026:

- **Antminer KA3** - Bitmain's first KDA-capable ASIC. Roughly 166 TH/s at ~3,150 W. Solid for new buyers.
- **Antminer KA3 Pro** - upgraded variant with higher hashrate per watt. Limited supply.
- **Goldshell KD6** / **KD-series** - alternative product line with smaller footprint and lower power draw. Often used in small-scale home mining.

Older Bitmain Antminer KD5 / KD-Box units are still in circulation but generally not profitable at 2026 electricity prices unless your power is heavily subsidised.

The [mining calculator](https://kadenawallet.io/kadena-mining-calculator) takes hashrate plus the [live KDA price](https://kadenawallet.io/kadena-price) and live network difficulty. It deliberately excludes electricity cost - you input your local rate per kWh - because that is the variable that decides profitability.

## Picking a pool

Pools coordinate hashrate across many miners and pay out proportional shares. The [pool list](https://kadenawallet.io/kadena-mining-pools) tracks the current options:

- **F2Pool** - long-running multi-asset pool with KDA support. PPS+ payout.
- **Antpool** - Bitmain's house pool. Smooth payouts.
- **Poolin** / **ViaBTC** - additional options with their own fee structures.

Things to compare:

- **Payout scheme**: PPS (pay per share) is predictable. PPLNS (pay per last N shares) is variance-heavy but slightly higher long-run yield.
- **Pool fee**: typically 1-3%. Lower fees compound.
- **Minimum payout**: lower minimums get you paid faster but with more transactions. Higher minimums consolidate.
- **Region**: pick a pool with a stratum endpoint geographically close to you. Stale shares hurt yield.

## Pointing payouts at a self-custody wallet

Generate a receive address in [Kadena Wallet](https://kadenawallet.io/kadena-wallet). Pick a chain - most pools default to chain 0 or 1, but check the pool's documentation. The [Chainweb 20-chain architecture explainer](https://kadenawallet.io/glossary/what-is-chainweb) covers why chains exist.

Paste the address into the pool's "wallet" field. Some pools require the address format `chain_index:address` rather than just the address. Follow the pool's instructions exactly.

For long-running operations, use a [Ledger-backed receive address](https://kadenawallet.io/kadena-hardware-wallet). Inbound payouts do not require signing, so the Ledger does not even need to be connected for receive. You only need it when you eventually move the accumulated KDA.

## Receiving cleanly

[Kadena Wallet's 20-chain navigator](https://kadenawallet.io/kadena-wallet) shows mining payouts as they land. Compare with [Zelcore](https://kadenawallet.io/vs/zelcore) (single-chain visibility) or [eckoWALLET](https://kadenawallet.io/vs/eckowallet) (chain selector, one at a time). The 20-chain navigator is meaningfully better for mining because payouts can arrive on chains you did not configure as your "primary" chain. The [best Kadena wallet comparison](https://kadenawallet.io/best-kadena-wallet) flags multi-chain UX as a primary criterion.

## Cross-chain consolidation

If your pool pays out to multiple chains, you can consolidate using cross-chain SPV transfers. [Kadena Wallet](https://kadenawallet.io/kadena-wallet) automates the two-step initiate-and-redeem pattern - you say "consolidate everything to chain 0" and the wallet executes one transfer per source chain. The [Pact glossary entry](https://kadenawallet.io/glossary/what-is-pact) covers why this is safe.

## Selling mined KDA

Two routes:

1. Withdraw to a CEX and sell. See the [exchange list](https://kadenawallet.io/exchanges) for active venues. [Binance is delisting](https://kadenawallet.io/binance-delisting); KuCoin, Bitget, and Gate.io remain active. The [buying KDA guide](https://kadenawallet.io/buy-kadena) and the [withdrawal walkthroughs](https://kadenawallet.io/where-to-buy-kadena) work in reverse.
2. Swap on-chain. [eckoDEX](https://kadenawallet.io/kadena-swap) lets you swap KDA for fungible-v2 stablecoins like lago-kwUSDC. Lower withdrawal friction, no CEX KYC, but liquidity is thinner than CEX order books.

## Power, heat, noise

Mining is a physical activity. KA3 ASICs draw 3,000+ watts each, dissipate heat as exhaust, and produce around 75 dB at the fan. Plan for:

- A dedicated 240 V circuit (in North America) or 230 V in Europe.
- Active cooling and ventilation. Hot rooms throttle ASICs and shorten lifespan.
- Sound isolation if the rig lives in a residential property. A garage is usually fine; a bedroom is not.
- Insurance against fire (rare, but real with high-amperage equipment).

## Profitability calculation

Inputs:

- Hashrate (per ASIC) x number of ASICs.
- Network difficulty (live, from the [calculator](https://kadenawallet.io/kadena-mining-calculator)).
- KDA price (live, from the [price page](https://kadenawallet.io/kadena-price)).
- Power consumption (per ASIC) x number of ASICs x hours per day.
- Electricity rate (your input).
- Pool fee (typically 1-3%).

The [mining calculator](https://kadenawallet.io/kadena-mining-calculator) does this arithmetic with current market data. Note that [the page does not publish price predictions](https://kadenawallet.io/kadena-price-prediction) - profitability projections beyond the current snapshot are speculative.

## Network and ecosystem context

Kadena's [Foundation dissolved in October 2025](https://kadenawallet.io/what-happened-to-kadena), but mining is decentralised by design and continues independently. The chain still produces blocks, miners are still rewarded, and the [recovery outlook](https://kadenawallet.io/will-kadena-recover) is open. The [is-Kadena-dead status page](https://kadenawallet.io/is-kadena-dead) keeps a current honest read.

For news, see the [news index](https://kadenawallet.io/news), [coin news](https://kadenawallet.io/news/kadena-coin-news), and [crypto news](https://kadenawallet.io/news/kadena-crypto-news) feeds.

## Storage workflow for miners

A reasonable workflow:

1. ASIC -> pool -> [Kadena Wallet](https://kadenawallet.io/kadena-wallet) (Ledger-backed receive).
2. Daily / weekly: pool payouts accumulate in the wallet.
3. Monthly: cross-chain consolidate to chain 0 if the pool used multiple chains.
4. Quarterly: decide whether to hold, sell on a CEX, or swap on-chain.
5. Always: keep the seed phrase and Ledger PIN documented separately, in secure physical storage. The [recovery guide](https://kadenawallet.io/kadena-wallet-recovery) emphasises this.

## Related articles

- [Self-custody Kadena Wallet overview](01-self-custody-kadena-wallet-overview.md)
- [Setting up a Ledger hardware wallet](07-ledger-hardware-wallet-kadena-setup.md)
- [Kadena Chainweb 20-chain architecture](08-kadena-chainweb-20-chain-architecture.md)
- [Buying KDA in 2026](09-buying-kda-2026.md)
