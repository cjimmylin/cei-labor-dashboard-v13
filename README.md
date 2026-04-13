# AI & Labor: Global Conversation Map — Dashboard v13

Interactive dashboard exploring the global discourse on AI and labor through heatmaps, geographic analysis, temporal trends, and voice gap analysis.

**Live:** https://cjimmylin.github.io/cei-labor-dashboard-v13/

## Data Source

- **Tapestry database**: ~3,253 AI governance statements
- **CEI-Lit-WS**: ~2,368 academic papers
- **Classification**: 17 labor sub-themes via English-language keyword regex heuristics
- **Regions**: 12 geographic regions

## v13 Changes (2026-04-13)

- **Surveillance theme precision corrected**: 51.3% -> 87.2% heuristic-precision (n=117 census)
- Root cause: S15 audit used a 1,500-char scan window; S16 widened to full 10,000-char EXTRACT_CAP
- 42 FP->TP flips on full population, 0 regressions
- 15 residual candidate FPs remain for human adjudication
- Added project explainer card, surveillance callout, methodology diff panel
- Prior version (v12 frozen snapshot): https://cjimmylin.github.io/cei-labor-dashboard/

## Architecture

"Fat Data, Thin Client" -- Python generator pre-computes all analytics into `data.js`; browser JS only renders ECharts charts from pre-computed data.

## Build

```bash
# From CEI-AI-Statements/LABOR/dashboard/
../.venv/bin/python generate_data.py
```

Runtime: ~240s. Output: `data.js` (~50KB).

## SRI Verification

Bootstrap 5.3.3 CSS and ECharts 5.5.0 JS are loaded via CDN with pinned SRI hashes.
Verify with: `python LABOR/PYTHON/verify_sri.py --self-test`

## License

Centre for Ethics and Integrity -- All rights reserved.
