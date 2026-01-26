---
title: "Search Platform Growth Model and Monetization"
excerpt: "Creating the first Search-to-purchase user journey on Volvo e-commerce channel by syncing real-time inventory with digital experiences.<br/><img src='/assets/porfolio-img/search-growth/banner.png'>"
collection: portfolio
---

*By Phong Trang - Software Product Manager - [thanhphong.trang@gmail.com](mailto:thanhphong.trang@gmail.com)*

![Banner Image](/assets/porfolio-img/search-growth/banner.png)

# 🚗 Industry Context (Mid-2024)

At the time, search functionality across most automotive websites was still primitive.

Unlike in mainstream e-commerce, where users could instantly search and filter live product availability, car brands were constrained by legacy systems, fragmented data layers, and complex dealer integrations.

- Inventory databases were often not connected to public-facing search tools, making it impossible for users to find in-stock cars directly.
- Syncing real-time inventory with digital experiences required cross-system orchestration, regional APIs, and data compliance handling — all of which made Search hard to modernize.

Against this backdrop, our challenge wasn't just UX optimization — it was about modernizing the role of Search within an industry still catching up to digital commerce standards.

**Technical Stack:**
![Azure OpenAI](https://img.shields.io/badge/Azure_OpenAI-412991?style=flat&logo=openai&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Proxy](https://img.shields.io/badge/Proxy_Layer-00599C?style=flat&logo=nginx&logoColor=white)
![Google Analytics](https://img.shields.io/badge/Google_Analytics-E37400?style=flat&logo=google-analytics&logoColor=white)
![JSON](https://img.shields.io/badge/JSON-000000?style=flat&logo=json&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=flat&logo=graphql&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)

# Problem Statement

- Volvo Cars faced high inventory costs due to excess vehicle stock tying up capital and resources.
- Helping consumers quickly find the right car from stock inventory became a critical business priority.
- However, the current interface required 5–14 clicks and multiple page reloads before a user could locate a matching car — a friction-heavy process that led to high drop-off and missed conversions.

The question was:

> 💡 Can we simplify this journey using AI while leveraging existing infrastructure?

Goal: The Search team — a small virtual squad (1 BE, 1 FE, 1 Designer, 1 PM) — set out to transform Search from a navigational utility into a monetized, conversion-driving experience without new backend systems.

## 🧩 Data


<!-- Control width and maintain aspect ratio -->
<img src="/assets/porfolio-img/search-growth/Data.png" alt="Data Visualization" style="width: 50%; max-width: 300px;">


<div style="display: flex; gap: 2rem; align-items: start;">
<div style="flex: 1;">

- Website analytics showed ~10,000 daily searches, but conversion from Search to configuration was only 5.8%.
- On average, customers needed 5–14 clicks and several page reloads to find a matching car from stock.

Search Behavior Breakdown - Analysis of 2024 search logs revealed where users' attention went:

- 35% searched for Car Models (e.g., "XC40," "EX30," "XC90") — strong purchase intent.
- 21% searched for User Manuals and App-related terms — high post-purchase engagement.
- 19% searched for Used Cars — a monetizable secondary funnel.
- 15% searched for Accessories ("roof box," "tow bar," "dog cage") — underexploited cross-sell potential.
- 10% were Miscellaneous queries.

## 💡 Insight - Who are the Search users on volvocars.com

Making about 10,000 submitted searches every day, Search users on dot com are explorers of what the website could offer them on many cycles of the car purchasing and ownership.

For car-buyers, they mostly leverage Search on dot com for research of official information issued by the OEM after they did their own research elsewhere.

They have a keen eye on nuanced information such as spec details (e.g., "XC40 charging time", "EX30 trunk size") or special personal needs (e.g., "car with 360 camera", "XC60 child seat").

<div style="display: flex; gap: 2rem;">
<div style="flex: 1;">

### 📷 Searchers are exploratory

- Users often begin with ambiguous queries (e.g., "EV SUVs") and refine them iteratively (e.g., "EVs under $50k" → "XC40 range and EX30 range")
- Queries like "XC40 winter tires" or "EV charging cost" reveal users envisioning life with the car. They seek reassurance about practicality, costs, or lifestyle fit—moments to educate and build trust.

</div>
<div style="flex: 1;">

### 🎯 Searchers are deterministic

- Approx. 5.8% every month of Configurator Purchase are from Searchers. This number increased to 10.5% for November, 2024 (Black week).
- Searchers are more likely to complete their configuration than the average rate – 28.9% compared to 23.4%

</div>
</div>

## 🔎 Belief

If we enable users to find relevant in-stock cars instantly through a smarter Search experience—powered by AI-driven language understanding—we can turn Search into a monetization lever that improves both user experience and business efficiency.

## 🎯 Bet - The opportunities from Search users

### Belief 1: Inventory Teasers for the Exploratory Searchers

![Inventory Teaser 1](/assets/porfolio-img/search-growth/inventory-teaser1.png)

![Inventory Teaser 2](/assets/porfolio-img/search-growth/inventory-teaser2.png)

> 💡 Key Insight:
> - Exploratory Searchers love ambiguous search strings ("XC90", "SUVs", etc.), Search windows can already dynamically introduce our offers (car shopping, car learning, digital manuals, etc.) to fulfill their curious minds.
> - Users get to know the car products but also the dot com tools (find a retailer, self service, book a test drive, etc.) from the first touch points of opening search.
> - Therefore, increasing transparency of Inventory but the Website capabilities as a shopping tool

### Belief 2: Free-text Search for the Deterministic Searchers

![Free Text Search](/assets/porfolio-img/search-growth/free-text-search.png)

> 💡 Key Insight:
> - Deterministic Searchers love to be specific, they have done their research well and they want cars that meet their personalized needs.
> - Adding a Free Text Search bar into Car Listing Page can liberate the users to find all offers in our inventory using natural languages

# Solution Space

<div style="display: flex; gap: 2rem; align-items: start;">
<div style="flex: 1;">

### 1. Proxy-based Search Form Injection

</div>
<div style="flex: 1;">

![Product Architecture](/assets/porfolio-img/search-growth/product-architecture.png)

</div>
</div>

To test and ship fast without new backend dependencies, we engineered a proxy insertion layer between the browser and volvocars.com.

- The proxy intercepts inventory page requests, injects a lightweight free-text Search component, and then returns the page to the browser.
- This allowed real-world experimentation without altering the existing CLE backend or core API contracts.
- Result: we could iterate on UX, measure performance, and validate monetization hypotheses in production safely and quickly.

---

### 2. Natural Language Mapping Logic (AI Layer)

To make Free-Text Search usable without a true NLP backend, we built a lightweight AI mapping layer that interprets user intent into structured Search parameters.

- Each query (e.g., *"red EV SUV under 50k"*) was parsed into a JSON object with fields like model, year, color, drivetrain, and price range.
- Custom rules mapped generic language to product attributes:
  - "Red" → *Fusion Red*, *Mulberry Red*
  - "Large SUV" → *XC90*, *EX90*
  - "Plug-in hybrid" → *T8* powertrain
- This simulated natural language understanding, making Search feel intelligent using only existing logic and data.

---

### 3. Dynamic Inventory Teasers

For Exploratory Searchers, we expanded the Search UI to display dynamic inventory previews and utility links:

- Surfaced real-time inventory cards alongside traditional search results.
- Introduced quick actions: *Book Test Drive*, *Find Retailer*, *View Offers*.
- Made Search an integrated entry point into the car-shopping flow rather than an isolated feature.

---

### 4. Optimized User Flow & Experience

- Reduced user journey from 5–14 clicks to 1–2 interactions.
- Enabled both discovery and conversion directly within Search results.
- The experience was AI-enhanced, but infra-light — an innovation in low-resource product delivery.

---

## 📈 Outcome & Impact

### Quantitative Gains

| Metric (t = 30 days) | Before | After | Δ |
|----------------------|--------|-------|---|
| CTR from Search results | 7.8% | 11.2% | +43% |
| Configurator starts from Search | 5.8% | 10.5% (Black Week 2024) | +81% |
| Conversion rate (Search users) | 23.4% | 28.9% | +24% |

- Higher click-through rates validated that dynamic inventory teasers captured user interest.
- Conversion uplift confirmed the hypothesis that simplifying Search directly supports monetization.
- The pilot also demonstrated that lean front-end experiments can yield enterprise-level business impact.

### Qualitative Gains

- Positive user feedback around "speed to find" and "smart suggestions."
- Improved perception of the brand's digital maturity through AI-led UX.
- Established Search as a commercial touchpoint — not just navigation — opening the door for future personalization and paid placements.

---

## 🏁 Key Learnings

- AI doesn't always require heavy infrastructure — intent mapping can unlock value fast.
- Existing infrastructure could be repurposed creatively without backend overhaul.
- Search data offers deep insight into both purchase behavior and ownership journeys.
- A small, empowered virtual team can deliver measurable business impact by focusing on leverage points — in this case, Search.
- Prompt Engineering is key to making lightweight AI solutions work effectively.


