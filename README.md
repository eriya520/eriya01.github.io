# ![GA Logo](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4: Animal Shelter Outcomes


Every year, over 7.6 million animals were found in shelter (dogs and cats), despite a majority of the population find their forever homes, still many are not as lucky, and over 2.7 million animals are enthanized every year in the US. We are asking to predict the outcome for each animals from Austin Animal Center based on breed, color, sex and age informations.
[kaggle resources:](https://www.kaggle.com/c/shelter-animal-outcomes)

-----

## Datasets
 - train.csv 
     - data entries: 26729
     - data features: 10
 - test.csv
 
## EDA

There are quite bit of missing values in Name and outcomesubtype, those are considered not relevant for the outcome of animals in shelter, therefore, were ignored.
 - Missing Values in `AgeuponOutcome` was dropped due to a small proportion of data
 - `AgeuponOutcome` contains age in different units such as ('year','month','week','day'). In order to get a common unit, convert `AgeuponOutcome` from string to numerical and transform into `age_in_week`
 - Convert object DateTime and get only the year and month from `DateTime` column
 - Convert feature columns from cateogrical into numeric type by get_dummies
 - For NN model, onehotencoder the target variable into a list of 5 classes and saved as y_test_nn, and y_train_nn.
-----


### Classification models

- Scikit-learn classification models
    - RandomForestClassifier with grid search

- TensorFlow keras with Scikit_learn wrapper
    - one hiden layer model
    - multiple hiden layers model with drop_out layers and grid-search

-----

### Model evaluation
- Random Forest classifier Gridsearch is not as efficient as NN models (computing time is likely 3 times longer)
- NN models with 1 hidden layers has similar accuracy score as baseline model
- NN model with 2 hidden layers and 2 drop out layers (with drop_rate of 0.2) has the best performance 

|Model|Accuracy on train|Accuracy on test|
|---|---|---|
|RFC|0.97|0.61|
|NN|0.61|0.618|
|NN_deep|0.61|0.623|


## Conclusion
- The model predicts the outcomes of animals mostly to the majority classes (such as `Adoption` and `Return_to_owner`) and not able to predict `Died` and `Entuanasia` likely due to the unbalanced population in the training set.
