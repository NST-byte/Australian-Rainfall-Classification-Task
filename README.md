## Classification Task predicting rain

The aim of this project is to create models that will best predict whether there will be rain on the following day. The datasets is taking from kaggle and includes weather information for a range of cities across Australia. The features include temperatures, wind speeds and sunshine amongst others.


* After initially analysing the data it was found there were large amounts of missing data: <br>
Data Imputation: <br>
1. Categorical Variables: The missing values were imputed by taking the most common value from all the data entries in that same city. For example, a missing value about wind direction in Sydney would be replaced by the most common wind direction in Sydney.<br>

2. Numerical Variables: The missing numerical values were imputed by a similar method, they were replaced by the median value of all the other entries in that same city. If whole cities were missing values they were imputed by taking the median of the whole dataset. <br>

This method of imputation was found to be the most effective for this dataset and meant that no data had to be deleted. <br>

The only remaining cleaning necessary was to one-hot encode the categorical variables which was done using the pandas library. After that the data had to be normalised since many of the variables were in different units. This was done using a robust scaler from sklearn as it was the most appropriate for this type of data.

* After splitting the data into a training and test set the models could be trained, a total of 6 models were trained and tuned to find which would return the best accuracy. Since the dependent variable in this dataset is unbalanced it was necessary to use metrics such as Precision and Recall alongside Accuracy to find the best model: <br>

1. Logistic Regression: This was the first model trained as it is one of the simpler models when doing classification tasks. After fine tuning this model returned an Accuracy of 84.72% which seems good, however as the dataset is quite unbalanced it is a little misleading.

2. K-Nearest Neighbours: This was the second trained and it gave an accuracy of 83.98% but a severely lower Recall score suggesting it was not as good of a model to use for this dataset.

3. Random Forest: The random forest model gave good results and after tuning gave an accuracy of 85.68% and decent Recall and Precision scores.

4. XGBoost: The XGBoost model turned out the be the best model, it was expected to outperform the Random Forest as it is often a better version of tree boosting. The Accuracy for this model ended up being 86.23%, the only downside of this model was the training time which was significant.

5. Neural Network: The Neural Network model closely matched the previous XGBoost model in terms of Recall score, however the Accuracy was substantially smaller coming in at 84.46%.

6. Cat Boost: The final model used was a Cat Boost model, it gave a good Accuracy score of 83.84%, however it did not perform so well in terms of the other metrics.

* Best Model: In the end the best model was decided to be the XGBoost model as it performed the best when taking into account all of the metrics.

Below is the comparison of all the models with the three metrics used:

![Model Comparison](https://user-images.githubusercontent.com/67882633/109438091-69883680-7a7c-11eb-8ad3-5f5158d386f0.PNG)
