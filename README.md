# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
**In 1-2 sentences, explain the problem statement: e.g "This dataset contains data about... we seek to predict..."**
The dataset contains data about a bank's marketing campaign. Data on Customers of the bank that were involved in the marketing campaign such as age, job, marital status, education and other bank operations information like when the customer was last contacted are used in order to develop model to predict customers the likelihood of Customers signing up for the banks new product.

**In 1-2 sentences, explain the solution: e.g. "The best performing model was a ..."**
THe best performing model was from the AutoML run - VotingEnsemble classifaction with an accuracy of 91.79%. This out performs the scikit-learn Logistic Regression model of the Hyperdrive tuning with an accuracy of 91.54%.
## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**
Using the Logistic Regression provided by scikit-learn to train and test the data.
The data is split was split using 30% as test data and 70% as training set. The `inverse of regularization strength` is used. This was used to obtain the best hyperparameter for the LogisticRegression within the range of 0.1 and 1.0 in uniform space.

**What are the benefits of the parameter sampler you chose?**
The Randomsampler was selected and used for tuning hyperparameters. Due to the ability of the Randomsampler to select values over a continous range and its ability to support  early termination policies, it is greatly beneficial in selecting the `inverse od regularization strength` to enable us get an exhuastive performance of the Logistic regression model.

**What are the benefits of the early stopping policy you chose?**
The early termination policy helps to increase computational efficiency. This stops the hyperparameter tuning when ther is consistent poorly performing triaing runs.

## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**

The best AutoMLmodel generated was the Voting Ensemble classifier. This model has an acccuracy of 91.79% and an l1 ratio of 0.38775. This helps to check overfitting in the model. The model also uses the inverse scaling learning rate which helps to converge to optimal solution without sacrificing computational effeiciency. The model automl_config takes in the training dataset, the cross validation is set to 4.  

The best AutoML model has the underlisted parameters:
 [(alpha=4.693930612244897, class_weight='balanced', eta0=0.001, l1_ratio=0.3877551020408163, earning_rate='constant', loss='squared_hinge', max_iter=1000, n_jobs=1, penalty='none', power_t=0.3333333333333333, random_state=None, tol=0.001))]

## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**

## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion**
