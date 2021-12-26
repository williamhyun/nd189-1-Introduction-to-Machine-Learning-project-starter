# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### William Hyun

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The `datetime` column was not accepted, therefore I had to separate it into three different columns of year, month, and day. 

### What was the top ranked model that performed?
The model with the split `datetime` column, eval_metric of `root_mean_squared_error`, preset of `best_quality`, and 120 second time limit was my best performing model. 

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
Since I already did EDA by splitting the datetime, I had to choose a different category. 
I saw in the histogram of the trian data that there were significantly more sales in months 1 and 12, so I re-divided the months into seasons (e.g. months 11, 12, and 1 being a group) and called it `season2`.

### How much better did your model preform after adding additional features and why do you think that is?
My model performed worse after adding the new 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: Add your explanation

### If you were given more time with this dataset, where do you think you would spend more time?
TODO: Add your explanation

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|?|?|?|?|
|add_features|?|?|?|?|
|hpo|?|?|?|?|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary
TODO: Add your explanation
