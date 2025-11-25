# Final Project: Medical Cost Regression Analysis
**Author:** Kellie Leopold  
**Date:** November 25, 2025  
**Objective:** Predict medical insurance charges using personal and lifestyle factors.

[Link to Medical Cost Regression Notebook](https://github.com/kjleopold/ml_regression_kjleopold/blob/main/ml_regression_kjleopold.ipynb)  
[Link to Peer Review](https://github.com/kjleopold/ml_regression_kjleopold/blob/main/peer_review.md)

---

## Introduction

Medical insurance costs vary for many reasons. Understanding what drives these charges can help providers and policyholders make better decisions. This project uses the Medical Cost dataset to explore how age, BMI, smoking status, number of children, sex, and region relate to insurance charges.

**Project Goals:**

- Explore and understand the dataset  
- Clean, preprocess, and engineer meaningful features  
- Train and evaluate regression models for insurance charge prediction  
- Compare models and interpret results  
- Identify which features most influence insurance costs  

---

## Dataset

- **Records:** 1338  
- **Features:** 7 (age, sex, bmi, children, smoker, region, charges)  
- **Target:** Continuous numeric (`charges`)  

**Observations:**

- Charges are skewed with some extreme values  
- Smoking status strongly influences charges  
- BMI and age show clear relationships with costs  
- Mix of numeric and categorical features  

---

## Features & Preprocessing

**Features used:**

- **age:** numeric, impacts health and insurance costs  
- **bmi:** numeric, linked to health risk and charges  
- **children:** numeric, number of dependents  
- **smoker_yes:** categorical converted to numeric 0/1  

**Interaction Features:**

- **bmi_charges:** BMI × log of charges  
- **smoker_charges:** Smoker × log of charges  
- **bmi_smoker:** BMI × Smoker  

**Preprocessing Steps:**

- Fill missing BMI values with median  
- One-hot encode categorical features  
- Log-transform charges to reduce skew  
- Create interaction features to capture combined effects  
- Scale numeric features in pipelines  

---

## Regression Models Tested

| Model              | Purpose                                           |
|-------------------|---------------------------------------------------|
| Linear Regression  | Baseline model for continuous prediction         |
| Pipeline 1         | Imputer → StandardScaler → Linear Regression     |
| Pipeline 2         | Imputer → Polynomial Features (degree=3) → StandardScaler → Linear Regression |

**Training:** 80/20 train-test split  

---

## Results

| Pipeline     | MAE      | RMSE     | R^2      |
|-------------|----------|----------|---------|
| Pipeline 1  | 1678.92  | 2346.50  | 0.965   |
| Pipeline 2  | 182.77   | 323.57   | 0.999   |

**Insights:**

- Smoking status, BMI, and age are the strongest predictors  
- Interaction and polynomial features significantly improve accuracy  
- Linear Regression handles main trends well; polynomial terms capture complex patterns  
- Pipeline 2 is extremely accurate, but Pipeline 1 is simpler and easier to interpret  

---

## Challenges

- Skewed distribution of charges required log transformation  
- Choosing interaction features without overcomplicating the model  
- Ensuring proper scaling and encoding for regression  

---

## Possible Next Steps

- Explore non-linear models like Random Forest or Gradient Boosting  
- Investigate outliers and unusual cases in the data  
- Experiment with feature selection to simplify the model  
- Test cross-validation for model stability  

---

## Key Learnings

- Feature engineering and interaction terms improve model performance  
- Scaling numeric features stabilizes predictions  
- Polynomial features capture complex relationships beyond linear trends  
- Interpreting results is as important as building models  
- Regression pipelines allow for reproducible and organized workflows  

---

## Set Up Machine

[Link to Instructions](https://github.com/kjleopold/ml_regression_kjleopold/blob/main/SET_UP_MACHINE.md)

## Set Up Project

[Link to Instructions](https://github.com/kjleopold/ml_regression_kjleopold/blob/main/SET_UP_PROJECT.md)

**This includes:** Set Up Virtual Environment (.venv)

Using a VS Code terminal, run the following commands to:

1. Create a local virtual environment using `uv venv`.
2. Pin a Python version. Version 3.12 is recommended for speed, stability, and current compatibility.
3. Install optional tools (for dev and docs) and update packages.
4. Install pre-commit so checks run automatically on each commit.
5. Verify the python version installed is 3.12 (not 3.13 or 3.14).
6. Finally, activate the environment (operating system specific).

```bash
uv venv
uv python pin 3.12
uv sync --extra dev --extra docs --upgrade
uv run pre-commit install
uv run python --version
```

**Windows (PowerShell):**

```bash
.venv\Scripts\activate
```

**macOS / Linux / WSL:**

```bash
source .venv/bin/activate
```

---

## Git pull-add-commit-push

Open a terminal in VS Code (PowerShell, zsh, or bash).

This keeps the local environment and GitHub in sync:
```shell
git pull 
```
This commits all changes made in the local environment to GitHub:
```shell
git add .
git commit -m "Meaningful comment"
git push -u origin main
```
IMPORTANT: Replace the commit message with a clear and descriptive note about what was added or changed.
Wrap the commit message in double quotes.

We can then use `git push` for later commits.
