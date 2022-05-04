# Model-for-Predicting-Housing-Price-

# Title 
Model for Predicting Housing Prices


# Description
The purpose of this project is to build a model of housing prices in California using the California census data. This data has features such as population, median income, median housing price and so on for each district in California.

The model would learn from the data and be able to predict the median housing price in any district, given all other attributes.

The CRISP-DM framework was used and the project was split according to the 6 phases of the framework:  
1. Business Understanding
2. Data Understanding
3. Data Preparation
4. Modeling 
5. Evaluation
6. Deployment

The problem is a supervised learning problem since the dataset contains the median housing prices which is the target variable (label) that needs to be predicted. Furthermore, since the goal is to predict a value, the problem is a regression problem. More specifically, this is a multiple regression problem since the model will use multiple features or variables to make a prediction (it will use the district’s population, the median income etc.). It is also a univariate regression problem because the task is to predict a single value.
Mean Absolute Error (MAE) and Root mean squared error (RMSE) are two of the most common metrics used to measure accuracy for continuous variables. RMSE is the performance measure used to evaluate the model because it is the typical performance measure for regression. It gives an idea of how much error the system typically makes in its predictions, with higher weight for larger errors. 
Even though the RMSE is generally the preferred performance measure for regression tasks, in some contexts you may prefer to use another measure. For example, suppose that there are many outlier districts. In that case, you may consider using the Mean Absolute Error (MAE). 

# Modeling
# Training and Evaluating on the Training Set
After framing the problem, the data was explored, a training set and a test set was sampled, and the data was prepared for Machine Learning models.
First, a Linear Regression model was trained but the model was underfitting the training data. The RMSE is approximately 68.961.
Next, a Decision Tree model was trained. This model is capable of finding complex non-linear relationships in the data. After the training, I got an RMSE of Zero (0), no error at all.  I realized that the model is badly overfitting the data. 
Then, I explored how I can perform Cross-Validation for the Decision Tree model. Cross-Validation means splitting the training set into K-folds (or K-validation sets), then making predictions and evaluating them on each fold using a model trained on the remaining folds. The Decision Tree Model did not look as good as it did earlier. In fact, it seems to perform worse than the Linear Regression model. The Decision Tree has an overall RMSE score of approximately 69.214. The Decision Tree model is a perfect example of overfitting. On the training set, the model performed perfectly, while on the validation sets, it did not. This can be generalized, that is, if a model performs better on the training set than on the validation sets, that is, with Cross-Validation, then the model is probably overfitting.
Furthermore, Cross-Validation for the Linear Regression model has an overall RMSE of approximately 69.193. Thus, the Decision Tree model performs worse than the Linear Regression model.  
Lastly, I looked at the Random Forest model. This model is an example of an Ensemble Learning. Suppose you ask a complex question to thousands of random people and then aggregate their answers. In many cases, you will find that this aggregated answer is better than an expert’s answer. This is called the wisdom of the crowd. Similarly, if you aggregate the predictions of a group of models, you will often get better predictions than with the best individual predictor. A group of predictors is called an ensemble; thus, this technique is called Ensemble Learning, and an Ensemble Learning algorithm is called an Ensemble method.
For example, you can train a group of Decision Tree models, each on a different random subset of the training set. To make predictions, you just obtain the predictions of all individual trees, then compute the averages of those predictions to obtain the final predictions. Such an ensemble of Decision Trees is called a Random Forest, and despite its simplicity, this is a powerful Machine Learning algorithm.
The RMSE on the training data is approximately 18.436. That is much better, Random Forest looks very promising. Next, Cross-Validation was applied, the overall RMSE, is 49.032. Note that the score on the training set is still much lower than on the validation sets, meaning that the model is still overfitting the training set.
Possible solutions for overfitting are to simplify the model, constrain it (i.e., regularize it), or get a lot more training data. Next we will explore how we can tweak the hyperparameters of the Random Forest model.   
# Model Fine-Tuning
The Random Forest model was explored in more depth and fine-tuned. By fine-tuning I mean hyperparameter optimization. The hyperparameters of the model are: 
•	The number of levels (tree depth): Number of tree levels to be learned. For instance, a value of 1 would only split the (single) root node (decision stump). 
•	Minimum child node size: Minimum number of records in child nodes. 
•	The number of models: The number of regression trees to be learned.
One way to do hyperparameter tuning would be to fiddle with the hyperparameter manually, until you find a great combination of hyperparameters values. The fine-tuning was implemented in KNIME. After fine-tuning the Random Forest Model, the best tree depth parameter is 21, and the best minimum child node size is 8. The RMSE score is approximately 49.235, which is slightly better than the score you got earlier using the default hyperparameter values. 
# Model Evaluation
At the evaluation phase, I evaluated the best model on the test set. The RMSE on the test data is approximately 59.128. The performance will usually be slightly worse than what we measured using Cross-Validation if you did a lot of hyperparameter tuning (because your system ends up fine-tuned to perform well on the validation data and will likely not perform as well on unknown datasets). When this happens, we must resist the temptation to tweak the hyperparameters to make the numbers look good on the test set; the improvements would be unlikely to generalize to new data.
# Deployment 
Below is the Project Workflow
 
