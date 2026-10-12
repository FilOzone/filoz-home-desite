---
title: 'FilOz in 2026: Progress Report'
description: "Molly Mackinlay (@momack28), Jennifer Wang (@_jennijuju), James Bluett (@TippyFlits) - 2026 has had one job so far: get real customers paying real money for onchain Filecoin services."
date: '2026-09-15T15:00:00.000Z'
categories: []
keywords: [FilOz, Filecoin Onchain Cloud, FOC, PDP, Filecoin Pay, Synapse SDK, Fil+]
slug: filoz-in-2026-progress-report
featured_image: /images/blog/filoz-2026-progress-report.png
---

![](/images/blog/filoz-2026-progress-report.png)

Molly Mackinlay ([@momack28](https://x.com/momack28)), Jennifer Wang ([@_jennijuju](https://x.com/_jennijuju)), James Bluett ([@TippyFlits](https://x.com/TippyFlits))

Over the past several years, the Filecoin ecosystem has built the foundations required for a decentralized storage network with verifiable, content-addressed data storage: protocol upgrades, proof systems, tooling, service design, and governance experimentation.

In mid-2024, Nicola Greco from FilOz proposed ["Filecoin Web Services"](https://www.youtube.com/watch?v=Yz5-9oP9d0Q) at FDS-Brussels, a new concept laying out a broader vision for Filecoin: expanding from pure storage capacity into a verifiable cloud service network built on onchain primitives, service markets, and verifiable payments that increase network utility & drive network value accrual.

That discussion helped shape the ecosystem's 2025 push toward paid demand and onchain ARR, and FWS (now FOC) became our major execution focus for FilOz. In H1 2025, we focused on developing the core protocol and service foundations: the new storage primitive PDP and [Filecoin Pay](https://pay.filecoin.cloud/mainnet) as an onchain payment service that provides transparent payment based on service delivered. In H2 2025, we expanded into the tooling and adoption layer, building the [Synapse SDK](https://docs.filecoin.cloud/), [Filecoin Pin](https://pin.filecoin.cloud/), and explorer tooling while working closely with early builders and adopters to dogfood, iterate on, and harden the system. That work culminated in the November 2025 launch of [Filecoin Onchain Cloud](https://filecoin.cloud/) (FOC), live on Mainnet since January.

2026 has had one job so far: get real customers paying real money for onchain Filecoin services. Today, Filecoin Pay activity represents over $139K in ARR. Customers are buying storage directly from decentralised providers within minutes. PDP deployments are proving data possession every day across Mainnet and Calibration. The whole loop is measurable onchain.

The numbers are still small, but they are no longer theoretical - we are turning Filecoin into a paid, working service marketplace. Here is what actually happened.

## 📊 What Has Already Shipped in 2026

2026 has focused on getting the service stack into motion and keeping it moving: protocol upgrades, PDP deployments, Filecoin Onchain Cloud, Synapse, Filecoin Pay, and provider operations.

### Filecoin Onchain Cloud

Filecoin Onchain Cloud is [live on Mainnet](https://pdp.filecoin.cloud/mainnet), with warm storage service deployments operated by Filecoin PDP storage providers.

The [Synapse SDK](https://docs.filecoin.cloud/) shipped v1 across the SDK, CLI, MCP and docs, including support for automatic two-copy replication. This makes FOC easier for builders to use without requiring every application to assemble its own reliability layer from scratch.

We also put a number on onboarding: a developer can now go from nothing to stored data with [filecoin-pin](https://pin.filecoin.cloud/) in under 2 minutes end-to-end, 2x faster than our 5-minute target. Getting started should not be the hard part, and now it isn't.

The team also hardened operational readiness and monitoring across the stack, improving our ability to operate, observe, and respond to production deployments. This work turns a launch into a robust, reliable service.

### PDP in production

PDP is now running in live environments across Mainnet and Calibration, backing every FOC warm storage deal.

Live visibility is available through the [PDP Scan Dashboard](https://pdp.filecoin.cloud/mainnet), Dealbot continuously tests provider performance in the open, and the ecosystem now has an independent public view of the whole FOC network through [Probelab's FOC dashboard](https://probelab.io/filecoin/foc).

Proof systems only become useful when they support real service expectations. PDP is moving from protocol component to production infrastructure.

### Filecoin Pay and paid usage

[Filecoin Pay](https://pay.filecoin.cloud/mainnet) is settling real service transactions, and this is where the story is strongest so far.

Customers are funding Filecoin Pay accounts. Services are being paid for. Providers are receiving payments. The network is capturing utility value through the Filecoin Pay auction pool.

As of mid-September:

- **$67,312 in stablecoins has been transacted** through onchain service payments: $5,634 in streaming settlements and $61,678 in one-time payments
- **$4,408 is locked across 560 active payment rails** between customers and service providers
- **165 unique payers** have purchased Filecoin services
- **31 unique payees or service providers** have received payments
- Current activity represents approximately **$139,789 in ARR**
- **65.43 FIL has been burned** from the Filecoin Pay auction pool as network value accrual

All figures exclude our own internal and test activity, so this is real usage from Filecoin customers. Payment volume is publicly trackable on the [Filecoin Data Portal](https://filecoindataportal.xyz/).

These are still small numbers for a cloud business, but they show that the core loop is working: customers can pay for Filecoin services, providers receive payment, and the network captures value from real service usage. As we scale customer volume, storage provider and protocol revenue scale as well, driving growth for the whole Filecoin economy.

### Protocol and network upgrades

Several protocol updates landed:

- The [nv28 "Fire Horse" upgrade went live on Mainnet on 27 May](https://github.com/filecoin-project/community/discussions/74). It delivered [FIP-0115](https://github.com/filecoin-project/FIPs/blob/master/FIPS/fip-0115.md), replacing utilization-based base fee adjustment with a premium-based target to help stabilise gas markets and improve tipset efficiency.
- [FIP-0109](https://github.com/filecoin-project/FIPs/blob/master/FIPS/fip-0109.md) and [FIP-0112](https://github.com/filecoin-project/FIPs/blob/master/FIPS/fip-0112.md) also went live in nv28, enabling programmable storage services backed by PoRep.
- [Fil+ reform](https://github.com/filecoin-project/FIPs/discussions/1249) has moved from discussion to acceptance, with the [Solstice work](https://github.com/filecoin-project/solstice/issues/1) and [FIP-0118](https://github.com/filecoin-project/FIPs/blob/master/FIPS/fip-0118.md) landing in the upcoming [nv29](https://github.com/filecoin-project/core-devs/discussions/221).

This matters because Filecoin's next phase depends on services that can be programmed, paid for, verified, and measured.

## 💳 What We Are Seeing From Real Usage

The most important 2026 signal isn't revenue size. It is that real paid usage is live and growing.

Customers can now purchase storage directly from decentralised providers within minutes, without intermediaries. They can fund an account, buy storage, have that service delivered, and see payment activity onchain. Providers can receive payment for the service they deliver. The network is also capturing value from that utility.

One concrete example: when Storacha wound down its IPFS pinning service, we helped their users migrate to [Filecoin Pin](https://pin.filecoin.cloud/). The migration is now complete, with more than 3.6 million pieces and nearly 5 TB of customer data stored and paying on Filecoin, each held in two copies across independent providers. These are real users with real data who chose Filecoin.

Usage is still early -- it is not enough volume to declare success. But it is a much cleaner signal than proxy metrics or test activity. Now the work is to make this path easier, more reliable, and large enough to matter.

Our focus now is scaling GTM, scaling customer sales, AI-optimizing our onboarding flow, and growing the community of service providers earning from paying customers.

- If you're an agent or AI developer, get started with the [Filecoin Pin CLI](https://pin.filecoin.cloud/) or [agent skills library](https://github.com/filecoin-project/filecoin-skills)
- If you're a builder, you can get started immediately [with the Synapse SDK](https://docs.filecoin.cloud/getting-started/)
- If you're a potential customer, we'd love to hear from you about what you need to get started quickly - book a call [here](https://filecoin.cloud/contact)
- If you're a potential service provider with storage, compute, or retrieval hardware to monetize -- we'd love to help you join Filecoin! With FOC it's faster and cheaper than ever before to start earning. Get started [here](https://docs.filecoin.io/provide-storage/pdp/install-and-run-pdp)!

## 🧠 What We Have Learned in 2026

2026 reinforced that go-to-market and customer pipeline work are core parts of production readiness. Real adoption requires more than working contracts. It requires documentation, examples, support paths, reliable tooling, and clear ownership when customers hit a problem. Putting services in front of paying users surfaced things that planning alone would never have found.

For customers, the goal is simple: buying storage on Filecoin should feel direct, reliable, and easy to understand. Filecoin Onchain Cloud is making that possible. Customers can fund Filecoin Pay accounts, purchase services, and see payments flow onchain. The experience still needs to improve, especially around onboarding, migration tooling, service expectations, monitoring, repair, and support, but many improvements are already in flight and the flywheel is accelerating.

For builders, the priority is reducing friction. The [Synapse SDK](https://docs.filecoin.cloud/), stable [Synapse documentation](https://docs.filecoin.cloud/), [Filecoin Pin](https://pin.filecoin.cloud/), and explorer tools all help make FOC easier to integrate and understand. Builders should not need to understand every contract, payment rail, and provider workflow before they can start building. Improving AI hooks and skills for integrating with Filecoin is also a key priority to further smooth the onboarding flow.

For storage providers, PDP and FOC create service opportunities beyond traditional capacity growth. Providers are now measured against service outcomes such as uptime, deal success, retrieval performance, proof reliability, and payment flow -- and paid for the valuable cloud services they offer. That changes the relationship between participation and reward.

This is why recent [Curio releases](https://github.com/filecoin-project/curio/releases), the [PDP Scan Dashboard](https://pdp.filecoin.cloud/mainnet), [Dealbot](https://dealbot.filoz.org/), and provider-facing performance work matter. They help make service delivery measurable, comparable, and trusted.

## ⚖️ What This Means for Incentives

Filecoin's incentive systems are also evolving as services are built on the network.

Fil+ and DataCap were created in an earlier phase, when the network was focused heavily on storage capacity. As Filecoin moves toward onchain services, incentives need to better reflect service delivery, customer demand, and measurable performance.

That does not mean reducing openness. It means making the connection between participation, service quality, and reward clearer.

In H1, this shift moved from talk to text. The [Fil+ reform discussions](https://github.com/filecoin-project/FIPs/discussions/1249) now have a concrete shape in the [Solstice proposal](https://github.com/filecoin-project/solstice/issues/1) and [FIP-0118](https://github.com/filecoin-project/FIPs/blob/master/FIPS/fip-0118.md), laying out the path from a capacity-first network toward a service economy where incentives reinforce useful work.

For FilOz, this is a major 2026 priority because protocol design, customer demand, and provider economics need to move together.

{{< youtube KxhverfrYcM >}}

## 📈 What FilOz Is Focused On Next

Filecoin Onchain Cloud is live. Paid usage has started. PDP deployments are running. Filecoin Pay is settling real transactions. Now we need to make the system more reliable, easier to adopt, and easier to measure. Next, we're focused on:

### Paid usage and Filecoin Pay

- Growing recurring paid usage
- Easy top-up and self-funding straight from the CLI and console
- Sponsored payment rails, so apps can cover costs for their users
- [Filecoin Pay](https://pay.filecoin.cloud/mainnet) v2, with a public-facing payments dashboard so anyone can watch the service economy working
- Connecting service revenue more clearly to network value accrual

### FOC reliability and operations

- Automated repair
- Active monitoring
- Smoother upgrade processes
- Better incident response loops
- Stronger service-level reporting
- A revamped [filecoin.cloud](https://filecoin.cloud/) user dashboard

### Protocol and incentive alignment

- Supporting the next network upgrade (NV29)
- Continuing [Fil+ reform](https://github.com/filecoin-project/FIPs/discussions/1249) toward a revenue-gated service economy
- Connecting allocations and incentives more directly to delivered service
- Improving the path for programmable storage services backed by PoRep
- Moving Lotus to a weekly automated release train, so improvements and security fixes reach the network faster

### Builder and provider experience

- Improving the [Synapse SDK](https://docs.filecoin.cloud/) and documentation
- A re-architecture of the warm storage service, so builders can price and package their own services on top of it
- Smaller CIDs to cut overhead, plus large file support and encryption
- Rolling out the new [PDP-first Curio build](https://docs.curiostorage.org/experimental-features/curio-pdp), so hardware providers can join the network and start earning with a single command
- Improving dashboards and public performance visibility
- Tightening feedback loops between engineering and customer-facing teams

We are building FOC in the open, and the roadmap is shaped by what builders and providers actually need. Tell us what would get you to adopt it: join the conversation in [Slack](https://filecoinproject.slack.com/archives/C07CGTXHHT4), or drop your input through the [feedback form](https://filecoin.cloud/contact) on the [Filecoin Cloud website](http://filecoin.cloud/).

## 🎯 Where We Want to Be by the End of 2026

By the end of 2026, success should be visible in the network itself.

We should see more customers purchasing storage directly through onchain services, more recurring revenue from real usage, more PDP-backed service deployments operating reliably on Mainnet, more providers meeting transparent service-level expectations, and a clearer connection between service delivery, provider rewards, and network value accrual. The loop is working. The rest of the year is about making it bigger.

That is the standard we are working toward -- a Filecoin service economy that customers can use, providers can earn from, and the network can measure.

As always, we're honoured to build the decentralised, efficient, and robust foundation for humanity's information alongside you. 🛠️ Let's FOC-ing go!
