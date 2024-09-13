# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Ming Lin

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I had to ensure all the predictions were positive and that there were no null values.

### What was the top ranked model that performed?
The WeightedEnsemble_L3 model.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
Through EDA, I added two additional features. Although Autogluon recognized one of the features as a datetime object, it was only concered with the year, month, day and day of week. But I believe that the time of day was a very imporant feature that was not parsed from the data. So I added the hour of day as a feature. In addition, I added whether it felt colder or warmer than the actual temperature in hopes that it gives the model more information about the climate. Since the weather is a big factor in determining whether people go outside in general.
### How much better did your model preform after adding additional features and why do you think that is?
My model did perform incredibly better after adding the additional features. I think the extra features were crucial in determining whether people went out to bike. So having those features gave the model a better chance at predicting the bike sharing demand.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Even though there was not a significant difference between the root mean squared errors when trained on the training dataset, my model performed significantly better on the Kaggle/test dataset. One interesting thing I found was that when I slightly increased the number of bag folds, the model performed worse by all metrics. 

### If you were given more time with this dataset, where do you think you would spend more time?
If given more time, I would try to visualize how the evaluation metric is changing between batches/epochs so I can determine whether I am overfitting/underfitting. I would also remove the time limit and just let the model take the time it wants to train fully. 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|n_estimator|iterations|num_bag_folds|score|
|--|--|--|--|--|
|initial|300|10000|8|1.78943|
|add_features|300|10000|8|0.62911|
|hpo1|400|15000|10|0.50127|
|hpo2|400|15000|8|0.48110|
### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](Project/img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](Project/img/model_test_score.png)

## Summary

In this project, I went through exploratory data analysis, creating a baseline model, iterating and finetuning that model. My biggest challenge was finding and reading documentation on how hyperparameter tuning worked in Autogluon. Since some of the resources were out of date online, I had to look through the source code on GitHub to get a better understanding. In the end, I learned a lot about putting my ML knowledge in practice through Autogluon and AWS SageMaker.

## Details in /Project folder
