# Aircraft Wildlife Strike Repair Cost Analysis

A machine learning project that predicts aircraft repair costs following wildlife strikes and explores causal relationships between aircraft models and repair expenses using FAA wildlife strike data (1990-2024).

## Overview

Wildlife strikes pose a significant threat to aviation safety and result in substantial financial costs for airlines. This project combines predictive modeling and causal inference to help airlines:

- **Predict repair costs** following wildlife strikes with machine learning models
- **Understand causal factors** that influence repair costs after wildlife encounters  
- **Optimize fleet composition** by analyzing whether specific aircraft models (e.g., Boeing 737) lead to lower repair costs
- **Make data-driven decisions** about risk management and cost mitigation strategies

## Key Features

- **Comprehensive Data Analysis**: Exploration of 30+ years of FAA wildlife strike reports with detailed feature engineering
- **Predictive Modeling**: Multiple ML models (XGBoost, LightGBM, Random Forest, Lasso) to predict inflation-adjusted repair costs
- **Causal Inference**: Advanced causal analysis using meta-learners (S-learner, T-learner, X-learner, R-learner) and DoWhy framework
- **Model Deployment**: Production-ready model with pickle serialization for real-world deployment
- **Interactive Visualizations**: Geospatial heatmaps, damage analysis, and cost distributions
- **SHAP Interpretability**: Model explainability using SHAP values to understand feature importance

## Project Structure

```
Airplane-Repair-Cost/
├── end-to-end-with-deployment.ipynb          # Complete ML pipeline: data cleaning, EDA, training, deployment
├── causal_inference.ipynb                    # Causal inference analysis (Boeing 737 study)
└── README.md                                 # Project documentation
```

## Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- At least 4GB RAM recommended

### Installation

1. Clone the repository:
```bash
git clone https://github.com/galaxyhikes/Airplane-Repair-Cost.git
cd Airplane-Repair-Cost
```

2. Install required packages:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
pip install xgboost lightgbm catboost
pip install statsmodels folium shap
pip install causalml dowhy
pip install openpyxl  # For reading Excel files
```

### Data Setup

1. Download the wildlife strike dataset from the [FAA Wildlife Strike Database](https://wildlife.faa.gov/search)
2. Save the file as `Strike_Reports.xlsx` or note the file path
3. Update the file path in the notebooks when prompted or in the data loading cells

### Project Workflow

#### 1. Predictive Modeling with Deployment

Start with [end-to-end-with-deployment.ipynb](end-to-end-with-deployment.ipynb) for the complete ML workflow:

```python
# The notebook guides you through:
# - Data loading and preprocessing
# - Exploratory data analysis with visualizations
# - Feature engineering
# - Model training and hyperparameter tuning
# - Model evaluation and comparison
# - Model serialization for deployment
```

Run the notebook cells sequentially. Key outputs include:
- Comprehensive EDA with damage patterns and cost distributions
- Trained ML models with performance metrics
- Production-ready serialized model

#### 2. Causal Inference Analysis

Explore [causal_inference.ipynb](causal_inference.ipynb) to understand causal relationships:

```python
# Analyze whether Boeing 737 usage leads to lower repair costs
# Using meta-learners and propensity score matching
```

This notebook investigates whether standardizing fleets with Boeing 737s can reduce overall wildlife strike repair costs.

## Model Performance

The project evaluates multiple machine learning algorithms:

- **XGBoost**: Gradient boosting with high accuracy
- **LightGBM**: Fast training with competitive performance  
- **Random Forest**: Robust ensemble method
- **Lasso Regression**: Baseline linear model with regularization

Models are evaluated using Mean Squared Error (MSE) on log-transformed repair costs.

## Key Findings

Based on the analysis:

1. **Aircraft type significantly impacts repair costs** - Different airframe designs and engine configurations lead to varying damage susceptibility
2. **Boeing 737 shows relatively lower repair costs** despite high wildlife strike frequency, attributed to parts availability and resilient design
3. **Time of day, flight phase, and wildlife size** are important predictive features
4. **Geographic patterns** in wildlife strikes can inform route planning and risk assessment

## Data Features

The analysis considers 40+ features including:

- **Temporal**: Incident month, time of day
- **Location**: Airport ID, latitude/longitude  
- **Aircraft**: Model, class, mass, engine type, number of engines
- **Flight conditions**: Speed, phase of flight, sky conditions, precipitation
- **Damage**: Damage to radome, windshield, nose, engines, propeller, wings, fuselage, landing gear, tail, lights
- **Wildlife**: Species, size, number struck
- **Cost**: Inflation-adjusted repair costs (target variable)

## Data Source

Wildlife strike data provided by the Federal Aviation Administration (FAA):  
[https://wildlife.faa.gov/search](https://wildlife.faa.gov/search)

## License

This project is available for educational and research purposes. Please cite the FAA as the data source when using this analysis.

## Acknowledgments

- Federal Aviation Administration for providing comprehensive wildlife strike data
- The open-source community for the excellent ML and causal inference libraries
- Boeing for historical context on the 737 aircraft family