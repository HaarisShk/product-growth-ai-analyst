# Business findings and interpretation

This note records the findings captured during project analysis. The source is synthetic/generated data; these findings demonstrate analysis methods and should not be presented as insights about a real company.

## 1. Product funnel

Recorded counts:
- Product-view sessions: 683,245
- Add-to-cart sessions: 87,055
- Checkout sessions: 48,549
- Purchase sessions: 39,149
- Product-view-to-purchase conversion: 5.73%

**Interpretation:** The large difference between product views and add-to-cart activity makes product discovery, product detail quality, pricing, and add-to-cart friction reasonable areas to investigate. The counts alone do not identify the cause.

## 2. Search association

- Search sessions conversion: ~ 6.50%
- Non-search sessions conversion: ~ 2.20%

**Interpretation:** Search use is associated with higher conversion in this dataset. Users who search may have stronger intent or differ in other ways. This is not proof that adding search causes conversion to increase.

## 3. D30 retention and acquisition

- Analyzed cohort: 25,888 users
- Retained users: 1,191
- D30 retention: 4.6006% (about 4.60%)
- Paid Social D30 retention: 2.0262% (about 2.03%)
- Other channels D30 retention: 5.5470% (about 5.55%)

**Interpretation:** Paid Social retention merits further cohort and acquisition-quality investigation. Compare cohort dates, user mix, campaign quality, and eligibility before attributing the gap to the channel itself.

## 4. Feature adoption

- Feature adopters D30 retention: 21.46%
- Non-adopters D30 retention: 3.54%

**Interpretation:** Adoption is strongly associated with retention. This is vulnerable to selection effects: users who are already more engaged may be more likely to adopt. Timing can also create immortal-time bias. A randomized encouragement or carefully designed time-aware analysis would be needed for stronger causal claims.

## 5. Experiments

Recorded experiment results:
- EXP_001: absolute lift +1.14 percentage points; p = 0.001076.
- EXP_002: absolute lift +0.6166 percentage points; p = 0.0521, inconclusive at a conventional 0.05 threshold.
- EXP_003: absolute lift +0.6007 percentage points; p = 0.0994, inconclusive at a conventional 0.05 threshold.

An exploratory subgroup comparison for EXP_002 recorded a negative Android treatment difference (about -1.78 percentage points) and a positive non-Android difference (about +3.19 percentage points). Treat this as exploratory unless the subgroup was pre-specified and the analysis accounts for multiple comparisons.

Do not state that an experiment is statistically significant based on lift alone. Report sample size, metric definition, test method, confidence interval if available, and any multiple-testing considerations when those are known.

## 6. Category funnel

- Home checkout-to-payment-attempt drop-off: 45.10%.

**Interpretation:** Review the checkout and payment-attempt experience for Home category purchases. A payment-attempt event is not a confirmed successful payment; the available metric should not be described as payment success or payment failure without additional evidence.

## 7. Category economics

Recorded figures:
- Electronics: revenue 2.167M; gross profit 256.8K; gross margin 11.85%.
- Fashion: revenue 996.6K; gross profit 545.4K; gross margin 54.72%.
- Beauty: gross margin 57.33%.

**Interpretation:** Electronics is the largest revenue contributor among the figures recorded, but has a lower gross margin than Fashion and Beauty. Validate the underlying units/currency and the gross-profit calculation before publishing the figures externally.

## 8. Promotions

Recorded comparison:
- Promoted sessions were associated with roughly 22% higher conversion.
- Gross margin was about 3 percentage points lower.
- Profit per converted session was about 12–18% lower.

**Interpretation:** Higher conversion alone may not imply better economics. Compare incremental gross profit, promotion costs, discount depth, user mix, and a credible control group before making a causal claim about promotion effectiveness.

## Recommended follow-up questions

1. Which funnel stage has the largest avoidable drop-off, after confirming consistent denominators?
2. Does the Paid Social retention gap persist after cohort-date and user-mix adjustment?
3. Can feature adoption be tested with randomized exposure or time-aware methods?
4. Are category-level profit and margin calculations consistent in currency, costs, discounts, and refunds?
5. Are experiment decisions based on pre-specified metrics, adequate sample sizes, and uncertainty intervals?

## Limitations

- The data is synthetic/generated.
- Observational associations are not causal effects.
- Subgroup experiment findings may be exploratory.
- Some metrics depend on project-specific event and session definitions.
- Numeric summaries should be checked against current Gold-table evidence before reuse.
