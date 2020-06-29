# predicting_machine_breakdowns

Working with machine sensor data, the goal was to predict when a breakdown will occur before it happens. I took two approaches:

1)In the first (notebook ‘machine_breakdown_prediction_final_rolled_up_time_JB), I rolled up the time series into 30 min intervals and labeled the intervals in which the machine broke. I then tested various classifiers that predict the interval in which the machine breaks from the sensor data. The best performing classifier was an SVM with polynomial kernel that classified the 2 test intervals correctly, but would also lead to misclassifications. The utility of such a classifier and the need for further tuning/ development would depend on the business problem (i.e how much in advance the issue would need to be detected and cost of inspecting the machines in the case of non-failure).
 
2)To build a tool that would allow to input a timespan in which a defect needs to be detected, I started a a second notebook (machine_breakdown_prediction_final_JB) in which I did not roll up the times series into larger intervals, but introduced an additional class that labels the time intervals before machine break (i.e 10 minutes before machine break). Using all sensors, Random Forest  allowed to predict abnormality before machine break in one of two test cases. I used this Random Forest classifier to select features that would be relevant to detect all the abnormal classes. Sensors 39 and 47 gave interesting patterns with respect to class separation, but did not perform better alone than the top ten features from the Random Forest. Again, SVM with polynomial kernel was the most successful in predicting failures before machine breaks occur, but also yielded false positives.

License
machine_breakdown_prediction_final_JB.ipynb and machine_breakdown_prediction_final_rolled_up_time_JB.ipynb are licensed under the MIT License. See the LICENSE file in this directory for the full license text.
