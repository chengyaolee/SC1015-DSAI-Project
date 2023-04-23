# SC1015 Mini-Project
For our mini project in the Introduction to Data Science and Artificial Intelligence module (SC1015), we performed analysis on the IMDb Movie Industry [dataset](https://www.kaggle.com/datasets/danielgrijalvas/movies) from Kaggle.


### Problem Definition
- Is it possible to create the most successful movie?
- How can we determine the components to create the most successful movie?

### Members (B135 - Team 2)
1. Lee Cheng Yao
2. Yau Jun Hao
3. Zane Yee Sun

### Folders Included
1. movies_original.csv - original dataset
2. images - contains images for the notebook

### Files Included
1. moviesclean.csv - cleaned dataset
2. SC1015 project presentation.pdf - presentation slides for our project
3. MiniProject2023_Team2.ipynb
    - Data Preparation and Cleaning
    - Exploratory Data Analysis
    - Feature Engineering
    - Building Models
    - Hyperparameters Tuning
    - Ensemble Learning
    - Prediction of Gross Revenue

### Notebook Details
#### Data Preparation and Cleaning
   a. Removing null values:
      - numeric columns are replaced with respective median values
      - categorical columns:
         1. 'rating' null value replaced with "Not Rated"
         2. 'company' and 'released' have less than 2% of rows with missing values, they will be removed from dataset

   b. Reserved 3 test samples for visualisation of prediction models (Final Testing)
      - "Star Wars: Episode V - The Empire Strikes Back"
      - "The Hunter"
      - "Videodrome"


#### Exploratory Data Analysis
   a. Uni-Variate: Used box plots, word map, lollipop chart, bar chart, tree map.

   b. Bi-Variate: Used pair-plots, strip plots, correlation plot, scatter plot.


#### Feature Engineering
   a. Skewness correction using Log transform for non-negative, right-skewed values

   b. Removal of insignificant columns: 
      - 'released' is very similar to 'country'
      - 'year' uncontrollable variable since we cannot traverse time
      these columns do not help with predictions and are dropped to prevent inaccuracies
      
   c. Enconding of categorical variables using Ordinal Encoder


#### Building Models
- We will evaluate the models on RMSE and MAPE(%)


*1. Multiple Linear Regressor*

    a. RMSE: 1.51
    b. MAPE(%): 7.13

*2. Polynomial Regressor*

    a. RMSE: 2.49
    b. MAPE(%): 10.00

*3. LightGBM*

    a. RMSE: 1.35
    b. MAPE(%): 6.40

*4. Gradient Boosting*

    a. RMSE: 1.35
    b. MAPE(%): 6.47
    
*5. Random Forest*

    a. RMSE: 1.36
    b. MAPE(%): 6.52
    
*6. XGBoost*

    a. RMSE: 1.41
    b. MAPE(%): 6.66


#### Hyperparameter Tuning
- we perform grid search cv optimisation on 'Light GBM', 'Gradient Boosting', 'Random Forest' and 'XGBoost'.
- evaluating each model on MAPE(%)


*1. LightGBM*

    a. Post grid search MAPE(%): 6.59

*2. Gradient Boosting*

    a. Post grid search MAPE(%): 6.28
    
*3. Random Forest*

    a. Post grid search MAPE(%): 6.31
    
*4. XGBoost*

    a. Post grid search MAPE(%): 6.42


#### Ensemble Learning
- Our project used Stacking regressor to combine our 4 machine learning algorithms to produce a more reliable model that can account for, and reduce, each sub-model's disadvantages
- each model is fitted with its optimal set of hyperparameters
- Base models: 'Gradient Boosting', 'Random Forest', 'XGBoost'.
- Final estimator: 'Light GBM'.

*Stacking Regressor*

    a. RMSE: 1.327
    b. MAPE(%): 6.338


#### Prediction of Gross Revenue
- Feeding the 3 preserved sample cases from before into the Stacking Regressor

*1. Star Wars: Episode V - The Empire Strikes Back*

    - 7.52% error

*2. The Hunter*

    - 7.50% error
    
*3. Videodrome*

    - 10.2% error

### Conclusion

*Machine Learning Comparisons*
- Stacking Regressor is successful in predicting movie gross revenue with satisfactory errors, and so it is mathematically possible to determine the components to create the most successful movie
- Ensemble Learning is effective in reducing liabilities of base machine learning models, thus improving accuracy of predictions

*Data Driven Insights*
- Revenue will be influenced by seasonal human preferences, marketing and advertising campaigns. 
- Actions for movie producers: Producers must study and understand their target demographic well should they wish to create a successful, high-earning movie 

### What we have learnt from this project?
- Ordinal Enconding 
- Random Forest
- Gradient Boosting
- XGBoost
- Light GBM
- Stacking Regressor

### References
1. sklearn.preprocessing.OrdinalEncoder — scikit-learn 1.2.2 documentation (https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OrdinalEncoder.html)

2. Random Forest Classification and it’s Mathematical Implementation | by RAHUL RASTOGI | Analytics Vidhya | Medium (https://medium.com/analytics-vidhya/random-forest-classification-and-its-mathematical-implementation-1895a7bb743e)

3. Block-distributed Gradient Boosted Trees (tvas.me) (https://tvas.me/articles/2019/08/26/Block-Distributed-Gradient-Boosted-Trees.html)

4. Light GBM vs XGBOOST: Which algorithm takes the crown (analyticsvidhya.com) (https://www.analyticsvidhya.com/blog/2017/06/which-algorithm-takes-the-crown-light-gbm-vs-xgboost/)

5. Ensemble Stacking for Machine Learning and Deep Learning (analyticsvidhya.com) (https://www.analyticsvidhya.com/blog/2021/08/ensemble-stacking-for-machine-learning-and-deep-learning/)
