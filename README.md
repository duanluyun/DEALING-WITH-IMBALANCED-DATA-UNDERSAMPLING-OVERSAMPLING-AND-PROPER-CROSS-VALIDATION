
In this work we focus on how to properly cross-validate when we have imbalanced data. As a matter of fact, in the context of many credit crad fraud, we have datasets where we have two classes for the main outcome; normal samples and relevant samples. For example we might have a small percentages of relevant samples while the majority of samples might be normal. Outside of the  space, this is true (even more) for the case for example in a cancer detection application we might have a small percentages of patients with cancer (relevant samples) while the majority of samples might be healthy individuals.

The main motivation behind the need to preprocess imbalanced data before we feed them into a classifier is that typically classifiers are more sensitive to detecting the majority class and less sensitive to the minority class. Thus, if we don't take care of the issue, the classification output will be biased, in many cases resulting in always predicting the majority class. Many methods have been proposed in the past few years to deal with imbalanced data. 

## What can we do when we have imbalanced data? Mainly three things:

### 1. Ignoring the problem.

### 2. Undersampling the majority class.

### 3. Oversampling the minority class.

### (1)Ignoring the problem:
 
Building a classifier using the data as it is, would in most cases give us a prediction model that always returns the majority class.

### (2)Undersampling the majority class:
One of the most common and simplest strategies to handle imbalanced data is to undersample the majority class. While different techniques have been proposed in the past, typically using more advanced methods did not bring any improvement with respect to simply selecting samples at random. So, for this analysis I will simply select n samples at random from the majority class, where n is the number of samples for the minority class, and use them during training phase, after excluding the sample to use for validation.

![input dataset](https://github.com/duanluyun/Credit-Card-Fraud-Detection/blob/master/image/import%20dataset.png)

## For more details :

https://nbviewer.jupyter.org/github/duanluyun/Credit-Card-Fraud-Detection/blob/master/Credit%20Card%20Fraud%20Detection.ipynb
