# Recovering a Kadena Wallet from a Seed Phrase

Self-custody puts the responsibility on you. The seed phrase you wrote down when you first set up your wallet is the only thing standing between continued access to your KDA and permanent loss. This article walks through how recovery actually works in [Kadena Wallet](https://kadenawallet.io/kadena-wallet), what the wallet can and cannot do for you, and the specific scams to avoid. The canonical reference is the [wallet recovery page](https://kadenawallet.io/kadena-wallet-recovery), which is updated as new scam patterns surface.

## What "recovery" means and does not mean

Recovery means: you have a seed phrase, and you want to restore the wallet on a new (or reset) machine. That is a deterministic operation. The seed deterministically derives your private keys, which deterministically derive your public addresses, which the chain reports balances for. There is no magic.

Recovery does **not** mean: you lost your seed and want to "recover" your wallet. The chain does not store your seed. No service can recover a lost seed. Anyone offering a paid recovery service for a lost seed is, without exception, running a scam. The [recovery page](https://kadenawallet.io/kadena-wallet-recovery) flags this explicitly. Read it twice.

## Three seed formats Kadena Wallet imports

[Kadena Wallet](https://kadenawallet.io/kadena-wallet) supports three seed formats:

1. **Chainweaver custom derivation** - 12-word seed, custom derivation path. Used by [Chainweaver](https://kadenawallet.io/vs/chainweaver) (now archived). The [migration guide](https://kadenawallet.io/chainweaver-alternative) walks through the import.
2. **BIP39 12-word** - standard BIP39, used by [eckoWALLET](https://kadenawallet.io/vs/eckowallet) and many other wallets.
3. **24-word** - the longer BIP39 format used by [Koala Wallet](https://kadenawallet.io/vs/koala) and Ledger devices.

If your seed is in any of these three formats, [Kadena Wallet](https://kadenawallet.io/kadena-wallet) imports it directly. If you are not sure which format you have, the import flow lets you try all three and tells you which one resolves to a non-zero balance.

## The recovery flow, step by step

1. Install [Kadena Wallet](https://kadenawallet.io/download) on your new machine. Verify the installer signature.
2. Launch the app. Choose "Restore from seed phrase".
3. Pick the seed format (Chainweaver / BIP39 12-word / 24-word). The wallet shows you a pictogram so you can recognise the format from your written seed.
4. Type the words in order. The wallet validates each word against the BIP39 wordlist (or Chainweaver's wordlist) and warns on typos.
5. Set a new passphrase. This passphrase encrypts the seed at rest on the new machine and is independent of your old setup.
6. The wallet scans all 20 Chainweb chains and surfaces balances on every chain that has them. The [Chainweb explainer](https://kadenawallet.io/glossary/what-is-chainweb) covers why this matters - your KDA might be spread across chains you do not actively use.
7. Verify total balance against an external source if you have one (a block explorer, your prior wallet, or your own records).
8. Send a small test transaction (1 KDA) to confirm signing works. Only then resume normal use.

## Recovery with a Ledger

If you used a [Ledger hardware wallet](https://kadenawallet.io/kadena-hardware-wallet) with the old setup, recovery has two components:

- **Ledger device**: if the device is intact, just plug it into the new machine and re-pair. The device retains the seed; nothing to restore there.
- **Ledger device lost or damaged**: buy a new Ledger, restore the same 24-word recovery phrase onto the new device, then pair with [Kadena Wallet](https://kadenawallet.io/kadena-wallet) the same way you would set up a fresh device.

Either way, the seed is the source of truth, not the device. Ledger does not store recovery information centrally. There is no "Ledger account recovery service".

## Common recovery problems and fixes

- **"My seed has 13 or 25 words"**: count again. BIP39 phrases are 12, 18, or 24 words. Chainweaver is 12. Anything else is wrong - probably a transcription error.
- **"The wallet says some words are not in the wordlist"**: typo. Check spelling. Some words look very similar (e.g., "abandon" vs "abdomen"). The BIP39 wordlist is small enough that any near-match should be obvious.
- **"My total balance is lower than I expected"**: check all 20 chains. The [Chainweb 20-chain navigator](https://kadenawallet.io/kadena-wallet) surfaces them automatically. If a balance is genuinely missing, [contact support](https://kadenawallet.io/contact) - sometimes named-account permissions confuse the import.
- **"I have a Chainweaver seed but the import says no accounts found"**: pick "Chainweaver custom derivation" explicitly rather than BIP39. The derivation paths differ. The [Chainweaver migration guide](https://kadenawallet.io/chainweaver-alternative) is the authoritative reference.
- **"I am being asked to send a small fee for recovery"**: stop. That is a scam. Recovery has no fee. Standard Kadena network gas applies once you send a transaction, but reception is free.

## Scam patterns to recognise

The [recovery page](https://kadenawallet.io/kadena-wallet-recovery) lists these explicitly. The common ones:

- **Fake "wallet recovery" websites** that look like Kadena Wallet but ask for your seed. The real wallet never asks you to type your seed into a website. Recovery happens inside the desktop app.
- **DM scammers on Discord/Telegram** offering recovery for a fee. Real support never DMs first; the only support channel is the [contact page](https://kadenawallet.io/contact).
- **"Recovery service" Google ads** at the top of search results. These are nearly always scams. Bookmark the official site and use that.
- **Fake browser extensions** named similarly to [eckoWALLET](https://kadenawallet.io/vs/eckowallet). Install only from official sources.
- **Phishing emails** claiming that a Kadena exchange has flagged your account and you must "verify" by entering your seed. No exchange ever needs your seed.

## After recovery: hardening checklist

1. Set a strong, unique passphrase on [Kadena Wallet](https://kadenawallet.io/kadena-wallet).
2. Pair a [Ledger device](https://kadenawallet.io/kadena-hardware-wallet) for long-term holdings.
3. Move bulk balance behind the Ledger; keep small daily-use balance in a non-Ledger account.
4. Re-write your seed on fresh paper. Old paper degrades.
5. Store the new paper in two physically separate locations.
6. Do not photograph the seed. Do not type the seed into any browser, email, or note-taking app.
7. Read the [privacy policy](https://kadenawallet.io/legal/privacy) and [terms](https://kadenawallet.io/legal/terms) once so you understand what the wallet does and does not do.
8. Skim the [news feeds](https://kadenawallet.io/news), [coin news](https://kadenawallet.io/news/kadena-coin-news), and [crypto news](https://kadenawallet.io/news/kadena-crypto-news) periodically. Reference unfamiliar terms in the [glossary](https://kadenawallet.io/glossary), and check [how to buy Kadena](https://kadenawallet.io/how-to-buy-kadena) if you also need an acquisition refresher.

## Withdrawing from exchanges into a recovered wallet

If your recovery is part of evacuating funds from an exchange (sensible after the [Binance delisting](https://kadenawallet.io/binance-delisting), see the [withdrawal procedure](https://kadenawallet.io/binance-kadena-withdrawal) and the [Crypto.com status](https://kadenawallet.io/kadena-on-crypto-com)), the workflow:

1. Confirm wallet recovery first with a small test transaction.
2. On the exchange, withdraw a small test amount (1 KDA).
3. Confirm it lands on the expected chain.
4. Withdraw the rest.
5. Optionally consolidate cross-chain into a single chain using the wallet's automated SPV transfer flow.

For broader context on what is happening with the network, see the [is-Kadena-dead status page](https://kadenawallet.io/is-kadena-dead), the [recovery outlook](https://kadenawallet.io/will-kadena-recover), and the [what-happened-to-Kadena timeline](https://kadenawallet.io/what-happened-to-kadena).

## Related articles

- [Self-custody Kadena Wallet overview](01-self-custody-kadena-wallet-overview.md)
- [Migrating from Chainweaver](02-migrating-from-chainweaver.md)
- [Setting up a Ledger hardware wallet](07-ledger-hardware-wallet-kadena-setup.md)
- [Is Kadena dead? Status outlook](11-is-kadena-dead-status-outlook.md)
