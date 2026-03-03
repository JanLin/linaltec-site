---
title: "What the Draft Implementing Acts Get Wrong About Wallet Access Control"
date: 2026-03-03
description: "A systematic review of three draft Implementing Acts amending the EUDI Wallet technical framework, identifying critical gaps in GDPR transparency, credential issuer obligations, and the wallet's ability to inform users at the moment of disclosure."
tags: ["EUDI Wallet", "eIDAS 2.0", "CEN Standards", "GDPR", "Implementing Acts", "Access Control"]
author: "Jan Lindquist"
summary: "As Lead Editor of CEN/TS 18297, I reviewed the three draft Implementing Acts against the EUDI Wallet regulatory framework and submitted 17 comments to the European Commission consultation. The three critical findings share a common root: the regulations define what the wallet must do, but do not ensure the information needed to do it is available at the point of disclosure."
cover:
  image: "images/draft-ia-wallet-access-control.jpg"
  alt: "European Union flag"
  caption: "Photo by Eberhard Grossgasteiger on Pexels"
  relative: false
---

*Jan Lindquist, Lead Editor CEN TC224 WG20 — CEN/TS 18297 Access Control for European Digital Identity Wallets*

*Consultation deadline: 5 March 2026*

On 5 February 2026 the European Commission published three draft Implementing Acts amending the technical framework for the European Digital Identity Wallet. These regulations will govern how wallets authenticate Relying Parties, enforce disclosure policies, log transactions, and protect citizens' personal data at the moment of every attribute presentation.

As Lead Editor of CEN/TS 18297 — the European standard that specifies the Wallet Access Control Engine (WACE) — I conducted a systematic review of all three drafts against the existing regulatory framework: eIDAS2 Article 5a, the five existing Implementing Regulations, the Architecture and Reference Framework (ARF), and the relevant ETSI standards. The result is a formal consultation response containing 17 comments, each with specific proposed amendment text.

The three findings below share a common root. The regulations define what the wallet must do — inform the user, enforce access policies, present a transparency notice — but do not ensure the information needed to perform these functions is available at the point of disclosure. CEN/TS 18297 identifies these gaps because it specifies the deterministic evaluation sequence the wallet must execute at every transaction, and each missing field or broken reference is a step in that sequence that cannot be completed.

## 1. GDPR transparency is structurally impossible without lawful basis and data sensitivity fields

CEN/TS 18297 requires the wallet to present a Processing Information Notice to the user before any attribute is disclosed (REQ-7.3). This notice must include the information that GDPR Articles 13(1)(c) and 13(2)(a) require at the point of data collection — including the legal basis for processing and, where applicable, whether the data is special category under Article 9.

The draft amendment to IA 2025/848 (Relying Party registration) introduces useful new fields such as the supervisory authority contact and intermediary flag. But it omits two fields that are fundamental to GDPR compliance:

**lawful_basis** — Under which GDPR Article 6(1) ground does the Relying Party process the disclosed attributes? Consent, contract performance, public task, legitimate interests? The user is being asked to approve disclosure without knowing the answer. For special category data (Article 9), the RP must additionally declare an Article 9(2) basis. Our proposal uses a single unified enumeration covering both Article 6 and Article 9 values, avoiding unnecessary schema complexity while ensuring the complete legal basis chain is declared.

**data_sensitivity** — Does the request involve health data, biometric data, data revealing racial or ethnic origin, or any other Article 9 special category? This determination has two sides. The credential issuer must flag at issuance time whether an attestation contains Article 9 data — a health certificate issuer knows this, a disability status provider knows this. The Relying Party must separately declare in their registration that they intend to process special category data. Without both signals, the wallet cannot distinguish between a standard disclosure and one that requires explicit consent and enhanced safeguards.

An important nuance: Level of Assurance High (required for PID) does not make data "sensitive" in the GDPR sense. Authentication assurance governs identity proofing strength, not data category. Most PID fields — name, date of birth, address — are not Article 9. The data_sensitivity flag enables granular treatment of individual attributes rather than blanket classification of entire credential schemes.

## 2. No obligation exists for credential issuers to include an access control policy

Embedded Disclosure Policies (EDPs) are the core access control mechanism in the EUDI Wallet framework. They allow credential issuers to specify which Relying Parties may receive their attestations — for example, restricting a health certificate so that only authorised healthcare providers can request it. The wallet's access control engine evaluates this policy before the user is even asked to approve a disclosure.

The current IA 2024/2979 Annex III defines three EDP types: "no policy", "authorised relying parties only", and "specific root of trust". IA 2024/2979 Article 10 requires wallet providers to process these policies. ETSI is actively developing the technical encoding standards (ETSI TS 119 472-3) that will specify how EDPs are structured and carried in attestations. The standards work is progressing and the technical specifications are taking shape.

But there is a structural gap in the regulatory chain that no standard can fill. The EDP framework depends on three sequential steps:

1. The credential issuer embeds an EDP indicator in the attestation at issuance
2. The wallet unit stores the EDP locally
3. The WACE evaluates the EDP at presentation time before user approval

Steps two and three are addressed by IA 2024/2979. Step one — the issuer obligation — does not exist anywhere in the regulatory framework. No provision in IA 2025/1569 (the EAA Implementing Act), either in its existing text or in the draft amendment, requires EAA providers to include an EDP indicator in the attestations they issue.

This is not a technical oversight that standards can resolve — it is a missing legal obligation. A WACE encountering an attestation with no EDP indicator faces an impossible interpretation problem: does the absence mean the issuer deliberately chose "no restriction", or that the issuer was simply unaware of the requirement? These are categorically different situations with different security implications, and the wallet cannot distinguish between them. Even the "no policy" type — indicating that no access restriction applies — must be explicitly asserted by the issuer. Absence of a policy is not the same as a policy of no restriction.

The practical consequence is significant. As the EUDI Wallet ecosystem grows, thousands of EAA providers will issue credentials. Without an explicit obligation, some will include EDPs and some will not. Wallet providers will be forced to choose between rejecting attestations without EDPs (breaking interoperability) or accepting them without policy evaluation (breaking access control). Neither outcome is acceptable.

Our proposal: add an explicit issuer obligation to Article 4 of IA 2025/1569 requiring that every issued attestation includes an EDP indicator compliant with the EDP types defined in Annex III of IA 2024/2979. Where no access restriction is intended, the "no policy" type must be indicated. This closes the regulatory gap and ensures the access control framework can function as designed, regardless of whether the attestation issuer is a national health authority, a university, or a private sector provider.

## 3. The wallet's transparency notice cannot be populated

CEN/TS 18297 REQ-7.3 requires that before any attribute is disclosed the wallet presents the user with a Processing Information Notice whose content is derived from the ISO/IEC TS 27560:2023 Table 7 field set. This is not an optional feature — it is the mechanism through which the wallet fulfils the GDPR transparency obligation at the moment of data collection.

Six fields from ISO 27560 Table 7 that are directly required by GDPR transparency obligations are absent from the IA 2025/848 Relying Party registration schema:

**storage_location** — Where will the Relying Party store or process your disclosed data? Will it leave the EU? GDPR Article 13(1)(f) requires this information when data is transferred to a third country. The registration schema does not capture it.

**retention_period** — How long will the Relying Party keep your data after you disclose it? GDPR Article 13(2)(a) requires this information at the point of collection. There is a subtle but important confusion in the current framework: IA 2024/2979 Article 9(6) defines a retention period, but this governs how long the wallet keeps its own transaction log — not how long the Relying Party keeps the received data. These are categorically different obligations, and the RP-declared retention period for disclosed attributes does not exist in any IA.

**recipient_third_parties** — Who else will receive your data after the Relying Party processes it? IA 2025/848 Annex I points 14–15 describe intermediaries acting on behalf of the RP — entities in the processing chain. GDPR Article 13(1)(e) additionally requires disclosure of downstream recipients (other controllers or processors) to whom data will be transferred after processing. These are different from intermediaries and are not captured.

**geographic_restrictions** — Are there geographic restrictions on where the disclosed data may be used or processed? No provision of any applicable IA addresses this field.

**lawful_basis** and **data_sensitivity** — as detailed in section 1 above, the legal basis for processing and the special category indicator are absent from the registration schema.

If these fields are not registered by the Relying Party, they cannot appear in the RP access certificate, and the wallet cannot include them in the notice it presents to the user. The Processing Information Notice — which CEN/TS 18297 specifies as a mandatory step before disclosure — is structurally empty for six of its most important GDPR-mandated elements.

We have proposed all six fields as additions to IA 2025/848 Annex I and the corresponding Annex VI schema, and will submit the same proposal to ETSI TC ESI as liaison input for inclusion in the RP access certificate profile (ETSI TS 119 475), so that the fields are available to the wallet at presentation time without requiring a live registry query — essential for offline and low-connectivity wallet deployments.

## Download the full consultation response

The complete response contains 17 comments — 3 critical, 9 important, 3 minor, and 2 positive — each with a structured comment table identifying the specific provision, current text, issue, and proposed amendment.

The comments are submitted in a personal technical capacity as Lead Editor of CEN TC224 WG20. They are based on the regulatory mapping and access control analysis conducted under the WG20 mandate for CEN/TS 18297.

The public consultation on these three Implementing Acts is open until 5 March 2026. Stakeholders can submit responses through the Commission's Have Your Say portal.

If you need help understanding how these regulatory gaps affect your EUDI Wallet implementation, or how CEN/TS 18297 maps to the Implementing Acts, [get in touch](/contact/).
