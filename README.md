# Final Project

## 👤 Student Information
* **Name:** 顏名萱
* **Student ID:** 113370212
## Project Repository
https://github.com/mandyapple66-dotcom/Final-Project.git
## Presentation Video
https://youtu.be/hNrv8sCSXds
---

## 📊 Dataset Used
* **Dataset:** Youth Risk Behavior Surveillance System (YRBSS) 2007, curated by the Centers for Disease Control and Prevention (CDC).
* **Final Analytical Sample Size ($N$):** 12,845 valid cases (after listwise deletion of missing responses during the data cleaning phase).

---

## 🔍 Selected Variables
Our statistical workflow maps the delicate balance between active and lifestyle habits using the following variables:
* **Dependent Variable ($Y$):** `BMIPCT` (Continuous Body Mass Index Percentile, ranging from 0 to 100).
* **Independent Variable ($X_1$):** `PhysicalActivity5OrMoreDays` / `Activity_Group` (Continuous weekly exercise days / Binned into `Low`, `Medium`, and `High` categories for variance testing).
* **Independent Variable ($X_2$):** `TelevisionWatching` (Discrete ordinal tiers of daily school-day television viewing hours, ranging from 1 to 7).
* **Control/Stratifier Variable:** `Sex_Label` (Categorical: `Male` or `Female`).

---

## 🎯 Benchmark Values
* **Benchmark Mean ($\mu_0$):** **`50.0`** * *Context:* The theoretical national median/mean benchmark for adolescent BMI percentiles. A healthy population should center tightly around the 50th percentile.

---

## ❓ Core Research Questions

#### **ANOVA Research Question:**
* Do an adolescent's **weekly physical activity levels** (categorized as Low, Medium, and High) and their **biological sex** significantly influence their BMI percentiles? Furthermore, does a significant **interaction effect** exist between these physical activity levels and biological sex?

#### **Regression Research Question:**
* Do an adolescent's **television watching hours** and **weekly exercise days** concurrently serve as significant predictors of their BMI percentiles?

---

## 🏁 Short Final Conclusion



Through a fully articulated data science pipeline, this project delivers three critical insights:
1. **The Overweight Shift:** A One-Sample $t$-test proves that the cohort's average BMI percentile (**`64.85`**) severely overshoots the healthy national baseline of `50.0` ($p < 0.001$), highlighting a prominent youth health emergency.
2. **The Sex-Exercise Interaction:** Two-way ANOVA successfully maps a highly significant interaction effect between gender and fitness groups ($p = 0.00035$). This establishes that weight responses to exercise are fundamentally non-linear and gender-dependent.
3. **The Sedentary Hazard:** Multiple Linear Regression isolates a fierce behavioral tug-of-war where daily screen exposure aggressively drives up body mass ($\beta = +1.64, p < 0.001$), while continuous linear exercise days hold no direct baseline effect ($p = 0.564$).

**Public Health Takeaway:** One-size-fits-all fitness campaigns are ineffective. Interventions must deploy **gender-tailored precision designs**—prioritizing strict screen-time limits for female students while expanding active fitness and physical programs to maximize weight-loss benefits for male students.
