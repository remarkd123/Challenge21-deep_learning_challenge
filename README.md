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

Now that the data was prepared, I split it into my training and testing sets and scaled the data to ensure the model weighed the variables appropriately.

I designed a Deep Learning model with keras Sequential function from TensorFlow.  Since I was dealing with about 40 input features from the data, I set my Input and First Hidden Layer of the model with 80 neurons.  I created a Second Hidden Layer with 40 neurons.  I used the ReLU activation for the hidden layers and a Sigmoid activation to study probability for the output layer.

For compiling the model, I measured loss with `binary_crossentropy` and used the `adam` optimizer.  I set callback checkpoints to save every 5 epochs when running the model.

I fit and trained the model on 100 epochs.

I saved the model as `AlphabetSoupCharity.h5`.

## Results
The initial evaluation of the model resulted in less than 73% accuracy, so I attempted several changes to the model to optimize the accuracy.
***Test 1: Lowered Neurons, Added Hidden Layer***

This did not improve the accuracy.

***Test 2: Kept Original Neurons, Added Hidden Layer***

This did not improve the accuracy.

***Test 3: Change the Compile Optimizer***

Several of the keras optimizers significantly reduced the accuracy of the model.  The `adamax` optimizer showed negligible improvement, but the accuracy was still below 73%

***Test 4: Change the activations***

I attempted many combinations of changing activations with `tanh`, `gelu`, `swish`, `sigmoid`, and `relu`, but none of these improved the accuracy of the model.

***Additional undocumented tests***

I tried resampling the data to balance out any discrepancies in input and output.  I tried increasing and lowering the epochs, and I added several hidden layers.  None of these improved the performance of the model.

## Summary
I was not pleased with the performance of any versions of my model.  When that is the case in Machine Learning, the issue may be with the data itself.  Some concerns may be:

- The categories of data given for these charitable donations do not have a correlation with donation success.  
- The definition of donation success needs to be revisited.  
- The sample size, although in the tens of thousands, is still insufficient.

With time, study, and reevaluation of data collection, I am confident a more robust model can be developed.
