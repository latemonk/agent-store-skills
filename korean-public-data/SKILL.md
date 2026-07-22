---
name: korean-public-data
description: >-
  Answer questions about Korea using the Agent Store MCP connector
  (https://agent.store/mcp): corporate filings & financials (DART), statutes &
  regulations, national statistics (KOSIS), Bank of Korea macro data,
  public procurement (KONEPS), real estate & building registries, and
  business verification. Use this skill whenever the user asks about Korean
  companies, Korean law, Korean economic indicators, Korean government tenders,
  Korean addresses/real estate, or needs to verify a Korean business number —
  and the Agent Store connector is available. Picks the right data agent,
  passes the correct identifier, and cites the official source.
---

# Korean Public & Financial Data via Agent Store

Agent Store federates 35+ Korean public- and financial-data MCP agents behind one
gateway. All tools are **read-only** and return source-cited data. Use them instead
of guessing from memory whenever a question is about Korea.

## Pick the right agent

| If the user asks about… | Use tools prefixed | Pass |
|---|---|---|
| Listed-company filings, financials, ratios, peer comparison | `dart__…` | company name / ticker |
| News, global/Korean research, US SEC filings, ETF/company data | `corporate-data__…` | company / ticker / query |
| Statutes, articles, regulations | `law__…` | natural-language legal question |
| National statistics, indicators, charts | `national-stats__…` | plain-language metric |
| Macro: base rate, FX, CPI, time series | `bok-stats__…` | indicator / theme |
| Public tenders / procurement / RFP / bids | `naramarket__…` | notice or query |
| Building registry, permits, assessed price, real estate | `archhub__…`, `apartment__…`, `apply-home__…` | address / region |
| Address ↔ coordinates | `geocoder__…`, `address-search__…` | address |
| Verify a business / closure / tax type | `business-status__…` | 10-digit business number |
| One-shot company profile (status + pension + insurance + financials) | `company-360__…` | business number |
| Pension / employment & accident insurance by workplace | `pension-workplace__…`, `labor-insurance__…` | business number |
| Korean equity research report (PDF/DOCX) | `kr-equity-report__…`, `us-equity-report__…` | ticker / name |
| Standard Korean dictionary definition | `korean-dict__…` | the word |
| Real estate transactions (apt·officetel·rowhouse·detached·commercial·land, sale/rent) | `real-estate-trades__…` | LAWD_CD (5-digit district) + YYYYMM |
| Land-use regulations (what you can build), land-use plan map | `land-use__…` | district code + zone code (UCODE) |
| Construction firm registrations / sanctions / closures (KISCON) | `construction-firms__…` | period + region |
| Capital-market stats & quotes (ETF/ETN/ELW, funds, trust, bonds, ELS/DLS) | `capital-markets__…` | category / product / date |
| Import-export trade statistics by HS code / country | `trade-stats__…` | HS code + month + country |
| Consumer staple prices (참가격) | `consumer-prices__…` | product id |
| Trains / domestic flights / airports / bridges & tunnels | `transport__…` | route / airport / year |
| Vessel port-calls & specifications | `vessel-info__…` | port / vessel name |
| Drugs, medical devices, health-functional foods, food ingredients (MFDS) | `food-drug-safety__…` | product / company name |
| Cosmetic ingredients, makers, functional cosmetics | `cosmetics__…` | ingredient / product |
| Hospitals · clinics · pharmacies (find by region/coords) | `medical-facilities__…` | region or coordinates |
| Clinical trials (CRIS) search / detail / stats | `clinical-trials__…` | query / trial id / year |
| School info · meals · timetables · academies (NEIS) | `school-info__…` | school name → office/school code |
| KCI scholarly papers · authors | `scholar-papers__…` | article id |
| Government startup-support programs (K-Startup) | `startup-support__…` | (page) |
| Livestock auction grades & prices (Hanwoo etc.) | `livestock-grades__…` | period · breed |
| National Assembly bills — search & progress timeline (committee→plenary→promulgation) | `assembly-bills__…` | bill title/proposer, or bill number |

## How to use the tools well
- **Resolve identifiers first.** Many tools need a code: search the company/ticker
  (e.g. `dart__dart_search_companies`), geocode an address, or confirm a business
  number before deeper calls.
- **Summary first, detail on demand.** Start with overview/search tools; only call
  expensive report/analysis tools when the user wants depth. This keeps responses
  token-efficient (the agents are pre-optimized for low token cost).
- **Always cite the source** returned by the tool (e.g. "Source: FSS DART").
- **Read-only & metered.** Tools never write to external systems; each call consumes
  the org's credits. Don't loop redundant calls.
- **Korean data, any language.** Tool inputs accept Korean or English; present
  results in the user's language with original Korean names where useful.

## Example flows
- "Compare Samsung's ROE to peers" → `dart__dart_search_companies` → `dart__dart_get_financial_ratios` / `dart__dart_compare_peers`.
- "Is this business still operating?" → `business-status__nts_check_business_status` (→ `company-360__company_profile` for the full picture).
- "Today's Korea economy" → `bok-stats__get_today_briefing`.
- "Building history for <address>" → `archhub__find_region` → `archhub__building_profile` / `archhub__parcel_history`.
- "Analyze this tender" → `naramarket__search_bid_notices` → `naramarket__analyze_rfp`.

## Setup
Connect the Agent Store connector at `https://agent.store/mcp` (OAuth sign-in).
Enable the agents you need in the console at agent.store. Docs: https://agent.store/docs/connect/
