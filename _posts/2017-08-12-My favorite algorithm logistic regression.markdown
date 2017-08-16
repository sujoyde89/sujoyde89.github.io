The beauty of logistic regression is that it can squeeze any number to the range between 0 and 1. Remember the expression of linear regression is yhat = ax + c. The logistic regression builds on this expression. Even though it takes help from this regression expression, it is essentially a classification algorithm.  

When it comes to classification, this is a very powerful algorithm which can give tough competition to the likes of more complex algorithms like bagging, boosting algorithms etc.  

If p is probability of getting a certain class then 1-p becomes the probability of getting the other class and we can express the natural logarithm of ratio of p to (1-p) as a regression equation. The equation can be written as below if we decide to include only two features in the regression equation; x<sub>1</sub> and x<sub>2</sub> having coefficients as a1 and a2.  

ln (p/(1-p)) = a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c. This equation can be modified as below.
p/(1-p) = e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>  

p = e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup> – p(e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>)  

p + p(e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>) = e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>  

p(1 + e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>) = e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>  

p = e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup> + c/(1+ e<sup>a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>)  

p = 1 /(1+ e <sup>–(a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>))  

The above equation is p = 1 /(1+ e <sup>–(a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>)) is also called the sigmoid function.

The graph of the sigmoid function is as shown below. As we can see the equation is squeezing the numbers to the range of 0 and 1.  

<img src="/assets/lr.png" height="300" width="500">
 
There is one thing that we should remember; Logistic regression is a classification algorithm and so it outputs probabilities and based on a threshold, it buckets the probabilities into classes.  

<i><b>Logistic regression is an extension of the linear model family.</b></i>  

Example,  

Let us say that we want to model some houses into good houses and bad houses depending on the number of rooms, the price of the house etc. Based on the input features, we can express the natural logarithm of the odds of a certain class to the odds of another class as a linear regression expression. That would give us a probability value and based on that value, we can the put the values into the classes of our interest.  

There are certain assumptions that logistic regression follows:-  

•	There is a linear relationship between the natural log of odds and the input features.  
•	The response variables must follow a binomial distribution.  

Even though logistic regression is known for binary classification, it can be used for multiclass classification as well. 
Lastly on an end note on logistic regression, when your peers would be using complex sophisticated  ensemble and boosting models, just take a deep breathe do some creative feature engineering and apply Logistic Regression. Always remember it can give fight to anyone.
The cost function for logistic regression is given below:-  

Cost function for logistic regression = -1/m {<sub>i=1</sub>∑<sup>i=m</sup> y<sub>i</sub> log (h * x<sub>i</sub> )+ (1-y<sub>i</sub>) log (1-h * x<sub>i</sub>)}  
Where h * x<sub>i</sub> is the equation for logistic regression = 1 /(1+ e <sup>–(a<sub>1</sub> * x<sub>1</sub> + a<sub>2</sub> * x<sub>2</sub> + c</sup>)), yi is the class of the target variable.  

The cost function given above is also refered to as the logarithmic loss function and it is tried to minimize when developing the model.

Please bookmark me if you found this helpful.
