# Measures of classification accuracy

## Terms

* True Positive = patient has cancer and test is positive
* True Negative = patient is healthy and test is negative
* False Positive = patient is healthy and test is positive
* False Negative = patient has cancer and test is negative

TPs and TNs are good. FP is bad but can be detected. FN is the worst, can go undetected.

* Precision = TP / (TP+FP) = probability that the patient is really sick in case he is classified sick
* Sensitivity (recall/true positive rate) = TP / (TP + FN) = probability that the test is positive in case patient is sick
* Specifity (true negative rate) = TN / (TN + FP) = probability that the test is negative in case patient is not sick
* F1 score = 2 (precision * TPR) / (precision * TPR ) 

## ROC curve (Receiver Operating Characteristic)

* False positive rate on the x-axis, true positive rate on the y-axis

