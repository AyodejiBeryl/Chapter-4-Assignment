# Chapter-4-Assignment

What Linear Regression training algorithm can you use if you have a training set with millions of features?
The Linear Regression training algorithms that can be used are stochastic gradient descent, mini-batch gradient descent, or batch gradient descent. Stochastic gradient descent and mini-batch gradient descent would be more preferable because both of them do not have to load the the entire dataset into memory in order to take one step of gradient descent. Batch gradient descent would be good to use if there is enough memory to load all the data. Normal equations are not efficient computatuionally. 
Suppose the features in your training set have very different scales. What algorithms might suffer from this, and how? What can you do about it?
There is a need to do feature scaling for the different gradient descent algorithms, it will help data converge quicker. The normal equations method do not require normalizing features, it remains unaffected by features in the training set having very different scales. 
Can Gradient Descent get stuck in a local minimum when training a Logistic Regression model?
Gradient Descent produces a convex shaped graph which only has one global optimum, so it cannot get stuck in a local minimum.
Do all Gradient Descent algorithms lead to the same model provided you let them run long enough?
No. If the optimization problem is convex (such as Linear Regression or Logistic Regression), and assuming the learning rate is not too high, then all Gradient Descent algorithms will approach the global optimum and end up producing fairly similar models. However, unless you gradually reduce the learning rate, Stochastic Gradient Descent and Mini-batch Gradient Descent will never truly converge, instead, they will keep jumping back and forth around the global optimum. This means that even if you let them run for a very long time, these Gradient Descent algorithms will produce slightly different models. One way to help them converge is to gradually reduce the learning rate hyperparameter.
Suppose you use Batch Gradient Descent and you plot the validation error at every epoch. If you notice that the validation error consistently goes up, what is likely going on? How can you fix this?
If the validation error consistently goes up after every epoch, then one possibility is that the learning rate is too high and the algorithm is diverging. If the training error also goes up, then this is clearly the problem and you should reduce the learning rate. However, if the training error is not going up, then your model is overfitting the training set and you should stop training, and apply the common solution to overfitting (regularization, more data, fix errors in data, remove outliers, or reduce number of features).
Is it a good idea to stop Mini-batch Gradient Descent immediately when the validation error goes up?
Due to their random nature, neither Stochastic Gradient Descent nor Mini-batch Gradient Descent is guaranteed to make progress at every single training iteration. So if you immediately stop training when the validation error goes up, you may have stopped too early, before the optimum is reached. A better option is to save the model at regular intervals, and when it has not improved for a long time, you can revert to the best saved model.
Which Gradient Descent algorithm (among those we discussed) will reach the vicinity of the optimal solution the fastest? Which will actually converge? How can you make the others converge as well?
Stochastic Gradient Descent has the fastest training iteration since it considers only one training instance at a time, so it is generally the first to reach the vicinity of the global optimum. However, only Batch Gradient Descent will actually converge, given enough training time, Stochastic GD and Mini-batch GD will bounce around the optimum, unless you gradually reduce the learning rate.
Suppose you are using Polynomial Regression. You plot the learning curves and you notice that there is a large gap between the training error and the validation error. What is happening? What are three ways to solve this?
If the validation error is much higher then the training error, then this is likely because the model is overfitting the training set. To fix this one way will be to reduce the polynomial degree: a model with fewer degrees of randomness is less likely to overfit. Secondly, you can regularize the model – for example, by adding a L_2 penalty (Ridge regression) or an L_1 penalty (Lasso) to the cost function. This will also reduce the degrees of freedom of the model. Thirdly, you can try to increase the size of the training set.
Suppose you are using Ridge Regression and you notice that the training error and the validation error are almost equal and fairly high. Would you say that the model suffers from high bias or high variance? Should you increase the regularization hyperparameter α or reduce it?
If both the training error and the validation error are almost equal and fairly high, the model is likely underfitting the training set, which means it has a high bias. You should try reducing the regularization hyperparameter.
Why would you want to use Ridge Regression instead of Linear Regression?
I would Ridge regression when my model is overfitting the training set. A model with some regularization typically performs better than a model without any regularization, so I would prefer to use Ridge Regression over plain Linear Regression
Why would you want to use Lasso instead of Ridge Regression?
Lasso performs automatic feature selection by dropping weights of the most important features. Concretely, Lasso regression uses an l1 penalty which tends to push the weights down to exactly zero. This leads to sparse models, where all weights are zero except for the most important weights. This is a way to perform feature selection automatically, which is good if only few features actually matter. When I am not sure, I would go with Ridge regression.
Why would you want to use Elastic Net instead of Lasso?
Elastic Net is preferred over Lasso since Lasso may behave erratically when the number of features is greater than the number of training instances or when several features are strongly correlated
Suppose you want to classify pictures as outdoor/indoor and daytime/nighttime. Should you implement two Logistic Regression classifiers or one Softmax Regression classifier?
If you want to classify pictures as outdoor/indoor and daytime/nighttime, since these are not exclusive classes (i.e., all four combinations are possible) you should train two Logistic Regression classifiers.
