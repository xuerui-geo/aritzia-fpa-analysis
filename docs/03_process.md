# 3. Process: Cleaning, comparability and the data model

[← Prepare](02_prepare.md) · Next: [Analyze →](04_analyze.md)

## Comparability rules

These rules apply everywhere in the project, in Excel, Python and Tableau.

| Issue | Treatment |
|---|---|
| Annual and quarterly periods differ in length | Compare annual with annual, a quarter with the same quarter last year, and H1 with H1. Never compare a quarter with a full year. |
| Seasonality | Quarterly growth is always year-over-year. FY2027 Q1 is compared with FY2026 Q1, never with FY2026 Q4. |
| 53-week FY2024 | Flagged in every annual growth comparison. Days in period (371 for FY2024; 98 for FY2024 Q4) are used for inventory days. |
| Flows vs balances | Revenue, profit and cash flows are summed. Inventory, cash and boutique counts take the period-end value. |
| Multi-period margins | Summed earnings divided by summed revenue, never an average of quarterly percentages. |
| Geography vs channel | U.S./Canada and Retail/Digital are two alternative splits of the same revenue, so they are never added together. |

## Adjusted EBITDA definition change

From FY2027 Q1, Aritzia excludes foreign-exchange gains and losses on intercompany balances from Adjusted EBITDA. The FY2027 Q2 MD&A restates FY2025 Q3 to FY2026 Q4 on the new basis.

| Series | Treatment |
|---|---|
| `Quarterly › Adj. EBITDA (Comparable)` | Restated values from FY2025 Q3 onward; earlier quarters keep the original definition, labelled in `EBITDA Basis` |
| `Annual › Adj. EBITDA (As Reported)` | Original reported series FY2022 to FY2026 (used for long-run trends) |
| FY2026 comparison base | Sum of the four restated quarters = **C$659.670m (17.82%)**, vs C$646.202m (17.5%) as reported |

The C$13.5m difference is definitional, not operating growth. The latest H1 comparison (FY2026 H1 vs FY2027 H1) and the forecast both use the FY2027 definition.

## Tariff refund (FY2027 Q2)

Aritzia recognised a **C$97.437m** tariff refund recovery in FY2027 Q2 gross profit and received it in cash.

- Reported Q2 gross margin is 57.1%; **excluding the refund it is 48.7%**. The forecast uses margins that exclude refunds.
- The company's Adjusted EBITDA already excludes the refund, so it is **not** deducted again.
- Cash sensitivities subtract the gross receipt and hold cash taxes unchanged. These are analyst sensitivities, not company-defined measures.

## Cleaning log

| Item | Problem | Fix |
|---|---|---|
| FY2022 boutique counts by country | First entry was 68 Canada / 41 U.S. | Corrected to **67 / 39** (total 106) from the FY2023 AIF "Measured Boutique Growth" chart, printed p.19 |
| Quarterly net cash | Some cash balances were matched to shifted or repeated dates | Each balance re-matched to its reporting date. FY2024 Q2 net cash is negative because of C$100m of bank indebtedness. |
| Quarterly free cash flow | Mixed definitions across quarters | Recomputed for every quarter on the company definition (CFO + credit interest − lease principal − net capex), so quarters reconcile to annual totals |
| Q4 cash-flow items | Only annual and nine-month figures are disclosed | Q4 = annual − nine-month year-to-date, for working-capital impact and lease principal |
| FY2026 SG&A ratio | An early raw entry showed 30.6% | Recomputed from reported amounts: 1,075.570 / 3,702.148 = **29.05%**. All ratios are now formulas, not typed values. |
| FY2024 current liabilities | Presentation changed in FY2025 | FY2024 year-end uses the FY2025 comparative (includes an 8.195 reclassification of deferred share units) |
| Comparable sales | Quarters do not sum exactly to annual (FY2024: 0.555; FY2026: 0.005) | Both official disclosures kept and the difference documented, rather than forcing a reconciliation |
| FY2022 comparable sales | Not disclosed (pandemic comparability) | Left blank, not zero |
| Units | Sources in C$ thousands | Converted once to C$ million at full thousand precision (e.g. 462.665) |
| FY2024 Retail / Digital YoY and FY2024 H1 growth | FY2023 quarterly channel revenue was missing | Added FY2023 Q1 to Q4 retail and eCommerce revenue from the official quarterly releases (Q3 retail derived as net revenue − eCommerce). The quarters reconcile exactly to FY2023 annual totals, and the resulting FY2024 growth rates match the company-reported figures. |
| FY2022 EBITDA bridge | FY2021 Adjusted EBITDA was missing | Added FY2021 Adjusted EBITDA of 76.812 from the FY2021 full-year release |
| FY2026 Adjusted EBITDA growth (forecast sheet) | FY2025 was never restated in full to the FY2027 definition | Calculated on the original definition for both years (+59.0%), with a cell note |
| Zero vs blank | Zeros displayed as "-" looked like missing data | Zeros now display as 0.0. Remaining blanks (FY2022 comparable sales; FY2022 to FY2025 Adjusted EBITDA on the FY2027 definition) were never disclosed by the company and carry an explanatory cell comment. |

## Tidy data model

The workbook was restructured from "metrics as rows, periods as columns" into tidy tables (one record per row, one field per column, a single header row, no merged cells). The same file therefore opens cleanly in Excel, Tableau Public and pandas.

| Sheet | Grain | Rows |
|---|---|---:|
| `Quarterly` | One fiscal quarter | 14 |
| `Annual` | One fiscal year | 5 |
| `Revenue_Mix` | Period × dimension (Geography / Channel) × segment | 76 |
| `H1_Comparison` | First half of each fiscal year | 4 |
| `Bridges` | Waterfall step | 11 |
| `Forecast_Assumptions` | Scenario × forecast quarter (inputs) | 18 |
| `Forecast_Quarterly` | Scenario × quarter (actual + forecast) | 36 |
| `Forecast_Annual` | Scenario × fiscal year | 9 |
| `Sensitivity` | U.S. growth change × gross-margin change | 9 |
| `Guidance_Check` / `Guidance_Requirements` | Measure / guidance case | 6 / 3 |
| `Benchmark` | Backtest quarter | 6 |
| `KPI_Summary` | Headline KPI | 40 |

Calculated columns are live Excel formulas (1,845 in total, with no errors after recalculation). Hardcoded inputs are blue, same-sheet formulas black and cross-sheet links green. Key forecast assumptions are highlighted yellow.

### Validation

- Quarterly revenue, CFO, capex and working-capital impact sum to the annual totals for FY2025 and FY2026.
- U.S. + Canada = Retail + Digital = net revenue for every period.
- Boutique roll-forward (opening + openings − closures + conversions = ending) closes every year, and U.S. + Canada = total.
- Every calculated value in the new workbook matches the earlier analysis sheets (0 mismatches).
- The pandas forecast rebuild in the notebook matches the Excel model to within 0.000001.
