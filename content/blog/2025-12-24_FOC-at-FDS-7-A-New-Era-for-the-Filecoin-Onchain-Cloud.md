---
title: "FOC at FDS-7: A New Era for the Filecoin Onchain Cloud"
description: "James Bluett (@TippyFlits) - The Filecoin community came together this year around two milestones: the Virtual FDS-7 Kickoff in October and the in-person summit in Buenos Aires in November."
date: '2025-12-24T17:19:20.312Z'
categories: []
keywords: [FOC, FDS-7, Filecoin Onchain Cloud, IPC, x402]
slug: foc-at-fds-7-a-new-era-for-the-filecoin-onchain-cloud
featured_image: /images/blog/foc-fds7-header.png
---

![](/images/blog/foc-fds7-header.png)

James Bluett ([@TippyFlits](https://x.com/TippyFlits))

The Filecoin community came together this year around two milestones: the Virtual FDS-7 Kickoff in October and the in-person summit in Buenos Aires in November. Across both gatherings, one theme stood out unmistakably:

**The Filecoin Onchain Cloud (FOC) has arrived — and it is already reshaping how builders think about verifiable data, compute, retrieval, and onchain services.**

From first introductions and demos to hands-on technical workshops, FOC was the heartbeat of FDS-7.

This recap highlights the key moments, breakthroughs, and conversations that defined the FOC track — and the talks you absolutely should not miss.

{{< youtube jqQIpMheeXk >}}

---

## Watch the full tracks

**Filecoin Onchain Cloud Launch Livestream**
[https://www.youtube.com/playlist?list=PL_0VrY55uV1_4N6-tGCtZ8SGbZV3Ug783](https://www.youtube.com/playlist?list=PL_0VrY55uV1_4N6-tGCtZ8SGbZV3Ug783)

**Virtual FDS-7 Playlist**
[https://www.youtube.com/playlist?list=PL_0VrY55uV180oE5CLIMr0VmFksA3z9SH](https://www.youtube.com/playlist?list=PL_0VrY55uV180oE5CLIMr0VmFksA3z9SH)

**In-Person FDS-7 Playlist (Buenos Aires)**
[https://www.youtube.com/playlist?list=PL_0VrY55uV1_iMFnyuua-kO5wDEEPb4Yo](https://www.youtube.com/playlist?list=PL_0VrY55uV1_iMFnyuua-kO5wDEEPb4Yo)

---

## Kicking Off the Onchain Cloud: The Virtual Summit

The Virtual Summit set the foundation for everything that followed. It was the first time the community saw the full conceptual model of the Filecoin Onchain Cloud — a unified, programmable stack for storage, retrieval, payments, and proof-based services.

It introduced:

- The Synapse SDK
- Becoming a Filecoin Onchain Cloud Service Provider
- FOC Alpha Cohort demos
- The new mental model of Filecoin as a verifiable cloud, not just a storage layer

**Speakers:** Jennifer Wang, Molly Mackinlay, Sarah Thiam, James Bluett, Tim Fong & Patrick Woodhead

**Watch:** [Introduction to the Filecoin Onchain Cloud](https://www.youtube.com/watch?v=1Q8POPzrnyw)

{{< youtube 1Q8POPzrnyw >}}

This session delivered the first fully articulated vision of FOC — how services like FWSS, PDP, retrieval, payments, and replication compose into a modern cloud environment. It reframed Filecoin as a programmable platform where builders can deploy real applications, real workloads, and real-time data services.

---

## Blazing Fast Onchain Cloud Services with IPC

**Speakers:** Philip Hutchins & Jennifer Wang

**Watch:** [Blazing Fast Onchain Cloud Services with IPC](https://www.youtube.com/watch?v=PXgliwsxLaA&list=PL_0VrY55uV1_iMFnyuua-kO5wDEEPb4Yo&index=13)

{{< youtube PXgliwsxLaA >}}

This session unveiled the introduction of **1-second finality IPC subnets**, powering a new class of real-time FOC services, including:

- Instant retrievals
- Micropayment settlement
- Real-time proofs
- Streaming workloads
- Responsive onchain APIs

IPC effectively gives Filecoin a "fast lane" for cloud-native apps — dramatically expanding what developers can build. After this talk, it became clear that FOC isn't just decentralised — it's **fast**.

---

## Designing x402 on Filecoin Pay + Pay-to-Access Retrievals

**Speakers:** Miroslav Bajtoš & Jennifer Wang

**Watch:** [Designing x402 on Filecoin Pay + Pay-to-Access Retrievals for Filecoin](https://www.youtube.com/watch?v=D1Eosh3rzDo&list=PL_0VrY55uV1_iMFnyuua-kO5wDEEPb4Yo&index=16)

{{< youtube D1Eosh3rzDo >}}

This session introduced x402 micropayments and the architecture for per-retrieval economic flows, finally enabling demand-driven markets for data access.

Key ideas included:

- Signed tickets for off-chain micropayments
- ZK rollup settlement
- SP-ready retrieval pricing
- Developer-friendly pay-as-you-go models

For the first time, retrieval becomes a first-class, monetizable service in the Filecoin economy — unlocking new business models for both builders and storage providers.

---

## What Else Happened in the FOC Track

Not every discussion in Buenos Aires became a recorded talk, but many of the most influential conversations took place in unscripted workshops and design sessions.

Much of the engineering focus centred around strengthening the foundations of the Onchain Cloud. Tim Fong and Irene Giacomelli led key conversations on the FOC durability and repairability baseline: how replicas are monitored, how repair flows work, and which reliability metrics matter most as the cloud scales.

These discussions fed into the FWSS economic design work. Luca Nizzardo walked through emerging models for rebates, collateral, and slashing that aim to keep data reliably accessible at scale.

Composability was another major thread. Rod Vagg hosted a hands-on walkthrough of how PDP, replication, repair, and retrieval fit together into a cohesive, programmable pipeline. Even without a recording, this became one of the most-referenced sessions of the week.

Object storage also took centre stage. Richard Herold guided the room through lessons from prior attempts and emerging plans for S3-compatible, Filecoin-native object storage. Portions of this work appear in the recorded material, but much of the design discussion took place in-room.

The track also explored how Filecoin can serve as a storage layer for other blockchains without leaking value — a highly interactive set of conversations around trust models and payment flows.

And as the week progressed, AI and DePIN emerged as major themes. Dhawal Shah's [recorded session](https://www.youtube.com/watch?v=bugRO-QP5SQ&list=PL_0VrY55uV1_iMFnyuua-kO5wDEEPb4Yo&index=10) showed how autonomous agents can use FOC to store, retrieve, and act on data. Meanwhile, Molly Mackinlay facilitated a forward-looking discussion on DePIN datasets and the specialised FOC services they will need — shaping priorities heading into 2026.

---

## A Coordinated Launch Across the Ecosystem

What made the FOC track special wasn't just the engineering — it was the alignment.

FOC was being discussed simultaneously across:

- Economic design
- Governance
- Retrieval markets
- Storage provider enablement
- SDKs & tooling
- Network architecture
- AI workloads
- DePIN verticals

FOC isn't a siloed initiative. It is the organising foundation for the next phase of the Filecoin ecosystem.

---

## The Road Ahead

Coming out of FDS-7, the community heads into 2026 with clear priorities:

- Make FOC durability guarantees measurable and visible
- Connect retrieval economics to Filecoin Pay + x402
- Onboard more SPs into the Onchain Cloud
- Unify developer tooling around the Synapse SDK
- Bring IPC into production for real workloads
- Support the rising demand for AI & DePIN data services

FOC is no longer "launching." — FOC is here — and now it **grows**.

---

## Closing Thoughts

FDS-7 marked a turning point.

From the Virtual Kickoff to the packed rooms in Buenos Aires, the Filecoin Onchain Cloud moved from concept → architecture → active ecosystem.

FilOz is proud to help steward this moment — and even more excited for what comes next.

2026 is the year FOC moves from *launch* to live, and we can't wait to see what the community builds.
