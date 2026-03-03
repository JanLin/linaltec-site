---
title: "prCEN TS 18297: Security Controls for Access Requests in the EUDI Wallet Ecosystem"
date: 2026-01-07
description: "A guide to prCEN TS 18297, the new CEN technical specification defining security controls for access requests in the EUDI Wallet ecosystem. What it covers, why it matters, and what '3 from 300' means."
tags: ["EUDI Wallet", "CEN Standards", "eIDAS 2.0", "Digital Identity", "Security Controls"]
author: "Jan Lindquist"
summary: "prCEN TS 18297 defines how relying parties request access to personal data in the EUDI Wallet — and how wallet users stay protected. As co-editor of this technical specification, I explain the five core security controls and why they matter for the everyday person navigating digital identity."
cover:
  image: "images/prcen-ts-18297-eudi-wallet.jpg"
  alt: "Smartphone displaying EU digital certificate alongside EU passport and QR code documents"
  caption: "Photo by Nataliya Vaitkevich on Pexels"
  relative: false
---

## Why access request security matters

The European Digital Identity Wallet will put citizens in control of their personal data — at least, that's the promise. But a wallet is only as secure as the moment someone asks to see what's inside it. Every time a relying party requests access to your credentials, there is a security decision to be made. Get that moment wrong, and the user is exposed to social engineering, credential over-sharing, or worse.

prCEN TS 18297 exists to get that moment right. It is a foundational technical specification from CEN that defines security controls for access requests in the EUDI Wallet ecosystem. I call it "3 from 300" as a mnemonic for the standard number 18297 — but the content is anything but forgettable.

## What prCEN TS 18297 defines

The specification addresses the critical interaction point where a relying party asks a wallet holder to share personal data. It establishes concrete, implementable security controls across five areas:

### Mutual authentication

Before any data is shared, both parties must verify each other's identity. The wallet holder needs assurance that the requesting party is legitimate, and the relying party needs assurance that the wallet and its credentials are genuine. This bidirectional verification is the foundation of trust in the ecosystem — without it, phishing attacks against wallet users become trivially easy.

### Embedded policies and metadata

Access requests must carry structured metadata that describes exactly what is being requested and under what conditions. This goes beyond a simple data request: it embeds the purpose, legal basis, retention period, and scope directly into the request itself. The wallet can then present this information to the user in a meaningful way, enabling informed decisions rather than blind acceptance.

### Clear notices to fight social engineering

One of the biggest risks in any identity system is social engineering — persuading users to share more than they should, or to share with someone they shouldn't. TS 18297 mandates clear, understandable notices that help users recognise legitimate requests and spot suspicious ones. This draws on lessons from my earlier work on ISO/IEC 27560, where we established that structured, real-time notifications and decision records consistently outperform static privacy policies.

### Stronger user decisions with verifiable audit trails

Every access request and the user's response to it must be recorded in a verifiable audit trail. This serves multiple purposes: it gives users a clear history of who asked for what and when, it provides evidence in case of disputes, and it creates accountability for relying parties who may be tempted to over-request. The audit trail is not just a log — it's a tool for user empowerment.

### User-centric security by design

Taken together, these controls shift the security paradigm. Rather than assuming the user will read terms and conditions or understand technical protocols, TS 18297 builds protection into the architecture itself. The wallet becomes an active participant in protecting its holder, not just a passive container for credentials.

## Why this matters now

The EUDI Wallet is moving from regulation to implementation. The revised eIDAS Regulation (eIDAS 2.0) mandates that EU Member States offer digital identity wallets to all citizens by 2026. As implementers build wallet solutions and relying parties prepare to integrate, they need concrete security specifications to work from — not just high-level principles.

TS 18297 fills a critical gap. Without standardised security controls for access requests, each implementation would make its own choices about how to protect users. That fragmentation would undermine both security and interoperability across the EU.

## The weakest link

The specification recognises something that security professionals know well: the weakest link is often the user. Not because users are careless, but because they are everyday people trying to navigate security decisions under pressure. TS 18297 is designed around this reality — it doesn't assume technical sophistication from wallet holders. Instead, it requires the system to present clear choices, prevent manipulation, and maintain accountability.

## How to get involved

The ballot for prCEN TS 18297 closed in February 2026. If you are involved in EUDI Wallet implementation — whether as a wallet provider, relying party, or national authority — this specification will directly affect your technical architecture. I encourage you to:

1. **Read the specification** — Contact your national CEN standardisation body for access
2. **Assess your implementation** — Map your current access request flow against the five security controls
3. **Engage with the standards process** — CEN working groups welcome expert input from implementers

## About my involvement

I co-edited prCEN TS 18297 together with Mourad Faher, with important contributions from Andrea Röck and Andreea Prian. This work builds on my broader standards engagement: I also serve as lead editor of ISO/IEC 27560 (consent records) and contribute to several CEN and ISO working groups on digital identity and privacy.

The connection between ISO 27560 and TS 18297 is direct — both address the moment when someone is asked to make a decision about their personal data. ISO 27560 standardises the record of that decision; TS 18297 standardises the security controls that ensure the decision is informed and protected.

If you need help understanding how TS 18297 affects your EUDI Wallet implementation, or how to align your access request architecture with these security controls, [get in touch](/contact/).
