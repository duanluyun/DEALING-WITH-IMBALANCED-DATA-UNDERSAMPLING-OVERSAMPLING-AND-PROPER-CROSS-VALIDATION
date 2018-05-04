
In this work we focus on how to properly cross-validate when we have imbalanced data. As a matter of fact, in the context of many credit crad fraud, we have datasets where we have two classes for the main outcome; normal samples and relevant samples. For example we might have a small percentages of relevant samples while the majority of samples might be normal. Outside of the  space, this is true (even more) for the case for example in a cancer detection application we might have a small percentages of patients with cancer (relevant samples) while the majority of samples might be healthy individuals.

The main motivation behind the need to preprocess imbalanced data before we feed them into a classifier is that typically classifiers are more sensitive to detecting the majority class and less sensitive to the minority class. Thus, if we don't take care of the issue, the classification output will be biased, in many cases resulting in always predicting the majority class. Many methods have been proposed in the past few years to deal with imbalanced data. 

## What can we do when we have imbalanced data? Mainly three things:

### 1. Ignoring the problem

Building a classifier using the data as it is, would in most cases give us a prediction model that always returns the majority class.

![Ignore1](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/Ignore1.png)

![Ignore2](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/Ignore2.png)

![Ignore3](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/Ignore3.png)


### 2. Undersampling the majority class

One of the most common and simplest strategies to handle imbalanced data is to undersample the majority class. While different techniques have been proposed in the past, typically using more advanced methods did not bring any improvement with respect to simply selecting samples at random. So, for this analysis I will simply select n samples at random from the majority class, where n is the number of samples for the minority class, and use them during training phase, after excluding the sample to use for validation.

![input dataset](https://github.com/duanluyun/Credit-Card-Fraud-Detection/blob/master/image/import%20dataset.png)
![value count](https://github.com/duanluyun/Credit-Card-Fraud-Detection/blob/master/image/value_count.png)
![undersample](https://github.com/duanluyun/Credit-Card-Fraud-Detection/blob/master/image/undersample.png)
![features_labels](https://github.com/duanluyun/Credit-Card-Fraud-Detection/blob/master/image/features_labels.png)

## split the train dataset and test dataset

![train_test_split](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/train_test.png)

## Cross validateion

![Kfold](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/KFold.png)

![Kfold_traindataset](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/train_test.png)

![Kfold_output](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/cvOutput.png)

Let's look at the result:

![result1](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/prediction_undersampling1.png)

![result2](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/prediction_undersampling2.png)

By undersampling, we solved the class imbalance issue, and increased the sensitivity of our models. However, results are very poor. A reason could indeed be that we trained our classifiers using few samples. In general, the more imbalanced the dataset the more samples will be discarded when undersampling, therefore throwing away potentially useful information. 

### 3. Oversampling the minority class.
This was a simple  method can be used to oversample. One of the most common being the SMOTE technique, a method that instead of simply duplicating entries creates entries that are interpolations of the minority class, as well as undersamples the majority class. Normally when we duplicate data points the classifiers get very convinced about a specific data point with small boundaries around it, as the only point where the minority class is valid, instead of generalizing from it. However, SMOTE effectively forces the decision region of the minority class to become more general, partially solving the generalization problem.

![oversample1](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/oversample1.png)

![oversample2](https://github.com/duanluyun/DEALING-WITH-IMBALANCED-DATA-UNDERSAMPLING-OVERSAMPLING-AND-PROPER-CROSS-VALIDATION/blob/master/image/oversample2.png)

Results are pretty good now.  We obtained auc = 0.99 without any feature engineering, simply using what was provided in the dataset, and without any parameter tuning for the classifier. Once again, apart from the differences in the two oversampling methods (replication of the minority class or SMOTE), the issue here is not even which method to use, but when to use it. Using oversampling before cross-validation we have now obtained almost perfect accuracy. 

## For more details :

https://nbviewer.jupyter.org/github/duanluyun/Credit-Card-Fraud-Detection/blob/master/Credit%20Card%20Fraud%20Detection.ipynb
