---
title: "Where the EUDI Wallet Certification Scheme Stops Short — and Three Changes We Asked For"
date: 2026-05-07
description: "ENISA's draft candidate EUDI Wallet certification scheme is mature in structure but leaves the wallet-held decision layer distributed across multiple sections rather than named and sequenced as one evaluable surface. Three focused additions — reference CEN/TS 18297, add a WACE clause, and add CTRL-CNDXS — consolidate that layer without rewriting the scheme."
tags: ["EUDI Wallet", "eIDAS 2.0", "ENISA", "CEN Standards", "Cybersecurity Certification", "Access Control"]
author: "Jan Lindquist"
summary: "ENISA's draft EUDI Wallet certification scheme handles the provider layer cleanly, but the wallet-held decision layer — where eIDAS 2.0 Article 5a user rights actually operate — sits distributed across sections of the Security Requirements rather than named and sequenced as one evaluable surface. This post explains how the scheme already touches the decision layer in pieces, shows the layered architecture, and sets out the three focused asks we submitted before the 30 April 2026 deadline — additions that consolidate the layer without expanding the scheme's scope."
cover:
  image: "images/cover-eudiw-decision-layer.svg"
  alt: "Stacked transparent glass layers, representing the four-layer assurance stack of the EUDI wallet"
  relative: false
---

*Jan Lindquist, Lead Editor CEN TC224 WG20 — CEN/TS 18297 Access Control for European Digital Identity Wallets*

*Consultation deadline: 30 April 2026 (closed)*

On 3 April 2026, ENISA opened a public review of its **draft candidate EU Digital Identity Wallet cybersecurity certification scheme** — the mechanism by which Conformity Assessment Bodies (CABs) will eventually verify that a wallet does what the eIDAS 2.0 regulation and its Implementing Acts require. The review closed on 30 April 2026. This post sets out the position WG20 contributors submitted during that window.

It is a continuation of [*What the Draft Implementing Acts Get Wrong About Wallet Access Control*](/resources/draft-implementing-acts-wallet-access-control/). The core argument in that March analysis was that the regulations define what the wallet must do, but do not always ensure the information needed to do it is available at the point of disclosure. The certification scheme is the other side of that same coin. It tells CABs how to check that a wallet does what the regulations require — and it, too, stops short of consolidating the layer where the user actually sees the wallet at work.

This is not a criticism of ENISA's approach. Structurally, the scheme is sound. Its design decisions — integrating with national certification systems, inheriting ETSI EN 319 401 for the provider-policy baseline, defining critical evaluation activities — are the right ones. What it needs is three focused additions that consolidate what is already distributed at the decision layer into something a CAB can evaluate end-to-end — all the way to the moment the user sees a request.

## The layered picture the scheme already relies on

ENISA's scheme is organised around a stack of evaluation layers, each producing evidence that composes upward. The scheme already names three of them explicitly, and that layering is how CABs are expected to reuse prior conformity assessment results rather than repeat them.

![The EUDI wallet assurance stack — four stacked layers of evaluation evidence, with the decision layer shown as a proposed reference](images/eudiw-assurance-stack.svg)

From the bottom up: the cryptographic protection layer is the WSCA Protection Profile under CEN TC 224 WG17, evaluated at AVA_VAN.5 under EUCC. Above it sits the instance-hardening layer — the wallet-instance Protection Profile currently under development, with OWASP MASVS for mobile-app hardening. Above that is the PID on-boarding layer, governed by CEN TS 18098.

And above all of those sits the layer at which a Relying Party's request is actually evaluated, a user decision is formed, and data either leaves the wallet or doesn't. This is the **decision layer**. It is the layer the user experiences. The scheme already touches it through requirements distributed across §8.2–8.6 of the Security Requirements — but it does not yet name it, organise those requirements as a sequence, or give a CAB a deterministic way to test the decision itself.

## Where the layer needs consolidating — and where it doesn't

The provider side of the certification is well covered. The Security Requirements document inherits ETSI EN 319 401 for the trust-service-provider policy baseline. That is the right choice: it reuses an established standard, it carries existing supervisory practice, and it means CABs that already certify Trust Services won't need duplicate accreditation. Nothing in this post argues for changing that inheritance.

The consolidation is specifically needed at the wallet-held decision layer. At that layer the SecReq has no consolidated clause. The requirements that ought to belong there are distributed across sections 8.2 through 8.6, but they are not organised as a deterministic evaluation sequence, they do not identify wallet-held policy metadata as the authoritative source of the decision, and they do not give a CAB a method to test the decision itself. The scheme also uses the same label — "access control" — for both senses (provider-side in §7.4, wallet-held in the emerging WG20 vocabulary), which makes the missing consolidation easy to miss.

![Scheme coverage — what is consolidated at the provider layer, what is distributed at the wallet-held decision layer, and the three proposed additions that consolidate it](images/eudiw-gap-mapping.svg)

This matters because the decision layer is where eIDAS 2.0 Article 5a user rights, GDPR Article 13 transparency at the point of collection, and six of the Annex I risks in Regulation (EU) 2024/2981 are actually operationalised. A Level-of-Assurance "high" certificate issued against a layer that exists only as scattered requirements — rather than a named, sequenced surface — is verifying a claim CABs cannot deterministically test at exactly the surface where the user encounters it.

## Three focused changes

Three focused changes consolidate the decision layer. All three sit inside the scheme's existing structure rather than extending it.

![Wallet Access Control Flow as a CAB Evaluation View — three sequential lanes (Wallet Unit Processing, Wallet User Decision, Wallet Response) mapping CEN/TS 18297 §6.2.2.6 steps onto ENISA Scheme §X.2 evaluation activities, with gap indicators marking where the proposed controls land](images/eudiw-cab-flow.svg)

**1. Reference CEN/TS 18297 in Scheme §X.1.4.** The scheme already anticipates WG20 work in §X.1.4, on the condition that the additional standard includes a mapping to the EUDIW criteria defined in the scheme. CEN/TS 18297 meets that condition: its §7 control set is organised directly around the Scheme §X.2 evaluation-activity taxonomy (conformance testing, specific testing, interactive testing, inspection, audit). Naming the standard — alongside the CEN TS 18098 reference the scheme already carries — activates the decision layer as an evaluable baseline.

**2. Add a Security Requirements clause for the Wallet Access Control Engine.** The engine — *WACE* — evaluates an RP request in three sequential steps: Wallet Unit Processing, Wallet User Decision, Wallet Response. Each step consists of named controls: CTRL-MTDMG for the metadata lifecycle that feeds every downstream decision, CTRL-VALID for validation, CTRL-POLCY for policy application, CTRL-RPCHK for Relying-Party checks, and so on. Consolidating these in a single clause gives CABs a deterministic sequence to test — one the scheme's existing activity types already cover. No new evaluation methodology is required.

**3. Add CTRL-CNDXS — evaluate Relying-Party declared conditions of use.** At the moment of attribute disclosure, the wallet is the point of collection for the RP's processing of personal data. GDPR Articles 13(1)(c), 13(1)(e), 13(1)(f), and Article 9 all require specific information to reach the data subject there. CTRL-CNDXS is the mechanism by which the wallet evaluates the RP's declared conditions against wallet-held metadata and presents the resulting notice. It has no counterpart in the current Security Requirements. It also depends on four ISO/IEC 27560 fields that are missing from the draft RP registration schema — a gap already identified in the [WG20 February 2026 response](/resources/draft-implementing-acts-wallet-access-control/) on the Implementing Acts.

## Why this works without expanding the scheme

Every CTRL- in CEN/TS 18297 maps to at least one of the six Annex I risks that the Implementing Regulation already enumerates, and to at least one of the five §X.2 activity types the scheme already defines. Referencing CEN/TS 18297 extends mitigation coverage for the majority of Annex I risks at incremental evaluation cost, not transformative cost. It activates an existing methodology against a well-defined control set — rather than inventing anything new.

The scheme is mature structurally. The principles are right. The decision layer is already there in pieces — these three focused additions name it, sequence it, and give a CAB a deterministic way to evaluate it end-to-end, including the moment when a user sees a request and decides whether data should leave.

## What happens next

The public-review window closed on 30 April 2026. ENISA now consolidates submissions before the scheme moves through the next stage of adoption under the Cybersecurity Act framework. The three changes described above are not framework rewrites — they are insertions inside structures the scheme already defines, and they remain available to ENISA between now and the formal adoption text.

If the decision layer belongs in the scheme as a named, consolidated surface, the case for putting it there does not expire with the consultation deadline. Wallet providers, CABs, member-state scheme owners, Relying Parties, and standards bodies still have a role to play as the scheme is finalised — and as national certification systems begin to interpret it.

If you need help understanding how CEN/TS 18297 maps to the ENISA scheme, or how the decision layer affects your wallet implementation or CAB evaluation plan, [get in touch](/contact/).
