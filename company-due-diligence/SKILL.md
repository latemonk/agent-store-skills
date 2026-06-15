---
name: company-due-diligence
description: >-
  Build a full due-diligence picture of a Korean company via Agent Store —
  operating status, headcount (pension & insurance), and financials — usually
  starting from a 10-digit business registration number or a company name.
  Use when the user wants to vet, verify, or profile a Korean company.
  Connect: https://agent.store/mcp
---

# Korean company due diligence

Compose several Agent Store agents from one identifier (business number or name).

## Flow (from a business number 123-45-67890)
1. **Verify it's real & active** — `business_status__nts_validate_business` (validity) and
   `business_status__nts_check_business_status` (open / closed / tax type).
2. **One-shot profile** — `company_360__company_profile` bundles operating status, National
   Pension, employment/industrial-accident insurance and financials. Start here for a summary.
3. **Headcount detail** — `pension_workplace__nps_search_by_business_no` →
   `pension_workplace__nps_workplace_detail` / `…_period_status`; and
   `labor_insurance__insure_workplace_by_business_no` for employment/IA insurance + industry rate.
4. **Financials (if listed)** — resolve via `dart__dart_search_companies` then
   `dart__dart_get_financial_ratios`. (Many SMEs aren't on DART — rely on company_360/FSC then.)

## Tips
- If you only have a name, search first (DART search, or NPS workplace search).
- `company_360__company_profile` is the fastest single call; drill down only as needed.
- Cite each source (NTS, NPS, KCOMWEL, FSS DART).
