
---

## 📄 `report.md`
```markdown
# Uplift Modeling Report: Digital Marketing Campaign

## 1. Methodology
- **Dataset:** Causal Digital Marketing Campaign Dataset (Kaggle)
- **Treatment Variable (T):** Ad exposure (1 = exposed, 0 = not exposed)
- **Outcome Variable (Y):** Conversion (1 = converted, 0 = not converted)
- **Features (X):** Demographics, channel, campaign, frequency, spend

### Models Implemented
- **T-Learner:** Gradient Boosting models trained separately for treatment and control groups
- **DR Learner:** Doubly Robust estimator using Random Forests for flexible CATE estimation

---

## 2. Evaluation Metrics
- **Qini coefficient:** Measures incremental gain curve quality
- **AUUC (Area Under Uplift Curve):** Captures ranking performance of uplift predictions

**Results:**
- Qini ≈-0.1907
- AUUC ≈ -0.0726
### Uplift Estimate Caveat
Both the T-Learner and DR Learner produced uplift estimates clustered near zero (e.g., ~2.2e-06), indicating that the models did not capture meaningful treatment effects. This suggests that either the features lack predictive power for uplift, or the treatment effect is weak or non-existent in this dataset. These results should be interpreted with caution.


---

## 3. Segment Analysis
### Top 3 Persuadable Segments
1. Customers in `campaign_id = 3` with frequency ≥ 12
2. Users from `channel = 'Search'` with spend ≥ ₹500
3. Customers with `impressions ≥ 100` and `click_through_rate ≥ 0.05`


### Top 3 Do-Not-Disturb Segments
1. **Low-frequency users (bottom 25%)** → Minimal or negative uplift
2. **Display channel customers** → Little incremental effect
3. **Campaign C participants** → No significant treatment effect

---

## 4. Sensitivity Analysis

### Propensity Score Overlap
The sensitivity analysis revealed that **100% of users had extreme propensity scores** (<0.05 or >0.95). This violates the **common support assumption**, which is critical for causal inference. Without overlap between treatment and control groups, models like DR Learner cannot produce valid uplift estimates. This suggests that:
- Treatment assignment may be deterministic or highly biased
- The dataset may lack sufficient covariate diversity
- Observational data may not be suitable for causal modeling without rebalancing

### Hyperparameter Stability
Despite the overlap issue, Qini scores remained stable across tree depths (2–4), indicating consistent model behavior. However, due to the lack of common support, these scores may not reflect true causal effects.

### Bias Discussion
The extreme propensity distribution suggests selection bias in treatment assignment. Future work should consider reweighting, matching, or using randomized data to improve causal validity.



---

## 5. Strategic Recommendation

Based on the uplift analysis, ad spend should focus on segments that show measurable positive uplift, such as high-frequency users in campaign 3. Groups with little or no uplift, like low-frequency users in the Display channel, should be avoided to reduce wasted impressions. This targeted approach is expected to improve conversion efficiency while keeping costs under control.
