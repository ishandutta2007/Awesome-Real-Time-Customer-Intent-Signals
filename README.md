# Awesome-Real-Time-Customer-Intent-Signals

# Awesome Real-Time Customer Intent Signals

> A curated list of top Real-Time Customer Intent Signal platforms — both SaaS/Hosted commercial intent data providers and open-source alternatives for identifying accounts and individuals actively researching a purchase.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [6sense](#6sense)
  - [Demandbase](#demandbase)
  - [Bombora](#bombora)
  - [ZoomInfo Intent](#zoominfo-intent)
  - [TechTarget Priority Engine](#techtarget-priority-engine)
  - [Leadfeeder (Dealfront)](#leadfeeder-dealfront)
  - [Clearbit Reveal](#clearbit-reveal)
- [Open-Source Software](#-open-source-software)
  - [looot-intent](#looot-intent)
  - [looot-crm](#looot-crm)
  - [tinytraffic](#tinytraffic)
  - [ai-lead-scoring-engine](#ai-lead-scoring-engine)
  - [Transparent Lead Scoring](#transparent-lead-scoring)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Real-Time Customer Intent Signal platforms. These are not open-source but are included as reference points for feature comparison.

### 6sense
**Type:** Account-based intent and buying-stage prediction  
6sense is the enterprise standard for account intent data, using AI to predict which accounts are in-market and what stage of the buying journey they are in. It combines third-party intent signals with first-party website activity and CRM data. Pricing is enterprise-quoted, with Vendr reporting annual escalators of 3% to 10% [citation:8].

### Demandbase
**Type:** Account-based marketing and intent platform  
Demandbase provides account-based marketing (ABM) with intent data, advertising, and personalization. It is a direct competitor to 6sense, with a focus on unifying intent signals with ABM execution. Pricing is enterprise-quoted with annual escalators [citation:8].

### Bombora
**Type:** B2B intent data cooperative  
Bombora is a leading third-party intent data provider, using a cooperative model where publishers contribute content consumption data to identify accounts researching specific topics. Vendr reports a median annual cost near $25,000, with onboarding fees of $5,000 to $20,000 [citation:8].

### ZoomInfo Intent
**Type:** Intent data within ZoomInfo's B2B database  
ZoomInfo provides intent data alongside its contact and company database, allowing sales teams to identify accounts researching relevant topics and reach out to contacts within them. It is often bundled with ZoomInfo's broader prospecting platform.

### TechTarget Priority Engine
**Type:** Permissioned intent from tech content network  
TechTarget Priority Engine provides intent data from a permissioned audience of technology buyers researching on TechTarget's network. It emphasizes person-level intent, telling you who inside an account is doing the research [citation:8].

### Leadfeeder (Dealfront)
**Type:** Website visitor identification with free tier  
Leadfeeder (now part of Dealfront) identifies companies visiting your website, revealing which accounts are researching you even if they do not fill out a form. Dealfront offers a free plan, with paid plans starting from EUR 79/month, making it the lowest-cost entry point among major intent tools [citation:8].

### Clearbit Reveal
**Type:** Website visitor de-anonymization  
Clearbit Reveal (now part of HubSpot) identifies the company behind a website visit, matching IP addresses to company data. It is often used alongside intent data to enrich website traffic with firmographic context.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Real-Time Customer Intent Signal tools. The open-source ecosystem is **nascent and fragmented** — most projects are early-stage, narrowly scoped, or require paid data APIs rather than providing free intent data themselves.

### looot-intent
**Stack:** TypeScript / Next.js / CLI | **License:** MIT  
looot-intent is an **MIT-licensed open-source alternative to 6sense** for scoring a list of company domains for buying intent and buying stage [citation:3][citation:12]. Key characteristics:
- **Eleven signals across ten categories**: hiring, funding, news, tech stack changes, SEO movement, web traffic, Google ads, LinkedIn ads, Reddit mentions, headcount growth, and third-party buying intent 
- **0–100 score and four stages**: accounts are ranked as unaware, aware, considering, or deciding (deciding requires a score of 70+ and at least three signal categories) 
- **Itemized scores**: each score lists the signals behind it, the provider, the weight in points, and the cost of each call 
- **Quote before spend**: a dry run prints the price first, and a real run is refused above the cap 
- **Demo mode**: `npm run demo` scores generated accounts on a reserved example domain with no token, no network call, and no cost 

**Critical limitation:** The **code is open source, but the data is not**. Every real run calls the looot data service and pays per call at the catalog price. The project has **0 stars and 1 contributor**, with no security policy and no PRs merged in 90 days [citation:3]. It is a very early-stage project.
**Best for:** Solo founders and small sales teams wanting a transparent, configurable intent scoring engine without paying enterprise platform fees, accepting that real data requires a paid looot balance and the project is extremely new.

### looot-crm
**Stack:** Next.js / Supabase | **License:** Open Source  
looot-crm is a companion project to looot-intent: an **open-source CRM with buying-intent signals built in** [citation:15]. It provides companies, people, a pipeline board, and an **Intent tab per account**, with per-action caps and workspace budgets to control spend. The data model includes 12 tables with row-level security tested on local Postgres. Like looot-intent, it relies on the paid looot data service for actual intent signals, and the project explicitly notes that no real looot run was made while building it.
**Best for:** Teams wanting an open-source CRM foundation with intent signals integrated, accepting the same paid-data dependency and early-stage maturity as looot-intent.

### tinytraffic
**Stack:** Go / DuckDB / ClickHouse | **License:** Open Source  
tinytraffic is a **self-hosted web analytics tool in a single binary** [citation:4][citation:9]. While not an intent data platform itself, it provides the **first-party website visitor tracking** that many intent workflows depend on. It tracks page views, custom events (e.g., `tinytraffic("Signup", { props: { plan: "pro" } })`), and outbound link clicks automatically, with GeoIP location from DB-IP's free database. The dashboard is embedded in the binary, and data can be stored in DuckDB or ClickHouse. It ignores localhost and automated browsers, and you can exclude your own visits via localStorage.
**Best for:** Teams wanting a lightweight, self-hosted analytics layer to capture first-party intent signals (page visits, events) without Google Analytics or a commercial platform, accepting that it does not provide third-party intent data or account de-anonymization.

### ai-lead-scoring-engine
**Stack:** Python / FastAPI / SQLite / Docker | **License:** Open Source  
ai-lead-scoring-engine is a self-hosted B2B lead scoring engine with **136 features** and **tri-dimensional scoring (Fit/Engagement/Intent)** [citation:11]. It includes a **6sense-inspired buying stage pipeline**, a fit-engagement matrix (A1-C3 grid), a sales feedback loop, scoring model templates, negative scoring rules, and account-based scoring (ABM). It runs entirely locally with zero API costs, using local LLM reasoning and a full web dashboard. Features include lead routing, Kanban pipeline board, pipeline velocity metrics, webhook event logs, and GDPR data export/deletion.
**Best for:** Teams wanting a comprehensive, self-hosted lead scoring engine with intent modeling and no per-call data costs, accepting the operational overhead of a Python/FastAPI stack and the need to supply your own data.

### Transparent Lead Scoring
**Stack:** Python | **License:** Open Source  
A lightweight open-source lead scoring tool with **transparent scoring reasons**, a priority-queue dashboard, and Telegram alerts [citation:2]. It is positioned among the 163+ lead-scoring repositories on GitHub, focused on explainable scoring rather than black-box intent prediction.
**Best for:** Small teams wanting a simple, self-hosted lead scoring foundation with explainable results and Telegram notifications.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Intent Data Source | Real-Time | Self-Hosted | Best For |
|----------|---------|-------|---------------------|-----------|-------------|----------|
| **6sense** | Proprietary | Cloud | Proprietary third-party | ✅ | ❌ | Enterprise ABM intent |
| **Demandbase** | Proprietary | Cloud | Proprietary third-party | ✅ | ❌ | ABM + intent execution |
| **Bombora** | Proprietary | Cloud | Cooperative publisher network | (Batch) | ❌ | Third-party topic intent |
| **Leadfeeder** | Proprietary | Cloud | First-party website visits | ✅ | ❌ | Free website visitor ID |
| **looot-intent** | MIT | TypeScript/Next.js | Paid looot API | (On run) | ✅ | Open-source 6sense alternative |
| **looot-crm** | Open Source | Next.js/Supabase | Paid looot API | (On run) | ✅ | CRM + intent signals |
| **tinytraffic** | Open Source | Go/DuckDB | First-party tracking | ✅ | ✅ | Self-hosted analytics |
| **ai-lead-scoring-engine** | Open Source | Python/FastAPI | Your own data | (On run) | ✅ | Comprehensive lead scoring |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Real-Time Customer Intent Signal tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for **third-party intent data** is essentially nonexistent — intent data is a commercial product built on publisher networks and data cooperatives that cannot be replicated by self-hosted software. The available open-source projects fall into two categories: **scoring engines that consume paid data APIs** (looot-intent, looot-crm) and **first-party tracking/scoring tools** (tinytraffic, ai-lead-scoring-engine, Transparent Lead Scoring) that help you capture and model your own signals. **looot-intent** is the most direct open-source attempt at a 6sense alternative, but its code is MIT while its data is paid and the project is extremely early-stage [citation:3][citation:12].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
