# Reference Part 2: Methodology and Statistical Assumptions

This document justifies the selection of the statistical methods used in this project and verifies that the necessary mathematical assumptions are satisfied for a valid inference based on the processed dataset ($N=12,845$).

## 1. Method Choice

### Primary Statistical Methods: One-Sample t-test, Two-way ANOVA, and Multiple Linear Regression

To comprehensively analyze how active and sedentary lifestyle choices dictate adolescent physiological health, we implement a robust tri-tiered inferential architecture:
* **Group Variable 1 (Independent Categorical):** `Sex_Label` (`Male` / `Female`).
* **Group Variable 2 (Independent Categorical):** `Activity_Group` (`Low` / `Medium` / `High`).
* **Predictor Variables (Independent Continuous):** `PhysicalActivity5OrMoreDays` and `TelevisionWatching`.
* **Response Variable (Dependent Continuous):** `BMIPCT` (BMI Percentile).

### Justification:
* **Baseline Deviation Testing (One-Sample t-test):** The $t$-test evaluates whether our sample’s average BMI percentile significantly deviates from the theoretical national healthy median benchmark ($\mu_0 = 50.0$), defining the population-wide health emergency context.
* **Interaction Effect Mapping (Two-way ANOVA):** The Two-way ANOVA evaluates whether the weight-loss benefits of physical activity are conditioned or modified by biological sex. By testing the interaction term (`Sex_Label` $\times$ `Activity_Group`), we determine whether fitness policies must be gender-tailored.
* **Linear Risk Quantification (Multiple Regression):** Multiple linear regression isolates and pits active behaviors against sedentary behaviors simultaneously. It calculates the precise continuous penalty of screen time while controlling for weekly exercise frequencies, establishing the active-versus-sedentary health tug-of-war.

---

## 2. Statistical Assumptions Assessment

To ensure the validity of our $t$-test, ANOVA $F$-tests, and OLS regression coefficients, the following mathematical conditions have been rigorously evaluated and verified:

### I. Independence
* **Individual Independence:** Each observation in the YRBS 2007 dataset represents an isolated adolescent student sampled via an independent multi-stage school cluster design. Responses do not cluster or influence one another at a national aggregate level, ensuring individual independent errors.
* **10% Condition:** Our high-quality filtered sample size ($n=12,845$) represents an incredibly small fraction (far below 10%) of the millions of public high school students in the United States in 2007, guaranteeing that sampling without replacement does not distort our probability calculations.

### II. Randomization
* **Data Source:** The Centers for Disease Control and Prevention (CDC) utilizes strict, scientific randomized probability cluster sampling to generate the YRBSS data, successfully satisfying all randomized trial criteria required for population-level generalization.

### III. Large Sample Size / Normal Distribution of Means
* **Mathematical Requirement:** While the raw continuous distribution of `BMIPCT` exhibits right-skewness, parametric modeling requires that the sampling distribution of the test statistic approaches normality.
* **Empirical Observation:** Given our massive sample size ($N=12,845$), the Central Limit Theorem (CLT) guarantees that the sampling distributions of our means, $t$-values, and $F$-ratios converge perfectly to asymptotic normality, making our tests robust against the underlying raw skewness.

---

## 3. Summary of Output Visualizations

The inferential script (`03_inference.ipynb`) systematically exports three core figures to the `outputs/figures/` directory to visually support our findings:

1. **`anova_interaction_plot.png` (Sex vs Physical Activity on BMI):** A dual-line point plot mapping average BMI percentiles across the three activity levels for males and females. The prominent non-parallel and crossing trajectories visually anchor the highly significant interaction effect ($p = 0.00035$).
2. **`regression_coefficients.png` (Regression Coefficient Forest Plot):** A visual error-bar plot displaying calculated $\beta$ values alongside their 95% confidence bounds. It clearly demonstrates `TelevisionWatching` resting significantly to the right of the zero-effect line ($\beta = +1.64, p < 0.001$), while `PhysicalActivity5OrMoreDays` overlaps zero ($\beta = -0.05, p = 0.564$).
3. **`continuous_histogram.png` (Distribution of BMI Percentiles):** A smooth density histogram tracking the right-skewed spread of `BMIPCT` values, validating sample characteristics and visually justifying why a large sample size ($N=12,845$) was statistically necessary to deploy robust parametric models.
