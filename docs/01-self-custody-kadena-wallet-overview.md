# Kadena Wallet: A Self-Custody Desktop Client for KDA Holders

When the [Kadena Foundation announced its dissolution in October 2025](https://kadenawallet.io/what-happened-to-kadena), and the Chainweaver wallet repository was archived three months later, KDA holders were left without a maintained first-party desktop client. [Kadena Wallet](https://kadenawallet.io/kadena-wallet) was built to fill that gap. It is a non-custodial desktop application, MIT-licensed, and published by KADENA WALLET LLC, an independent Florida company that exists for one reason: to keep the lights on for self-custody KDA storage.

This article walks through what the wallet does, who it is for, and how to get started. If you want to skip the explanation and download the installers, head to the [official download page](https://kadenawallet.io/download).

## Self-custody by default

Self-custody means you hold the keys, and nobody else can move your coins. [Kadena Wallet](https://kadenawallet.io/kadena-wallet) generates your private keys on your machine, encrypts them at rest with a passphrase you choose, and never transmits them. The publisher cannot freeze, reverse, or recover your funds, which is the entire point. If you have used a hardware-backed wallet before, the security model is identical. If you have only ever used an exchange, this is the moment to internalise that the responsibility moves to you - which is also covered in the [wallet recovery guide](https://kadenawallet.io/kadena-wallet-recovery).

The wallet talks to public Kadena Chainweb nodes over HTTPS. You can leave the defaults alone, or you can point it at your own self-hosted node. Cross-chain transfers are handled through Kadena's native SPV continuation pattern, but you do not have to think about that - the wallet automates the two-step initiation and redemption so KDA simply lands on the chain you asked for. For background on why Kadena has 20 chains in the first place, see the [Chainweb glossary entry](https://kadenawallet.io/glossary/what-is-chainweb).

## Who builds it, and why it matters

[KADENA WALLET LLC](https://kadenawallet.io/about) is a Florida limited liability company formed on December 2, 2025. It is not the Kadena Foundation. It is not affiliated with Kadenamint, eckoDAO, or any prior Kadena entity. It is an independent publisher whose only product is this wallet, and whose entire brand sits or falls on whether the wallet stays maintained and trustworthy.

Why is independence helpful? Because the [Kadena ecosystem in 2026](https://kadenawallet.io/is-kadena-dead) is in a different place than it was at mainnet launch. The Foundation is wound down, [Chainweaver is archived](https://kadenawallet.io/vs/chainweaver), [Binance announced KDA delisting](https://kadenawallet.io/binance-delisting), and the core development effort has shifted to community contributors. A wallet provider that depends on Foundation grants would be a fragile dependency. KADENA WALLET LLC is funded independently and does not rely on the Foundation continuing to exist.

## What the wallet does

A short feature list, with links to the relevant pages:

- Native installers for Windows 10/11 (x64 and ARM64), macOS 12+ (Intel and Apple Silicon), and major Linux distros - see [Download](https://kadenawallet.io/download).
- Full 20-chain Chainweb support with automated cross-chain SPV transfers.
- Ledger Nano S Plus and Nano X integration via WebHID - the [hardware wallet guide](https://kadenawallet.io/kadena-hardware-wallet) walks through pairing.
- Seed import from [Chainweaver](https://kadenawallet.io/chainweaver-alternative), [eckoWALLET](https://kadenawallet.io/vs/eckowallet), and [Koala Wallet](https://kadenawallet.io/vs/koala) without manual conversion.
- A Marmalade / KIP-0011 NFT viewer for collections, royalty info, and per-token metadata.
- A DeFi position dashboard for [eckoDEX and KDSwap](https://kadenawallet.io/kadena-swap).
- No third-party analytics, no behavioural tracking - read the [privacy policy](https://kadenawallet.io/legal/privacy).

## Comparison with other Kadena wallets

If you are coming from another wallet and want a side-by-side, the [best Kadena wallet comparison](https://kadenawallet.io/best-kadena-wallet) is the right starting point. For one-to-one comparisons, see [vs Chainweaver](https://kadenawallet.io/vs/chainweaver), [vs eckoWALLET](https://kadenawallet.io/vs/eckowallet), [vs Koala](https://kadenawallet.io/vs/koala), [vs Zelcore](https://kadenawallet.io/vs/zelcore), and [vs Enkrypt](https://kadenawallet.io/vs/enkrypt). The general shape: Kadena Wallet is desktop-native and Kadena-specialised; the alternatives trade off depth (Kadena coverage) for breadth (other chains, browser surface, mobile).

## Getting started

1. Visit the [download page](https://kadenawallet.io/download) and pick the installer for your operating system.
2. Run the installer, launch the app, and choose either to create a new wallet or to import an existing seed.
3. If you are migrating from Chainweaver, follow the [migration guide](https://kadenawallet.io/chainweaver-alternative). It walks through the custom-derivation import.
4. Verify your balance against [a Kadena explorer](https://kadenawallet.io/glossary/what-is-kadena) before transacting.
5. Pair a Ledger if you want hardware-level isolation - see the [Ledger setup guide](https://kadenawallet.io/kadena-hardware-wallet).
6. If you are buying KDA fresh, the [buy guide](https://kadenawallet.io/buy-kadena) lists every active venue.

For step-by-step purchase walkthroughs see [how to buy Kadena](https://kadenawallet.io/how-to-buy-kadena), and for definitions of common terms see the [glossary](https://kadenawallet.io/glossary).

## Pricing, fees, and what the wallet does not do

The wallet itself is free. There is no subscription, no transaction fee added by KADENA WALLET LLC, no recovery service, no premium tier. The only cost is standard Kadena network gas - and gas on Kadena is famously low. The wallet does not provide investment advice, [price targets](https://kadenawallet.io/kadena-price-prediction), or recovery for a lost seed phrase. Anyone offering to recover a seed for a fee is running a scam, which the [recovery guide](https://kadenawallet.io/kadena-wallet-recovery) flags explicitly.

## Related articles

- [Migrating from Chainweaver to Kadena Wallet](02-migrating-from-chainweaver.md)
- [Best Kadena wallet 2026](03-best-kadena-wallet-2026.md)
- [Setting up a Ledger hardware wallet](07-ledger-hardware-wallet-kadena-setup.md)
- [Recovering a wallet from a seed phrase](12-recovering-kadena-wallet-from-seed.md)
