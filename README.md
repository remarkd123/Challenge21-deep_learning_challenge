# Challenge21-deep_learning_challenge
 Deep Learning Challenge - Challenge 21


# Neural Network Charity Analysis

## Overview
A Deep Learning model was built to analyze charitable contributions and determine the predictability of the contributions leading to successful outcomes.

## Resources
- charity_data.csv
- Python Scikit
- TensorFlow

## Process
**Data Processing**

Initally, Identification Numbers and Charity Names were dropped from the database, as that information was not necessary for the model.  All other categories were left in the dataset as the most informative data is yet to be determined. The category of focus for the model is the “IS_SUCCESSFUL” column as that is what the model will be predicting.

Since the model runs on Integer values, the categorical data was converted into variables through use of the `get_dummies` tool.  Application Type and Classification needed to be first transformed into bins before encoding to integers.  The number of bins for each was kept under 10.

**Compile, Train, Evaluate**

The data was scaled with StandardScaler, split into training and testing sets, fit to a keras sequential deep learning model with tensorflow.

For the initial run the following was used:
two dense layers (80, 30 neurons each respectively) using the relu activation function.  The model measured loss with `binary_crossentropy`, and the `adam` optimizer was used.  The model was fit and trained for 100 epochs.

The initial model was saved as:  `AlphabetSoupCharity.h5`.

## Results
The inital model yielded less than 73# average accuracy.  As such, the following optimization efforts were undertaken:

***Test 1: Added a third Hidden Layer with 10 neurons with relu activation.***

This did not improve the accuracy.

***Test 2: Returned to initial layers and neurons (2, 80 & 30), but changed the first layer activation function to tanh.  THe number of epochs was reduced to 50 to save time.***

A minute dip in accuracy was observed.

***Test 3: Changed the two layers activation functions to sigmoid and reduced the neurons to 50, 20 respectively.***

Saw an even further minute dip in accuracy.

***Test 4: increased to four hidden layers with: 80 neurons & relu, 80 neurons & softmax, 30 neurons and softmax and 30 neurons and softmax respectively.***

Again saw an even further minute dip in accuracy.

***Test 5: the test columnns `STATUS` and `SPECIAL_CONSIDERATIONS` were dropped from the data, and the data was recompiled into the model. it was tested with three hidden layers according to: 80 neurons with relu activation, 80 neurons with sigmoid activation, and 30 neurons with relu activation respectively. ***

Saw a minor increase in balanced accuracy with the 50th epoch attaining 74.3% accuracy

***Test 6: The reduced data model was tested with three hidden layers as previously set, except that all activation layers used relu activation.***

Saw a minor increase in balanced accuracy with the 50th epoch attaining 74.4% accuracy

***Test 7: iThe reduced data model was tested with three hidden layers according to: 160 neurons with relu activation, 160 neurons with sigmoid activation, and 60 neurons with relu activation respectively (double the neurons/layer. ***

Again saw an even further minute dip in balanced accuracy with the 100th epoch attaining 74.6% accuracy

***Undocumented testing.***

Further reductions in the dataset led to drastic decreases in the predictive accuracy (30-50%). as was drastic increases in the neurons/layer or number of layers.

## Summary
I was not pleased with the performance of any versions of my model, nor was I able to attain a 75% accuracy.  When that is the case in Machine Learning, the issue may be with the data itself.  Some explanations may be that:

- The categories of data given for these charitable donations do not correlate with donation success.  
- The definition of donation success needs to be further defined (perhaps bins?).
- The sample size, although in the tens of thousands, is may be still insufficient.
- Perhaps the dataset may be incomplete or have some confounding information (solicited donoations to one company yielded donations from the parent and subsidiary companies without solicitation, etc).

With time, study, and reevaluation of data collection, I am confident a more robust model can be developed.
