# Agent Store — Claude Skills

Task playbooks that help Claude (and any MCP client) use the **Agent Store** connector
(https://agent.store/mcp) for Korean public & financial data. Connect via OAuth; enable
agents in the console. Also exposed by the gateway as MCP resources (resources/read).

## Skills
- **korean-public-data** — umbrella router: which agent for any Korea question. Start here.
- **dart-financial-analysis** — Korean listed-company ratios, distress screening, peers, reports (`dart__`).
- **equity-report-jobs** — async create→poll→deliver flow for KR/US equity research reports.
- **company-due-diligence** — verify & profile a Korean company from a business number (status + pension + insurance + financials).
- **korean-real-estate** — buildings, permits, assessed price, apartment transactions, new-home subscriptions, from an address.
- **commercial-district-analytics** — store density / industry mix within a radius, polygon, or trade zone.

Docs: https://agent.store/docs/connect/
