# Reference Part 1: Variable and Group Definitions

## 1. Variable Coding Reference

The source of the data is the YRBS 2007 Codebook. The raw continuous and categorical values were recoded into appropriate formats (binary, discrete numeric, and structured factors) to facilitate categorical data analysis, analysis of variance (ANOVA), and multiple linear regression modeling.

### Behavior Variable: Activity_Group
We transformed the continuous weekly exercise day frequencies into a structured, three-level categorical factor for analysis of variance.

* **Recoding Logic:**
  * `Low (0-2 days)`: Codes 0 through 2. Represents students who reported being physically active for at least 60 minutes on 2 days or fewer in the past 7 days (Sedentary baseline).
  * `Medium (3-5 days)`: Codes 3 through 5. Represents students who reported being physically active between 3 to 5 days in the past 7 days (Moderate activity).
  * `High (6-7 days)`: Codes 6 through 7. Represents students who reported being physically active 6 to 7 days in the past 7 days (Highly active group).
* **Justification:** This transformation allows us to satisfy the categorical independent variable requirements for a Two-way ANOVA, enabling us to detect non-linear structural thresholds in fitness behaviors rather than assuming a strict linear relationship.

### Behavior Variable: TelevisionWatching (New)
To observe the health risks associated with sedentary screen behavior, the original ordinal CDC television viewing responses were maintained as a discrete numeric ranking variable.

* **Recoding Logic:** Continuous ordinal scales spanning from code `1` (No TV on an average school day) to code `7` (5 or more hours of TV per day), mapped directly as integers to preserve the chronological magnitude of daily screen exposure.
* **Justification:** Converting screen time into sequential ordinal integers allows the regression model to treat the variable as a continuous predictor, dynamically calculating the continuous linear trajectory of sedentary behavior on adolescent BMI percentiles.

---

## 2. Group Definitions

The primary stratified analysis compares independent populations based on biological sex.

* **Exposed Group (1): Female**
  * *Source Code:* `WhatIsYourSex` = 2.
  * *Analytical Label:* Mapped to the string text factor `Female` to serve as a distinct demographic domain for stratified comparison lines.
* **Comparison Group (0): Male**
  * *Source Code:* `WhatIsYourSex` = 1.
  * *Analytical Label:* Mapped to the string text factor `Male` to serve as the baseline comparison demographic.

---

## 3. Summary of Processed Variables

Following the Project Cycle 3 guidelines, our final processed dataset utilizes the following structured format ($N=12,845$):

| Variable Name | Data Type | Value / Label Definition |
| :--- | :--- | :--- |
| **`BMIPCT`** | Continuous | Dependent Variable (Y). Continuous body mass index percentiles ranging from 0.0000 to 100.0000. |
| **`Sex_Label`** | Categorical | Categorical factor with 2 levels: `Male` and `Female`. Used as an independent grouping variable. |
| **`Activity_Group`** | Categorical | Structured factor with 3 levels: `Low (0-2 days)`, `Medium (3-5 days)`, and `High (6-7 days)`. Used for multi-group variance testing. |
| **`TelevisionWatching`** | Ordinal Numeric | Integer sequence ranging from 1 to 7, representing ordinal tiers of daily school-day television viewing. |
| **`PhysicalActivity5OrMoreDays`** | Continuous | Discrete integer counts ranging from 0 to 7, tracking exact days of weekly physical activity for linear regression testing. |

> **Note:** All missing values (`NaN`), blank entries, and invalid response codes across these target vectors were systematically stripped out using an explicit file parser with utf-8 encoding during the data cleaning phase to secure a fully balanced listwise-deletion analytical sample ($N=12,845$) and prevent missing data bias from corrupting the inference models.
