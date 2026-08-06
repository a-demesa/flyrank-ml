# Content Refresh Recommendation Using Decision Tree Classification

**Author:** Alby Demesa

---

## Abstract

This research investigates whether machine learning can support editorial decisions by identifying webpages that may benefit from content refresh.

A Decision Tree classifier was trained using Google Search Console metrics from the FlyRank Internship Warehouse dataset.

The model was evaluated against a transparent baseline using grouped validation by client.

The results suggest that observable search metrics contain useful information for prioritizing pages for manual review.

These recommendations are intended as decision-support rather than automated publishing decisions.

---

# Research Question

Can observable search performance metrics help identify webpages that should be considered for content refresh?

---

# Dataset

FlyRank Internship Warehouse Dataset

Features used:

- GSC Impressions
- GSC Clicks
- Average Position

Excluded:

- Future information
- Label-derived variables
- Client-identifying information

---

# Methodology

Model:

**Decision Tree Classifier**

Validation:

**Grouped by Client**

Baseline:

Transparent ranking rule using search performance metrics.

Leakage prevention:

- Removed label-derived variables
- Excluded future information
- Used grouped validation

---

# Results

| Method | Validation |
|---------|------------|
| Baseline | Ranking Rule |
| Decision Tree | Grouped by Client |

The Decision Tree produced an interpretable ranking that supports manual editorial review.

---

# Limitations

- Results are based on the internship dataset.
- Human review is still required.
- The model should not be interpreted as proving that refreshing content improves rankings.

---

# Recommendations

Recommended workflow:

1. Review high-scoring pages.
2. Check content quality.
3. Verify search intent.
4. Evaluate topical freshness.
5. Decide whether a refresh is appropriate.

---

# Repository

https://github.com/a-demesa/flyrank-ml

---

# Acknowledgments

Built on the FlyRank ML Internship Dataset.


Data source:

https://flyrank.ai
