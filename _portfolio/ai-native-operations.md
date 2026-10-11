---
title: "Fewer Meetings, No New Layer: Running a 50-Person Startup on a Shared AI Memory"
excerpt: "Designed, built and measured an AI operating layer for a ten-year-old software company across three countries: 20% fewer meeting minutes, two hires avoided, for 10,000 SEK a month.<br/><img src='/assets/portfolio-img/ai-native-ops/dashboard.svg'>"
collection: portfolio
---

- **The company:** a 50-person energy-software startup, ten years old, with teams in three countries.
- **My role:** I designed it, built it with our engineering managers and two super users, led the rollout, and designed how we would know it worked.
- **The result:** 20% fewer meeting minutes, a sales assistant and a Ruby developer we did not need to hire, and an AI bill of 10,000 SEK a month.
- **The idea in one line:** we did not remove the org chart. We changed what has to travel up it.

## Why org charts slow companies down

Every company with more than a handful of people builds an org chart, and every org chart creates the same two problems. Decisions wait in queues for the one person allowed to make them, and teams drift into silos because information only moves along the reporting lines.

Nobody designs it that way on purpose. A person can only hold and process so much information, so organizations break the work into layers: each layer filters what it hears and passes a summary up. Researchers described this trade-off in the 1970s and framed organization design as matching the information a company has to handle to the capacity its people have to handle it (Galbraith, 1974).

Fifty years later it still holds. I saw it first-hand at this company. A customer detail agreed in a meeting last spring lived in one person's notes. Ten years of Confluence pages had no owner and no structure, so finding last year's decision meant booking a meeting with whoever might remember it. And with leaders spread across three countries, a simple question could wait a day for the right time zone.

## The bet

If AI can collect, store and find information faster than any person, then most questions no longer need to climb the ladder. They can be answered where they come up, and only the exceptions need a manager.

There is evidence for that bet. A study of firms in the US and seven European countries found that tools which make information easier to get push decisions down to the people doing the work (Bloom et al., 2014). And in an experiment with 776 professionals at Procter & Gamble, individuals working with AI performed as well as teams working without it, and the usual gap between technical and commercial thinking narrowed (Dell'Acqua et al., 2025). That is what we were betting on: fewer hand-offs, and fewer walls between teams.

![Before: questions climb through layers and wait. After: a shared memory answers most questions where they arise, and only exceptions reach a leader, already summarized and ranked](/assets/portfolio-img/ai-native-ops/information-flow.svg)

## What we built

Four building blocks, all on Claude, connected to the tools the company already used.

| Building block | What it does | Where a person stays in charge |
|---|---|---|
| Meeting memory | Every meeting transcript goes into HubSpot, so customer context lives in one place instead of in someone's notebook | People decide what becomes a task |
| Leaders' stand-ins in Slack | While a leader is away, an agent answers staff questions from that leader's own knowledge base. What it cannot answer, it summarizes and ranks by urgency for the leader | Anything the agent cannot answer goes to the leader |
| Customer meeting to plan | A transcript becomes requirements, then Jira tasks and a draft change to the Confluence page it affects | A person approves high-stakes changes before they reach Confluence, and assigns the work |
| Permission lines | High-stakes work, such as the pricing model, stays out of the AI's reach by design | The whole task stays human |

The customer-meeting workflow is the one I would point to first. The service delivery team built it with me. The sales team then adopted it for their own customer meetings. One team's workflow became another team's habit, which is the opposite of a silo.

![Customer meeting to plan: transcript, requirements, Jira tasks and a Confluence draft, with a human approval gate for high-stakes changes](/assets/portfolio-img/ai-native-ops/meeting-to-plan.svg)

## The hard parts, and what we did about them

**A ten-year-old Confluence nobody owned.** The obvious fix was a clean-up project, and nobody had time for one. We did two things instead. Claude searched the mess as it was, so people could find the right page from years back without anyone tidying it first. And every new change to Confluence went through the approval gate, so the mess stopped growing. We fixed the past for reading and the future for writing, and skipped the clean-up project entirely.

**Deciding what not to hand over.** Giving the AI everything is easy, and trusting the results afterwards is hard. We drew the line by stakes, not by task type. Routine retrieval and drafting went to the AI. Changes to the single source of truth needed a person's approval. Pricing and other high-stakes work stayed fully human, and the permission settings enforced that rather than relying on people to remember.

**Leaders as the bottleneck.** With leadership across three countries, the queue for their attention was the slowest part of the company. The leadership team set up stand-ins that answered from their own knowledge, and passed on the rest with a summary and an urgency ranking. Leaders came back to a ranked list instead of a full inbox.

**Getting people to use it.** Tools announced by email rarely get used. Two super users built the workflows with me, so the first versions fitted real work rather than a demo. We also held lunch sessions with Claude, where people shared what they had learned. Sales adopted the customer-meeting workflow after service delivery had proved it.

## How we knew it worked

I designed the measurement before the rollout, combining numbers from the tools with interviews.

| What we looked at | How | Result |
|---|---|---|
| Time spent in meetings | Meeting minutes before and after | 20% fewer minutes |
| Roles we planned to hire | Hiring plan before and after | A sales assistant and a Ruby developer no longer needed, because the workflows covered the work in between |
| Running cost | Monthly invoice | 10,000 SEK a month for Claude, a fraction of one salary |
| Spread across teams | Which teams used the workflow | Two: built in service delivery, adopted by sales |
| What people experienced | Interviews with staff and leaders | See below |

![Pilot readout: 20% fewer meeting minutes, two hires avoided, 10,000 SEK a month, two teams on one workflow, and what staff said](/assets/portfolio-img/ai-native-ops/dashboard.svg)

In the interviews, the strongest reaction was to search. People could quickly find the right page in ten years of badly structured Confluence, and they no longer needed a meeting to find out what had been said and noted the year before.

They also raised a worry I had not planned for: running out of tokens before the monthly limit reset. Once a tool becomes the way you find things, losing access mid-month feels like losing your memory. That is a new kind of dependency, and it changes how you budget for AI. Usage limits stop being an IT setting and become part of how the work is designed.

## What I would tell another founder

Start with the information that already exists and is hard to find, not with the org chart. Put a person at every point where a mistake is costly, and enforce it with permissions. Let one team prove a workflow before asking anyone else to adopt it. And budget for the moment your team depends on the tool, because it comes sooner than you think.

*This way of working started with how I organize my own work. I write about that on the [My one-person org chart](/blog/2026/my-one-person-org-chart/).*

## References

Bloom, N., Garicano, L., Sadun, R., & Van Reenen, J. (2014). The distinct effects of information technology and communication technology on firm organization. *Management Science, 60*(12), 2859–2885.

Dell'Acqua, F., Ayoubi, C., Lifshitz, H., Sadun, R., Mollick, E., Mollick, L., Han, Y., Goldman, J., Nair, H., Taub, S., & Lakhani, K. (2025). *The cybernetic teammate: A field experiment on generative AI reshaping teamwork and expertise* (NBER Working Paper 33641).

Galbraith, J. R. (1974). Organization design: An information processing view. *Interfaces, 4*(3), 28–36.
