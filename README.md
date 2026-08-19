# Smartphone Addiction Prediction

A machine learning classification project developed for a Kaggle competition to predict whether a user is classified as addicted to smartphone usage based on behavioral and demographic features.

## Problem Statement

The objective of this project is to predict the `addicted_label` of a user.

- `0` → Not Addicted
- `1` → Addicted

The model uses information such as daily screen time, social media usage, gaming hours, sleep, app usage, notifications, stress level, gender, and academic work impact.

## Dataset

The dataset contains behavioral and demographic information about smartphone usage.

### Features

| Feature | Description |
|---|---|
| `age` | User age |
| `daily_screen_time_hours` | Average daily smartphone screen time |
| `social_media_hours` | Hours spent on social media |
| `gaming_hours` | Hours spent gaming |
| `work_study_hours` | Hours spent on work/study |
| `sleep_hours` | Daily sleep duration |
| `notifications_per_day` | Number of notifications received per day |
| `app_opens_per_day` | Number of application openings per day |
| `weekend_screen_time` | Smartphone usage during weekends |
| `gender` | User gender |
| `stress_level` | Reported stress level |
| `academic_work_impact` | Whether smartphone usage impacts academic/work activities |
| `addicted_label` | Target variable |

The dataset was provided through a Kaggle competition and is not included in this repository.

## Project Workflow

The project follows the following machine learning workflow:

1. Load and inspect the dataset
2. Perform exploratory data analysis
3. Check missing values and duplicates
4. Clean and preprocess the data
5. Separate features and target
6. Split the training data into training and validation sets
7. Train a Logistic Regression baseline
8. Train a Random Forest classifier
9. Evaluate the models using classification metrics and ROC-AUC
10. Analyze feature importance
11. Train the final Random Forest model
12. Generate predictions for the Kaggle test dataset
13. Create the final submission file

## Data Cleaning

The following preprocessing steps were performed:

- Removed the `id` column because it is an identifier rather than a predictive feature.
- Checked for duplicate records.
- Investigated missing values.
- Numerical missing values were handled using median imputation.
- Categorical missing values were handled using the most frequent category.
- Checked categorical values for consistency.
- Investigated numerical ranges for invalid values.
- The target variable was kept separate from the input features.

For the final modeling workflow, preprocessing was handled through a Scikit-learn pipeline to maintain consistent transformations between training, validation, and test data.

## Models

### Logistic Regression

Logistic Regression was used as a baseline classification model because it is simple, fast, and provides an interpretable benchmark.

### Random Forest

Random Forest was selected as the main model because the dataset is tabular and may contain nonlinear relationships and interactions between behavioral features.

## Model Performance

Validation results obtained during development:

| Model | Accuracy | ROC-AUC | Recall (Class 1) | F1 (Class 1) |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.84 | 0.9145 | 0.91 | 0.89 |
| Random Forest | 0.87 | 0.9417 | 0.92 | 0.91 |

Random Forest performed better than Logistic Regression on the validation dataset.

> Note: These are local validation results, not the official Kaggle leaderboard score.

## Feature Importance

The Random Forest model identified the following features as the most important:

| Feature | Importance |
|---|---:|
| `daily_screen_time_hours` | 0.2535 |
| `weekend_screen_time` | 0.1883 |
| `social_media_hours` | 0.1867 |
| `work_study_hours` | 0.0736 |
| `gaming_hours` | 0.0599 |
| `app_opens_per_day` | 0.0527 |
| `sleep_hours` | 0.0513 |
| `notifications_per_day` | 0.0511 |
| `age` | 0.0349 |

These values represent model feature importance and should not be interpreted as proof of causal relationships.

## Kaggle Submission

The final submission file contains:

```text
id,addicted_label
