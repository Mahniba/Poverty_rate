##### Poverty Rate Analysis Tool

## Overview
This tool analyzes poverty rates using the Multidimensional Poverty Index (MPI) and investigates relationships between poverty and various socioeconomic factors. The analysis uses machine learning models to identify key predictors of poverty rates across different countries, income groups, and years.

## Features
- Data preprocessing and cleaning for poverty-related datasets
- Descriptive statistical analysis of poverty indicators
- Visualization of poverty rates across countries and years
- Correlation analysis between poverty and socioeconomic factors
- Predictive modeling using multiple regression techniques
- Feature importance ranking to identify key poverty predictors
- Model performance evaluation using RMSE and R² metrics

## Requirements
- Python 3.6+
- Dependencies:
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - scikit-learn
  - warnings

## Dataset Requirements
The code is designed to work with the "TEST IT_ZENITHE.csv" dataset that includes:

### Required Columns
- **MPI**: Multidimensional Poverty Index (target variable)
- **Countries**: Country names
- **Années**: Years
- **Income group**: Income classification of countries
- **informality**: Informality measure
- **Dev fin**: Financial development indicator
- **Control of Corruption**: Governance indicator
- **Government Effectiveness**: Governance indicator
- **Urbanisation**: Urban population percentage
- **Log GDP**: Logarithm of GDP
- **EDUC**: Education measure
- **Croiss Pop**: Population growth

### Optional Columns (for inequality analysis)
- **RN AI 10% les +**: Income share of top 10%
- **RN AI 1% les +**: Income share of top 1%
- **RN AI 50% les -**: Income share of bottom 50%

## Code Structure and Workflow

### 1. Data Loading and Initial Exploration
```python
# Load the data
df = pd.read_csv("TEST IT_ZENITHE.csv")

# Clean column names and explore data
df.columns = [col.strip() for col in df.columns]
print("Dataset Overview:")
print(f"Shape: {df.shape}")
display(df.head())
```

### 2. Data Preprocessing
- Handling missing values with median imputation, using group medians where possible
- Checking for remaining missing values after imputation

### 3. Exploratory Data Analysis
- Statistical summaries of the data
- Distribution plots of numerical features
- Correlation analysis with the poverty rate (MPI)
- Correlation heatmap of all features
- Poverty rate analysis by country and year:
  - Bar charts of average poverty rates by country
  - Heatmap of poverty rates by country and year
- Relationship analysis:
  - Scatter plots of poverty vs. key predictors
  - Boxplots of poverty rates by income group
  - Analysis of wealth inequality metrics (if available)

### 4. Predictive Modeling
- Feature and target definition
- Data preprocessing pipeline setup:
  - Standardization of numerical features
  - One-hot encoding of categorical features
- Train-test split for model evaluation
- Model training and evaluation with multiple algorithms:
  - Linear Regression
  - Ridge Regression
  - Lasso Regression
  - Random Forest
  - Gradient Boosting
- Cross-validation to ensure robust model performance
- Performance metrics calculation (RMSE and R²)

### 5. Model Analysis and Interpretation
- Identification of the best-performing model
- Feature importance analysis:
  - Feature ranking for tree-based models
  - Coefficient analysis for linear models
- Residual analysis to assess model quality
- Visualization of actual vs. predicted poverty rates
- Recommendations of the most influential factors for poverty prediction

## Usage

1. Ensure the "TEST IT_ZENITHE.csv" file is in the same directory as the script
2. Run the script:
   ```
   python poverty_analysis.py
   ```
3. Review the generated visualizations and model results

## Interpreting the Results

The results provide insights into:

1. **Descriptive Statistics**: Understanding the distribution and central tendencies of poverty rates and related factors

2. **Geographic Patterns**: Identifying countries and regions with higher poverty rates

3. **Temporal Trends**: Analyzing how poverty rates have changed over time

4. **Key Relationships**: Understanding which factors show the strongest correlation with poverty

5. **Predictive Factors**: Identifying which variables are most important for predicting poverty rates:
   - For tree-based models (Random Forest, Gradient Boosting): Feature importance values
   - For linear models: Coefficient magnitudes
   - For correlation analysis: Correlation strength with MPI

6. **Model Performance**: Evaluating model accuracy through RMSE (lower is better) and R² (higher is better)

## Customization

To adapt this code for different datasets:

1. Ensure your dataset has similar columns or modify the code to match your column names
2. Adjust the feature selection in the modeling section as needed
3. Modify the visualization titles and labels to match your specific analysis context

## Troubleshooting

### Common Issues:
1. **Missing columns**: Ensure your dataset contains all required columns or modify the code accordingly
2. **Data type issues**: Check that numerical columns are properly formatted
3. **Visualization errors**: Adjust plot sizes and layouts based on your dataset characteristics

### For Large Datasets:
- Consider sampling or chunking the data before analysis
- Adjust figure sizes for better visualization clarity
