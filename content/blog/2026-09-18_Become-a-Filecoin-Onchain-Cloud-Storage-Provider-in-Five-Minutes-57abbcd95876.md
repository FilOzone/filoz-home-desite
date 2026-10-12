---
title: 'Become a Filecoin Onchain Cloud Storage Provider in Five Minutes'
description: "Andy Jackson (@snadrus), James Bluett (@TippyFlits) - Storage is one of the most common things people buy online. Filecoin Onchain Cloud (FOC) lets you sell it from your own hardware, and everything you need runs on a single machine."
date: '2026-09-18T15:00:00.000Z'
categories: []
keywords: [Filecoin Onchain Cloud, FOC, PDP, Curio, storage provider, Docker]
slug: become-a-filecoin-onchain-cloud-storage-provider-in-five-minutes
featured_image: /images/blog/sp-in-five-minutes.png
---

![](/images/blog/sp-in-five-minutes.png)

Andy Jackson ([@snadrus](http://snadrus.github.io/)), James Bluett ([@TippyFlits](https://x.com/TippyFlits))

Storage is one of the most common things people buy online. [Filecoin Onchain Cloud](https://filecoin.cloud/) (FOC) lets you sell it from your own hardware, and everything you need runs on a single machine. The chain proves you're still holding the data, and the network sends paying customers your way.

Until now, getting a PDP node running meant setting up a chain node, a database, and [Curio](https://github.com/filecoin-project/curio) yourself, then wiring the three together. We've done that bit for you. The whole stack is now packaged; one command brings it up, and a web guide handles the rest.

Downloads aside, setup takes about five minutes. A video of the whole process is at the end of this post.

## 📦 What's in the Box

Curio PDP now ships as a single Docker Compose stack made up of three pieces:

- **Forest** -- the Filecoin chain daemon
- **Yugabyte** -- the database
- **Curio PDP** -- the storage node itself, with a web dashboard

They all run in Docker on their own private network. Only Curio PDP faces the internet, on ports 80 and 443.

The first time you open the dashboard, it lands you on a setup guide. The guide checks your node and ticks off each step as it completes. Everything is set from the dashboard, so there's no config file to edit.

## ✅ What You Need

- A Linux or macOS machine with Docker installed (Docker Compose comes with it)
- 32 GiB+ RAM and an 8-core+ CPU (no GPU required)
- About 100 GB of disk for the chain state and database, plus the storage you want to sell (the guide needs at least 20 GiB of that attached)
- A reliable internet connection
- A domain or subdomain you own
- A little FIL to fund a wallet

## 🚀 Start the Stack

Run these on the machine that's going to be the node. Use the mainnet lines to run for real, or the Calibration lines to try it on the test network first, where everything runs on free test funds:

```bash
git clone https://github.com/filecoin-project/curio.git
```

```bash
# Mainnet
docker compose -f curio/docker/skiff/docker-compose.yaml up -d
docker compose -f curio/docker/skiff/docker-compose.yaml logs -f
```

```bash
# Calibration test network (free test funds, no real FIL)
cd curio/docker/skiff
docker compose -f docker-compose.yaml -f docker-compose.calibnet.yaml up -d
docker compose -f docker-compose.yaml -f docker-compose.calibnet.yaml logs -f
```

That brings up the node. Yugabyte is up in seconds. Forest downloads a chain snapshot the first time it starts, which takes about 20 minutes, and the first run also builds the Curio PDP image. Curio PDP starts as soon as Forest is accepting connections, although the wallet balance and registration checks wait for Forest to finish syncing. By default, everything lives under ***curio/docker/skiff/data/***.

Now open [***http://127.0.0.1:4701***](http://127.0.0.1:4701) in a browser. The dashboard only listens on localhost and has no login, so please keep it that way! If you're working on a remote box, forward the port over SSH:

```bash
ssh -fN -L 4701:127.0.0.1:4701 you@your-host
```

You'll land on the PDP Guide page.

## 📋 The PDP Guide Does the Rest

The guide is a checklist that the node verifies for you. The boxes tick themselves as each step is confirmed, and you can re-run the checks with the Re-check button. There are four steps.

1. **Fund a wallet**  
   Click ***Create wallet*** to make a new signing key, or paste in one you already have. A hex private key or the output of ***lotus wallet export*** will both do. Keep the key safe: if you create it here, this is the only time it's shown. Then send some FIL to the address on screen. Once it lands, the box ticks itself.
2. **Attach your storage**  
   Open the Storage page and attach the folders Curio PDP should use. The stack has already mounted a ***/data*** folder for you, and attaching that is the simplest option. If your disks are elsewhere, map them under ***/data*** in ***docker/skiff/.env*** before you start the stack.
3. **Set your domain**  
   On the Configuration page, set ***HTTP.DomainName*** to a domain or subdomain you own and point its DNS at this machine. The guide then checks if it can reach your node at that address.

   Don't want to open inbound ports? Create a tunnel in the Cloudflare Zero Trust dashboard and paste its token into the guide. It downloads ***cloudflared*** and starts the tunnel for you. Entirely optional.
4. **Register with FOC**  
   When the first three are green, the register button unlocks. One click adds you to the Filecoin Onchain Cloud service provider registry. After the network's quality checks have approved you (more on that below), data starts arriving.

From then on, the PDP Overview is your home page: data under proof, proving success and net income over the last 30 days, chain status, wallet balance and any open alerts, all on one screen.

## 💰 What You Earn

Customers pay in USDFC, a US dollar stablecoin on Filecoin, and the money streams to you through [Filecoin Pay](https://pay.filecoin.cloud/mainnet) as you prove you're holding their data. The price list is written into the storage contract, so every provider gets paid the same rates:

- **2.50 USDFC per TiB per month** for storage
- **0.12 USDFC per month** per data set for proving
- **0.025 USDFC** each time a customer creates a data set with you
- **0.008 USDFC per call plus 0.003 USDFC per piece** when pieces are added
- **0.007 USDFC** per call for scheduled piece removals
- **0.006 USDFC** for a customer-signed termination
- **7 USDFC per TiB** served to the CDN on a cache miss

There's no commission on the storage rate. A 0.5% network fee comes off at settlement, and that's the only deduction.

A few worked examples, storage plus proving, before the network fee:

- 1 TiB for one customer: **2.62 USDFC** a month
- 10 TiB for one customer: **25.12 USDFC** a month
- 100 TiB for one customer: **250.12 USDFC** a month

The one-time fees cover the FIL gas you spend submitting your customers' transactions, and the proving fee covers the daily proof. Both were calibrated in August 2026 at ten times the measured gas cost, so the on-chain side of running a node more than pays for itself. Your own costs are the machine, the disks and the connection. The full schedule and how it was worked out is in the [pricing rationale](https://github.com/FilOzone/filecoin-services/blob/main/docs/pricing-rationale.md).

Before you plan around these numbers, a quick note on how data reaches you. Registration gets you into the registry, but the network's quality checks decide when data is routed to you. [Dealbot](https://dealbot.filoz.org/) continuously tests new providers on deal success, retrieval success, and proof retention, and those that pass are approved to store customer data. Keep the node up and proving, and the data will come.

## 🎬 Watch It Happen

{{< youtube _qoB56qkOy4 >}}

## 🔗 Get Started

- The [operator runbook](https://docs.curiostorage.org/experimental-features/curio-pdp) goes into more depth on this stack: external chain nodes, custom storage paths and troubleshooting
- Prefer to run Lotus, YugabyteDB and Curio as separate services instead of in Docker? The [Install & Run PDP guide](https://docs.filecoin.io/provide-storage/pdp/install-and-run-pdp) walks through building and wiring up each component by hand, useful if you want closer per-service monitoring or already run your fleet that way
- You can see your node's proving and payments on the [PDP Scan Dashboard](https://pdp.filecoin.cloud/)
- Come and say hello in [#fil-curio-help](https://filecoinproject.slack.com/archives/C06LF5YP8S3) on Filecoin Slack if you get stuck or have feedback
- If you'd like a hand getting your hardware onto the network, [talk to us](https://filecoin.cloud/contact)

Huge thanks to the Curio team for getting this over the line. We've wanted a one-command PDP node for a long time, and it's brilliant to finally have one. 🛠️ Let's FOC-ing go!
