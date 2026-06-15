# Agent Store — Claude Skills

Skills that help Claude use the **Agent Store** MCP connector (https://agent.store/mcp)
for Korean public & financial data. Connect via OAuth; enable agents in the console.

## Skills
- **korean-public-data** — umbrella router: which agent to use for any Korea question
  (companies, law, statistics, macro, procurement, real estate, business verification),
  with identifier resolution and source citation. Start here.
- **dart-financial-analysis** — deep playbook for Korean listed-company financial
  analysis (ratios, distress screening, peer benchmarking, reports) via `dart__` tools.
- **equity-report-jobs** — the async create→poll→deliver flow for Korean/US equity
  research reports (`kr_equity_report__` / `us_equity_report__`).

Docs: https://agent.store/docs/connect/
