# IEEE-CIS-Fraud-Detection
Fraud prevention system in online transactions is actually saving consumers millions of dollars per year. It is also important to minimize the rate of transactions that are predicted as fraud but are actually not a fraud (false-positive rate) for better customer experience. Researchers from the IEEE-CIS want to improve this figure(FPR) posted a competition in Kaggle. The Data is provided by the Vesta corporation.

# Understanding as a Machine Learning Problem
* Binary Classification problem with some form of interpretability.
* It's an intermediate action for a transaction. Need for a Low Latency system.
* The evaluation metric to be used is ROC-AUC. In addition, we should consider FPR as a metric.

# Data
* We can get the Data Set here.
* Two data sets given: 1. Transaction 2. Identity in CSV formats.
* TransactionID - unique id representing a transaction in both data sets.
* Mentioned Categorical features: ProductCD, card1 - card6, addr1, addr2, P_emaildomain, R_emaildomain, M1 - M9,DeviceType, DeviceInfo, id_12 - id_38.
* TransactionDT - represents the time of the transactions in timedelta format.

### We found many features contain NaN values. For Visualization, we consider the missing values itself as a separate category in all categorical features.

# Some Insights on Data

* We found only 3.5% of data is toxic. Data is highly imbalanced. A high chance of false-positive in our model.
* We can consider as a time series data. Fraud Transactions are uniformly distributed all over the time.
* 'C' Category in ProductCD feature, 'M2' Category in M4 feature contributes mostly to fraud transactions.
* 150 and 185 category values have major distributions. 185, 119, 144 category values contributes (12, 9, 8) % of fraud transactions in Card3 feature.
* 336, 224, 117, 166, 138, 126 category values have major distributions. 137, 147 category values contributes (15, 10) % of fraud transactions Card5 feature.
* Gmail, Hotmail, Yahoo, outlook contributes to 45 % in overall transactions. mail.com, protonmail.com are considered as odd email domains.
* 'id_30' feature represents the OS like Windows, Android, etc. We found the specifications of the version in this feature. All the versions of the same OS categories are grouped together. eg: Windows 9, Windows 8 is considered as Windows. Here we are not taking advantage of the versions specified.
* 'id_31' feature represents the Browsers used for transactions like IE, Chrome, etc. Here also we grouped the browsers versions in the same way we did for 'id_30'.

# Data Cleaning
Data contains many nan values. 
* The features where the nan values contribution is more than 90%. These features are not useful.
* Remove columns if 90% of the feature value is taken by one value count. That feature is not informative.
* Fill nan values with 'MISSING' for categorical values, median for numerical values.

# Data Preprocessing
Encode categorical values with label encoder or one-hot encoder. A label encoder assigns a number for each category. A One-Hot encoder generates a 1-D vector of n dimensions where n is the number of unique categories. Using label encoder, a model may get confuse about the sequences generated. This can be avoided if any tree based model is used. Using One-Hot encoder is not good for a feature having many categories. It produces huge vectors. One-Hot encoding is an advantage for linear models.
