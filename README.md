# Shaadi.com Data Scientist interview task (Customer Behavior Analytics for Product Adoption)

Hello, I am Janavi Vishwakarma, and here's my understanding of the datasets provided, the problem statement, and the technique or step-by-step procedure I used to obtain the desired output.

So, for the given problem statement, two datasets were provided to me:

1. Dataset.txt:
It's a text data file with customer records, which consists of 101180 rows and 24 columns.
It's last column/variable/feature is 'C' (which tells whether a customer purchased a specific product or not), which is the "target column', and is fully or slightly dependent on the other 23 columns.
The remaining 23 columns are independent features that provide relevant information about the customers, like their past purchases, etc.
This dataset is basically provided for model training purpose.

2. Dataset_test.txt:
This dataset, too, has the same features/columns (with different customer records), but the only difference here is it does not consist of the target column 'C'.
This dataset is provided for testing purpose, and here, for every row or record, the value of 'C' needs to be predicted (i.e., whether the customer is likely to purchase a specific product or not).
It has 19913 records and 23 columns.

Now, here, we need to classify whether the customer is likely to purchase an item or not; hence, it's a "classification problem", which comes under supervised Machine Learning. (Hence, the training data is provided with the target column 'C').
Here, we can use ML classification algorithms like Logistic regx., Decision trees, Random forest, XGBoost, CatBoost etc.

So now, we know how to deal with this problem statement; let's start with it. (I'm using Python as the programming language.)

-> 1st we'll import all the required Python modules. (From pandas, matplotlib to sklearn, catboost, etc.)

-> Next, we'll read both the provided files (using pandas.read_csv()) and print some of their records.

-> Now, we'll check the basic statistics of the data, like what the data types of the columns are, what the size and shape of the datasets are, whether the datasets contain any duplicate or null values, etc.

-> By checking all this, we get the idea of what preprocessing we need to do with our data before feeding it to the model.

-> So, we'll see that the data type of two columns (F15 and F16) in both the datasets is string, and as ML models do not accept string or object data types, we need to perform encoding over here to convert string data type to numeric (int/float).

-> Now, these two columns consist of dates; hence, we'll convert them from string data type to datetime format (using pandas.to_datetime()).

-> Then, we'll separate these dates into year, month, day, etc., so that we get pure numeric features.

-> Then, we'll arrange the columns in the proper sequence, along with dropping the 'Index' column, as it's of no use in the model training.

-> Now, we'll split the 'Dataset' data into independent (x) and dependent (y) features and further into separate training and validation/testing parts. (using the train_test_split API)

-> Now, we'll scale our training data (using StandardScaler()) to bring our data in a certain range/scale so that our model does not get biased towards certain features.

-> Now, we see that our training set has many dimensions, which may lead to the curse of dimensionality and degrade and slow the model's performance.

-> Hence, we'll perform dimensionality reduction by using PCA (Principal Component Analysis), which is a type of lossless feature extraction technique that helps reduce the number of dimensions in a dataset without losing any feature/characteristic of the data.

-> But 1st, we'll see whether we can drop any column manually, and for that we'll perform correlation analysis (using the corr() function, followed by plotting a heatmap).

-> We see that no two features are highly correlated or similar, i.e., every feature has some unique information and importance; hence, we'll proceed with PCA.

-> Now, our dataset is ready or clean for training purpose.

-> Now, we'll train 6-7 classification models that seem relevant to be used in this task (like Log. regx., random forest, xgboost, lightgbm, etc.), using a 'for loop'.

-> We'll further make sample predictions from these trained models and check their accuracy by comparing their predictions with the actual target values.

-> We'll use the evaluation metrics like 'accuracy_score,' 'roc_auc_score,' and most importantly, 'classification_report' to give us the values of 'F1-Score,' 'Precision,' 'Recall,' etc., as it is a classification problem.

-> By comparing the accuracy and roc_auc scores of all the trained classification models, we see that "XGBoost Classifier" has the best performance of all.

-> Now, we'll make a separate XGBoost Classifier model and train it with our training data.

-> Now, our trained XGBoost Classifier model will classify the value of 'C' as '0' or '1' for our separated test/validation data and our 'Dataset_test' data separately.

-> Now, we'll save these predictions in the format 'Index --> Class' in separate text files.

-> We can save the model, scaling object, etc., in separate Pickle (.pkl) files (to use them without building and training them again and again), if necessary.

-> And, we're done!!

So, this is how I understood the problem statement, analyzed how to proceed with solving it, solved it programmatically step-by-step, and obtained the required outputs!

THANK YOU!!

