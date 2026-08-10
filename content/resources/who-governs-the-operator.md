---
title: "Who Governs the Agent Operator?"
date: 2026-08-10
description: "Your AI policy covers the decision to use AI — register, declare, get approval. Nothing covers what happens six weeks later. Three gaps in the operator layer, and why per-project instruction files do not close them."
tags: ["AI Governance", "ISMS", "ISO 27001", "ISO 42001", "EU AI Act", "Agent Governance"]
keywords: ["AI Governance", "ISO 27001", "ISO 42001", "EU AI Act", "ISMS", "Agent Governance", "Operator"]
author: "Jan Lindquist"
summary: "Agent governance is maturing fast — budgets, allowlists, custodians, sign-off. The human directing those agents has none of it. Three gaps keep coming up: no guidance on how many pieces of AI-assisted work one person can hold, access decided in seconds mid-task with the approved scope six weeks behind them, and initiatives that no approval process ever declares finished. All three come back to one question — where the context between AI sessions actually lives — and per-project instruction files do not answer it."
cover:
  image: "images/cover-who-governs-operator.jpg"
  alt: "The operator's chair — a blue office chair at a desk with a keyboard, currently occupied by a cat"
  caption: "The operator's chair. Currently held by Nugget, the only member of the lab with no governance framework whatsoever."
  relative: false
---

Your AI policy probably covers the decision to use AI. Register the intention. Declare what data will be shared. Identify the risks. Wait for management approval. Mine does, and it is a good policy — that gate has caught things.

What it does not cover is what happens on an ordinary working day six weeks after approval.

Approval is a gate. It fires once, before the work begins, and everything it evaluates is a prediction: the data you expect to share, the risks you can foresee, the one use you had in mind. Then the work starts. The person who filed that registration now has six pieces of AI-assisted work open at once instead of the one they described. They are pasting material into their fortieth session that nobody imagined during the first. They are carrying four initiatives that no approval process will ever declare finished. The agents in that setup have budgets, allowlists and sign-off. The operator has a form they filled in six weeks ago.

In an [earlier post](/resources/agent-governance-isms-different-costume/) I argued that agent governance is ISMS in a different costume, drawn from running a small fleet of agents on a machine on my desk. The fleet has budgets, allowlists, custodians with interrupt authority. It behaves. The gap I keep finding since is one layer up, and it doesn't require a lab to have — if your organisation's AI adoption is a dozen people with a chat tab open, you have it already.

Three gaps come up in nearly every conversation. Each looks like a personal failing. None of them is.

**Concurrency.** An agent runs one task with a definition of done. The operator runs six pieces of work at once and has been given no guidance whatsoever on how many is too many, how to keep hold of them, or how to hand one over to somebody else. We would never deploy a system with unbounded parallelism and no queue discipline. We do it to people daily and call the result busyness. Ask anyone on your team how many pieces of AI-assisted work they have open this week. The number will be higher than they expect and higher than they will admit.

**Access decided in the moment.** For agents we enumerate permissions in advance, in a file, and we can audit it. For people, access was declared once at registration and is decided ever after at the point of use: whether to paste that document into a session, whether this material may go to that model, whether the answer that came back can be forwarded on. Those are real access-control decisions, made in seconds, by someone mid-task, with the approved scope six weeks behind them and no record of the divergence. That is not carelessness. That is a control that was issued once and never renewed. The EU AI Act's human oversight expectations assume the human has been equipped to exercise it; equipping them is the part that gets skipped.

**Initiatives that never conclude.** This is the one nobody logs, and the one no approval process touches — registrations open a piece of work, nothing closes it. AI has made an enormous number of things worth attempting that were not worth attempting two years ago — a market you can now credibly research yourself, a prototype you can now build in an evening, a subject you can now learn properly. So people start them, and starting is now cheap. Nothing declares them finished, so they don't finish. They fade, resurface at the worst moment, and quietly occupy the operator's attention for months. A backlog you can see is a plan. A backlog nobody has written down is a tax on judgement, and it compounds.

None of the three is exotic. Concurrency limits, access that is reviewed rather than assumed, and a definition of done are the most ordinary controls in the discipline. We have simply been applying them to the machines, and to the moment of approval, and nowhere in between.

## Where does the context actually live?

All three come back to one question: where does the context between your AI sessions actually live? There are only a handful of answers, and they are not equally priced.

| Where the context lives | What it costs the operator | What it covers |
|---|---|---|
| **1.** Re-explained each session | The same briefing, paid again every time | Only what was retyped this morning |
| **2.** In the operator's head | Nothing until they are ill, away, or busy | Nothing anyone else can pick up |
| **3.** In one session kept open for weeks | Fragile: one lost window and it is gone | Everything, until it isn't |
| **4.** In per-project instruction files | Kept current per project, and only there | One project, from the agent's side |
| **5.** In one record across all the work | The discipline of keeping it current | Everything the operator is carrying |

Two rows deserve a note.

Row 3 is the quiet favourite: never close the session, and the context never has to be rebuilt. It works, until the window is lost or the thread grows too long to steer — and while it lasts it is invisible to everyone else in the organisation.

Row 4 is where most people who take this seriously already sit, and it is worth being precise about why it is not the answer. Instruction files — the ones every agent tool now expects you to keep at the root of a project — are genuinely good practice. But they are written for the agent, scoped to one project, and they say nothing about the other five things you are carrying this week. The format question is settled: everybody has text files. The scope question is not. You cannot count what is open, decide access before you are mid-task, or declare an initiative finished from inside a single project's instruction file, because none of those judgements is about one project.

There is some evidence for the narrower point too. Researchers at York University and the University of Calgary [worked through 1.1 million Reddit posts](https://arxiv.org/abs/2607.26390) about LLM-native IDEs and built a taxonomy of what developers actually reported going wrong, [covered by The Register](https://www.theregister.com/ai-and-ml/2026/08/08/devs-to-anthropic-openai-cursor-and-friends-make-security-and-privacy-the-default/5285107) earlier this month. In 16.5 percent of the security-related reports the tool ignored user instructions, allowlists, permission settings or `.ignore` files, and the authors conclude that most of the problems come from system-level design choices rather than from the models. Their sample is self-reported and skewed toward bad days, and it covers coding tools rather than knowledge work generally — but the direction is clear enough. The instruction file is not only narrow in scope. It is not always honoured.

What row 5 asks for is duller and rarer: one record of the work itself — commitments, decisions, what is open and what is closed — spanning every area, that happens to be readable by an agent rather than written for one. Tiago Forte's *Building a Second Brain* makes the case that structured capture is what lets ideas compound rather than merely accumulate; the practical addition now is that the same structure, kept where a machine can read it, is the difference between an agent re-briefed from scratch each time and one that resumes an initiative where it was left. The operator starts and stops the work; the agent runs the stretches in between.

The separation drawn on top is what makes it a bridge rather than a shared folder: which material an agent may read, where its output lands, and what is marked as the operator's own decision rather than a model's. Set that out and the audit trail falls out as a by-product.

## Which row are you in?

I have my own view of which row most people are in. It comes from my own week and from a lab that is not representative of anybody's organisation, so I have put it to a poll on LinkedIn rather than answering it here. It doubles as an audit: ask your team before you vote. I am most interested in the people who have solved it — how you keep instructions and context straight across many parallel sessions is the part nobody has written down properly yet.

If your honest answer is one of the first four rows, you are in ordinary company — that is where most organisations are, including mine until fairly recently. Those rows are what the next posts in this series are about: what a concurrency limit looks like when the resource is a person, how access gets reviewed rather than assumed once the approved scope has drifted, and what a definition of done means for an initiative nobody owns. Each of them lands on ground an ISMS practitioner already stands on — the capacity, access control and monitoring clauses of ISO 27001, and the operational obligations in ISO/IEC 42001. The mapping is the interesting part, and it needs a post of its own rather than a paragraph here.

## Where that leaves the operator

The agents, meanwhile, are fine. They have budgets, permissions, and someone watching. It is the person at the top of the org chart — the one with a job, a household, something voluntary, and four open explorations — who is running without instrumentation.

Same discipline. Different chair.

---

*The study referenced above is Akhond, Mamun, Uddin and Wang, ["Impossible to hide secret …": Uncovering Security and Privacy Issues in LLM-native IDEs](https://arxiv.org/abs/2607.26390), a preprint accepted at ASE 2026, reported by [The Register](https://www.theregister.com/ai-and-ml/2026/08/08/devs-to-anthropic-openai-cursor-and-friends-make-security-and-privacy-the-default/5285107) on 8 August 2026.*
