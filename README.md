# Predicting-Housing-Price
Predicting Housing Price using Regularized Regression (Dibimbing-Homework)
## The Data 
The Data can be download here : https://github.com/pararawendy/dibimbing-materials/blob/main/boston.csv
## Overview
The data is about predicting housing price (**medv**) in  Boston city, features:
- Criminal rate (**crim**)
- Residential land zoned proportion (**zn**)
- Non-retail business acres proportion (**indus**)
- Is bounds with river (**chas**)
- Nitrogen oxides concentration (**nox**)
- Number rooms average (**rm**)
- Owner age proportion (age)
- Weighted distance to cities (**dis**)
- Accessibility index (**rad**)
- Tax rate (**tax**)
- Pupil-teacher ratio (**ptratio**)
- Black proportion (**black**)
- Percent lower status (**lstat**)
## Steps
1. Split data: train - validate - test
    - 80% → 80% training vs 20% validation
    - 20% testing
2. Multicollinearity check
    - Calculate VIF score for each feature
    - Correlation analysis to drop redundant feature
3. Fit models on training data (lambdas = [0.01, 0.1, 1, 10])
    - Ridge regression
    - LASSO
4. Choose the best lambda from the validation set
    - Use RMSE as metric
    - Interpret a sample of the coefficients of the best model
      - Ridge regression
      - LASSO
5. Evaluate the best models on the test data 
   - MAE
   - MAPE
   - RMSE
