# Predicting Cooking Time

### Framing the Problem

#### Project Identification

**Prediction Problem**: Predict the number of minutes to prepare recipes

I will be creating a model to predict how long it will take to prepare recipes. I will be creating a regression model in order to predict the cooking time. The response variable that I will be predicting is the number of minutes it takes to prepare a recipe because it can be helpful in predicting how much time is needed to spend on meal preparation. To evaluate the model, I will use the root mean squared error (RMSE) metric over other suitable metrics because it penalizes larger errors more strongly, allowing me to focus on improving the predictions of cooking time for recipes. This is important because recipes with longer cook times are not as suitable on nusy weekdays. I chose to use RMSE over the mean squared error (MSE) because the units for RMSE is the same as the units for the original value.
At the time of prediction I will have access to the number of steps for each recipe, the number of ingredients, the average rating, contributor_id, the number of minutes, number of calories, total fat, sugar, sodium, protein, saturated fat, and carbohydrates for each recipe.
