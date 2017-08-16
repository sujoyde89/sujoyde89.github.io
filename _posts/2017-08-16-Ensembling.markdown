<b>Let us talk about ensembling!!!!</b>  

What!! You have never done ensembling before.  

Wait let us just check it out? You had done a regression problem last week and you averaged the results of the Lasso, Ridge, Xgboost. Congrats you have successfully created an ensemble model.  

Ensemble models can be of several types. Two of the most simple ensemble models are listed below.  

•	When the target variable is continuous in nature – we can average the results of the regression models.
•	When the target variable is categorical in nature – we can use voting method between several classification models. 

Along with them, we can use weighted average in case of regression models. For classification problem also, we can use average or weighted average on the probabilities of the various classification models.  

There are other sophisticated types of ensembling methods which we will get to know in detail below.  

But first of all let us establish why we would want to do ensembling. Basically all the models have their own strengths, weaknesses and uniqueness. So, when we are doing ensembling, we are essentially trying to create a structure which is more than the sum of its parts. We are trying to create a model which will combine the strengths of the individual models and as a result it will become a stronger model. Ensemble models really shine when we combine models of different types like a random forest (tree based) with a lasso model (linear model).  

For understanding the various types of ensemble, you will have to have a basic idea of decision trees. You can visit the link below to get an idea about decision trees  
<a href="http://scikit-learn.org/stable/modules/tree.html">http://scikit-learn.org/stable/modules/tree.html</a> 

We are going to learn about various ensembling models which are:-  

•	Bagging  
•	Random Forest  
•	Boosting  
•	Stacking

<b>Bagging</b>  

Bagging stands for bootstrap aggregating. Bagging is an ensemble model of decision trees.  

It generates randomized sample of the dataset and takes 2/3rd of the data for training the decision trees. The remaining 1/3rd of the data is used for estimating the errors of the decision treess. All the features are normally used for training the data which makes the model prone to overfitting because the order of splitting in the trees remains the same as the features are always the same. The bagging model uses averaging in case of continuous values or voting in case of categorical values to get the final prediction.  

One big problem with bagging is that since it uses all the features for creating the decision trees, it generates correlated trees. Since all the decision trees are learning from the same features, the structure of the trees and the order of splitting would be the same. Let us say one decision tree has made the first split on the feature ‘a’ and the second split on the feature ‘b’ ( a and b being the strongest predictors), the second tree would also make the first split on ‘a’, the second split on ‘b’ and so on. What this is essentially doing is it is magnifying the importance of strongest features while decreasing the importance of weak predictors even more. This is essentially producing correlated trees and making the model prone to overfitting.  

<b>Random Forest</b>  

Random forest is similar to bagging with one major difference. It uses a randomized subset of features for training the different decision trees.  

It also uses 2/3rd of the data for training the decision tree and uses 1/3rd of the data for estimating the out of fold errors. It also uses averaging in case of continuous values or voting in case of categorical values to get the final prediction.
Since it uses a randomized subset of the features for training the different decision trees, it produces uncorrelated trees. It is robust to overfitting.  

In fact from my personal experience I have found that random forest is very robust to overfitting.  

<b>Boosting</b>  

Now we come to boosting. Boosting applies on the principle of creating a strong learner based on the mistakes of the weak learners. It again uses a randomized subset of the samples as well as randomized subset of features (The ratio of the samples and the features to be used can be set by us. It can range from 0 to 1. If it is close to 0 then we will be creating a model which will suffer from bias error and if it is close to 1 then we will be creating a model which will be suffering from overfitting or variance error).  

In boosting, the weak learners are the decision trees. So after a decision tree is trained, the following decision will give greater weights to the data points which were wrongly classified or wrongly predicted by the first decision tree. The third decision tree will greater weights to the data points misclassified by the second decision tree and so on. The model tries to learn the relationship between the dependent and the independent variables and improves its predictions in subsequent iterations. 
Since boosting tries to rectify the mistakes done in the previous iteration; it can over fit when the number of iterations is very large because after a certain point of time it will try to memorize the relationship between the dependent and the independent variable and fail to generalize well.  

<b>Stacking</b>  

In this type of ensemble models we are stacking different types of models on top of another. We are going to see how stacking works below.  

Let us say we have a regression problem at our hand. We have two layers of models. The first layer has 3 models say linear, xgboost and random forest and the next layer has lasso. The output of the second layer is normally taken as the final output. Let me try to explain stacking pointwise. Our stacked models would look like below.

<img src="/assets/ensembling_1.PNG" height="200" width="900">  

In the image above, we divided the training data into 3 parts. Linear regression learned from the first two parts and then predicted on the 3rd part of the training data as well as on the test data which is denoted as Predict 4.  Similarly Predict 2 and Predict 3 are also created, we then create a new feature Output 1 which consists of Predict 3, Predict 2 and Predict 1. Similarly we have also created another test 1 which is the mean of Predict 4, Predict 5 and Predict 6 (Predict 4, Predict 5 and Predict 6 are all predictions on the test data).  

Similarly for our example above we have two other models Xgboost and Random forest. The table for xgboost and random forest would be similar (Just that the outputs would be different)  
 
<img src="/assets/ensembling_2.PNG" height="200" width="900">  

<img src="/assets/ensembling_3.PNG" height="200" width="900"> 

So we have in particular developed a new set of features for train and test which we will use for the model in the second layer which in our case is Lasso. The next model is trained on the new set of features. The trained model is then used to predict using the data from the new set of features.  

New set of features = [output 1, output 2, output 3]  

This new set of features is fed as input to the models in the second stacked layer.  

Stacked models have always been proven to be capable of increasing the overall model performance.  

In case of stacking, the number of models in the first layer of stacking can be increased as per the requirement; the number of layers in stacked model can also be increased. Stacking is computationally expensive so be careful in stacking with so many layers.
