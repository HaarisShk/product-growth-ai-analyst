# Data and metric dictionary

## Source entities

| Entity | Recorded size | Intended role |
|---|---:|---|
| `users` | 100,000 × 6 | User attributes and segmentation |
| `products` | 5,000 × 6 | Product metadata |
| `sessions` | 992,464 × 6 | Session-level activity |
| `events` | 9,536,511 × 13 | Event-level behavior |
| `experiments` | 3 × 10 | Experiment assignments/metadata |
| `releases` | 9 × 5 | Product release metadata |

These counts are recorded project counts, not guarantees about a future refresh. Refer to the actual schema and notebooks for full column names and types.

## Layers

- **Bronze:** raw ingested records.
- **Silver:** cleaned records; duplicate event IDs removed. Recorded Silver event count: 9,498,495.
- **Gold:** analytics-ready tables used by the app.

## Metric definitions

Confirm these definitions against the SQL in the repository before changing or publishing them.

| Metric | Working interpretation | Caution |
|---|---|---|
| Product-view-to-purchase conversion | Purchase sessions divided by product-view sessions in the defined funnel | State the denominator and session definition |
| Funnel step count | Sessions reaching each defined event/step | Counts across steps are not necessarily mutually exclusive users |
| D30 retention | Cohort users who returned on the defined day-30 rule divided by eligible cohort users | Document cohort entry date and return window |
| Feature adoption | Users meeting the project's feature-use rule | Adoption is not randomly assigned |
| Revenue | Revenue summed under the project's event/order definition | Confirm currency, refunds, and duplicate-order handling |
| Gross profit | Revenue less the cost component defined by the model | Confirm the cost fields and units |
| Gross margin | Gross profit divided by revenue × 100 | Not the same as markup |
| Checkout-to-payment-attempt drop-off | Checkout sessions that do not reach the defined payment-attempt event, divided by checkout sessions | Attempt does not mean payment succeeded |
| Experiment absolute lift | Treatment conversion rate minus control conversion rate | Report in percentage points |
| Experiment relative lift | (Treatment rate − control rate) / control rate × 100 | Can look large when baseline rate is small |

## Data quality notes

- Raw event IDs had 38,016 duplicated IDs, involving 76,032 rows, before deduplication.
- Silver event records: 9,498,495; unique event IDs after deduplication: 9,498,495.
- Product references outside the known product ID range were identified during validation. Review the data-quality notebook for the handling decision.
- Some event fields are naturally sparse because they only apply to particular event types. Missing `payment_status`, `quantity`, `product_id`, or `price` should be assessed by event type, not automatically treated as a global data defect.

Do not claim that every data-quality issue was resolved unless the committed validation code demonstrates it.
