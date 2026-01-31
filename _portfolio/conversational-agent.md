---
title: "Internal-Facing GenAI Chatbot for Customer Care"
excerpt: "Led product development of an AI-powered chatbot empowering Volvo Cars customer care agents with instant access to accurate, multi-market knowledge, achieving 35% automation and 94% agent satisfaction.<br/><img src='/assets/porfolio-img/chatbot/hero-banner.png'>"
collection: portfolio
---

*By Phong Trang - Product Manager - thanhphong.trang@gmail.com*

![Chatbot Hero Banner](/assets/porfolio-img/chatbot/hero-banner.png)

## Overview

As a Web Platform Product Manager working with the customer care team, I led the product development of an AI-powered virtual agent designed to empower Volvo Cars customer care agents with instant access to accurate, multi-market knowledge.

**The Challenge:** Customer care agents across 12+ markets struggled with fragmented information sources, outdated content, and time-consuming manual searches, leading to inconsistent customer experiences and extended handling times.

**The Impact:** Delivered a production-ready chatbot achieving **35% automated resolution rate (ARR)**, **94% agent satisfaction**, and measurable improvements in First Contact Resolution (FCR) and Average Handle Time (AHT).

**Key Metrics:**
- 35% ARR (Automated Resolution Rate) within 90 days
- 94% Agent Satisfaction at alpha release
- 10pp FCR improvement on bot-eligible intents
- 20-30% AHT reduction target achieved
- 4.5/5 Bot CSAT maintained

---

## Tech Stack

<img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white" alt="Python">
<img src="https://img.shields.io/badge/LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white" alt="LangChain">
<img src="https://img.shields.io/badge/LangGraph-FF6B6B?style=flat&logo=langchain&logoColor=white" alt="LangGraph">
<img src="https://img.shields.io/badge/Azure_OpenAI-412991?style=flat&logo=openai&logoColor=white" alt="Azure OpenAI">
<img src="https://img.shields.io/badge/GPT--4o-74AA9C?style=flat&logo=openai&logoColor=white" alt="GPT-4o">
<img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white" alt="Streamlit">
<img src="https://img.shields.io/badge/ChromaDB-FF6584?style=flat&logo=databricks&logoColor=white" alt="ChromaDB">
<img src="https://img.shields.io/badge/Cohere-39594D?style=flat&logo=ai&logoColor=white" alt="Cohere">
<img src="https://img.shields.io/badge/Langfuse-000000?style=flat&logo=lightning&logoColor=white" alt="Langfuse">
<img src="https://img.shields.io/badge/Azure_Container_Apps-0078D4?style=flat&logo=microsoftazure&logoColor=white" alt="Azure Container Apps">
<img src="https://img.shields.io/badge/OpenAI_Embeddings-10A37F?style=flat&logo=openai&logoColor=white" alt="OpenAI Embeddings">

---

## Problem Statement

### Current Challenges

![Agent Workflow Pain Points](/assets/porfolio-img/chatbot/problem statements.webp)

**Existing Agent Workflow Pain Points:**

- Memory Dependency: Agents rely heavily on personal experience and memory
- Fragmented Sources: Must navigate multiple systems (Salesforce, public websites, internal tools)
- Information Quality Issues: Content is often outdated, lacking, or hard to locate
- Time-Consuming: Significant time spent searching across systems
- Manual Collaboration: Dependent on colleague availability via Teams/face-to-face
- Personal Workarounds: Creating and maintaining individual notes/cheat sheets

**Business Impact:**
- Inconsistent customer experiences across agents and markets
- Extended handling times
- Lower first contact resolution rates
- Increased agent frustration and training burden
- Knowledge gaps during cross-border chat transfers

> **💡 DIBB Framework Alignment**
>
> - Data: Top 20 intents account for ~65% of volume; 40% of contacts after-hours; high average handle time on order-status and account questions
> - Insight: Most top intents follow structured flows with clear outcomes; knowledge is scattered; escalations lack context
> - Belief: Automating top intents and grounding responses in existing knowledge will lift ARR and CSAT while reducing costs
> - Bet: Build a guardrailed, grounded chatbot with seamless handoff in 3–4 weeks to realize immediate savings and learn quickly

---

## Ideation Phase

### User Stories Mapping Workshop

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin: 2rem 0;">
  <div>
    <p><strong>🎯 Goal:</strong> To identify and align on the key user personas, their motivations, pain points, and the outcomes they expect from the chatbot — converting these insights into structured user stories that guide design and feature prioritization.</p>
    <p><strong>👥 Participants:</strong> Product Manager, UX Designer/Researcher, Technical Lead/Solution Architect, Selected frontline agents or end users</p>
    <p><strong>👨🏻‍🦱 My Role:</strong> I facilitated the session by framing the objectives, ensuring every story was actionable and traceable to user needs. I also captured dependencies, clarified business impact, and synthesized outputs into the initial backlog.</p>
  </div>
  <div>
    <p><strong>📤 Workshop Outcome:</strong></p>
    <img src="/assets/porfolio-img/chatbot/workshop-user-stories.webp" alt="User Stories Mapping" style="width: 100%;">
  </div>
</div>

### Core Feature Mapping Workshop

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin: 2rem 0;">
  <div>
    <p><strong>🎯 Goal:</strong> To translate user stories into tangible features, grouped and prioritized (High, Medium, Low) based on impact, feasibility, and alignment with MVP scope — creating a clear product definition for the first release.</p>
    <p><strong>👥 Participants:</strong> Product Manager, Engineering Lead/Developers, UX Designer, Data Analyst, Customer Support or Operations Representative</p>
    <p><strong>👨🏻‍🦱 My Role:</strong> I led the feature prioritization discussions, balancing user value with technical complexity and business constraints, maintaining focus on MVP deliverables, resolved scope debates, and documented final feature groupings used for roadmap planning.</p>
  </div>
  <div>
    <p><strong>📤 Workshop Outcome:</strong></p>
    <img src="/assets/porfolio-img/chatbot/workshop-core-feature.webp" alt="Core Feature Mapping" style="width: 100%;">
  </div>
</div>

### User Experience Mapping Workshop

**🎯 Goal:** To visualize the end-to-end chatbot experience — defining conversation flows, handoff points, and emotional journey touchpoints to ensure the interaction feels intuitive, human, and consistent across channels.

**👥 Participants:** Product Manager (facilitator), UX/UI Designer, UX Writer, Engineering Lead (for flow feasibility), Support/Service Team Representative

**👨🏻‍🦱 My Role:** Ensured alignment between design intent and product goals by helping translate insights from user stories and features into journey maps, validated feasibility with engineering, and documented key UX principles and success metrics.

**📤 Workshop Outcome:**

![User Experience Journey](/assets/porfolio-img/chatbot/ux-journey-1.png)

![Conversation Flow Design](/assets/porfolio-img/chatbot/ux-journey-2.png)

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin: 2rem 0;">
  <div>
    <img src="/assets/porfolio-img/chatbot/flow-detail-1.png" alt="Flow Details 1" style="width: 100%;">
  </div>
  <div>
    <img src="/assets/porfolio-img/chatbot/flow-detail-2.png" alt="Flow Details 2" style="width: 100%;">
  </div>
</div>

---

## Success Metrics Definition

### 🧩 Product Performance Metrics (Core KPIs)

| Metric | Target | Why It Matters |
|--------|--------|----------------|
| **ARR (Automated Resolution Rate)** | ≥ **35%** within 90 days | Core measure of automation efficiency; indicates % of issues resolved without human intervention |
| **Bot CSAT** | ≥ **4.5/5** or ≥ **75% positive** thumbs-up ratio | Ensures automation doesn't come at the cost of experience |
| **Escalation Accuracy** | ≥ **90%** for low-confidence or user-requested cases | Validates quality of routing logic; minimizes unnecessary handoffs |
| **Bot Response Time** | Median ≤ **1s**, P95 ≤ **2s** | Maintains conversational flow and perceived responsiveness |
| **Cost per Contact Reduction** | ↓ **20–30%** vs baseline | Demonstrates business efficiency gains and ROI from automation |

### 💬 User-Centric Metrics

| Metric | Target | Why It Matters |
|--------|--------|----------------|
| **First Contact Resolution (FCR) uplift** | +**10pp** on bot-eligible intents | Reflects effectiveness and completeness of bot interactions |
| **After-Hours CSAT** | ≥ **4.6/5** | Captures value during periods of limited agent availability |
| **Feedback Participation Rate** | ≥ **25%** of conversations | Ensures sufficient user feedback for continuous improvement |

### ⚙️ Technical & Safety Metrics

| Metric | Target | Why It Matters |
|--------|--------|----------------|
| **Uptime** | ≥ **99.9%** business hours; ≥ **99.5%** overall | Ensures reliability and user trust |
| **Hallucination Rate** | ≤ **2%** of audited conversations | Measures factual accuracy and knowledge grounding quality |
| **PII Leakage Incidents** | **0 critical**; mitigation ≤ **24h** for high severity | Protects customer privacy and compliance |

---

## Rapid Prototyping with AI

### Accelerating Time-to-Feedback with Lovable.dev

To validate concepts before full development, I used **Lovable** - an AI-powered full-stack development platform that enables rapid prototyping of web applications.

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin: 2rem 0;">
  <div>
    <blockquote>
      <p><strong>💡 Benefits of this Approach:</strong></p>
      <ul>
        <li><strong>Speed to Feedback:</strong> Prototype in 1 day vs. 2-4 weeks traditional development</li>
        <li><strong>Cost Efficiency:</strong> Validate concepts before committing full engineering resources</li>
        <li><strong>Real Interactions:</strong> Stakeholders can click, type, and experience features rather than reviewing static mockups</li>
        <li><strong>Iterative Refinement:</strong> Quickly incorporate feedback and re-test within same sessions</li>
        <li><strong>Technical Validation:</strong> Engineering team can assess architecture and feasibility with real code</li>
      </ul>
    </blockquote>
  </div>
  <div>
    <p><strong>Quick Interactive Prototype (3 Intents):</strong></p>
    <img src="/assets/porfolio-img/chatbot/lovable-prototype.png" alt="Lovable Prototype" style="width: 100%;">
  </div>
</div>

**My Validation Approach:**
1. **Product Definition** → Created comprehensive product requirements document
2. **AI-Powered Prototyping** → Used Lovable to translate requirements into working prototype within hours
3. **Stakeholder Validation** → Brought functional prototype to key stakeholders:
   - **User Testing:** Customer Care agents tested chatbot interface for usability
   - **Business Leadership:** Demonstrated working dashboard for strategic alignment
   - **Design Team:** Validated look & feel and Volvo brand consistency
   - **Development Team:** Showcased feature functionality and technical feasibility

---

## Technical Architecture

### Data Ingestion Pipeline

**Key Capabilities:**
- **Recursive Scraping Solution:** Asyncio-based for performance
- **Article De-duplication:** Handles complex URL variants and parameters
- **CDN Bot Detection Bypass:** Custom headers and request throttling
- **Media Extraction:** Images and video scraping with JS dynamic DOM rendering (scroll-based)

**Example Challenge:** Support articles with complex URL structures requiring de-duplication logic:
