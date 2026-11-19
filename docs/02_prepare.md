# 2. Prepare: Data requirements, sources and quality

[← Ask](01_ask.md) · Next: [Process →](03_process.md)

The aim of this phase was not to draw conclusions. It was to make sure the data collected could answer the Ask questions:

**Business questions → data requirements → official sources → data inventory → quality check**

## Step 1: Business questions → data requirements

| Business question | Data needed |
|---|---|
| What drives revenue growth? | Total, U.S., Canada, Retail and Digital revenue; comparable sales; boutique counts |
| Has growth improved profitability? | Gross profit, SG&A, Adjusted EBITDA, net income, inventory, operating cash flow |
| Is U.S. expansion sustainable? | U.S. revenue and mix, boutique openings by country, capital expenditures, margins |
| What could future performance look like? | Historical quarterly data, management guidance, margin trends, inventory, capex |

**Scope:** annual FY2022 to FY2026; 14 standalone quarters from FY2024 Q1 to FY2027 Q2; FY2027 management guidance as of 8 October 2026.

## Step 2: Official sources

| Priority | Source | Documents used |
|---|---|---|
| Primary | [Aritzia Investor Relations](https://investors.aritzia.com/financial-reports/default.aspx) | Annual reports, audited financial statements, quarterly results releases, interim statements, MD&A, investor presentations |
| Secondary | SEDAR+ | Annual Information Forms (boutique counts by country) |

Every figure is traced to a document. The workbook's `Sources` sheet lists all 59 documents with URLs, including the cash-flow statement page used for each quarter.

## Step 3: Data inventory and dictionary

Each metric was first recorded as reported, before any growth rates or margins were calculated. Later these records were consolidated into the tidy tables of [`Aritzia_FPA_Workbook.xlsx`](../data/Aritzia_FPA_Workbook.xlsx):

| Attribute recorded | Example |
|---|---|
| Fiscal period | FY2026 |
| Metric | Net revenue |
| Geography | Consolidated / U.S. / Canada |
| Channel | Total / Retail / Digital |
| Reported value | 3,702.148 |
| Unit | C$ million (source reports C$ thousands) |
| Source document and page | FY2026 Annual Report, MD&A |
| Reported or calculated | Reported |
| Note | Fiscal year ended 1 March 2026 (52 weeks) |

The `Data_Dictionary` sheet records each of the 287 fields with:

- definition and unit
- source type (reported, calculated, analyst assumption or management guidance)
- classification (IFRS, non-IFRS, operating metric or calculated ratio)
- the correct aggregation rule in Tableau

### Fiscal calendar

| Fiscal year | Year end | Weeks |
|---|---|---|
| FY2022 | 27 Feb 2022 | 52 |
| FY2023 | 26 Feb 2023 | 52 |
| FY2024 | 3 Mar 2024 | **53** (Q4 = 14 weeks) |
| FY2025 | 2 Mar 2025 | 52 |
| FY2026 | 1 Mar 2026 | 52 |
| FY2027 H1 | 30 Aug 2026 | 26 |

## Step 4: Quality check

| Check | Result |
|---|---|
| All monetary figures in Canadian dollars? | Yes. U.S. revenue is reported in C$ and includes FX translation. |
| C$ thousands vs millions kept separate? | Source values are in thousands and are converted once to C$ million at full precision. |
| FY2026 treated as calendar 2026 by mistake? | No. Fiscal years are named by the year in which they end, and period-end dates are stored. |
| Revenue recorded as period flows? | Yes. Quarters sum to annual totals, as checked in the notebook. |
| Inventory and cash recorded as ending balances? | Yes. They are never summed across periods. |
| Adjusted EBITDA flagged as non-IFRS? | Yes. Its definition also changed in FY2027 (see [Process](03_process.md)). |
| Metrics available only for some years? | FY2022 comparable sales are not disclosed. Adjusted EBITDA on the FY2027 definition exists only from FY2025 Q3. FY2023 quarterly channel revenue and FY2021 Adjusted EBITDA were added later to complete FY2024 and FY2022 comparisons (see [Process](03_process.md)). |
| Did definitions change? | Yes: Adjusted EBITDA (FY2027) and the comparable-sales eligible base. Boutique counts exclude Reigning Champ. |

### Missing data (not publicly disclosed)

- U.S. or Canada operating profit
- Store-level profitability, capex, opening costs and payback
- Boutique opening cohorts and new-store ramp profiles
- U.S. Digital vs U.S. Retail split
- Constant-currency U.S. growth

### Data quality notes

- FY2027 H1 covers 26 weeks, not a full fiscal year. Compare it only with FY2026 H1.
- Revenue and cash flows are period measures. Inventory, cash and boutique counts are point-in-time measures.
- Adjusted EBITDA is a non-IFRS measure, and the company redefined it from FY2027 Q1.
- FY2024 contains a 53rd week, which inflates FY2024 growth and depresses FY2025 growth.
