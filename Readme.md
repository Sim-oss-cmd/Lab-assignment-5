ANALYSIS QUESTIONS.

Explained Variance in PCA

Observation: The explained variance indicates how much of the total data variability is captured by each principal component.

Trend: The first few components capture most of the variance, while later components contribute progressively less.

Example (Wine dataset): In our PCA plot, the first 2–3 components explained a large proportion of the variance (~60–70%), while cumulative variance showed that about 8 components are needed to reach 95% of the total variance.

Implication: You can reduce dimensionality while retaining most information, but too few components may lose significant details.

PCA vs. LDA

PCA:

Unsupervised, ignores class labels.

Finds directions of maximum variance, not necessarily those that separate classes.

Useful for visualization and noise reduction.

LDA:

Supervised, uses class labels.

Finds directions that maximize class separability (ratio of between-class to within-class scatter).

Produces at most C−1 components (here, 3 classes → 2 components).

Comparison:

PCA projections show overlapping clusters in 2D.

LDA projections show well-separated class clusters, leading to better classifier performance.

Conclusion: LDA is generally better as a preprocessing step for classification because it explicitly optimizes class separation, not just variance.

KPCA Gamma Parameter

Observation: γ controls the width of the RBF kernel:

Small γ: The kernel is too broad → all points appear similar → nonlinear patterns are not captured, classes may remain overlapping.

Large γ: The kernel is very narrow → the transformation is highly sensitive to small differences → can overfit, classes may scatter too much or produce noisy projections.

Ideal γ: Moderate value (e.g., γ=15) balances smooth nonlinear mapping and class separability.

Effect on linear separability:

Proper γ transforms data so that classes become linearly separable in the KPCA space.

Too small → insufficient separation.

Too large → unstable projection, possible overfitting.

Classifier Performance

Method: Apply Logistic Regression (or SVM) on:

Original standardized data

PCA-transformed data (2D)

LDA-transformed data (2D)

Observations:

Original data: High accuracy, but more features → higher computation time.

PCA 2D: Lower accuracy because PCA does not optimize class separation; computation is faster.

LDA 2D: High accuracy, often similar to original data, because LDA maximizes class separability while reducing dimensions → fast and effective.

Conclusion: LDA is a better preprocessing step for classification than PCA when the goal is accuracy in low-dimensional space.

Classifier Performance

Method: Apply Logistic Regression (or SVM) on:

Original standardized data

PCA-transformed data (2D)

LDA-transformed data (2D)

Observations:

Original data: High accuracy, but more features → higher computation time.

PCA 2D: Lower accuracy because PCA does not optimize class separation; computation is faster.

LDA 2D: High accuracy, often similar to original data, because LDA maximizes class separability while reducing dimensions → fast and effective.

Conclusion: LDA is a better preprocessing step for classification than PCA when the goal is accuracy in low-dimensional space.

Limitations

When standard PCA fails:

PCA assumes linear variance directions.

Example: make_moons or make_circles datasets → classes are nonlinear. Linear PCA cannot separate the classes, so classification in PCA space performs poorly.

How KPCA addresses nonlinearity:

KPCA uses kernel functions to map data into a higher-dimensional feature space.

Nonlinear patterns in the original space become linearly separable in the kernel space.

Allows linear classifiers to work effectively on nonlinearly separable data."# Lab-assignment-5" 
