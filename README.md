
# Composite Stock Investment Attractiveness Index (CSIAI)

Data-driven stock attractiveness ranking system built using 21 normalized indicators across five financial dimensions to deliver a transparent composite index for U.S. equities.

## Project Overview

**CSIAI** ranks listed U.S. stocks by computing a composite score based on:

- Financial Strength
- Growth Potential
- Market Performance
- Risk & Volatility
- Liquidity & Trading Activity

Each dimension is constructed from indicators drawn from financial fundamentals and market data. The final index supports **both equal-by-group** and **PCA-based variance** weighting.


## Key Features

- **Multi-dimensional indicator system** across five financial categories
- **Multiple imputation** using Bayesian Ridge + Rubin’s rule
- **Min-Max scaling** after Yeo-Johnson power transformation
- **PCA-based** weighting driven by explained variance + loadings
- **Composite index** built via linear and geometric aggregation
- **Correlation validation** against SPY, QUAL, MTUM benchmarks
- **Visual summaries**: scree plots, radar charts, bar decompositions

---

## Data Sources

- [Yahoo Finance](https://finance.yahoo.com) via [`yfinance`](https://pypi.org/project/yfinance/)
- Stock universe filtered from the Russell 3000
- Historical range: `2023-01-01` to `2025-05-06`
- All indicators sourced from free public APIs or derived from raw financials

---

## Methodology Summary

| Step                      | Methods Used                                                                 |
|---------------------------|------------------------------------------------------------------------------|
| Data Collection           | yfinance pull + custom feature engineering                                   |
| Missing Data              | Iterative Imputer (Bayesian Ridge), Rubin’s Rule                            |
| Normalisation             | PowerTransformer (Yeo-Johnson) + MinMaxScaler                               |
| Indicator Validation      | KMO, Bartlett’s Test, Pearson correlation                                   |
| Redundancy Check          | PCA loadings, dendrograms, silhouette scores                                |
| Weighting                 | Equal-by-group (adjusted) and PCA-based variance weighting                  |
| Aggregation               | Linear (main) and geometric (robustness)                                    |
| Benchmark Validation      | Spearman correlation with SPY, QUAL, MTUM returns                           |
| Visualisation             | Radar charts, top-10 tables, sub-index decompositions, correlation heatmaps |

---

## Installation & Setup

> Python ≥ 3.9 is recommended.

```bash
# Clone repository
git clone https://github.com/PatrickOrjieh/csiai-project.git
cd csiai-project

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

---

## License

This project is for academic, non-commercial use. MIT License.
