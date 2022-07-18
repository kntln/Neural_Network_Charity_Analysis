# Neural Network Charity Analysis

![Neural Network](https://d2r55xnwy6nx47.cloudfront.net/uploads/2022/02/SCALING_NETS_2880x1620_Lede.svg)

## Overview of the Analysis

Alphabet Soup is a non profit philantrophic foundation dedicated in helping organization that protect the environment, improve people's well-being and unifying the world. They have raised and donated over $10 billion in the past 20 years. For this analysis, using a neural network, a binary classifier will be created that is capable of predicting whether applicants will be successful if funded by Alphabet Soup. This helps ensure that the money is being used efffectively. 

Neural networks (also known as artificial neural networks, or ANN) are a set of algorithms that are modeled after the human brain. They are an advanced form of machine learning that recognizes patterns and features in input data and provides a clear quantitative output. In its simplest form, a neural network contains layers of neurons, which perform individual computations. These computations are connected and weighed against one another until the neurons reach the final layer, which returns a numerical result, or an encoded categorical result.

## Results
From Alphabet Soup’s business team, a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years were analyzed. The files contained the following: 

* **EIN** and **NAME**—Identification columns
* **APPLICATION_TYPE**—Alphabet Soup application type
* **AFFILIATION**—Affiliated sector of industry
* **CLASSIFICATION**—Government organization classification
* **USE_CASE**—Use case for funding
* **ORGANIZATION**—Organization type
* **STATUS**—Active status
* **INCOME_AMT**—Income classification
* **SPECIAL_CONSIDERATIONS**—Special consideration for application
* **ASK_AMT**—Funding amount requested
* **IS_SUCCESSFUL**—Was the money used effectively

### Preprocessing Data for a Neural Network Model
Using Pandas and the Scikit-Learn’s `StandardScaler()`, the data were pre-processed in order to compile, train, and evaluate the neural network model. 

* **EIN** and **NAME** columns were dropped.
* The **APPLICATION_TYPE** were binned and categorized any unique values with less that 500 records as "Other".  
* A list of categorical variables were encoded using one-hot encoding.
* The target variable for this analysis is the **IS_SUCCESSFUL** column.
* The remaining variables were added as the features for instance, STATUS, ASK_AMT, APPLICATION TYPE etc.

### Compile, Train, and Evaluate the Model
For the initial model a total of 5,981 parameters (2 hidden layer and 1 output layer). The first hidden layer had 43 inputs, 80 neurons and 80 bias terms. The second hidden layer had 80 inputs, 30 neurons and 30 bias terms.The output layer had 30 inputs, 1 neuron, and 1 bias term. Both the first and second hidden layers were activated using `RELU - Rectified Linear Unit` function. The output layer was activated using the `Sigmoid` function. For the model target performance, the goal is 80% acccuracy, however the model only generated 72.44%.

### Optimize the Model

Three additional attempts were made to optimize the model's performance.

 * **Attempt #1:**
    * **INCOME_AMT** column was binned
    * The change resulted in 5,821 total parameters. 
    * The accuracy slightly increased from 72.44% to 72.50%
    * Loss was also reduced from 57.65% to 57.39%


* **Attempt #2:**
    * **INCOME_AMT** column was binned
    * Increased the neurons in the first hidden layer to 100 and 50 on the second hidden layer.
    * The change resulted in 9,301 total parameters
    * The epoch was also changed to 125.
    * The change generated 72.35% accuracy and 60.75% loss. The model decreased in accuracy from the initial model.


 * **Attempt #3:**
    * **INCOME_AMT** column was binned
    * Added a third hidden layer for 25 neurons which resulted in 10,551 total parameters. 
    * The change generated 72.37% accuracy and 58.82% loss.


## Summary
In Summary, optimizing the model does not always yield better results. Out of all the 3 attempts, only 1 slightly increased accuracy and reduced loss. As for other machine learning models, `Random Forest Classifier` would be recommended. `Random Forest Classifier` are structurally similar to neural network. In addition, the model is also robust and scalable therefore it is ideal for handling this type of data. Lastly, `Random Forest Classifier`'s output and feature selection are easy to interpret and can easily handle outliers and nonlinear data.





