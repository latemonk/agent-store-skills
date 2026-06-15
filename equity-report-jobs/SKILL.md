---
name: equity-report-jobs
description: >-
  How to generate Korean or US equity research reports via Agent Store
  (kr_equity_report__ / us_equity_report__). These run as ASYNC JOBS: create a
  job, poll its status until complete, then deliver — they are not instant. Use
  when the user asks for a full equity research report (PDF/DOCX) on a Korean or
  US listed company. Connect: https://agent.store/mcp
---

# Equity research reports — async job flow

`kr_equity_report__` (Korean listings) and `us_equity_report__` (US listings) generate
a multi-page PDF/DOCX report. The key: it is an **asynchronous job**, so don't expect a
finished report from one call.

## Flow
1. (optional) `…__get_market_status` and `…__get_report_options` — confirm the market is
   covered and which report options/sections exist.
2. `…__search_company` — resolve the ticker / company (don't guess the symbol).
3. `…__create_report_job` — start generation; returns a **job id**.
4. **Poll** `…__get_job_status` with that job id until status is complete/done. Wait
   between polls; do not spam-call or assume it finished immediately.
5. When complete, present the report link/output to the user.

## Tips
- Tell the user it may take a little time (it's generating a full report).
- One job → poll → deliver. Don't create duplicate jobs while one is pending (credits).
- KR vs US: pick the prefix matching the listing market.
