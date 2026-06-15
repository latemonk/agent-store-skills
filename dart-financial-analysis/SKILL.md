---
name: dart-financial-analysis
description: >-
  Deep playbook for Korean listed-company financial analysis using the Agent
  Store DART tools (dart__). Use when the user wants in-depth analysis of a
  Korean listed company: financial ratios, financial statements, distress
  screening, peer benchmarking, major shareholders, or a full analysis report.
  Connect: https://agent.store/mcp
---

# DART — Korean listed-company financial analysis

The `dart__` tools wrap Korea's Financial Supervisory Service DART. Read-only,
source-cited, credit-metered. Work from cheap → expensive.

## Recommended order
1. **Resolve the company** — `dart__dart_search_companies` (name → corp code). Don't
   guess codes.
2. **Snapshot** — `dart__dart_get_company_overview` for the basics.
3. **Numbers** — `dart__dart_get_financial_statements` (raw) or, better for analysis,
   `dart__dart_get_financial_ratios` (47 ratios + 4 distress-prediction models in one call).
4. **Benchmark** — `dart__dart_compare_peers` for same-sector ranking, or
   `dart__dart_get_multi_company_financials` for a specific set. Use
   `dart__dart_scan_market` only for broad cross-market screens (heavier).
5. **Filings** — `dart__dart_search_disclosures` / `dart__dart_search_periodic_reports`
   → `dart__dart_get_disclosure_detail` / `…_document` for the source text.
6. **Deep report (expensive, long-running)** — `dart__dart_generate_financial_report` or
   `dart__dart_generate_screening_report`. Only when the user wants a full written report;
   warn that it costs more credits and may take longer.

## Tips
- The ratios tool already includes distress models — don't recompute by hand.
- Always cite "Source: FSS DART" and the fiscal year.
- Peer comparison needs the sector; if unknown, the overview/ratios tools infer it.
