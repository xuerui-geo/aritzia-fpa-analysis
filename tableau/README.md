# Tableau Public dashboards

[Open the interactive story on Tableau Public](https://public.tableau.com/app/profile/xuerui.zhang4116/viz/AritziaFPAU_S_ExpansionandProfitableGrowth/Story)

The Share phase is delivered as a Tableau Public story with three dashboards. Each answers one question. All three connect to [`data/Aritzia_FPA_Workbook.xlsx`](../data/Aritzia_FPA_Workbook.xlsx): every sheet is a single tidy table, so no Data Interpreter or reshaping is needed.

| Dashboard | Question | Views | Data sources |
|---|---|---|---|
| 1. Growth | Where is growth coming from? | KPI tiles (71.9% / 80.3% / 20.6%) · U.S. vs Canada revenue · Retail vs Digital quarterly mix · U.S. boutiques and net capex | `KPI_Summary`, `Revenue_Mix`, `Annual` |
| 2. Profitability & Cash | Is growth turning into margin and cash? | Annual margin trends · H1 margin comparison (consistent EBITDA definition) · FY2026 CFO bridge · inventory vs revenue growth | `Annual`, `H1_Comparison`, `Bridges`, `Quarterly` |
| 3. Outlook | What could FY2027 and FY2028 look like? | Scenario fan chart (actual + Base/Upside/Downside) · annual scenario comparison · guidance check · FY2028 sensitivity heat map | `Forecast_Quarterly`, `Forecast_Annual`, `Guidance_Check`, `Sensitivity` |

## Build decisions

- **Ratios are rebuilt as `SUM(numerator) / SUM(Net Revenue)`**, so margins stay correct at any level of aggregation. Pre-computed ratio columns are only used where one row equals one point.
- **Waterfall** (CFO bridge): Gantt bars on the pre-computed `Bar Start`, with size `Bar End − Bar Start`.
- **Scenario fan chart:** actual quarters are repeated in every scenario in `Forecast_Quarterly`, so the three lines share one history and fan out after FY2027 Q2.
- **No dual axes:** measures with different units are stacked as separate panes.
- **Colour has one meaning throughout:** navy = U.S. / current / Base, grey = Canada / prior, teal = Upside / Digital / positive, copper = Downside / items to watch.
- **Conclusion-led titles** and a footnote on every view stating fiscal periods, the Adjusted EBITDA definition and the tariff-refund treatment.
