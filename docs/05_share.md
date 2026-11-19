# 5. Share: Communicating the findings

[← Analyze](04_analyze.md) · Next: [Forecast →](06_forecast.md)

## Audience and format

The audience is an FP&A or financial-analysis hiring manager, and by extension a CFO-level reader who needs the answer first and the evidence on demand. The findings are delivered in two layers:

| Layer | Purpose | Link |
|---|---|---|
| Interactive dashboards and story | Conclusion-led story; explore growth, profitability, cash and the forecast by period and scenario | [Tableau Public](https://public.tableau.com/app/profile/xuerui.zhang4116/viz/AritziaFPAU_S_ExpansionandProfitableGrowth/Story) |
| Workbook and notebook | Calculations, definitions and sources behind every number | [Excel](../data/Aritzia_FPA_Workbook.xlsx) · [Notebook](../notebooks/aritzia_analysis.ipynb) |

## Story structure

The story follows four questions:

1. **Where did growth come from?** The U.S. contributed 71.9% of FY2026 incremental revenue and 80.3% in FY2027 H1.
2. **Did profitability improve?** FY2027 H1 Adjusted EBITDA margin was 20.6%, vs 15.5% on the same definition a year earlier. The improvement holds after removing the tariff refund.
3. **How much cash generation is repeatable?** Working capital explains 50.3% of the FY2026 CFO increase. FY2027 H1 free cash flow is C$108.3m without the tariff receipt.
4. **What does it mean for planning?** Model U.S. and Canada separately, keep quarterly seasonality, use margins that exclude refunds, and test inventory and capex needs.

## Tableau dashboards

The Tableau Public workbook has three dashboards, combined in a story:

| Dashboard | Question | Views |
|---|---|---|
| **1. Growth** | Where is growth coming from? | KPI tiles · U.S. vs Canada revenue · Retail vs Digital mix · boutique network |
| **2. Profitability and cash** | Is growth profitable and funded? | Annual margin trends · H1 margin comparison · CFO bridge · inventory vs revenue growth |
| **3. Outlook** | What could FY2027 and FY2028 look like? | Scenario revenue and EBITDA · guidance check · FY2028 sensitivity grid |

Build decisions and data sources for each view are in [`tableau/README.md`](../tableau/README.md).

## Presentation choices

- **Conclusion-led titles:** every chart title states the finding (e.g. "The U.S. became the larger revenue base"), not just the metric.
- **Consistent colour meaning:** navy = U.S. / current period / Base, grey = Canada / prior period, teal = Upside / positive change, copper = Downside / items to watch.
- **Direct labels** on bars and line ends, so colour is never the only cue.
- **Explicit periods and definitions:** fiscal periods, the EBITDA definition and the tariff-refund treatment are stated under every chart.
- **Sources** are noted on each page, with full URLs in the workbook.

## Limitations stated to the audience

Public disclosures do not isolate U.S. boutique profit or investment return. The analysis therefore identifies strong U.S. revenue growth and improving company-level profitability, without claiming that new boutiques *caused* the margin improvement or achieved a specific return on investment.
