# ML4DQM – GSoC 2026 Evaluation Work

I am working on the ML4SCI GSoC 2026 ML4DQM evaluation task.

## Current Status
- Environment setup in progress
- Dataset exploration completed
- CNN baseline model implementation in progress

## Next Steps
- Complete CNN baseline training
- Perform validation checks
- Move toward Vision Transformer (ViT) model

 1️⃣ data_exploration.ipynb
 What was done:

Loaded Run A and Run B datasets

Checked shape and label distribution

Computed statistics (mean, std, min, max)

Key Observations:

Both runs have similar std and max values

Slight difference in mean values

Data ranges are comparable

Conclusion:

Basic statistics alone do not explain cross-run failure. More advanced feature analysis is required.

2️⃣ baseline_cnn.ipynb
What was done:

Built CNN classifier

Trained on mixed Run A + Run B

Evaluated on mixed test set

 Results:

Test Accuracy ≈ 100%

 Conclusion:

The model can easily distinguish between samples when both runs are present in training. This suggests strong separability between runs.

3️⃣ cross_run_validation.ipynb
 What was done:

Trained on Run A only

Tested on Run B only

 Results:

Cross-Run Accuracy ≈ 0%
 Conclusion:

The model does not generalize across runs. It learns run-specific patterns rather than physics-based invariant features.

This indicates strong domain shift between runs.

 4️⃣ per_image_normalization.ipynb
 What was done:

Applied per-image normalization

Repeated cross-run experiment

 Results:

Cross-Run Accuracy ≈ 0%

 Conclusion:

Per-image normalization does not remove run-dependent distribution differences.

Domain shift persists.

 5️⃣ batch_normalization_experiment.ipynb
 What was done:

Added Batch Normalization layers in CNN

Repeated cross-run validation

 Results:

Cross-Run Accuracy ≈ 0%

 Conclusion:

Internal normalization within the model is not sufficient to handle domain shift.

 6️⃣ feature_space_analysis.ipynb (PCA)
What was done:

Extracted CNN features

Applied PCA (2D projection)

Visualized Run A vs Run B

Observation:

Clear separation into two clusters

Minimal overlap between runs

 Final Insight:

The CNN is primarily learning run-dependent detector patterns rather than anomaly-specific features.

This explains:

100% accuracy on mixed data

0% cross-run generalization
