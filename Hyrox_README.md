# HYROX Results Analysis — Automated Data Pipeline & Analytics

Postgraduate diploma project (AI Analyst 5.0) focused on collecting and analyzing HYROX competition results.

Built an automated workflow in **n8n** to extract data from the official HYROX results website and transfer it into **Supabase**, structured across 5 connected tables. Performed data cleaning, transformation, and exploratory analysis using **Python** and **Marimo**, supported by AI.

## Pipeline

```
results.hyrox.com → n8n (scraping + parsing) → Supabase (PostgreSQL, 5 tables) → Python / Marimo (analysis)
```

## Dataset

- HYROX Doubles · Women 35–39 · Warsaw 2026
- 209 race results, ~4,000 individual data points
- Data quality check: 0 missing values, 0 duplicates, 0 outliers removed — full sample used

## Method

- Hypothesis: does running time correlate with race outcome more strongly than station time?
- Pearson correlation between each performance component and final result
- Steiger's test for comparing two dependent correlations
- R² to quantify explanatory power of each component

## Key finding

Running time correlates with final result far more strongly (**r = 0.96, R² = 0.93**) than station time (**r = 0.84, R² = 0.71**) — a statistically significant difference (Steiger's test, p < 0.001). The finding was translated into a concrete training recommendation: prioritizing running volume gives the largest performance return for this group.

## Tools

n8n · Supabase (PostgreSQL) · Python · Marimo · Statistical hypothesis testing

## Limitations

- Single event, single division, single age group — findings apply to this sample, not to HYROX overall
- Correlation, not causation — running also makes up ~58% of total race time, which naturally strengthens its association with the result
- Penalty data (17.2% of pairs) excluded from the main hypothesis due to unclear whether penalty seconds are already included in recorded times

---

*Author: Aleksandra Dudek · June 2026*
