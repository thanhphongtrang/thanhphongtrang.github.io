---
title: "My One-Person Org Chart"
standfirst: "I run my own work the way I would want a small company to run: one memory, agents doing the bookkeeping, and me at every decision."
tags: [ai, ways-of-working]
---

Even a team of one has an org chart. Mine used to look like this: a planner in one app, notes in two others, decisions scattered across chat threads that disappeared when the session ended, and the same paragraph written three times because I could not find the first two. The bottleneck was me. Every question about my own work had to go through my memory, and my memory is not very good.

That is the same problem a company has, only smaller. So I set up my own work on the same principle I used at a 50-person startup: put everything worth knowing in one place, let AI agents do the collecting and filing, and keep a person, which here means me, at every point where a decision is made.

## Where things live

The first decision was to separate what I know from what I am doing. They change at different speeds, and mixing them was what made both messy.

| Place | What lives there | Who writes it |
|---|---|---|
| A Git repository | Everything I know: notes, sources, drafts, one file per idea, linked to each other like Wikipedia pages | I write anything that states a view. Agents handle filing and links |
| Notion | Everything in motion: the project list, a work log, a register of decisions and assumptions, hand-offs between workstreams, and meeting transcripts | Mostly agents, with me signing off decisions |
| Claude | The planner. It reads the current state and writes the next work order | |
| Codex | The executor. It carries out the work order in the repository and reports back | |

The Wikipedia idea matters more than it sounds. Most pages stand alone. You follow a link only when you need it. That keeps every agent session small: it loads the one page it needs, not the whole history.

## How a day runs

A morning summary tells me what moved since yesterday and what is waiting on me. When I know what I want done, Claude writes it as a work order in a file called `NEXT.md`. Codex picks it up, does the work in the repository, and writes what it did and anything it could not resolve into a report file that Claude reads next time. Meeting transcripts are filed the same day, so nothing important lives only in my head for long.

The hand-off through files sounds old-fashioned, and it is on purpose. A file is something both agents can read, I can open, and Git keeps a history of. A chat window is none of those.

## Three rules that made it work

**Pointers, not copies.** When one part of the work needs something from another, it links to it. It does not paste it. Copies drift apart within a week, and then you have two versions of the truth and no way of knowing which is current.

**Small doors between rooms.** Each workstream has its own folder and a short interface file, about thirty lines, that says what it holds and what it needs. Other workstreams may read that file and nothing else. It keeps agents from wandering through everything, and it keeps my token bill down, because a session never loads more than it needs.

**I write every claim.** Agents can file, link, summarize and draft. Anything that says what I think, I write myself. That is my version of the approval step in the company workflow: a cheap, fast system everywhere except where a mistake would cost something.

## What it cost

Setting it up took time, and some of it broke along the way. A network drive turned out to break the bridge between my laptop and the agents, so everything had to move to a local disk. I also hit the worry my former colleagues described: running out of tokens before the monthly reset. The small doors are my main defence against it.

Once a quarter, a separate agent inspects the whole system and judges whether it is still working. It does not look at the work itself, only at whether the system is still doing its job. A system like this decays quietly, and I would rather find out from a scheduled check than from a missing file.

## What I took from it

The rules hold at both sizes. One memory, small doors, a person at every decision. Running it alone shows me where the design breaks, because when it breaks, the only person it inconveniences is me.

If you want to see how the same principle ran at company scale, with meeting minutes, avoided hires and the token worry included, it is in the [case study](/portfolio/ai-native-operations/).
