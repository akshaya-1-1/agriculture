# Agri AI Project

Machine Learning-Based Crop Yield Risk Forecasting and Agricultural Decision Support System.

## Project Overview

This project analyzes crop yield stability and agricultural risk using historical crop production, rainfall, and soil health data.

The work begins with data integration and statistical analysis, followed by risk analysis using yield variability. The final stage uses a rolling-window forecasting framework where historical crop performance is used to predict future yield instability.

## Data Sources

The project uses:

- Crop production data
- Rainfall data
- Soil health data

These datasets are processed and integrated to form a state-crop-year dataset containing features related to production, area, yield, rainfall, and soil conditions.

## Dataset Flow

Two integrated datasets are retained because they represent different stages of the project:

- `data/final/agri_combined_dataset.csv`  
  Original integrated dataset used during the initial analysis.

- `data/final/agri_combined_datasets.csv`  
  Updated/cleaned dataset used for the later risk modelling and forecasting stages.

During cleaning, the total number of missing cells was reduced from **2,223 to 30**.

The remaining missing values are:

- Area: 15
- Production: 15

The yield, rainfall, and soil variables used in the forecasting models contain no missing values.

## Project Workflow

```text
Raw Crop + Rainfall + Soil Data
            ↓
Data Processing and Integration
            ↓
mca_agri_ai.ipynb
            ↓
Original Integrated Dataset
agri_combined_dataset.csv
            ↓
mca_agri_ai_copy.ipynb
            ↓
Updated / Cleaned Dataset
agri_combined_datasets.csv
            ↓
Week3.ipynb
            ↓
risk_model_week4.ipynb
            ↓
WEEK5.ipynb
            ↓
forecasting_rolling_complete.ipynb
            ↓
Final Forecasting Results
```

## Project Structure

```text
.
├── data/
│   ├── raw/
│   ├── processed/
│   └── final/
│       ├── agri_combined_dataset.csv
│       └── agri_combined_datasets.csv
│
├── outputs/
│
├── mca_agri_ai.ipynb
├── mca_agri_ai_copy.ipynb
├── Week3.ipynb
├── risk_model_week4.ipynb
├── WEEK5.ipynb
├── forecasting_rolling_complete.ipynb
└── README.md
```

## Notebook Description

### `mca_agri_ai.ipynb`

Initial data preparation and exploratory analysis.

Main tasks include:

- Data integration
- Missing-value analysis
- Descriptive statistics
- Yield trend analysis
- Rainfall analysis
- State-wise and crop-wise analysis

### `mca_agri_ai_copy.ipynb`

Used during the data updating and cleaning stage.

This notebook works with the original integrated dataset and generates the updated dataset used in the later stages of the project.

### `Week3.ipynb`

Statistical and hypothesis-based analysis of crop yield stability.

Includes:

- Mean yield analysis
- Standard deviation
- Coefficient of Variation (CV)
- Temporal robustness analysis
- Rainfall-yield relationship
- Stability and variability analysis

### `risk_model_week4.ipynb`

Development of the agricultural risk framework.

Includes:

- State-crop level mean yield
- Standard deviation
- Coefficient of Variation
- Normalized CV
- Risk categorization
- Risk distribution analysis
- Yield-risk comparison

### `WEEK5.ipynb`

Machine-learning-based risk analysis and explainability.

Includes:

- Random Forest classification
- Model comparison
- Cross-validation
- Confusion matrix
- Classification metrics
- Feature importance
- SHAP analysis
- Risk-based advisory outputs

### `forecasting_rolling_complete.ipynb`

Final forecasting notebook.

Historical crop behaviour is used to forecast instability in a later period.

The notebook includes:

- Rolling historical windows
- Historical mean yield
- Historical yield CV
- Rainfall mean
- Rainfall standard deviation
- Rainfall CV
- Soil features
- Random Forest models
- Logistic Regression baseline
- Expanded rolling evaluation
- Strict walk-forward validation
- Final 2019-2022 holdout evaluation
- Feature importance analysis

## Forecasting Setup

Example rolling-window structure:

```text
2012-2014 features → 2015-2017 instability
2013-2015 features → 2016-2018 instability
2014-2016 features → 2017-2019 instability
...
```

A total of **150 possible rolling samples** were generated, of which **140 valid samples** were used.

The final future holdout uses:

```text
2016-2018 historical features
            ↓
2019-2022 future instability
```

## Final Model Results

### Expanded Rolling Evaluation

| Model | Balanced Accuracy |
|---|---:|
| Mean Yield Only | 0.429 |
| Mean + Historical CV | 0.448 |
| Full Climate + Soil Model | 0.533 |

### Strict Walk-Forward Validation

| Model | Balanced Accuracy |
|---|---:|
| Mean Yield Only | 0.396 |
| Mean + Historical CV | **0.429** |
| Full Climate + Soil Model | 0.354 |

### Final 2019-2022 Holdout

| Model | Accuracy | Balanced Accuracy |
|---|---:|---:|
| Mean Yield Only | 0.348 | 0.404 |
| Mean + Historical CV | 0.391 | **0.461** |
| Full Climate + Soil Model | 0.391 | 0.380 |
| Random Baseline | 0.327 | 0.326 |

The model using **historical mean yield and historical CV** achieved the strongest balanced accuracy on the final future holdout.

## Feature Importance

| Feature | Importance |
|---|---:|
| Historical Yield CV | 0.126 |
| Historical Mean Yield | 0.094 |
| Rainfall Standard Deviation | 0.070 |
| Mean Rainfall | 0.069 |
| Rainfall CV | 0.059 |

Historical yield variability was the strongest individual feature, while rainfall variability also contributed information to the model.

## Key Findings

- Historical yield variability provides useful information for forecasting future crop instability.
- Mean yield alone is not sufficient to characterize agricultural risk.
- The Mean + Historical CV model performed best under strict temporal validation and on the final holdout.
- Rainfall and soil features provide additional information, but they do not consistently improve forecasting performance across all validation settings.
- Temporal validation is important when evaluating agricultural forecasting models.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- SHAP
- Jupyter Notebook

## Outputs

The `outputs/` folder contains:

- Yield and rainfall plots
- Hypothesis-testing outputs
- Risk distribution plots
- Model comparison results
- Confusion matrix
- Feature importance outputs
- SHAP plots
- Advisory tables

## Final Notebook

For the latest forecasting implementation and final model results, refer to:

`forecasting_rolling_complete.ipynb`