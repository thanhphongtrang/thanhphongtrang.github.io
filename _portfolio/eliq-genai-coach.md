---
title: "Building a GenAI Coach for Energy Retailers, and Learning What Its Numbers Actually Meant"
excerpt: "Pitched, defined, built and priced a GenAI energy coach inside an existing energy-insights platform, now part of the core product at three utility clients, and traced the numbers behind it back to their sources.<br/><img src='/assets/portfolio-img/energy-coach/coach-chat.png'>"
collection: portfolio
---

![The energy coach mid-conversation, citing the customer's own figures with a caveat about uncertain hourly values](/assets/portfolio-img/energy-coach/coach-chat.png)
*The coach mid-conversation, citing figures and flagging which hourly values are uncertain. Dummy "Demo" account, no client branding, no personal data.*

- **Role:** AI Product Builder, Eliq
- **When:** May 2026
- **What shipped:** a GenAI energy coach that explains a customer's bill as a conversation, grounded in their own consumption data. Merged into the platform's main product line and live at three utility clients.
- **What came next:** a 500-household pilot with a utility client, designed as a randomized trial across six customer segments.
- **The short version:** my pitch became my role. I proposed a generative AI layer on top of the platform, was given the job of building it, and took it from an open direction to part of the core product, with every answer it gives grounded in the customer's own data.

<p class="stack">Azure OpenAI · Model Context Protocol (MCP) · .NET · Lovable · Claude</p>

## The gap nobody owned

Eliq sells an energy-insights platform to utilities and energy retailers. It turns smart-meter data into something a household can read. When I arrived, the platform already had a usage tab that broke a customer's consumption down accurately, hour by hour. Yet calls about "why is my bill so high" had not moved.

An accurate chart in a tab the customer has to find, open and interpret alone does not turn into understanding. It certainly does not at the moment a shock bill lands and the customer is anxious and short on patience. Data engineering owned correctness. Design owned the screens. The space between an accurate number and a customer who trusts it was open.

I pitched a generative AI layer on top of the insights we had already shipped: something that could answer "why is my bill high" as a conversation, grounded in data we had already computed. That pitch became my role, and the coach described below.

The problem is bigger than one company. Utilities carry a high cost to serve and thin support margins, and a bill shock is one of the most reliable ways to turn an accurate insight into an expensive call or a lost customer. Any company adding AI to an analytics-heavy product meets the same gap.

## One product, staged three ways

Two directions were live when I started: a chat-first "ask anything" coach, and a push to bring insights to customers the platform did not yet have a full profile for. I framed discovery with a jobs-to-be-done lens on what the customer was trying to do when they opened a bill, and an Opportunity Solution Tree linking that job to the solution bets on the table. That gave the decision a paper trail rather than a gut call.

The decision was to collapse two bets into one. I defined the minimum testable product as a GenAI energy coach on the platform's existing consumption backend, shipped first as a monthly report that opens as a conversation with one predefined question, and widened toward open chat as it earned trust. Delivery ran in three phases of that one product:

1. An internal alpha scoped to a single job: explaining this month's bill.
2. A client-employee alpha that added notifications and comparisons.
3. Full chat, designed as a 500-household pilot with a utility client.

Each phase carried forward what the last one proved instead of restarting the trust argument. The first phase was locked to a single surface: one relevance-ranked summary card, no charts, no source-verification screen. That kept the team from building five things at once against an unproven premise.

![The first surface: one spotlight card, an energy-balance panel and a daily consumption chart](/assets/portfolio-img/energy-coach/coach-spotlight.png)
*The locked-down first surface. Live capture on a seeded "Demo" account, not a recreation.*

## Testing the premise before a pilot could

Underneath everything sat a hypothesis: that a language model, grounded in a customer's own data, could explain their energy use accurately enough for a utility to let real customers talk to it. I wanted to find out cheaply and early, with a method that could actually fail.

So I designed and ran an internal testathon. About seventeen colleagues role-played customer personas and worked through a graded set of realistic questions, and every answer was scored against what the platform's own data said was true, not against what sounded plausible. It found real failures fast. One household with no EV was flagged as an EV owner with more confidence than a household that had one, because the detector picked up a coincidental load pattern. Elsewhere, numbers quietly failed to reconcile within the same conversation. Five classes of failure went on a must-fix list, and all five were closed before the next round.

![Evaluation method: fixed personas and a graded question set feed a scoring step, with a separate adversarial lane](/assets/portfolio-img/energy-coach/eval-framework.svg)
*The method, generalized: fixed personas, a graded question set, scoring for groundedness and risk, and an adversarial lane, producing a baseline and a ranked fix list.*

## Building it

I wrote code as well as directing it. Two pieces are worth describing.

**An architecture argument.** The coach's first version made one model call per turn, carrying one long instruction file that tried to do seven jobs at once: detect intent, detect language, read tone, choose data, apply safety rules, write the reply and pick a widget. That shape has a ceiling. Its failures are routing problems dressed up as prompt problems, and no prompt tuning fixes them. With the CTO, I set the direction of narrowing what the model decides and moving the deterministic parts into typed tools over the Model Context Protocol. A turn becomes "route to the right tool, then explain what it returned". The first phase, wrapping the coach's analysis logic as separately callable tools, went into code review.

![Left: one model call doing seven jobs. Right: a scope check, a narrower model call, and typed tools](/assets/portfolio-img/energy-coach/architecture-shift.svg)

**A pricing simulator.** I could not get a straight answer to "what does this cost us, and what is it worth to a client" out of a spreadsheet only one person could safely edit. So I built a simulator in Lovable, with Claude connected over MCP for the parts worth reasoning through. I built it in phases. First came the arithmetic, ported cell for cell from the spreadsheet and checked against it automatically so it could not drift. Then came a second pricing shape on the same inputs. Last came a live count of how many inputs were still assumptions rather than sourced numbers. That counter is the part I am proudest of. It turned "trust me, it's roughly right" into a number that shrank every time I replaced a guess with a citation. Using the tool myself also surfaced real bugs, including a display bug that silently turned every percentage into a hundredth of itself.

## What I trusted less once I checked it

This is the part of the work I would point to first.

A commercial colleague asked whether there were results from the summer's testing worth sharing with a prospective client. I went looking for the source of a headline accuracy figure that had circulated internally for weeks. It traced back to a single Slack message, and part of it had been softened by its own author two hours after posting, in a follow-up nobody had reread. I flagged it before it reached anything external, at a moment when a press mention could have quoted it as measured fact. I am not naming the figure here. What matters is that nobody, me included at first, had gone back to the source before repeating it.

The second case was in my own work. My pricing model depended on one input: the share of a utility's customer contacts a coach could plausibly influence. It came through four rounds of my own review unchanged, because it was a hardcoded number with no entry in the place my model kept every input's source. When I finally checked it against the market-research slide it was meant to summarize, it did not hold. It merged two questions into one multiplier. The slide answered which contact themes a coach could help with, but nothing yet answered what share of all contacts the sample covered. I corrected it the same day in both live pricing documents, and it moved the value estimate by a meaningful multiple in the client's favor. Colleagues caught two more of my errors: a cost multiplier our own billing never tracked, and the engineering time missing from a cost line that counted only cloud inference. Both are now modelled as their own lines.

Two smaller checks, same habit. The instruction file everyone planned around was cited as about 6,000 tokens. When I opened it and counted, it was about 11,000, which nearly doubled the room for the planned rewrite. And when I told a colleague a compliance document already had sign-off, I went back to the document itself, found it did not, and corrected the record.

The lesson generalizes: a number's home matters more than the number. A constant with no source field, a claim nobody rereads after it is softened, a memory of a conversation instead of the document, a plan built on a citation instead of the primary source. Each fails silently until someone checks. Building that habit into myself and into the tools I built is the part of this work I stand behind hardest.

## Readiness as seven gates, not an average

The same instinct shaped how I defined "ready to launch". It is tempting to average a checklist: five items green, two open, mostly there. I argued for an AND across independent gates instead. A launch with an unsigned compliance sign-off is not 85% launchable. It is not launchable, however good the other six gates look.

![Readiness framework: seven independent gates, all of which must pass](/assets/portfolio-img/energy-coach/gate-framework.svg)
*A recreation of the framework, authored for this page. No live status or client details.*

## The commercial model

I built the case for two ways to charge: a per-customer price for utilities running the coach white-labelled in their own app, and a lighter per-account price for the coach exposed as callable tools. Both rested on cost measured from our own cloud bill for the traffic we were already running, set against what a client would otherwise spend building the same thing, plus a separately labelled estimate of reduced contact volume.

One thing I chose not to do is a better example of product judgment than anything I shipped. A plausible upsell case appeared: the coach noticing a customer's situation and suggesting a better-fitting contract. When I worked the funnel math, hitting a meaningful number meant assuming a share of an entire customer base would switch contracts because a chatbot suggested it, at a rate no one in the industry has published. With nothing to anchor it, I took it out of the headline case and kept it as a labelled upside, reduced to the two inputs that matter, until a pilot could measure it. I would rather under-claim a business case than dress a guess up as a finding.

## Where it landed

The coach is part of the platform's main product line and live at three utility clients. The next step, a full-chat pilot with a utility client, is designed as two randomized groups across six customer segments, read with difference-in-differences rather than a naive before-and-after.

![Pilot design: households stratified into six segments, randomized into a coached group and a control group](/assets/portfolio-img/energy-coach/pilot-design.svg)
*Eligible households stratified into six segments with equal quotas, randomized within each into a coached group and a control group.*
