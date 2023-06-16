### Framing the Problem

#### Project Identification

**Prediction Problem**: Predict the number of minutes to prepare recipes

I will be creating a model to predict how long it will take to prepare recipes. I will be creating a regression model in order to predict the cooking time. The response variable that I will be predicting is the number of minutes it takes to prepare a recipe because it can be helpful in predicting how much time is needed to spend on meal preparation. To evaluate the model, I will use the root mean squared error (RMSE) metric over other suitable metrics because it penalizes larger errors more strongly, allowing me to focus on improving the predictions of cooking time for recipes. This is important because recipes with longer cook times are not as suitable on nusy weekdays. I chose to use RMSE over the mean squared error (MSE) because the units for RMSE is the same as the units for the original value.
At the time of prediction I will have access to the number of steps for each recipe, the number of ingredients, the average rating, contributor_id, the number of minutes, number of calories, total fat, sugar, sodium, protein, saturated fat, and carbohydrates for each recipe.


### Baseline Model
I am creating a linear regression model with the features: `n_steps`, `n_ingredients`, `name`, and `contribuor_id`. 

From the listed features, `n_steps` and `n_ingredients` are all quantitative features. On the other hand, `contributor_id` is a ordinal feature that represents the user id of the person who submitted the recipe. The `name` feature is  I converted the `contributer_id` column using OneHotEncoder and then I standardized the `n_steps` column using the StandardScaler function from sklearn.preprocessing. 
To build my regression model, I first created a LinearRegression object and then assigned the features to variable X and assigned column `minutes` to variable y. Then I transformed the `contributor_id` and `n_steps` column using OneHotEncoder and StandardScaler respectively. After that I split the data into training and testing sets in order to evaluate the efficiency of the regression model I created. I trained a Linear Regression model. 
To evaluate the baseline model's performance, I calculated the root mean squared error (RMSE) and R-squared values on the test set.

The root mean squared error of the regression model is 1153.3285965736623.


In terms of evaluating the performance of the linear regression model, the root mean squared error is too high and it shows that the model is not a good fit. The predicted values are too far from the original.


### Final Model
I added the `calories (#)` feature to the model and transformed the `n_step` and `n_ingredients` features. I think adding the calories improved my model because having a lower calorie could potentially increase the cooking time. Adding the `n_steps` and `n_ingredients` features also improved the model because having a greater number of steps andingredients potentially means that the cooking time for the recipe would be longer.

I uused a RandomForestRegressor to model because it can consider multiple input variables and their interactions to make more accurate predictions.Random forest regression is a powerful machine learning algorithm that is able to handle non-linear relationships and outliers in the dataset. It is also robust to overfitting compared to other regression models like linear regression making it a good choice. The hyperparameters 

The Final Model significantly outperformed the Baseline Model. The Baseline Model had an RMSE value of 1153.3285965736623, while the Final Model had an RMSE value of 860.4055716524407. The addition of the extra features and the use of a more powerful modeling algorithm allowed for a much better prediction of the preparation time of recipes.


### Fairness Analysis

**Null Hypothesis:** Our model is fair. Its R^2 for high calories and low calories are roughly the same, and any differences are due to random chance.

**Alternative Hypothesis:** Our model is unfair. Its R^2 for high calories is lower than its precision for low calories

Group X: high calorie intake

Group Y: low calorie intake

Evaluation Metric: R^2

Test Statistic: I chose to use the difference in R^2 means

Significance Level: 0.05

P-Value = 0.844

I can conclude that I fail to reject the null hypthoesis. It seems like the difference in accuracy across the two groups is significant.
