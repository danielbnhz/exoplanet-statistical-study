# Exoplanet Controversy Classification Study
## Project Overview

This project investigates whether measurable exoplanet characteristics can help predict whether a planet’s detection is flagged as “controversial” in NASA’s Exoplanet Archive dataset.

## The central question:

__Can physical and observational features of exoplanets statistically explain controversy status?__

The target variable (pl_controv_flag) is highly imbalanced (~0.4% positive), making this a rare-event classification problem.

## Methodology

The analysis includes:

Feature engineering (log transformations of skewed variables such as mass and orbital period)

Encoding of detection methods

Model training using tree-based classifiers

Evaluation using ROC-AUC, Precision-Recall curves, and calibration analysis

Exploratory distributional analysis of key physical parameters

Because of extreme class imbalance, performance was evaluated primarily using Precision-Recall metrics rather than accuracy.

## Key Findings
1. Model Performance

  ROC-AUC: ~0.94
The model demonstrates strong ranking ability, effectively distinguishing controversial from non-controversial cases.

  Average Precision (PR-AUC): ~0.047
Baseline precision is ~0.004, meaning the model performs roughly 11x better than random guessing in identifying rare controversial cases.

  Calibration:
Probability outputs are overconfident and would benefit from post-hoc calibration (e.g., isotonic regression or Platt scaling).

Overall, the model captures meaningful structure despite the rarity of the positive class.

2. Feature Behavior

Distributional analysis shows:

Planet radius (pl_rade) and orbital period (pl_orbper) exhibit strong overlap between classes.

Planet mass (pl_bmasse) shows comparatively more variation among controversial cases.

This aligns with astrophysical intuition: mass estimation is often more uncertain and model-dependent than orbital period measurements, potentially increasing the likelihood of dispute.

However, single-variable separation is weak. The model’s predictive strength appears to arise from multivariate interactions rather than obvious marginal differences.

## Interpretation

The results suggest that controversy is not strongly explained by intrinsic planetary characteristics alone. Instead, controversy likely reflects:

Measurement uncertainty

Detection methodology

Model assumptions

Observational limitations

Scientific disagreement or follow-up validation issues

This indicates that controversy is partly a methodological phenomenon layered on top of astrophysical data.

Limitations

Severe class imbalance

Lack of direct uncertainty metrics in baseline features

Potential sociological factors (publication dynamics, follow-up studies) not captured in the dataset

Future work could include incorporating uncertainty bounds, citation metadata, or detection instrument information.

## Takeaways

This study demonstrates:

Proper handling of imbalanced classification

Use of ROC and Precision-Recall analysis

Calibration assessment

Distributional exploration

Thoughtful interpretation beyond surface metrics

Rather than optimizing for accuracy, the analysis focuses on statistical signal, structure, and interpretability in a rare-event setting.