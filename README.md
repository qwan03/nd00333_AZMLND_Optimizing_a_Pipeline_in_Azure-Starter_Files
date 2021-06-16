<!-- #region -->
# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
This dataset contains data about bank marketing date of individual people. we seek to predict whether each person would subscribe the bank service (column y).

The best performing model for HyperDrive model was : 'HD_0a00e340-567c-4df8-9a5d-6ec3d8e0678b_4'with'best_primary_metric': 0.9161204175770818. The best performing model for Automl model was 'AutoMLfa883fd2746' with 'score': '0.9161153262518968' (VotingEnsemble).

## Scikit-learn Pipeline
Specify parameter sampler, Specify a early stopping policy were included in the process.
In random sampling, hyperparameter values are randomly selected, which is fast and supports early termination of low-performance runs. 
The early stopping policy I choose is - Bandit policy is based on slack factor/slack amount and evaluation interval. Bandit ends runs when the primary metric isn't within the specified slack factor/slack amount of the most successful run.

## AutoML
I set up the AutoML configuration as:
automl_config = AutoMLConfig(
    experiment_timeout_minutes=30,
    task='classification',
    primary_metric='accuracy',
    training_data=ds,
    label_column_name='y',
    n_cross_validations=2)
 
Some parameters I specified: The type of task to run. Value here is 'classification'. "accuracy" is the metric that Automated Machine Learning will optimize for model prediction.


## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**
The prediction accuracy results of two models have almost no difference. But the best thing of AutoML is that it is super easy to use. We do not have to do anything, just wait. If we can have longer time AutoML, we might be able to generate a better model. But of course, with Scikit-Learn pipline, we have more freedom to modify the details.

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
Better data preparation

## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion*
![image.png](attachment:image.png)
<!-- #endregion -->
