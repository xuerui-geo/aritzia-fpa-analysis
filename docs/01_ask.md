# 1. Ask: Defining the business task

[← README](../README.md) · Next: [Prepare →](02_prepare.md)

## Business task

Evaluate Aritzia's recent financial performance and assess whether its U.S. expansion is associated with sustainable, profitable growth.

The project:

- identifies the main drivers of revenue growth
- evaluates profitability and investment trends
- compares an independent forecast with management guidance
- builds scenario-based projections to support FP&A planning

### What "profitable growth" means here

Revenue growth together with stable or improving:

| Dimension | Measured by |
|---|---|
| Gross margin | Gross profit / revenue, excluding one-off tariff refunds |
| Operating profitability | Adjusted EBITDA margin (non-IFRS) on a consistent definition |
| Cost leverage | SG&A as a % of revenue |
| Inventory performance | Inventory growth vs revenue growth; days in inventory |
| Capital efficiency | Net capital expenditures vs revenue; boutique openings |
| Cash generation | Operating cash flow and free cash flow, with and without timing effects |

**Scope boundary:** the project looks at evidence *associated with* U.S. expansion. It does not claim that expansion *caused* revenue or profit growth.

## Stakeholders

| Stakeholder | Business need |
|---|---|
| **CFO / finance leadership** | Know whether growth is improving profitability and financial flexibility |
| **FP&A team** | Build revenue, margin, expense, inventory and capital expenditure forecasts |
| **U.S. retail and expansion leadership** | Check whether the pace of expansion is financially supported |
| Senior management / board | Assess future expansion opportunities and financial risks |
| Investors / equity analysts | Judge the sustainability and quality of growth |

This is a public-data analysis. It does not imply access to Aritzia's internal management information.

## Key business questions

### Primary

1. **What are the main drivers of recent revenue growth?**
   U.S. vs Canada · Retail vs Digital · boutique openings · comparable sales · revenue mix
2. **Has revenue growth turned into stronger operating profitability?**
   Gross margin · SG&A % of revenue · Adjusted EBITDA margin · net income margin · inventory growth vs revenue growth · capital expenditures and cash flow
3. **What financial evidence supports or challenges the sustainability of U.S. expansion?**
   U.S. growth and mix · U.S. vs Canada growth · boutique openings · comparable sales · Digital growth · margin trends · capital investment

### Supporting

4. **What could FY2027 and FY2028 look like under different scenarios?** Base, Upside and Downside cases.
5. **Which risks and KPIs should FP&A monitor?** U.S. revenue growth · comparable sales · gross margin · SG&A % · Adjusted EBITDA margin · inventory growth and turnover · capex · boutique openings · tariffs and FX.

## Planned deliverables

| Phase | Deliverable | Where |
|---|---|---|
| Ask | Business task summary | this document |
| Prepare | Data inventory, data dictionary, source log, quality checks | [02_prepare.md](02_prepare.md), workbook `Data_Dictionary`, `Sources` |
| Process | Cleaning and comparability log | [03_process.md](03_process.md), workbook `Notes` |
| Analyze | Excel FP&A model + Python notebook | [04_analyze.md](04_analyze.md), [`data/`](../data), [`notebooks/`](../notebooks) |
| Share | Tableau Public dashboards and story | [05_share.md](05_share.md), [`tableau/`](../tableau) |
| Forecast | FY2027 and FY2028 scenario model | [06_forecast.md](06_forecast.md) |
| Act | Recommendations and KPIs to monitor | [README](../README.md#recommendations-for-fpa) |

## Project positioning

> This project evaluates whether Aritzia's rapid U.S. expansion is creating sustainable, profitable growth, and develops a scenario-based FP&A outlook to support future planning decisions.
