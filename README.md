# DataCamp Data Scientist Certification - Practical Exam

This repository contains my submission for the DataCamp Data Scientist Professional Practical Exam. It focuses on predicting recipe traffic to optimize homepage features and drive website subscriptions.

Complete details of the certification can be found [here](https://www.datacamp.com/certification/data-scientist).

---

## Project Overview: Recipe Site Traffic

### Business Goal
The objective is to predict which recipes will lead to **high website traffic** when featured on the homepage. 
* **The Impact:** Featuring a popular recipe on the homepage can increase overall site traffic by up to **40%**, directly boosting new subscriptions.

---

## Navigating the Ambiguous Business Target

The practical exam project brief came with a somewhat vague success target:
> *"Correctly predict high-traffic recipes $\ge 80\%$ of the time."*

This requirement is open to two distinct mathematical interpretations, representing different business strategies:

### Option 1: Precision-Focused Approach (The Chosen Strategy)
* **Definition:** Out of all the recipes we predict as "High Traffic" and display on the homepage, at least 80% must actually turn out to be high traffic ($\text{Precision} \ge 80\%$).
* **Business Justification:** Homepage real estate is highly valuable. Showing a low-traffic recipe on the homepage results in a wasted slot and lost subscription opportunities. A precision-focused strategy minimizes False Positives (predicting high traffic for a recipe that performs poorly).

### Option 2: Recall-Focused Approach
* **Definition:** Out of all the actual high-traffic recipes in the pool, the model must successfully identify and capture at least 80% of them ($\text{Recall} \ge 80\%$).
* **Business Justification:** This aims to discover as many high-traffic recipes as possible. However, to capture 80% of actual high-traffic recipes, the model's classification threshold must be lowered (e.g., to `0.42` in our Logistic Regression model). This increases the rate of False Positives, leading to more low-traffic recipes being featured on the homepage.

### How I Chose the Approach
I chose to prioritize **Option 1 (Precision)**. Here is why:
1. **Homepage Value:** The business metric that matters most to stakeholders is the **Homepage High-Traffic Recipe Precision Rate** (the proportion of featured recipes that succeed). A false positive has a high opportunity cost.
2. **Model Performance:** Our tuned Logistic Regression model naturally achieves **85% precision** at a default threshold of `0.50` (on test data), comfortably exceeding the 80% requirement. If we forced a recall-focused threshold of `0.42`, it would degrade overall precision and dilute the homepage performance.
3. **Internal vs. Business Metrics:** I evaluated models internally using **AUC (ROC)** because it is threshold-independent, but reported **Precision** to the business, ensuring that 85% of featured recipes are high performers.

---

## Repository Structure

* `notebook.ipynb`: The end-to-end Jupyter Notebook containing data validation, exploratory data analysis (EDA), feature engineering, model tuning (Logistic Regression and Decision Trees), and final comparisons.
* `recipe_site_traffic_2212.csv`: The raw dataset containing recipe nutritional metrics, categories, servings, and traffic flags.
* `client_request_project_brief.pdf`: The official practical exam project guidelines and specifications.
* `recipe_presentation.pptx`: The stakeholder presentation deck summarizing the findings and model recommendation.
* `certificates/`: Contains the PDF certificates and verification links for both the Data Scientist Associate and Professional certifications.
