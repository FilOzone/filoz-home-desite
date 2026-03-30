---
title: 'Filecoin Onchain Cloud: From Design to Reality'
description: "Luca Nizzardo (@lucaniz_) - As Filecoin Onchain Cloud approaches mainnet readiness, payments are beginning to flow. For the first time, Filecoin is earning from actual infrastructure usage."
date: '2026-03-30T12:00:00.000Z'
categories: []
keywords: [Filecoin Onchain Cloud, FOC, PDP, Filecoin Pay, USDFC, FIL burn]
slug: filecoin-onchain-cloud-from-design-to-reality
featured_image: /images/blog/foc-design-to-reality.png
---

![](/images/blog/foc-design-to-reality.png)

Luca Nizzardo ([@lucaniz_](https://x.com/lucaniz_))

As Filecoin Onchain Cloud (FOC) approaches mainnet readiness, **payments are beginning to flow**. For the first time, Filecoin is earning from actual infrastructure usage.

Early activity on calibnet and mainnet demonstrates a pivotal shift: infrastructure usage and economic activity now directly feed back into the network.

This represents something fundamental for Filecoin: a direct connection between usage, revenue, and token supply.

## From Storage Network to Verifiable Cloud

Filecoin has established strong cryptoeconomic foundations:

- Gas fees
- Collateral requirements
- Consensus participation

These mechanisms link network usage to the token.

FOC extends this model beyond blockspace into the **service layer**.

As Filecoin becomes a verifiable cloud platform, two value accrual mechanisms emerge:

- Service fees
- Payment fees

Both tie real-world usage directly to FIL.

## Service Fees: Infrastructure Usage Paid in FIL

Service fees activate when network services are utilized.

**Proof of Data Possession (PDP)** provides the clearest example today.

PDP enables storage providers to cryptographically demonstrate that data remains stored and accessible over time.

When a dataset is verified:

- A size-based fee is charged
- The fee is paid directly in FIL
- That FIL can be burned

Current parameters set PDP at **0.00023 FIL per TiB per proof**.

This creates a direct feedback mechanism:

**More data -> more proofs -> more FIL burned**

As additional data enters verifiable storage:

- More proofs generate
- More fees are paid
- More FIL is burned

PDP marks just the beginning. As FOC services expand, this framework scales further.

## Payment Fees: Converting Economic Activity into FIL

The second mechanism operates at economic throughput levels.

Filecoin Pay introduces a **0.5% fee on settlements** when applications transact on-chain for services.

Payments often use ERC20 tokens like **USDFC**.

Without intentional design, this could disconnect usage from FIL.

FOC implements a bridge: a **continuous Dutch auction mechanism**.

- ERC20-denominated fees accumulate over time
- Recurring auctions convert those tokens into FIL
- Participants bid FIL to acquire accumulated tokens
- FIL used in auctions is burned

Even stablecoin-denominated payments funnel value back into FIL.

## USDFC and the Locking Effect

USDFC is becoming the primary stablecoin for ecosystem storage payments.

Because storage deals typically recur:

- USDFC accumulates between auction cycles
- It ties to total monthly storage payment rates

This creates a **persistent pool of locked value** in the payment system while FIL used to clear auctions continuously burns.

Notably, USDFC is overcollateralized by FIL. Each USDFC in circulation requires more than 1x FIL locked as collateral.

As USDFC adoption grows, it increases locked value tied to storage payments and drives additional FIL locking at protocol level.

This produces strong alignment:

- Stablecoins enable predictable payments
- FIL remains the value sink

## Auctions Are Live and Participatory

The auction mechanism operates live and accepts participation.

When payment fees accumulate:

- Anyone can participate in auctions
- Including automated agents

Since auction prices decay over time:

- Participants can bid strategically
- Arbitrage opportunities exist between auction prices and external markets

When auctions clear:

- FIL is burned
- ERC20 tokens are distributed
- The next cycle begins

Tools are available: [filecoin-pay-auction-bot](https://github.com/FilOzone/filecoin-pay-auction-bot)

This creates an active connection between the ecosystem and Filecoin's token economy.

## Two Streams, One Outcome

FOC introduces two complementary mechanisms:

Service fees scale with infrastructure usage and generate **direct FIL burn**.

Payment fees scale with economic activity and generate **FIL burn via auctions**.

Both produce identical results:

**As Filecoin is used, FIL is removed from circulation.**

## Why This Matters Now

The distinction lies not merely in design but in **timing**.

**FOC is no longer theoretical.**

Approaching mainnet launch:

- Payments flow on calibnet
- Early mainnet activity emerges
- Real usage generates real economic signals

For the first time, Filecoin moves past:

- securing data
- coordinating storage

and into: **earning from its own infrastructure usage**

## A New Feedback Loop for Filecoin

FOC establishes powerful alignment between:

- infrastructure growth
- economic activity
- token supply

More stored data leads to increased service usage and more FIL burned.

More settled payments lead to more auctions and more FIL burned.

Adoption growth compounds these effects.

## Looking Ahead

FOC transcends adding new services.

It extends Filecoin's cryptoeconomic design into the cloud layer -- ensuring network growth drives token growth.

Early indicators are present.

The focus now shifts to scaling them.
