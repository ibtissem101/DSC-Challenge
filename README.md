# Fish Market Weight Prediction

## Project Overview
This project analyzes the Fish Market dataset to build predictive models for fish weight based on physical measurements. The dataset contains measurements of various fish species commonly found in markets, including dimensions like height, width, and length, along with the target variable weight.

## Approach

### Data Preprocessing
1. **Data Cleaning**:
   - Checked for missing values (none found)
   - Removed records with zero values in measurements, as these likely represented data entry errors
   - Examined the distribution of variables

2. **Feature Engineering**:
   - Identified and addressed multicollinearity among length measurements (Length1, Length2, Length3)
   - Created species-specific ratio features to capture how individual fish compare to the average dimensions for their species:
     - Length3_to_mean_ratio
     - Height_to_mean_ratio
     - Width_to_mean_ratio
   - Applied square root transformation to the target variable (Weight) to address right-skewed distribution

3. **Exploratory Data Analysis**:
   - Analyzed species distribution, identifying class imbalance with Perch being most common
   - Performed correlation analysis revealing strong relationships between physical dimensions
   - Used ANOVA to confirm significant differences in measurements across species
   - Visualized relationships between features and weight

### Modeling
Multiple regression models were evaluated:

1. **Linear Regression**: Applied to square root transformed weight data
2. **Ridge Regression**: Used to manage potential multicollinearity
3. **Elastic Net**: Tested for feature selection capabilities
4. **XGBoost**: Employed to capture potential non-linear relationships
5. **Support Vector Regression (SVR)**: Used with linear kernel

### Results
- The Linear Regression model with square root transformation achieved the best performance with an R² score of 0.9894
- The model can explain approximately 99% of the variance in fish weight using the selected features
- Dimension-to-species-average ratios proved to be valuable predictive features

### Key Insights
1. Physical measurements have a strong, nearly linear relationship with the square root of fish weight
2. Species-specific features enhance prediction accuracy
3. Complex models did not significantly outperform the properly transformed linear model
4. The three length measurements contained redundant information, allowing simplification to just Length3

## Applications
This model can be used in:
- Fish markets for quick weight estimation from easily measurable dimensions
- Marine biology research for understanding dimensional relationships across fish species
- Quality control in fish processing and sorting operations

## Technologies Used
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- XGBoost
- SciPy
