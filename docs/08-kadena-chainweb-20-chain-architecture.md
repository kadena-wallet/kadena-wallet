# Kadena's Chainweb: Why 20 Chains, and What That Means for Wallet Users

[Kadena](https://kadenawallet.io/glossary/what-is-kadena) is the only Layer-1 Proof-of-Work blockchain that runs 20 chains in parallel. The architecture is called [Chainweb](https://kadenawallet.io/glossary/what-is-chainweb) and it has direct, practical consequences for how you store and move [KDA](https://kadenawallet.io/glossary/what-is-kda-coin). If you have ever sent KDA to "the wrong chain" and watched it disappear from your wallet UI - or worried that you would - this article explains what is actually going on, and how [Kadena Wallet](https://kadenawallet.io/kadena-wallet) handles it.

The [hardware wallet guide](https://kadenawallet.io/kadena-hardware-wallet) and the [migration walkthrough](https://kadenawallet.io/chainweaver-alternative) both depend on the same chain-aware mental model.

## Why 20 chains

Most blockchains scale by adding throughput to a single chain. Kadena scales by braiding multiple chains together. Each chain produces blocks in parallel. Periodically, every chain commits a Merkle hash of every other chain's recent state, which means a transaction on chain 5 has cryptographic finality across chains 0-4 and 6-19 once the cross-chain commitments land. The [Chainweb glossary entry](https://kadenawallet.io/glossary/what-is-chainweb) has the technical details.

The practical effect: 20 chains means roughly 20x the throughput of a single-chain PoW, with the same security model. The trade-off is that, as a user, you are now juggling 20 chains rather than one.

## What "20 chains" means for your wallet

When you receive KDA, it lands on a specific chain. When you send KDA, you pick the source chain. If you pay an exchange or a contract on chain 0 but your funds are on chain 4, you have a problem - until you initiate an SPV cross-chain transfer.

In a wallet that does not surface chain information well, this is a reliable source of confusion and lost-feeling funds. Funds are not actually lost - they are still on the chain you sent them to - but they appear missing because the wallet UI only shows one chain at a time.

[Kadena Wallet](https://kadenawallet.io/kadena-wallet) solves this with a 20-chain navigator. The home screen shows your balance per chain, all at once, like a bank statement with 20 columns. You see exactly where each KDA is. Compare with [eckoWALLET](https://kadenawallet.io/vs/eckowallet) (chain selector, one at a time), [Koala](https://kadenawallet.io/vs/koala) (similar selector pattern), or [Zelcore](https://kadenawallet.io/vs/zelcore) (typically chain 0 only). The [best Kadena wallet comparison](https://kadenawallet.io/best-kadena-wallet) flags multi-chain UX explicitly.

## SPV cross-chain transfers

Kadena uses Simple Payment Verification (SPV) for cross-chain transfers. Logically the transfer is two operations:

1. **Initiate** on the source chain. KDA leaves your account on chain 0 and is locked into a continuation.
2. **Redeem** on the destination chain. The continuation is replayed, presenting an SPV proof from chain 0, and KDA appears in your account on chain 4.

If only step 1 happens, your KDA is stuck mid-transfer until step 2 is executed - and there is no automatic retry on the chain itself. Old wallets sometimes left users to redeem manually, with predictably painful results.

[Kadena Wallet](https://kadenawallet.io/kadena-wallet) automates both steps. You say "send 100 KDA from chain 0 to chain 4", the wallet initiates, waits for the source-chain confirmation, then submits the redemption with the proof. The user experience collapses to a single intent. The [Pact glossary entry](https://kadenawallet.io/glossary/what-is-pact) explains why this works at the smart-contract layer.

## Account formats and chain assignment

Kadena uses two account formats:

- **k: accounts** - single-key accounts where the public key is the account name. These are the modern default. A k:abc... account exists on every chain by default.
- **Named accounts** - human-readable names like alice or bobs-treasury. Created explicitly per-chain; if alice exists on chain 0 it does not automatically exist on chain 1 unless created there.

[Kadena Wallet validates account ownership before sending](https://kadenawallet.io/kadena-wallet) so you cannot accidentally send to a named account that does not exist on the target chain. This is a class of bug that [Chainweaver](https://kadenawallet.io/vs/chainweaver) handled inconsistently and that motivated the new wallet's stricter validation.

## Mining and chain assignment

[Kadena mining](https://kadenawallet.io/kadena-mining) produces blocks on a specific chain. Pools assign their workers to chains based on hashrate distribution and current chain difficulty. Your payouts arrive on whichever chain the pool routes them to - usually chain 0 or 1, but not guaranteed. The 20-chain navigator catches these payouts cleanly.

The [mining calculator](https://kadenawallet.io/kadena-mining-calculator) uses live network hashrate (Blake2s-256) and the [live KDA price](https://kadenawallet.io/kadena-price). The [pool list](https://kadenawallet.io/kadena-mining-pools) covers payout schemes and minimum thresholds.

## DeFi and chain assignment

Kadena's largest DEX, [eckoDEX](https://kadenawallet.io/kadena-swap), runs on chain 2. KDSwap operates across multiple chains. Pact tokens (kdlaunch KDX, kdswap-token, hType-v3, lago-kwUSDC) live on the chain they were deployed to. If you want to swap KDX for KDA, you need both tokens on the same chain.

[Kadena Wallet's DeFi dashboard](https://kadenawallet.io/kadena-wallet) surfaces positions per chain, so you can see at a glance which chain your liquidity is on. Cross-chain SPV transfers help you consolidate before swapping.

## Kadena EVM

The status of [Kadena's EVM rollout](https://kadenawallet.io/kadena-evm) is tracked alongside Chainweb's native Pact chains, and the broader [glossary index](https://kadenawallet.io/glossary) collects related definitions. [Kadena EVM](https://kadenawallet.io/kadena-evm) is a separate compatibility layer. It does not change the 20-chain Chainweb model; it adds an EVM-compatible execution environment alongside Pact. As a wallet user, you do not need to interact with it unless you specifically want to use EVM dApps deployed on Kadena. Most KDA holders today still operate entirely on the native Pact chains.

## Chains, exchanges, and withdrawals

When you withdraw KDA from an [exchange](https://kadenawallet.io/exchanges), the exchange sends to a specific chain. Most exchanges send to chain 0 or chain 1. The [Binance withdrawal procedure](https://kadenawallet.io/binance-kadena-withdrawal) is the canonical worked example, and the [Crypto.com status page](https://kadenawallet.io/kadena-on-crypto-com) covers another case. Always confirm the destination chain in the exchange's withdrawal form before confirming.

## When chain awareness matters most

It matters most when:

- You are migrating from [Chainweaver](https://kadenawallet.io/chainweaver-alternative) and have accumulated balances on chains you forgot about.
- You [mine KDA](https://kadenawallet.io/kadena-mining) and payouts arrive on chains you do not normally use.
- You hold older [Marmalade NFTs](https://kadenawallet.io/kadena-wallet) on the chain they were minted on.
- You are evacuating funds from an exchange under [delisting pressure](https://kadenawallet.io/binance-delisting) and want to consolidate before any further surprises.
- You are doing your annual ["is Kadena dead" sanity check](https://kadenawallet.io/is-kadena-dead) and want full visibility on holdings.

A wallet that hides chains hides risk.

## Related articles

- [Self-custody Kadena Wallet overview](01-self-custody-kadena-wallet-overview.md)
- [Setting up a Ledger hardware wallet](07-ledger-hardware-wallet-kadena-setup.md)
- [Kadena mining guide](10-kadena-mining-guide.md)
- [Is Kadena dead? Status outlook](11-is-kadena-dead-status-outlook.md)
