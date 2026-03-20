---
title: "\"It's Too Complicated\" — Why Transparency in the EU Digital Identity Wallet Is Not the Enemy"
date: 2026-03-20
description: "The EUDI Wallet must perform dozens of security checks at every transaction. The question isn't whether those checks happen — it's whether the citizen sees the results. A car dashboard model shows how layered transparency can be both simple and protective."
tags: ["EUDI Wallet", "eIDAS 2.0", "CEN Standards", "GDPR", "User Experience", "Access Control"]
author: "Jan Lindquist"
summary: "Working on wallet notifications in CEN TC224 WG20, I keep hearing the same objection: 'This is too complicated for the average user.' But the complexity isn't optional — it's already mandated. The real question is whether we trust citizens with the information they need to protect themselves."
cover:
  image: "images/transparency-vs-simplicity.jpg"
  alt: "Car dashboard in the dark"
  caption: "Photo by Unsplash"
  relative: false
---

*Jan Lindquist, Lead Editor CEN TC224 WG20 — CEN/TS 18297 Access Control for European Digital Identity Wallets*

You don't read your car's diagnostic report every time you start the engine. You turn the key, the dashboard lights cycle, and you drive. But when the check engine light comes on, you want to know exactly what's wrong — not just "something is broken."

That's the tension at the heart of the EU Digital Identity Wallet: how much should the citizen see?

## The feedback I keep getting

Working on wallet user notifications in CEN TC224 WG20, I've heard the same objection repeatedly: "This is too complicated for the average user." The concern is understandable. Nobody wants to turn a simple data-sharing transaction into a technical audit. But the objection misses something fundamental: **the complexity isn't optional — it's already mandated.**

The security checks that the Wallet Access Control Engine (WACE) performs are required by eIDAS 2.0, the Implementing Acts, ETSI standards, and GDPR. Certificate validation, relying party role matching, embedded disclosure policy evaluation, processing information notice validation — these checks *will* happen. The only question is whether the citizen sees the results.

## The car dashboard model

Think about how a modern car communicates with its driver. At the surface level, it's simple: green means go, amber means caution, red means stop. You don't need to understand fuel injection timing to drive safely.

But the information is layered. When that amber warning appears, you can check the dashboard display for a plain-language explanation. If you want more, the mechanic can plug in an OBD reader and see the exact fault codes, sensor readings, and diagnostic history.

This is exactly the model CEN/TS 18297 follows for wallet notifications. The citizen sees a clear recommendation: **Granted**, **Advisory**, **Not Recommended**, or **Denied**. That's the dashboard light. If they want to understand why, they tap Details and see which checks passed or failed — the plain-language display. And for each check, they can expand into the technical detail: the certificate policy OID, the trust list registration status, the specific retention period conflict. That's the OBD reader. You can explore all four outcomes in the [interactive Wallet Access Control demo](https://linaltec.com/tools/wallet-access-control/).

## Structured inputs vs privacy policies

Here's where the "too complicated" argument actually inverts. What we have today — free-text privacy policies — is genuinely complicated. They're unstructured, inconsistent between providers, written by lawyers for legal protection rather than citizen understanding, and practically impossible to compare across services.

What CEN/TS 18297 proposes is structured, machine-readable input. The processing information builds on ISO/IEC TS 27560, and the relying party metadata maps to the ETSI TS 119 475 Registration Certificate. Because the data is structured, the wallet can *automate* the comparison: does this relying party's retention period exceed my stated preference? Is their jurisdiction within my permitted regions? Is their role type authorised for this credential?

The citizen doesn't need to read and parse these fields. The WACE does it for them and surfaces only what matters. That is simpler than a privacy policy — not more complicated.

I explored this contrast further in a separate [Privacy Processing Receipt Explorer](https://linaltec.com/tools/27560-receipt-explorer/). Traditional privacy policies average over 4,000 words of legalese, written for legal protection rather than comprehension, with vague descriptions of how to exercise your rights. An ISO/IEC TS 27560 processing receipt replaces that with a structured, individual-specific record tied to a specific purpose and lawful basis — using standardised vocabulary that a wallet can evaluate automatically. The difference is not cosmetic. A machine-readable receipt means the wallet can check retention periods, flag jurisdiction mismatches, and verify lawful basis *before* the citizen shares anything. A 4,000-word policy cannot do that no matter how carefully you read it.

## Who writes the warning?

There's a deeper challenge that the "simplicity" argument often overlooks: even if you strip the notification down to a single sentence, *who writes that sentence*?

A wallet provider is a technology platform. They can tell you a certificate check failed, but they can't tell you what that means for your tax filing, your health insurance, or your driving licence. That domain expertise belongs to the credential issuer — the national identity authority, the health insurer, the transport ministry.

The difference is striking. The wallet says: "The relying party's role type is not recognised." The issuer says: "Your national identity authority restricts PID disclosure to government, healthcare, financial, and transport roles. Retail businesses should use the age-over-18 attestation instead."

One is technically accurate but unhelpful. The other gives the citizen actionable understanding.

## Transparency is the protection

The argument for simplicity often comes from a good place: don't overwhelm the user, don't create friction, don't make sharing data feel like a security audit. But oversimplification creates its own risk.

A citizen who sees only "Approve / Decline" with no context is more vulnerable to social engineering — not less. If a fraudulent relying party presents a clean-looking request, the citizen has no basis for suspicion. The WACE checks can detect the red flags (missing certificate policy, absent trust list registration, no embedded disclosure policy), but if those results are hidden behind a generic "proceed" button, the citizen never benefits from them.

Cross-border scenarios illustrate this clearly. A US-based service requesting health data can't be verified through EU trust infrastructure — role, identity, and EDP checks are simply unavailable. Showing those checks as greyed-out and explaining *why* they're unavailable gives the citizen something a "simple" interface never could: the ability to make an informed decision about risk they wouldn't otherwise know existed.

## The real question

The question isn't whether wallet notifications are "too complicated." It's whether we trust citizens with the information they need to protect themselves. The car dashboard doesn't hide fault codes because drivers might find them confusing — it layers the information so that everyone gets what they need, from the casual driver to the professional mechanic.

Regulators and issuers have a unique opportunity here. They hold the domain expertise to author clear, contextual warnings. CEN/TS 18297 gives them the framework to deliver that expertise to the citizen at exactly the moment it matters. The alternative — generic, unexplained approval buttons — isn't simpler. It's just less transparent.

If you're a wallet provider, regulator, or credential issuer — consider becoming active in CEN TC224 WG20 or contacting your national representative. This is where the standard is being shaped. And if you need help understanding how CEN/TS 18297 applies to your wallet implementation, [get in touch](/contact/).
