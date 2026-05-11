# Migrating from Chainweaver to Kadena Wallet

The [Chainweaver wallet repository was archived in January 2026](https://kadenawallet.io/vs/chainweaver), shortly after the [Kadena Foundation dissolved](https://kadenawallet.io/what-happened-to-kadena). The application still runs - archived does not mean uninstalled - but no further security patches, dependency upgrades, or browser-API fixes are planned. For most KDA holders, the right move is to migrate to a maintained client. [Kadena Wallet](https://kadenawallet.io/kadena-wallet) was built specifically to be that destination, and the [Chainweaver alternative page](https://kadenawallet.io/chainweaver-alternative) is the canonical migration walkthrough.

This article condenses that walkthrough and adds notes on edge cases that catch long-time Chainweaver users.

## Before you start: what you actually need

You need three things before opening either wallet:

1. Your Chainweaver mnemonic (the phrase you wrote down when you first set Chainweaver up). If you do not have it, see the [recovery guide](https://kadenawallet.io/kadena-wallet-recovery).
2. The list of accounts you actively used in Chainweaver. For each one, note the chain (0-19) and the account name. Account names matter on Kadena because of named accounts; the [Chainweb explainer](https://kadenawallet.io/glossary/what-is-chainweb) covers why.
3. A clean machine to run the new wallet on, ideally the same one you used for Chainweaver. Download the new installer from the [official page](https://kadenawallet.io/download).

Do not rush. There is no deadline. Chainweaver still functions for read access; you can verify balances side by side.

## Why direct seed import works

Chainweaver uses a custom derivation path that is not standard BIP44. That is why you cannot simply paste a Chainweaver mnemonic into a generic Bitcoin or Ethereum wallet and see your KDA. [Kadena Wallet](https://kadenawallet.io/kadena-wallet) implements the Chainweaver derivation natively, alongside [BIP39 12-word (eckoWALLET)](https://kadenawallet.io/vs/eckowallet) and [24-word (Koala Wallet)](https://kadenawallet.io/vs/koala). Same seed, same keys, same accounts - no manual key dump or paper conversion is needed.

## The migration, step by step

1. Install [Kadena Wallet](https://kadenawallet.io/download) from the official site. Verify the installer signature if you are running the macOS or Windows-signed builds.
2. On first launch, choose "Import existing wallet" and select "Chainweaver custom derivation".
3. Enter your 12-word Chainweaver mnemonic. The wallet will scan all 20 Chainweb chains and surface every account with a non-zero balance.
4. Confirm each account by visual inspection. Account names should match what you remember from Chainweaver.
5. Set a new passphrase. This passphrase encrypts the seed at rest on your device. It is independent of Chainweaver and cannot be recovered if lost - the [recovery guide](https://kadenawallet.io/kadena-wallet-recovery) is explicit on this.
6. Send a small test transaction (1 KDA) to a chain you control. Confirm it lands. Only then move larger amounts.

## Things to verify after import

- Total balance across all 20 chains matches what Chainweaver reported. The wallet's chain navigator displays per-chain balances.
- Named accounts appear correctly. If you used named accounts under k: addresses, both formats should resolve.
- DeFi positions on [eckoDEX or KDSwap](https://kadenawallet.io/kadena-swap) show up in the dashboard. Position-level detail mirrors what you saw in Chainweaver.
- Marmalade NFTs (KIP-0011) appear in the NFT viewer. Royalty info and collection grouping should match.

## What about Ledger?

If you used Ledger with Chainweaver, you can keep the same device. Pair it with [Kadena Wallet via WebHID](https://kadenawallet.io/kadena-hardware-wallet). Nano S Plus and Nano X are both supported with the official Ledger Kadena app. The seed never leaves the Ledger, and signing happens on the device exactly the way it did under Chainweaver.

## Edge cases

- Multi-key accounts: if a Chainweaver account had multiple keys, the import preserves all of them. Threshold and multisig logic is read from the chain, not from the seed.
- Old test accounts on chains you do not use: by default the import surfaces only chains with non-zero balances. You can manually add empty chains later.
- Stuck cross-chain transfers: Chainweaver occasionally left half-completed cross-chain transfers (init done, redeem stuck). The new wallet detects these and offers to redeem them automatically. If you cannot recover one, [contact support](https://kadenawallet.io/contact).

## Why migrate at all

Beyond the obvious "Chainweaver is no longer maintained", the practical reasons:

- Modern macOS and Windows builds. Chainweaver's signing chain expired with the Foundation's release infrastructure.
- A 20-chain navigator that surfaces all chains by default - relevant if you accumulated dust on chains you forgot about.
- Native Ledger via WebHID rather than the older USB pathway, which has been [increasingly fragile in modern browsers](https://kadenawallet.io/glossary/what-is-pact).
- Privacy: no third-party analytics, [explicitly](https://kadenawallet.io/legal/privacy).
- An [independent third-party security audit](https://kadenawallet.io/about) has been completed.

## What if the network is dying?

Some Chainweaver users hesitate to migrate because they wonder whether the [network itself is winding down](https://kadenawallet.io/is-kadena-dead). The honest answer: the [Foundation is dissolved](https://kadenawallet.io/what-happened-to-kadena), but the chain itself is still producing blocks, [mining is still active](https://kadenawallet.io/kadena-mining), [exchanges still list KDA](https://kadenawallet.io/exchanges) (with notable exceptions like [Binance](https://kadenawallet.io/binance-delisting)), and [recovery scenarios](https://kadenawallet.io/will-kadena-recover) are open. Holding KDA in a maintained wallet is the strictly safer bet regardless of which way the network goes.

## Related articles

- [Self-custody Kadena Wallet overview](01-self-custody-kadena-wallet-overview.md)
- [Best Kadena wallet 2026](03-best-kadena-wallet-2026.md)
- [Is Kadena dead? Status outlook](11-is-kadena-dead-status-outlook.md)
- [Recovering a wallet from a seed phrase](12-recovering-kadena-wallet-from-seed.md)
