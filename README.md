# machine-learning-challenge

For this exercise, I used the Random Forest Classifer and SVC methods to try to predict if known features are an Exoplanet. 

### Random Forest Classifer

When using the Random Forest Classifer Machine Leaning method on my cleaned data, using the default parameters, my model was able to get a R^2 score of 0.8895 on testing data. After going through multiple rounds of removing unimportant features, grid searching, and eventually increasing the amount of training data, I was able to get my R^2 score up to 0.9014. 

The majority of my models has a R^2 of 1.0 on training data, which may be an indication of overfitting, and needing more data. Due to the nature of my data source, obtaining more data is not an option. The R^2 of a model that uses a 90%/10% split of training/testing data was at 1.0 on the training data. This may be an indication that using a Random Forest Classifer ML method is best with larger datasets than ~7000 rows. 

As discussed above, my best model scored at 0.9014, meaning it can predict the outcome correctly just over 90% of the time. This model is sufficiently reliable such that it is good enough to predict Exoplanets. If my model returns a prediction that an object is a confirmed Exoplanet, it would be wise to invest more resources into looking at that object over an object that my model predicts to be a False Positive.

### SVC

When using the SVC ML method on my cleaned data, my model able to get a R^2 score of 0.8827 using the default parameters. Most attempts to tune my model, either by dropping unimportant features, or increasing the training data resulted in a lower R^2 score. I was able to increase my R^2 score incrementially by hypertuning certain parameters, and using the best parameters searched. My random state value was choosen without prior knowledge of how the resulting training/testing data would score, and was kept the same throughout my tests. I was able to get a higher R^2 score using a 60%/40% split of training/testing data (compared to a 75%/25% split I initially used), however the increase was only 0.0068, and I am afraid this was due to a "lucky split" and as such, declined to use this model. 

In general, each of my model's testing score was within 0.02 of the training score. This indicates that overfitting is probably not a problem. While hypertuning, I found that certain parameter combinations involving kernel="linear" took a long time to evaluate. If using SVC in the future, I may attempt to tune parameters other than kernel to save on time it takes to run a grid search. 

My best model has a score below 0.9 on testing data, so I would generally not use the model to predict Exoplanets. An exception to this would be in a situation where there are insufficient resources to look at every Exoplanet found. In this case, I would use the probability parameter, and call the predict_proba class on objects predicted to be a confirmed Exoplanet, and only invest resources into objects with very high predict_proba for the index associated with 'confirmed'. 
