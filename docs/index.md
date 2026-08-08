# Capstone Report — Content Refresh Recommendation Using Decision Tree Classification

- **Author:** Angeline de Mesa
- **Lane:** Content Refresh Recommendation
- **Repo:** https://github.com/a-demesa/flyrank-ml
- **Date:** August 2026

---
# Abstract

This project investigates whether machine learning can support FlyRank's content refresh workflow by helping identify webpages that may benefit from editorial review. A Decision Tree classifier was developed using observable Google Search Console metrics from the FlyRank Internship Warehouse dataset. The model was compared with a transparent baseline using grouped validation by client to reduce data leakage. The observed results suggest that search performance metrics can help prioritize webpages for manual review. These findings are intended to support editorial decision-making and should not be interpreted as automated publishing decisions.

---
# Introduction

FlyRank manages large collections of website content, making it difficult for editors to manually determine which pages should be refreshed first. This project explores whether observable search performance metrics can help prioritize webpages for editorial review. By using an interpretable Decision Tree model and honest validation practices, this work aims to provide decision-support that helps content teams focus their efforts while acknowledging the limitations of the available data.

---
## 1. Problem framing

This project supports the decision of which webpages should be reviewed for possible content refresh.

The unit of analysis is an individual webpage in the FlyRank internship dataset.

The output is a ranked recommendation score that prioritizes pages for manual review.

A content editor can use the ranked list to identify pages that may benefit from refreshing.

The cost of a wrong recommendation is spending time updating pages that may not improve search performance or overlooking pages that actually need attention.

Machine learning helps identify patterns across many observations that would be difficult to recognize manually.

---
## 2. Data safety

The project uses the FlyRank Internship Warehouse dataset.

The primary features include:

- gsc_impressions
- gsc_clicks
- gsc_avg_position

The following were intentionally excluded:

- Future performance information
- Label-derived variables
- Client-identifying information
- trend_direction
- trend_pct

Client identifiers were only used for grouped validation and never as model features.

No client names, URLs, or private search queries appear anywhere in this project.

---
## 3. Baseline

The baseline model used a transparent scoring rule based primarily on Google Search Console impressions.

Pages with higher impressions received higher priority for manual review.

The baseline produced a ranked recommendation list that served as the comparison for the Decision Tree model.

Both approaches were evaluated on the same dataset and validation design.

---
## 4. Model / analysis

The final model is a Decision Tree classifier.

This method was selected because it is easy to interpret and produces understandable decision rules.

The model uses:

- gsc_impressions
- gsc_clicks
- gsc_avg_position

The target variable indicates whether a webpage received at least one Google Search click.

Several fields were intentionally excluded to reduce the possibility of data leakage.

---
## 5. Evaluation

Grouped validation by client_hash_id was used to reduce leakage between training and testing data.

Model performance was compared directly against the baseline using the same split.

The grouped validation produced an observed accuracy of 1.00 on the sampled dataset.

Error analysis suggests that future evaluation on larger datasets would provide a more reliable estimate of generalization performance.

---

# Results

The Decision Tree was compared with the Week-4 baseline using the same sampled dataset, validation split, and accuracy metric.

| Method | Accuracy |
|---|---:|
| Week-4 Baseline | 1.00 |
| Decision Tree | 1.00 |

![Baseline vs Decision Tree Accuracy](../work/baseline_vs_model_accuracy.png)

Both approaches achieved an observed accuracy of 1.00 on the sampled validation data. This result should be interpreted cautiously because the target variable is whether a page received at least one click, and the evaluation used a sampled dataset. The result does not demonstrate that the model will generalize to new data or that refreshing a page will improve its future search performance.

---
## 6. Interpretation

The Decision Tree relied primarily on impressions, clicks, and average search position.

These features appeared to contain useful information for identifying pages that may deserve review.

The model provides decision-support rather than proof that refreshing content will improve future search performance.

No causal relationship is claimed.

---
## 7. Recommendation

The ranked recommendations should be used as a starting point for editorial review.

Editors should manually verify:

- content quality
- topical relevance
- business importance
- search intent

The recommendations should not be applied automatically.

Confidence in the recommendations is moderate because they were evaluated only on the internship dataset.

---
## 8. Reproducibility

Clone the repository.

Open each notebook under work/notebooks.

Run all notebook cells from top to bottom.

The project uses fixed random seeds where appropriate.

The required Python packages are listed in requirements.txt.

All reported results can be regenerated by executing the notebooks.

---

## Claims checklist

- All claims use observed, measured, or decision-support language.
- No causal claims are made.
- No client-identifying information appears.
- Metrics were reproduced from notebook executions.
- Recommendations require human review before action.
  
---

## Acknowledgments & Data Credit

Built on the FlyRank ML Internship dataset.

Data source: [FlyRank](https://flyrank.ai)
