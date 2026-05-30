---
title: "Agent Governance Is ISMS in a Different Costume"
date: 2026-05-29
description: "Five lessons from running an on-prem agent lab — and how each one maps onto ISO 27001, ISO/IEC 42001 and EU AI Act controls an ISMS practitioner already knows. If you run a serious 27001 or 22301 programme, you are not behind on AI governance."
tags: ["AI Governance", "ISO 27001", "ISO 42001", "EU AI Act", "ISMS"]
keywords: ["AI Governance", "ISO 27001", "ISO 42001", "EU AI Act", "ISMS", "Agent Governance"]
author: "Jan Lindquist"
summary: "Somebody on your team has started using AI agents, the governance question just landed in your lap, and the auditor will ask in nine months. The reflex is to hire an 'AI governance consultancy.' I want to argue the opposite: if you already run a serious ISO 27001 or 22301 programme, you hold the unfair advantage. Five lessons from running an on-prem agent lab, each mapped onto controls you already operate."
cover:
  image: "images/cover-erik-agent-governance.jpg"
  alt: "Erik — a Mac Mini on a wooden desk, with a folk-art mug on a coaster to the right and a pink bonsai by the window on the left"
  caption: "The lab: Erik — on-prem, segregated, and patient with late nights."
  relative: false
---

I have a Mac Mini on my desk I named Erik.

He runs OpenClaw — the local agent runtime I use as a reference implementation — entirely on-prem and segregated from the public internet. Over the last four months he's become host to what is, at this point, a small organisation of agents — each with its own persona and its own job. Scotty handles devops. The others have their own roles. It has involved more late nights than I'd care to admit. It has also been the most useful thing I've done for understanding agent governance, because Erik makes every control surface visible end-to-end.

![Agent organisation chart — Jan (Operator) sits at the centre with Erik (Mac Mini, COO) just to the right working in parallel; five governance officers below above five specialist teams, each officer aligned to the team they oversee (Architect over Rotary, Chief of Staff over Customer Services, Strategy over Knowledge, Product over Development, Security top-right over Infrastructure)](/images/erik-agent-org-chart.svg)

Before Erik arrived in early 2026, I'd spent the previous year using ChatGPT and then Claude for everyday work — drafting emails, developing strategy, some vibe coding. The conclusion that surfaced through both — the year of practical use and the four months of late nights with Erik — is the same: an LLM is just another tool. As the operator you have to keep a short leash on it, or the output drifts.

I've watched a pattern repeat in conversations with Nordic CISOs and ISMS leads over the same period: somebody on their team has started using AI agents — for ticket triage, for draft documentation, for first-pass code review — and the governance question lands in their lap with no warning. The agent is already deployed. The risk register has nothing on it. The auditor is going to ask about it in nine months.

The reflex move is to look for an "AI governance consultancy." I want to argue the opposite reflex is healthier. If you already run a serious 27001 or 22301 programme, you have most of what you need. You're not behind. You're holding the unfair advantage.

Five things keep coming back from running Erik's little organisation, and all five map onto controls any ISMS practitioner already knows. Agent governance, it turns out, needs to be built into the seams of the architecture — and the seams are familiar.

**1. Token runaway is a control failure, not a price failure.** The first time an agent runs in a loop, the bill arrives. The reflex is to treat it as a budgeting problem and put a credit-card cap on it. That's wrong. A runaway is a system that lost containment. Budget per role — not per prompt — at the harness layer, alarm on overrun, and treat each event as a logged incident. The ISMS reader already recognises this: it's ISO 27001 A.8.6 capacity management and ISO/IEC 42001's resource-handling obligations, written for systems that bill in tokens instead of CPU minutes.

**2. Model selection is a policy decision, not a procurement one.** Every role in a fleet has its own job. Routing and triage need small, fast, cheap models; judgement and synthesis need the larger ones. Document *why* each role uses which model — not in a contract negotiation, but as a control. When the model market shifts again in eight months (and it will), the policy survives the rotation. This is ISO 27001 A.8.27 secure system architecture, applied to a stack where the architecture is the model graph.

**3. Agents must not grade themselves.** The well-documented bias in self-grading LLMs is the AI version of "developer signs off own code." The fix is older than AI: separate the generator from the evaluator. In practice this means one agent does the work, a second agent — tuned to be skeptical — reviews it, and a human signs off the final result. The standards mapping is direct: ISO 27001 A.5.3 segregation of duties, EU AI Act Article 14 human oversight, ISO/IEC 42001 on the use of AI systems. There is no clever prompt that substitutes for this.

**4. Boundaries are the spec, not the prompt.** The most common failure I see in early agent setups is treating the system prompt as the security boundary. It isn't. The actual control surface is the filesystem allowlist, the tool permission list, the channel routing rules, the escalation queues. Prompts are guidance; allowlists are control. If your agent's permissions are not enumerated in a file you can audit, you do not have access control — you have a hopeful suggestion. This is ISO 27001 A.5.15 and it is not new.

**5. Every fleet needs two custodians.** A security observer and an operations agent — both implemented as agents themselves, both with the authority to interrupt, not just to log. Without them the fleet audits itself, which is no audit at all. This is the part most lab setups quietly skip. It maps onto ISO 27001 A.5.24 / A.8.16 monitoring and incident management and onto ISO 22301's incident-response structure. The same controls. New venue.

![Five learnings, mapped to existing ISO 27001, ISO/IEC 42001 and EU AI Act controls](/images/learnings-controls-mapping.svg)

None of this is a prediction about where AI is going. I don't know where it's going. The honest position is that the discipline of running it well is older than the technology, and it lives in the standards practitioners have been working with for a decade.

A harness — whether it's OpenClaw (the local runtime I use), Cursor, Claude Code, or whatever you build internally — doesn't repair weak structure. If your change control is loose, an agent fleet will industrialise the looseness. The harness just makes it tidier to delegate work; it does not improve the operator's judgement. You are still the expert. Your job becomes deciding what is worth deciding, while delegating the rest with an audit trail.

That last point — the audit trail — is where this thread continues. Most ISMS programmes I see have one consistent weakness: evidence collection. It's not the policies. It's not the controls. It's the boring work of making sure the records, dated correctly, find their way into the right folder under the right ID. That's the next post in this series, and it's where agent governance and GRC stop being separate conversations.

If you're working through similar questions in your own organisation, I'd be interested to hear what you're seeing. Linaltec runs gap assessments against ISO/IEC 42001 and the EU AI Act high-risk obligations, mapped onto whatever ISMS you already have — fixed-price, a few weeks.
