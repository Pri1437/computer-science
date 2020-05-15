This has basics of data science

### Evaluating the performance of a model
We use multiple parameters like accuracy, precision, recall (also known as senstivity), F1-score.

Before that we have to see terms like true positive, true negative, false postive and false negative. Here True &rarr; prediction is on par with the actual value.
Similarly false &rarr; prediction is not on par with actual value.

* True Positive &rarr; Value on par with actual class value and both actual and predicted class value is positive.
* True Negative &rarr; Value on par with actual class value and both actual and predicted class value is negative.
* False Positive &rarr; Value not on par with actual class value and predicted value is positive whereas actual val is negative.
* False Negative &rarr; Value not on par with actual class value and predicted value is negative whereas actual val is positive.

Confusion Matrix: Tests performance of a classification model(aka classifier) using a test data whose true values are known. Visualizes performance of algo.

* A confusion matrix is really helpful in seeing how our model is performing against given truth values of the dataset.
* A confusion matrix is a table that holds values of classification and the predictions are considered on the left side(each row) and actual values are considered on the top (each column).
* **The diagonal represent represent true positives** &rarr; these values show how many times it has predicted correctly.
* The **size of confusion matrix is given by the number of things you want to predict** (basically how many values are present in the field you want to predict)
* Confusion matrix will always be a *square matrix*.
* Ultimately confusion matrix shows what our model did right what it did wrong.

**Accuracy**: accuracy of a model is defined as ratio of number of correct predictions (true positive and true negative) to total number of predictions made.

**Precision**: ratio of correct predictions to all values of that prediction values (inclusive of correct and wrong).
* This value is for each thing you want to predict.

**recall (senstivity)**: ratio of correct prediction to all values taken by respective actual class.

