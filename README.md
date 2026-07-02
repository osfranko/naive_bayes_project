# Naive Bayes NBA Player Longevity Prediction

## Project Overview
This project implements a **Gaussian Naive Bayes classifier** to predict whether an NBA rookie will have a career lasting at least 5 years in the league (`target_5yrs = 1`).

**Business Goal**: Assist scouting departments in identifying high-potential talent while minimizing financial risk from "busts" (false positives) and missed opportunities (false negatives).

## Dataset
- **Filename**: `nba_data.csv` (used in notebook)
- **Samples**: 1,340 NBA rookies
- **Target Variable**: `target_5yrs` (binary: 1 = ≥5 years, 0 = <5 years)
  - 62% positive class (long career)
  - 38% negative class
- **Features**: 10 continuous metrics (`fg`, `3p`, `ft`, `reb`, `ast`, `stl`, `blk`, `tov`, `total_points`, `efficiency`)

**Data Status**: Cleaned and engineered (no missing values, 12 duplicates noted but retained for modeling).

## Methodology
1. **Data Loading & Inspection** — Confirmed target and class balance.
2. **Preprocessing** — Feature-target split, correlation analysis.
3. **Train-Test Split** — 80/20 stratified split.
4. **Model** — Gaussian Naive Bayes (`sklearn.naive_bayes.GaussianNB`).
5. **Evaluation** — Confusion Matrix, Precision, Recall, F1-Score.
6. **Assumption Analysis** — Discussed independence and Gaussian distribution assumptions.

## Model Performance

| Metric              | Value   | Business Interpretation |
|---------------------|---------|-------------------------|
| Accuracy            | 0.6381 | 63.81% overall correct |
| **Precision**       | **0.8000** | Excellent — 80% of predicted long-career players actually succeed (Strong for avoiding busts) |
| Recall              | 0.5542 | Moderate — Catches 55.4% of true long-career players |
| **F1-Score (macro)**| **0.64** | Balanced performance |

**Key Insight**: High Precision makes the model valuable as a **conservative risk filter** for scouting.

## Top Predictive Features
- `total_points` (strongest)
- `reb` (Rebounds)
- `tov`, `fg`, `efficiency`

## Assumption Analysis
- **Independence Assumption**: Violated (e.g., points, rebounds, efficiency are correlated). Still, the model performs adequately due to robustness of GaussianNB.
- **Gaussian Distribution**: Features are mostly right-skewed. Visual distributions were analyzed.

## Visualizations Included
- Confusion Matrix
- Predicted probability distribution
- Feature distributions (Gaussian check)
- Correlation heatmap
- Boxplots of key features vs target

## Scouting Recommendations
- Use the model for **initial screening** of draft prospects and free agents.
- Combine with expert scouting, video analysis, and advanced metrics.
- Retrain periodically with new season data.
- Consider ensemble methods for improved Recall in future iterations.

## Repository Contents
- `naive_bayes_nba.ipynb` — Fully executed Jupyter Notebook with all code, outputs, and visualizations.
- `README.md` — This documentation.
- `.gitignore` — Excludes data files.

## Technologies
- Python, pandas, scikit-learn, matplotlib, seaborn

**Status**: All cells executed, outputs visible, ready for review.

---

**Project demonstrates end-to-end classification workflow with strong business interpretation for sports analytics.**
