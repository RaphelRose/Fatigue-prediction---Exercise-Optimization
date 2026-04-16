## Problem Statement

In current physiotherapy practice, exercise plans are mainly given based on the therapist’s experience, observation, and patient feedback. There is no proper quantitative or computational model to measure muscle fatigue accurately.

Because of this, the prescribed exercises may not always match the patient’s actual muscle capacity. If the exercise intensity or duration is too low, the muscle may be undertrained, leading to slow recovery. On the other hand, if it is too high, it can cause overtraining, resulting in fatigue, strain, or even injury.

Therefore, there is a need for an objective, data-driven system that can accurately predict muscle fatigue and help in prescribing safe and effective exercise levels.

## Proposed Solution

To overcome the limitations of subjective muscle fatigue assessment, this project proposes a **data-driven computational system** that predicts muscle strength, estimates fatigue progression, and provides personalized exercise recommendations.

The system uses patient-specific inputs such as age, gender, activity level, and smoking history. A hybrid approach combining **statistical analysis, machine learning, and mathematical modeling** is used to analyze muscle fatigue and optimize exercise duration.

A **Random Forest regression model** is trained to predict Maximum Voluntary Contraction (MVC), while an exponential fatigue model is used to estimate endurance and safe exercise limits. The system also performs statistical testing and visualization to better understand muscle performance patterns.

---

## System Modules

### 1. Dataset Loading
* The dataset used in this project is obtained from Mendeley Data by Eika, Fredrik and Blomkvist, Andreas Wahl (2019), titled “Reference data on hand grip and lower limb strength using the Nintendo Wii Balance Board: A cross-sectional study of 354 subjects from 20 to 99 years of age”
* Dataset is loaded from an Excel file (`rawdata.xlsx`)
* Contains physiological and lifestyle parameters along with grip force values

### 2. Dataset Description

The dataset contains physiological and lifestyle parameters used to analyze muscle fatigue and predict muscle strength.

Features Description
**Pack Years**
Represents the smoking exposure of the individual over time.
**Activity Level (Work)**

* 1 → Sedentary work (desk job, minimal movement)
* 2 → Light activity (occasional walking, light tasks)
* 3 → Moderate activity (manual tasks, frequent movement)
* 4 → Heavy activity (physically demanding work)

**Activity Level (Spare Time)**

* 1 → No exercise (inactive lifestyle)
* 2 → Light activity (walking, casual movement)
* 3 → Moderate activity (regular exercise)
* 4 → High activity (intense workouts, sports training)

These parameters significantly influence muscle strength, endurance, and fatigue characteristics

---

### 3. Data Cleaning & Preprocessing

* Removal of missing values in force measurements
* Conversion of gender into numerical format
* Handling missing values in activity level and smoking data
* Creation of new labels (e.g., Male/Female)

---

### 4. MVC Computation

* MVC (Maximum Voluntary Contraction) is calculated as:

  * Average of grip force values (`RFD, RFND, RHD, RHND`)
* Represents maximum muscle strength

---

### 5. Outlier Removal

* Outliers are removed using **Interquartile Range (IQR)** method
* Improves model accuracy and reliability

---

### 6. Feature Engineering

* Age grouped into:

  * Young
  * Middle
  * Older
* Helps in statistical comparison and visualization

---

### 7. Statistical Analysis

* **ANOVA test** → compares MVC across age groups
* **T-test** → compares muscle strength between groups
* Helps identify significant influencing factors

---

### 8. Data Visualization

The system generates:

* Correlation heatmap
* MVC distribution histogram
* Boxplots (Age, Gender, Activity vs MVC)
* Feature importance graph

These help in understanding relationships between variables.

---

### 9. Machine Learning Model

* Model: **Random Forest**

* Input features:
  * Age
  * Activity levels (work & spare time)
  * Smoking (packyears)
  * Gender

* Output: Predicted MVC

---

### 10. Fatigue Modeling

* Fatigue is modeled using an **exponential decay function**
* A personalized fatigue coefficient (alpha) is computed using:

  * Age
  * Activity level
  * Smoking history

---

### 11. Safe Exercise Time Estimation

* Safe exercise duration is calculated using fatigue model
* Ensures muscle does not exceed fatigue threshold

---

### 12. Personalized Prediction System

Physiotherapist inputs:

* Age
* Gender
* Activity levels
* Smoking history

System outputs:

* Predicted MVC
* Fatigue coefficient
* Safe exercise time
* Recommended contraction duration
* Rest interval
* Fatigue risk level (Low / Moderate / High)

---

## Key Features

* Combines **ML + Mathematical Modeling + Statistics**
* Personalized fatigue prediction
* Real-time user input-based recommendations
* Visualization for better interpretability


---

## Conclusion

This project presents a comprehensive computational framework for muscle fatigue analysis. By integrating machine learning, statistical analysis, and mathematical modeling, it enables accurate prediction of muscle strength and fatigue, supporting physiotherapists in designing safe and personalized exercise programs.
