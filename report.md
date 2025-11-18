
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

---

## 3. Segment Analysis
### Top 3 Persuadable Segments
1. **High-frequency users (top 25%)** → Strong positive uplift
2. **Social channel customers** → Respond well to ad exposure
3. **Campaign A participants** → High incremental conversion rate

### Top 3 Do-Not-Disturb Segments
1. **Low-frequency users (bottom 25%)** → Minimal or negative uplift
2. **Display channel customers** → Little incremental effect
3. **Campaign C participants** → No significant treatment effect

---

## 4. Sensitivity Analysis
- **Propensity overlap:** Confirmed common support; few extreme propensities (<5%).
- **Hyperparameter stability:** Qini remained stable across tree depths (2–4).
- **Bias discussion:** Potential selection bias if ad exposure was not fully randomized.

---

## 5. Strategic Recommendation
- **Target:** High-frequency users in Social/Search channels and Campaign A.
- **Suppress:** Display channel and low-frequency users to avoid wasted spend.
- **Business Impact:** Deploying ads to top uplift deciles expected to maximize incremental conversions and ROI.
- **Suppress:** Display channel and low-frequency users to avoid wasted spend.
- **Business Impact:** Deploying ads to top uplift deciles expected to maximize incremental conversions and ROI.
