# Agri AI Project

Machine Learning-based Decision Support System for Agricultural Crop Selection and Yield Forecasting.

## Project Overview

This project focuses on developing a machine learning-based agricultural decision support system using historical crop production, rainfall, and soil health data. The work evolved from a risk-aware crop recommendation model to a forecasting framework that predicts crop suitability while considering climate variability.

## Datasets

- Crop Production Dataset
- Rainfall Dataset
- Soil Health Dataset

The datasets are merged to create a unified dataset containing crop, district, state, production, yield, rainfall, and soil-related features.

## Project Structure

```
.
├── data/
│   ├── final/
│   ├── processed/
│   └── raw/
├── outputs/
├── Week3.ipynb
├── risk_model_week4.ipynb
├── WEEK5.ipynb
├── forecasting model.ipynb
├── mca_agri_ai.ipynb
└── README.md
```

## Notebooks

### Week3.ipynb
- Exploratory Data Analysis
- Yield stability analysis
- Rainfall analysis
- Statistical insights

### risk_model_week4.ipynb
- Risk-aware crop recommendation
- Mean Yield
- Standard Deviation
- Coefficient of Variation (CV)
- Risk categorization

### WEEK5.ipynb
- Machine learning models
- Random Forest classification
- Cross-validation
- Performance evaluation
- SHAP feature importance

### forecasting model.ipynb (Latest)
This notebook contains the latest version of the project.

Key improvements include:
- Reframing the work as a forecasting model.
- Sample expansion using rolling-window forecasting.
- Rainfall incorporated as a climate variability feature.
- Feature engineering for historical crop performance.
- Model evaluation using Accuracy, Precision, Recall and F1-score.
- Future crop suitability forecasting.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- SHAP
- Jupyter Notebook

## Outputs

The `outputs` folder contains:
- Plots
- Model evaluation results
- Advisory tables
- Performance metrics

## Future Work

- Weather forecast integration
- Satellite imagery
- Deep learning models
- Web-based farmer advisory system
