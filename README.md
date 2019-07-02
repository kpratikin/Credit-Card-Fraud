<h1> Credit Card Fraud Detection</h1>

<b>Objective:</b><br>
<ul><li>To detect fraudulent credit card transactions and 
 <li>To understand how to work with imbalanced dataset.</ul>


<b>Datset:</b>
<br>The dataset is downloaded from: https://www.kaggle.com/mlg-ulb/creditcardfraud
<br> The datasets contains transactions made by credit cards in September 2013 by european cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.

<p align="center"><img src="https://github.com/kpratikin/Credit-Card-Fraud/blob/master/Class_split.PNG">
 <br>Figure: Class (1- Fradulent transaction, 0- Non-fradulent transactions)
 </p>

It contains only numerical input variables which are the result of a PCA transformation. Unfortunately, due to confidentiality issues, we do not have original features and more background information about the data. Features V1, V2, ... V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'. Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-senstive learning. Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.

<b>Analysis:</b>
<br> For detailed analysis refer the Code:
<br>Following are the techniques I have tried out.
<ol><li> Normalization of variables
    <li> Cross-Validation
    <li> Oversample minority class (i.e. fradulent transactions)
    <li> Ensemble modelling (Random Forrest)
    <li> Bagging
    <li> Boosting (XGBoost, ADABoost)
    <li> Changing the Threshold


<b>Conclusion:

Summary of all the models are as follows:
<p><table style="width:100%">
  <tr>
    <th>Model</th>
    <th>Accuracy</th>
    <th>AUC</th> 
    <th>Precision</th>
    <th>Recall</th>
    <th>F1-Score</th>
  </tr>
  <tr>
    <td>Original Model</td>
    <td>0.99</td> 
    <td>0.96</td>
      <td>0.6</td>
      <td>0.87</td>
      <td>0.71</td>
  </tr>
    
  <tr>
    <td>Cross Validation</td>
    <td>0.99</td> 
    <td></td>
      <td>0.59</td>
      <td>0.85</td>
      <td>0.69</td>
  </tr>
  
  <tr bgcolor="blue">
   <font color='red'>
    <td>Oversampling (SMOTE)</td>
    <td>0.946</td> 
    <td>0.989</td>
      <td>0.92</td>
      <td>0.97</td>
      <td>0.95</td>
    </font color='red'>
  </tr>
  
   <tr>
    <td>Ensemble (Random Forrest)</td>
    <td>0.99</td> 
    <td>0.928</td>
      <td>0.93</td>
      <td>0.75</td>
      <td>0.83</td>
  </tr>
  
   <tr>
    <td>Bagging (Decision Trees)</td>
    <td>0.99</td> 
    <td>0.97</td>
      <td>0.61</td>
      <td>0.88</td>
      <td>0.72</td>
  </tr>
  
  <tr>
    <td>Boosting (XGBOOST)</td>
    <td>0.99</td> 
    <td>0.98</td>
      <td>0.79</td>
      <td>0.92</td>
      <td>0.85</td>
  </tr>
  
  <tr>
    <td>Boosting (ADABOOST)</td>
    <td>0.99</td> 
    <td>0.969</td>
      <td>0.83</td>
      <td>0.65</td>
      <td>0.73</td>
  </tr>
  
  <tr>
    <td>Threshold change to 10%</td>
    <td>0.99</td> 
    <td>0.968</td>
      <td>0.79</td>
      <td>0.83</td>
      <td>0.81</td>
  </tr>
</p>
<b><p>Out of all the methods we tried, we found that oversampling(SMOTE) method is best suited for our analysis. Significant high F1, Precision and recall scores are observed at a cost of small decline in the accuracy score.
Thus, with use of oversampling(SMOTE) model, banks can better detect fradulent transactions.
