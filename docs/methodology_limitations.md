# Methodology and limitations

## Analytical workflow

1. Profile source tables and identify schema, missingness, duplicate IDs, and invalid references.
2. Clean and standardize event data in the Silver layer.
3. Build/reuse Gold tables for product funnel, retention, feature adoption, category funnel, category economics, experiments, and daily metrics.
4. Use SQL-derived evidence to answer product questions.
5. Present findings with metric definitions, denominator context, and caveats.
6. Use an AI layer to explain retrieved evidence in accessible language.

## Interpretation rules

- A relationship between two metrics is not automatically causal.
- Report conversion lifts as percentage points when subtracting rates.
- Use relative lift only with the baseline rate visible.
- Distinguish sessions, events, and unique users.
- Distinguish payment attempts from completed payments.
- Treat subgroup findings as exploratory unless pre-specified and appropriately tested.
- Do not report significance without the corresponding statistical test.
- Do not invent confidence intervals, sample sizes, or causal impact estimates.

## AI limitations

The AI layer is an explanation interface, not a replacement for SQL, data validation, or statistical reasoning. Numeric answers should be checked against the supporting evidence. A natural-language explanation may omit context or overstate a result; retain clear metric definitions and limitations.

## Reproducibility

The deployed app relies on an existing Databricks environment, warehouse, permissions, and Gold tables. This documentation alone does not recreate that environment. Add only the actual notebooks, SQL, and dependency files used by the project. Do not publish credentials or private workspace details.
