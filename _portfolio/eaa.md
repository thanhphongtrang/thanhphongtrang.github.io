---
title: "EU Accessibility Act Compliance: Managing Risk and Building Capability"
excerpt: "Led 27-market accessibility compliance program, preventing potential legal exposure while establishing sustainable governance framework across 20 front-end teams. <br/><img src='/assets/porfolio-img/eaa/hero-banner.png'>"
collection: portfolio
---
*By Phong Trang - Software Product Manager - *[*thanhphong.trang@gmail.com*](mailto:thanhphong.trang@gmail.com)
![Dashboard](/assets/porfolio-img/eaa/hero-banner.png)

## Overview
When the EU Accessibility Act deadline approached in 2025, Volvo Cars faced a straightforward challenge: ensure volvocars.com meets regulatory requirements across 27 EEA markets before June 28, 2025. As Program Manager for the EU Accessibility Compliance initiative, I coordinated 20 front-end teams to resolve over 14,000 accessibility violations across 7,000+ pages.
The work wasn't particularly dramatic. It required structured governance, clear ownership, and pragmatic solutions to scale remediation across a complex organization. We achieved full compliance ahead of schedule and built a framework to maintain it going forward.

**Key Outcomes:**
- **100% compliance** achieved ahead of the June 28, 2025 deadline
- **14,000+ accessibility violations** resolved across 27 markets
- **Zero legal exposure** - prevented potential regulatory penalties
- **Sustainable governance** established for ongoing compliance
- **"Highly positive" external audit** from accessibility consultancy Funka

**Technical Stack:**

![Azure](https://img.shields.io/badge/Azure%20OpenAI-0078D4?style=flat&logo=microsoft-azure&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white)
![Dashboard](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=power-bi&logoColor=black)
---

## Why This Mattered
The EU Accessibility Act isn't optional. Non-compliance carries legal and reputational risk. For a premium automotive brand operating across the European Economic Area, meeting accessibility standards protects both brand standing and business continuity.
Beyond regulatory compliance, accessibility improves the digital experience for users with assistive technologies. This aligns with Volvo's broader commitment to inclusive design and serves customers across 27 markets more effectively.
From a business perspective, the project had three objectives:

1. **Risk mitigation:** Prevent legal exposure from non-compliance
2. **Operational efficiency:** Build scalable processes rather than one-time fixes
3. **Brand alignment:** Demonstrate commitment to inclusive design standards

---
## The Challenge

When we assessed volvocars.com's compliance status, the scope became clear:
- **14,000+ accessibility violations** spread across approximately 7,000 pages
- **27 EEA markets** with localized content requiring remediation
- **200,000 global asset instances** needing updates (images, buttons, links)
- **20 front-end teams** working across different technical stacks
- **Siloed organization** with content, platform, quality, governance, and market teams operating independently

The regulatory deadline created urgency. The distributed nature of the violation types—from simple alt-text gaps to complex keyboard navigation issues—meant no single team could resolve everything alone.

### The Specific Bottleneck
Manual alt-text creation for 100,000+ assets wasn't feasible. Local content editors were already managing market rollouts and model updates. Adding accessibility remediation to their workload would either delay compliance or require significant additional hiring.
Generative AI offered a potential solution for scaling alt-text generation. However, Volvo Cars' internal AI governance process required formal approval from the Generative AI Committee before deployment. This process typically took months. We had weeks.

---
## Approach: Program Management and Pragmatic Solutions
As Program Manager, my role centered on three areas: establishing governance structures, coordinating cross-functional remediation, and identifying scalable solutions for the highest-volume problems.
### Governance and Stakeholder Alignment
The first step was clarifying ownership. With 20 front-end teams, multiple market organizations, and various platform teams involved, everyone's responsibility easily becomes no one's responsibility.
I established a steering group with design and product leadership to drive strategy. We created a centralized dashboard integrating Playwright and SiteImprove data, providing a single source of truth for tracking requirements, progress, and blockers.
Communication cadence followed a structured approach:
- Weekly steering group check-ins for executive alignment
- Bi-weekly team syncs for technical coordination
- Targeted updates via 20 emails and 14 Slack posts to relevant stakeholder groups
- 9 dedicated Slack channels for specific workstreams
The goal was transparency without noise. Teams needed to know what they owned, when it was due, and how it connected to other teams' work.
### Scenario Planning for Executive Decisions
Rather than presenting problems for executives to solve, I prepared scenario planning:
- **Plan A:** Primary approach with timeline and dependencies
- **Plan B:** Contingency approach if key dependencies failed
This enabled leadership to make confident decisions quickly. When the GenAI governance process looked uncertain, we had a manual remediation fallback ready. When that process accelerated, we could pivot back without losing momentum.
### Scaling Alt-Text with GenAI (Pragmatically)
To accelerate the GenAI governance approval, I coordinated with adjacent teams facing similar challenges:
- **CMS team:** Needed AI-assisted content workflows
- **Price Engine team:** Had pending GenAI use cases
By presenting a unified case and sharing architecture, we collectively raised visibility within the AI governance board. The combined business case—three teams solving similar problems with a shared technical approach—moved faster through approval than individual requests would have.
Once approved, the technical implementation followed a risk-mitigated approach:
**Architecture:**
![Dashboard](/assets/porfolio-img/eaa/architecture.png)
- Azure OpenAI API for alt-text and ARIA label generation
- Content Safety API for automated moderation filtering
- Statistical sampling (1,000-2,000 outputs) manually reviewed by Content Management teams
- Market-specific editor validation before publishing
**Safety Guardrails:**
The API automatically flagged any content exceeding safety thresholds:
<pre>
  <code>
"prompt_filter_results": {
  "sexual": {"severity": "safe", "filtered": false},
  "violence": {"severity": "safe", "filtered": false},
  "hate": {"severity": "safe", "filtered": false},
  "self_harm": {"severity": "safe", "filtered": false},
  "profanity": {"detected": false, "filtered": false}
}</code>
</pre>
This wasn't about deploying cutting-edge AI. It was about using available technology with clear constraints to solve a specific scaling problem. The validation process ensured outputs met EU Accessibility Act standards before going live.
![label](/assets/porfolio-img/eaa/aria-label.png)
### Building for Sustainability
Fixing 14,000 violations addressed the immediate deadline. The more important objective was preventing future violations from accumulating.
We integrated accessibility checks into the standard development pipeline by coordinating with the Quality & Release Engineering (QRE) team. I developed dashboard requirements and mockups, which the QRE team implemented as an executive dashboard tracking compliance in real-time.
![label](/assets/porfolio-img/eaa/dashboard-dev.png)

Beyond tooling, we established a **Community of Practice** with 20 trained accessibility advocates across teams, a `#digital-accessibility` Slack channel for peer support, and a central knowledge library for accessibility guidelines.
This moved accessibility from a one-time project to an ongoing organizational capability.
---
## Results
**Compliance Achieved:**
- 100% compliance with EU Accessibility Act ahead of June 28, 2025 deadline
- 14,000+ violations resolved across 27 markets in two months
- Zero legal exposure from regulatory penalties

**Cost Prevention:**
- Avoided potential legal penalties and reputational damage
- Prevented need for emergency hiring of content editors through AI-assisted scaling
- Built reusable architecture adopted by CMS and Price Engine teams, avoiding duplicate development costs

**External Validation:**
- "Highly positive" audit from accessibility consultancy Funka
- Recognized internally as benchmark for accessible design governance maturity

**Ongoing Capability:**
- Community of practice with 20 accessibility advocates
- Automated monitoring via Playwright and SiteImprove
- Integrated QRE dashboard for continuous compliance tracking
- Sustainable governance framework embedded in delivery process

<div style="display: flex; gap: 20px;">
  <img src="/assets/porfolio-img/eaa/accessibility-lib-1.png" alt="lib1" style="width: 50%;">
  <img src="/assets/porfolio-img/eaa/accessibility-lib-2.png" alt="lib2" style="width: 50%;">
</div>
---
## Program Management Approach
### What Worked
- Clarifying ownership early: In complex, multi-team programs, ambiguity creates delays. Establishing clear ownership for each violation category and setting review checkpoints kept teams moving without constant coordination overhead.
- Centralized tracking with distributed execution: The dashboard provided visibility without creating bottlenecks. Teams knew their responsibilities and could execute independently while leadership tracked overall progress.
- Scenario planning for executives: Presenting options (Plan A/Plan B) rather than problems enabled faster decision-making and demonstrated preparedness.
- Building coalitions for governance: The GenAI approval moved faster when presented as a shared need across three teams rather than individual requests. Understanding how internal governance processes work and adapting approach accordingly prevented delays.
- Investing in sustainability over quick fixes: The community of practice, knowledge library, and integrated tooling ensure compliance isn't a recurring crisis every time regulations update.
### Key Learnings
1. Transparency builds trust in high-pressure programs: When coordinating 20+ teams under deadline pressure, clear communication about what's certain versus what's uncertain prevents chaos. Teams could plan around dependencies because we were explicit about status and risks.
2. Systems thinking prevents future problems: Fixing 14,000 violations addressed the immediate deadline. Building the governance framework, tooling, and community of practice prevented those 14,000 from becoming 30,000 next year.
3. Executive alignment unlocks team execution: Getting timely decisions from leadership—enabled by concise updates and scenario planning—removed blockers for the 20 delivery teams. Alignment up cleared the path for alignment across.
---
