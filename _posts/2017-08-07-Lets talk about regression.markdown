Think of a house whose price depends only on the number of rooms it has. Think of a car whose price depends on the space it has.
The above two cases are problems of regression where we can develop a regression model to know the price of the house and the car if we knew the number of rooms of the house and the space of the car.  

The regression model in this case would be of the form yhat = ax + c  
Where,  
yhat -> the predicted price of the house or the predicted price of the car;  
x -> the number of rooms of the house or the space in the car;  
a -> the coefficient of the independent variable  
c -> the price of the house or the car when there is no rooms or no space (it seems kinda hard to imagine).  
But for our problem solving purposes we will have to consider a case when the space inside the car and the number of rooms in the house is zero. For our case here we can consider it to be zero;  

Up till now we have established a simple linear regression where given the value of an independent variable we can determine the dependent variable.  

Simple linear regression => yhat = ax + c  

What does training a model mean??  

Whenever we say we are training a model, we are making the model learn the relationship between the dependent and the independent variable.In this case of simple linear regression, we are training the model to learn the parameter ‘a’   

In the above case, we took into account only one dependent variable, what if there are multiple dependent variables. Suppose for example, now we decide to include the number of bathrooms in our model for determining the price of the house. Now if x<sub>1</sub> and x<sub>2</sub> are the number of rooms and bathrooms respectively, then the price of the house would become yhat = a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c.  
Here in the above case the model would have to learn a<sub>1</sub> and a<sub>2</sub>, the coefficients of the two dependent variables.  

Now, we have introduced more than 1 variable which effectively changes our model from simple linear regression to multivariate linear regression.  

Also we can extend multivariate or simple linear regression to include higher orders of some dependent variables like yhat = a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + a<sub>3</sub> * x1<sup>2</sup> + c and now we have turned our regression model into a polynomial regression model.  

Now how does a model learn the parameters say a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub> etc. Whenever we are predicting a dependent variable, there is always bound to be some difference between the actual dependent variable and the predicted dependent variable. We can calculate the sum of squared differences between the values of the actual and the predicted dependent variable. We will term this sum of squared differencing the cost function. This is how we make the model learn the relationship between the dependent and the independent variable so that the value of the cost function is as low as possible.  

Every model has a cost function, whose value it tries to lower as much as possible by learning the relationship between the dependent and the independent variable.  

Now in this case, the cost function would look like below:  

Cost function = <sub>i=1</sub>∑<sup>i=N</sup> (y-yhat)<sup>2</sup> if N is the number of samples. The cost function is sometimes referred to as the loss function.
Linear regression works very well when the relationship between the dependent and the independent variable is linear and additive and when there is no correlation between the dependent variables.  

In the above statement, we said that linear regression works very well when there is a linear relationship between the dependent and the independent variable. In real life though that is rarely the case. For introducing non linearity to the model we include higher orders of the dependent variable, we also try various feature interactions. Now the problem with the above approach is that we are introducing more and more complexity to the model and with that overfitting the model.  

<img src="/assets/o.png" height="300" width="500">

In the above image we can see that there are two kinds of errors. One is bias error when the model fails to learn the relationship between the dependent and the independent variables and the other is the overfitting error referred to as variance when the model becomes very complex and tries to memorize the training data and in the process fails to generalize. So we should try to maintain a balance between overfitting error and the bias error.  

Example of bias error would when we are modeling the price of the house based on only the number of rooms in the house whereas example of overfitting error would be when we are modeling the price of the house based on all the legitimate features like number of rooms, number of bathrooms, square feet of the house etc. and also introducing the higher orders of the variables into the model.  

Till now we have learned about the following:-  

<b>•	Simple linear regression</b>  
<b>•	Multivariate regression</b>  
<b>•	Polynomial regression</b>  

Along with that we have also gone over the basic types of errors that our model might suffer from.  
Let us look at some other types of regression that are there. 

<b>Ridge regression</b>  

Remember earlier we had initialized the cost function for our regression model as below.  

Cost function = <sub>i=1</sub>∑<sup>i=N</sup> (y-yhat)<sup>2</sup>  

We can further modify the cost function as Cost function = <sub>i=1</sub>∑<sup>i=N</sup> (y-yhat)<sup>2</sup> + α (<sub>i=1</sub>∑<sup>i=K</sup> a<sub>i</sub> )<sup>2</sup> if N is the number of samples and K is the number of features based on which the model predicts the dependent variables. Here the cost function contains the loss function which is the first term and the L2 regularization function which is the second term.  

In the above cost function we have added another term to the earlier cost function. Here a<sub>i</sub> are the coefficients of the dependent variables in the model and α is a hyper parameter of the model which can take on any value. What we are effectively trying to do here is that we are trying to not let the coefficients become very big (remember that the objective of our model is to lower the value of the cost function as much as possible) because then the model would become very sensitive to the features whose coefficient is large. Essentially we are trying to reduce the overfitting error in this case.  

Since Ridge regression is concerned with regularizing the model by influencing the square of the coefficients, the extra term in the cost function is called the L2 regularization term. Here regularization means opposite of overfitting and α is the L2 regularization capability.  

Ridge regression also work well in case of correlated features. It divides the overall coefficient of all correlated features into each of the features so that the effect of correlation in the model performance is diminished. 

Ridge regression does not remove correlated features. It includes all the features in the model so working with ridge regression can sometimes prove to be computationally challenging when there are lots of features and you desperately want to remove some of them.  

<b>Lasso regression</b>

Lasso regression is another type of regression which computes the cost function in a different way. The cost function in case of lasso regression is as below.  

Cost function = <sub>i=1</sub>∑<sup>i=N</sup> (y-yhat)<sup>2</sup> + α (<sub>i=1</sub>∑<sup>i=K</sup> | a<sub>i</sub> |).  

Here again, N is the number of samples and K is the number of features based on which the model predicts the dependent variables. The cost function here contains the loss function and the L1 regularization function.  

Just like ridge regression we have added another term to the sum of squared errors. It is the sum of the absolute values of the coefficients of the dependent variables multiplied by α. Remember α is a hyper parameter of the model which can take on any value. Lasso regression also works well in case of correlated variables. In case of say 3 correlated variables it will remove 2 of the correlated variables and include only one coefficient in the model. The features that it will remove in case of correlated features is non deterministic in nature i.e. we cannot control which features it will remove in case of correlated features. Lasso regression can also be used as a feature selection tool since we can remove the features whose coefficients are zero in the model. Lasso regression works very well when there are lots of features in the dataset and we want to remove some features.  

Since Lasso regression is concerned with regularizing the model by influencing the absolute value of the coefficients, the extra term in the cost function is called the L1 regularization term. Here α is the L1 regularization capability.  

The function of α is to reduce overfitting behavior of the model. So, the bigger the alpha, the lesser the chances of overfitting for the model or the greater the generalization or regularization objective.  

<b>Elastic net regression</b>

This regression is a combination of Lasso and Ridge regression. It combines the regularization capabilities of both Lasso and Ridge regression.  

Here in the case of elastic net regression, we can say that there are two alphas. α1 can be said to control the L1(Lasso) regularization capability and α2 can be said to be the L2(Ridge) regularization capability. Elastic net tries to combine the beauty of both worlds of Lasso and Ridge regression. In case of elastic net regression, the cost function is as below.  

Cost function = <sub>i=1</sub>∑<sup>i=N</sup>(y-yhat)<sup>2</sup> + α1 (<sub>i=1</sub>∑<sup>i=K</sup> | ai |) + α2 (<sub>i=1</sub>∑<sup>i=K</sup>a<sub>i</sub> )<sup>2</sup>.  
The cost function here contains the loss function, the L1 regularization function and the L2 regularization function.  

Till now from simple linear regression, multivariate and polynomial regression, we have extended our understanding to  :-  

<b>•	Ridge regression</b>  
<b>•	Lasso regression</b>  
<b>•	Elastic net regression</b>    

Please bookmark me if you found this helpful.
