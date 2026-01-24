---
title: "AI Semantic Search for New Car Sales"
excerpt: "Led development of an intelligent search system using AI-powered intent recognition, achieving 85% search accuracy and driving 11% higher purchase conversion.<br/><img src='/images/semantic-search-hero.jpg'>"
collection: portfolio
---

*By Phong Trang - Software Product Manager - thanhphong.trang@gmail.com*

## Overview

**The Challenge:** Transform Volvo's car discovery experience by building an intelligent search system that understands customer intent, bridging the gap between natural language queries and technical car specifications.

**The Impact:** Achieved 85% search accuracy (NDCG score), increasing 19% to Car Listing Pages, and make search user 11% more likely to complete a car purchase.

**Key Metrics:**
- **85% NDCG** search accuracy score
- **+19% traffic** to Car Listing Pages from search
- **+11% conversion** rate for search users
- **Sub-second** response times at scale

![Semantic Search Architecture](assets/images/semantic-search-architecture.jpg)

---

## Problem Statement

### 💔 What Was Breaking

**🚙 Complex Purchase Decisions**

Cars represent the second-largest purchase after homes, with hundreds of configurations and features. Customer research typically spans weeks, but our existing search made it difficult to find the right match in inventory.

**🏗️ Legacy System Limitations**

The backend GraphQL system provided comprehensive car data but lacked semantic search capabilities:
- Fixed nomenclature without synonym support
- Filter-based architecture requiring exact matches
- No natural language processing layer
- Gap between customer language and system terminology

**🗣️ Semantic Language Gap**

A critical disconnect existed between how customers search and how we catalog cars:
- Customers: *"surrounded cameras"* → Our system: *"360° camera"*
- Customers: *"family cars"* → Our system: required specific model browsing
- Customers: *"eco-friendly vehicles"* → Our system: needed exact fuel type filters

**🛒 Direct-to-Consumer Strategy Risk**

The UK market pilot for transparent, haggle-free car sales required self-service discovery capabilities that our legacy search couldn't support, threatening the strategic initiative.

> **💡 The Opportunity**
>
> - **Revenue Recovery:** Capture lost sales from customers who couldn't find suitable cars in our existing inventory through better discovery
> - **Competitive Advantage:** Differentiate Volvo's direct-to-consumer experience with Google-like search intelligence while competitors rely on traditional dealership browsing
> - **Inventory Optimization:** Convert hidden quick-delivery stock into competitive advantage by making 3-week delivery cars easily discoverable

---

## 🕵️ Discovery & Research

### Data-Insight-Belief-Bet Framework

**📐 Data (what we can reliably measure)**

- **Structured (clickstream & session):** search submits, result clicks, time on search results, scroll depth, device, market, search destination (Car Listing Page, PDP, support pages), zero-result, abandonment, add-to-cart, orders, orders-with-search, latency.
- **Unstructured (customer language):** raw search terms (incl. misspellings, synonyms, colloquialisms), query length, language/market, intent phrases ("family car", "surrounded cameras", "eco-friendly"), reformulations.

**The baseline facts:**
- Analyzed **25,000 unique search queries** from UK market data, revealing:
  - 80% of queries contained 2-5 words
  - High frequency of colloquial terms and misspellings
  - Intent-based searches (e.g., "family car") vs. specification searches (e.g., "XC90")
  - Geographic and cultural language variations
- Achieved **85% NDCG** on 🇬🇧 UK, **72% NDCG** in 🇩🇪 DE with **English-only indexing** performing better than German-only (**~0.72 vs 0.58 NDCG**).
- Launch impact: **+19% traffic to Car Listing Pages** from search and search users **+11% more likely to purchase**.

**💠 Canonical metrics & formulas**
- **Search Interaction Rate (SIR)** = `clicked results / submitted searches`
- **Search CTR to Listing** = `clicks to CLP / submitted searches`
- **Zero-Result Rate** = `searches returning 0 results / submitted searches`
- **Search Abandon Rate** = `searches with no click / submitted searches`
- **Query Reformulation Rate** = `sessions with ≥1 re-query / search sessions`
- **Search→Order Rate** = `orders with prior search / search sessions`

### 👥 User Research Insights

**🗺️ Customer Journey Mapping**

Identified three primary search intents:
1. **🛒 Purchase Intent:** New car buyers with specific needs
2. **📚 Information Seeking:** Research-phase customers exploring options
3. **🔧 Existing Owner Support:** Current customers seeking information about their vehicles

### 🔬 Technical Insight

**🧠 Semantic Router Investigation**

Researched industry-standard approaches, focusing on the semantic router methodology:
1. Intent classification through utterance databases
2. Vector similarity matching using embedding models
3. Real-time query processing and ranking

**⚖️ Embedding Model Evaluation**

Used NDCG (Normalized Discounted Cumulative Gain) as the primary evaluation metric to measure ranking quality across 1,200+ test queries to benchmark:
- `OpenAI text-embedding-3-large`
- `Multilingual-e5-small`
- `Elasticsearch ELSER v2`
- `Cohere multilingual models`

---

## 💡 Solution Strategy

### 🎯 Strategic Approach

**🧭 Intent Recognition First**

Rather than treating this as a pure search problem, I positioned it as an intent recognition challenge. The key insight: understand what customers want, not just what they type.

**🏗️ Semantic Router Architecture**

Designed a three-layer system:
1. **🎭 Intent Classification:** Categorize user queries into predefined intents (EV interest, car type preferences, feature requirements)
2. **🔗 Semantic Matching:** Use vector similarity to find relevant cars in inventory
3. **🎯 Intelligent Reranking:** Apply cross-encoder models for final result optimization

### 🚀 Key Product Decisions

**🔀 Multi-Modal Search Approach**
- Combined semantic search (dense retrieval) with traditional lexical search
- Weighted field approach: "summary" fields (model, price, specs) vs. "details" fields (features, accessories)
- Dynamic query expansion using LLM capabilities

**🌍 Multilingual Strategy**

For German market expansion:
- Discovered English-only indexing performed better than German-only (0.72 vs 0.58 NDCG)
- Simplified evaluation and maintenance processes
- Enabled consistent performance across markets

**⚡ Performance-First Design**
- Optimized for 600-1,000 car inventory sizes
- Computational efficiency for real-time search
- Scalable architecture supporting multiple markets

### 🧪 Interactive Prototype

Built a real-time demo application using semi-live UK market data to showcase the semantic search capabilities and validate performance with stakeholders.

![Semantic Search Demo - Lexical vs Semantic](/images/semantic-search-demo.jpg)

**Comparison:**
- **Lexical Search Results:** Traditional keyword matching showing limited, often irrelevant matches for "leather family car with sun roof"
- **Semantic Search Results:** Intelligent understanding that surfaces relevant XC90 models with actual leather interiors, panoramic roofs, and family-friendly features

> **💡 The Power of Context**
>
> Notice how semantic search correctly identifies that "family car" means larger SUV models (XC90) rather than compact cars (EX30), and "sun roof" maps to "panoramic roof" in the vehicle specifications - exactly the kind of intelligent interpretation that traditional search systems miss.

---

## 🛠️ Implementation

### System Architecture

![Implementation Architecture](/images/semantic-search-implementation.jpg)

![Technical Flow Diagram](/images/semantic-search-flow.jpg)

### 🪙 Cost-Effective Implementation

- **Monthly cost**: ~150 SEK for UK market (250 daily queries)
- **Processing**: 1M tokens at $1.3 + 1000 queries at $2.00
- **ROI**: Significant inventory utilization improvement

---

## 📊 Results & Impact

### 🎯 Performance Metrics

**🏆 Search Accuracy Achievement**
- **85% NDCG score** with OpenAI embedding + Cohere reranking
- **19% improvement** over best traditional approach (E5 + lexical search)
- **77% standalone semantic search** performance vs 70% for multilingual-e5-small

**🥇 Model Performance Ranking**

![Model Performance Comparison](/images/semantic-search-results.jpg)

**🌍 Cross-Market Validation**
- **UK Market:** 85% NDCG performance
- **German Market:** 72% NDCG performance (English-only indexing)
- Consistent performance across 1,200+ diverse test queries

### 💼 Business Impact

**🎯 Conversion Funnel Improvements**
- **19% increase** in traffic to Car Listing Pages from search results
- **11% higher** purchase completion rate among search users
- Significant improvement in search-to-conversion pathway

**😊 Customer Experience Improvements**
- Semantic query understanding (natural language to car features)
- Reduced search friction and improved discoverability
- Enhanced inventory utilization for quick-delivery options

**⚡ Technical Achievements**
- Sub-second search response times
- Scalable architecture supporting multiple markets
- Robust multilingual capabilities

**📈 Operational Efficiency**
- Reduced customer support queries about search functionality
- Streamlined inventory management through better visibility
- Automated evaluation framework reducing manual testing overhead

---

## Tech Stack

- **Embedding Models:** OpenAI text-embedding-3-large, Multilingual-e5-small
- **Reranking:** Cohere multilingual models
- **Search Engine:** Elasticsearch ELSER v2
- **Backend:** GraphQL API
- **Evaluation:** NDCG metrics, custom testing framework

---

## Skills Demonstrated

- AI/ML Product Strategy
- Semantic Search & NLP
- Vector Databases & Embeddings
- User Research & Intent Analysis
- A/B Testing & Metrics
- Cross-functional Leadership
- API Integration
- Stakeholder Management
