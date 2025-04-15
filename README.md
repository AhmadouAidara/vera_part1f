
# Vera Health Challenge — Part 1 (Structured Version)

## Goal

Design a reliable and interpretable scoring system to rank scientific articles for 11 clinical questions based on citation metrics and physician relevance ratings.

## Project Structure

vera-part1/
├── PART-1_VERA.ipynb         # Full notebook: pipeline, optimizations, charts
├── requirements.txt          # Required packages
└── README.md                 # This file

## How to Run

1. Clone the repo
2. Install dependencies from `requirements.txt`
3. Open `notebook/PART-1_VERA.ipynb` to reproduce the full pipeline and visualizations

## Deliverables

- Final score formula and weighting strategy
- Merged physician rankings (gold standard)
- MSE + NDCG evaluations (global and per question)
- Visual analysis comparing strategies

## Summary of Findings

| Strategy         | NDCG     | MSE     |
|------------------|----------|---------|
| Manual Weights   | 0.885    | 54.43   |
| Optimized MSE    | 0.843    | 53.66   |
| Optimized NDCG   | 0.906    | 54.02   |

Optimizing NDCG offers the best trade-off between reliability and relevance.

## Final Choice: Optimized NDCG Strategy 

Among the three approaches tested, the Optimized NDCG strategy provides the best trade-off between clinical relevance and quantitative reliability. It achieves the highest average NDCG score (0.906), which reflects how well the ranking aligns with physicians’ opinions. While its MSE is slightly higher than the MSE-optimized version, this is acceptable because relevance to clinicians is the top priority in real-world decision support.

Final selected weights:
	•	Publication Type Score: 0.13099
	•	Impact Factor (Normalized): 0.06014
	•	Citation Score: 0.54444
	•	Recency Score: 0.26443

These weights highlight the importance of citation velocity and recency, with a smaller (but non-zero) influence of formal publication type and journal reputation.