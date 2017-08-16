<b>Let us try to remove the confusion around the confusion matrix!!!!</b>  

Normally a confusion matrix can be built for multiple classes but it is most prevalently used for binary classes. A confusion matrix normally looks like the table below.  

<table>
<tbody>
<tr>
<td colspan="2" rowspan="2" width="162">
<p>&nbsp;</p>
</td>
<td colspan="2" width="150">
<p>Predicted value of y</p>
</td>
</tr>
<tr>
<td width="60">
<p>0</p>
</td>
<td width="90">
<p>1</p>
</td>
</tr>
<tr>
<td rowspan="2" width="120">
<p>Actual value of y</p>
</td>
<td width="42">
<p>0</p>
</td>
<td width="60">
<p>TN</p>
</td>
<td width="90">
<p>FP</p>
</td>
</tr>
<tr>
<td width="42">
<p>1</p>
</td>
<td width="60">
<p>FN</p>
</td>
<td width="90">
<p>TP</p>
</td>
</tr>
</tbody>
</table>

Where,  
TN = true negatives
TP = true positives
FP = false positives
FN = false negatives  

There are several metrics by which we can evaluate a classification problem.  

Accuracy = (TN + TP)/ (TN + TP + FN + FP)  

But accuracy does not always solve our purpose. In an imbalanced classification problem (where the number of one class is significantly larger than the other). Accuracy will always be high. In a cancer detection problem, we can predict that all cases to be non-cancerous and that will still put our accuracy to be higher than say may be 99.5%.  

To solve this problem of an imbalanced classification problem we have created other metrics which prove to be particularly useful.  

•	Precision = TP/ (TP + FP)  

Normally precision is used when we want to decrease the false positives (Cases which are negative actually but have been classified as falsely positive).  

Example - Marking an email as a spam when it is not can amount to in losing certain kind of information. In this case precision is used as the metric  

•	Recall = TP/ (TP + FN)  

Normally recall is used when we want to decrease the false negatives (Cases which are positive actually but have been classified as falsely negative). Building a model for fraudulent cases would do well to select this model for evaluation purposes because classifying a case to be non-fraudulent when it is actually fraudulent can lead to severe repercussions.  

Example – Recall is the metric used when we want to identify fraud cases in several settings.  

•	F1 score = (2 * precision * recall)/ (precision + recall).  

F1 score is the harmonic mean of precision and recall. F1 score is used when we want to use the best of both worlds i.e. when we want to decrease false negatives as well as false positives. 
Please bookmark me if you found this helpful
