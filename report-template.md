
# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Moses Kipngetich Kurui

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: In my case there were no changes in the output as the predictions did not have any negative values. However, for the submission file, there was a need to ensure that the index column was not included as it would generate an error in kaggle. 

### What was the top ranked model that performed?
TODO: The topped ranked model was WeightedEnsemble_L3 in all the  cases. It produced the best results as compared to the others.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO: The exploratory analysis  used  were a couple. First, I had to check if there were missing values which the dataset did not have. Correlatin analysis was used to show the relationship  of each of the variables. High correlation  between the independent variables would have affected the model. However,  no variables had high correlation.

### How much better did your model preform after adding additional features and why do you think that is?
TODO: The accuracy of the model jumped from 1.84 to 0.6538 which is very impressive. The new features were created from the date variable  which shows that the variable date was not contributing well in the predictive power of the model. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: This improved the model further taking the accuracy to 0.49.This was used on the tuned data which showed a high level of accuracy.
### If you were given more time with this dataset, where do you think you would spend more time?
TODO: I would spend more time on generating new features and tuning the hyperparameters of the model. Advanced methods that are provided with Sklearn would be used. Also, feature selection  is the method I would  have applied on the dataset to increase its accuracy.
### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|default|default|default|0.49|
|add_features|default|default|time category, wind category, humidity category, temp category|0.49|
|hpo|hyperparameters = {
    'XGB': {
        'ag_args_fit': {
            'num_boosting_rounds': ag.common.space.Categorical(100, 500, 1000),
            'max_depth': ag.common.space.Categorical(3, 5, 8)
        },
        'ag_args_ensemble': {
            'num_bag_folds': ag.common.space.Categorical(5, 10, 15)
        }
    },
    'RF': {
        'ag_args_fit': {
            'num_estimators': ag.common.space.Categorical(100, 200, 300)
        },
        'ag_args_ensemble': {
            'num_bag_folds': ag.common.space.Categorical(5, 10, 15)
        }
    }
}|hyperparameters = {
    'XGB': {
        'ag_args_fit': {
            'num_boosting_rounds': ag.common.space.Categorical(100, 500, 1000),
            'max_depth': ag.common.space.Categorical(3, 5, 8),
            'eta': ag.common.space.Categorical(0.01, 0.05, 0.1),  # Learning rate
            'min_child_weight': ag.common.space.Categorical(1, 3, 5),
            'gamma': ag.common.space.Categorical(0, 0.1, 0.2),  # Minimum loss reduction
            'subsample': ag.common.space.Categorical(0.5, 0.7, 1.0),  # Row subsampling
            'colsample_bytree': ag.common.space.Categorical(0.5, 0.7, 1.0)  # Column subsampling
        },
        
}
}|hyperparameters = {
    'XGB': {
        'ag_args_fit': {
            'num_boosting_rounds': ag.common.space.Categorical(100, 500, 1000),
            'max_depth': ag.common.space.Categorical(3, 5, 8),
            'eta': ag.common.space.Categorical(0.01, 0.05, 0.1),  # Learning rate
            'min_child_weight': ag.common.space.Categorical(1, 3, 5),
            'gamma': ag.common.space.Categorical(0, 0.1, 0.2),  # Minimum loss reduction
            'subsample': ag.common.space.Categorical(0.5, 0.7, 1.0),  # Row subsampling
            'colsample_bytree': ag.common.space.Categorical(0.5, 0.7, 1.0)  # Column subsampling
        },
        'ag_args_ensemble': {
            'num_bag_folds': ag.common.space.Categorical(5, 10, 15)
        }
    },
    'RF': {
        'ag_args_fit': {
            'num_estimators': ag.common.space.Categorical(100, 200, 300),
            'max_depth': ag.common.space.Categorical(5, 10, None),  # None means no limit
            'min_samples_split': ag.common.space.Categorical(2, 5, 10),
            'min_samples_leaf': ag.common.space.Categorical(1, 2, 4),
            'max_features': ag.common.space.Categorical('sqrt', 'log2', None)  # sqrt or log2 of num_features
        },
        'ag_args_ensemble': {
            'num_bag_folds': ag.common.space.Categorical(5, 10, 15)
        }
    }
}
|0.4899|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary
The project has utilized fine tuning and feature selection to create a  model that predicts bike demand. However, there is still some improvement need to be made to ensure that we have a highly accurate model. 