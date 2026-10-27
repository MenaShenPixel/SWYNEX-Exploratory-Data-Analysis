# Superstore Exploratory Data Analysis (Excel)

Exploratory analysis of the Superstore sales dataset: summary statistics, trends, patterns and anomalies, with five business insights.

## Dataset
- Source: cleaned Superstore dataset from Task 1 ([link to Task 1](link))
- 51,252 order lines | 25,035 orders | 795 customers | 2011-2014
- Total sales: $12.63M | Total profit: $1.46M | Profit margin: 11.6%

## Tools
Microsoft Excel: PivotTables, PivotCharts, Data Analysis formulas (AVERAGE, MEDIAN, STDEV.S, QUARTILE.INC, SKEW, CORREL).

## Workbook structure

| Sheet | Content |
|---|---|
| `superstore` | Cleaned data (Excel Table `Sales_Data`) plus added analysis columns |
| `Tables & analysis` | PivotTables: category, region, market, segment, ship mode, top/least products, customers, YoY |
| `insights` | The five insights |
| `Statistics` | Descriptive statistics and correlation matrix |
| `Anomalies` | Outlier detection (IQR and Z-score) |
| `Charts` | Visualizations |

## Key statistics

| Variable | Mean | Median | Skewness |
|---|---|---|---|
| Sales | 246.43 | 85 | 8.15 |
| Profit | 28.58 | 9.24 | 4.16 |
| Shipping Cost | 26.37 | 7.79 | 5.86 |
| Quantity | 3.48 | 3 | 1.36 |

The data is strongly right-skewed: the mean is well above the median because of a small number of very large orders.

**Correlations:** Sales-Shipping Cost 0.77 (strong), Sales-Profit 0.48 (moderate), Quantity-Profit 0.10 (weak).

## Trends
- Sales: $2.26M (2011) to $4.30M (2014). YoY growth: +18.5%, +27.4%, +26.3%.
- Profit: $248K (2011) to $504K (2014). YoY growth: +23.8%, +32.5%, +24.0%.
- Margin stayed around 11-12% throughout.
- Seasonality: December and November are the strongest months.

## Anomalies
- IQR method flagged **9,753** profit outliers (19%), Z-score (|z| > 3) flagged **864** (1.7%).
- IQR flags more because most profit values sit near zero, which makes the interquartile range very narrow.
- No outliers were removed, because they are genuine transactions.

## Insights
1. **Tables is the only loss-making sub-category.** Margin of -8.5% despite $757K in sales. Likely driven by discounts and shipping costs, so review its pricing and discount policy.
2. **Discounted orders lose money.** -$412K profit vs +$1.88M for non-discounted orders. Set a maximum discount cap.
3. **Some top sellers are unprofitable.** Motorola Smart Phone, Cordless and Hoover Stove, White rank among top sellers and among the least profitable products.
4. **EMEA has the weakest margin.** 5.4% vs 10-13% in other markets. Investigate discounts and shipping costs.
5. **Growth comes from volume, not profitability.** Profit roughly doubled from 2011 to 2014 while margin stayed flat.

## Data cleaning notes
- `Customer.ID` has 4,873 values for 795 customers, so customers are counted by `Customer.Name`.
- `Sales` values are rounded to whole numbers, and one row has a sales value of zero. Margins on very small sales lines can be unstable.
- Columns added for the analysis: `Ship Days`, `IQR Flag`, `Profit Z`, `Z Flag`.

## Limitations
- Because the discount percentage is missing, the discount insight is based on the True/False flag only.
- Likely causes for Tables and EMEA (discounts, shipping) are hypotheses and were not tested.

## How to use
Open the workbook in Excel. If the PivotTables do not refresh, use `Data > Refresh All`.