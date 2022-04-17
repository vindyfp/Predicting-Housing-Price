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
## Data Analysis
- From **VIF score for each feature**, indicates that there is Multicollinearity, because there is a VIF value that ">3".

![image](https://user-images.githubusercontent.com/99865400/163710896-f9cb2bf2-e7c7-42cc-bb0f-679212466103.png)

- **From Heatmap Correlation**, tax & rad features are correlated with each other and have a correlation value >= 0.8, so tax & rad must be dropped before training the model

![image](https://user-images.githubusercontent.com/99865400/163710058-25262c84-182b-47de-b158-5e66f69b02bc.png)

- **On the Ridge Regression model, the best lambda is 10**. With RMSE value : 4.87 (smallest value)

![image](https://user-images.githubusercontent.com/99865400/163710144-97a66e75-1b9c-417f-886d-2e27663842f4.png)

- **On the Lasso model, the best lambda is 1**. With RMSE value : 4.84 (smallest value)

![image](https://user-images.githubusercontent.com/99865400/163710251-2d645932-bb9c-47be-9b04-cdf206a004cb.png)

- **Interpret Ridge Regression best model**
    - Ridge Regression best model ->> medv = 15.15 + (-0.08 crim) + 0.03 zn + (-0.087 indus) + 1.95 chas + (-1.67 nox) + 4.75 rm + (-0.01 age) + (-1.23 dis) + (-0.73 ptratio) + 0.01 black + (-0.53 istat)
    - Sample coefficient interpretation : the addition of 1 point 'rm' by assuming other features are considered fixed, will increase the housing price (medv) by 4.75
    - 'rm' is a variable that is very influential on housing price because it has the highest coeff value

![image](https://user-images.githubusercontent.com/99865400/163710358-3749c14d-2fd6-4c9c-bb93-d4050f86ca6e.png)

    - R-squared Ridge Reg for training data is 0.65, it means that the ability of the independent variable to explain the dependent variable (medv) is 65% (the model is acceptable because R-squared >60%)
    
![image](https://user-images.githubusercontent.com/99865400/163710671-e891b7e6-a445-4bb1-880e-89410d2e16b9.png)

- **Interpret Lasso best model**
    - Lasso Best Model ->> medv = 25.86 + (-0.05 crim) + 0.02 zn + (-0.02 indus) + 2.46 rm + 0.02 age + (-0.55 dis) + (-0.71 ptratio) + 0.01 black + (-0.71 istat)
    - Sample coefficient interpretation : the addition of 1 point 'rm' by assuming other features are considered fixed, will increase the housing price (medv) by 2.46
    - 'rm' is a variable that is very influential on housing price because it has the highest coeff value

![image](https://user-images.githubusercontent.com/99865400/163710514-24919f49-ec7c-4238-ba67-a8c17ec97695.png)

    - R-squared Lasso for training data is 0.51, it means that the ability of the independent variable to explain the dependent variable (medv) by 51% (the model is not acceptable because R-squared <60%)

![image](https://user-images.githubusercontent.com/99865400/163710757-492fc842-a241-472f-aaa6-1d4c772f5008.png)
    
## Model Evaluation
- **Ridge Regression**

![image](https://user-images.githubusercontent.com/99865400/163710962-1a4b7894-f5e9-42c5-a444-ef3c8d87e963.png)
![image](https://user-images.githubusercontent.com/99865400/163710976-fd9ceb76-56f4-495b-8a9c-af7b9ab6846f.png)

- **LASSO**

![image](https://user-images.githubusercontent.com/99865400/163710968-736d93e7-e4aa-4b3a-a481-f9f61cc4e5d1.png)
![image](https://user-images.githubusercontent.com/99865400/163711009-dfe0a385-56a0-4101-84e8-8f8a8004f161.png)

## CONCLUSION
Model with the best and most acceptable performance is Ridge Regression with lambda 10. Because R-square is 65%, the model can be said to be acceptable (R-square value ">60%"), besides that the MAPE value is between Training & Testing error not much different and still below 30%.
