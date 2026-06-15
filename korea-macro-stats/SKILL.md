---
name: korea-macro-stats
description: >-
  Answer Korean macroeconomic and national-statistics questions via Agent Store —
  base rate, FX, inflation, indicators, and any KOSIS statistic — turning plain
  language into the right time series with charts and a briefing. Use for "how is
  the Korean economy", interest/FX/CPI trends, or any Korea statistic over time.
  Connect: https://agent.store/mcp
---

# Korea macro & national statistics

Two complementary agents: `bok_stats__` (Bank of Korea ECOS — macro/finance time series)
and `national_stats__` (KOSIS — all national statistics). Map plain language → official series.

## Flow
1. **Quick read** — for "today's economy / overview" use `bok_stats__get_today_briefing` or
   `bok_stats__get_top_indicators` (100 key indicators snapshot). Done in one call.
2. **Find the right series** — natural language → `bok_stats__resolve_series` /
   `bok_stats__search_stats` (macro), or `national_stats__stats_search` → `…__stats_info` (KOSIS).
3. **Fetch & transform** — `bok_stats__get_series` (with transforms) or `national_stats__stats_data`.
   Compare multiple with `bok_stats__compare_series`; find neighbors with `…__discover_related_series`.
4. **Explain / visualize** — `bok_stats__explain_series` for prose; `national_stats__stats_visualize`
   or `bok_stats__build_macro_brief` for charts / a themed brief.

## Tips
- Start at the briefing/top-indicators for broad questions; resolve a specific series only when needed.
- Use bok_stats for rate/FX/CPI/monetary/financial series; national_stats (KOSIS) for everything else.
- Always state the base period and units, and cite the source (Bank of Korea ECOS / KOSIS).
