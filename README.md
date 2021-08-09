# Neural_Network_Charity_Analysis

## Overview

With the use of Machine Learning and Neural Network the goal of this project is to create a binary classifier that is able to predict which applicants will or will not receive funding from the Alphabet Soup Charity Group. This machine learning will be used on a dataset containing 34,000 organizations and the metadata of each organization. There are 11 parameters we will be looking at and those are:

- EIN—Identification number
- APPLICATION TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

## Results

The project will consisted of three steps: Preprocessing the data for neural networks, compling, training, and evaluating the model, and optimizing the model

### 1. Preprocessing data

The first was preprocessing the data for the neural network which consisted of firstly, dropping any columns that would be unbeneficial to the decision making process. The next was to determine the number of unique values in each column. Because there are many unique values and this can lead to an uneven distribution we want to bucket the rare values into another category. For this case we binned APPLICATION_TYPE and CLASSIFICATION. To determine the unique values of APPLICATION_TYPE and CLASSIFICATION a value count visualizations were created. According to the density plots, the most common unique values have more than 10,000 for APPLICATION_TYPE and about 1800 for CLASSIFICATION. 

![Screen Shot 2021-08-09 at 11 47 15 AM](https://user-images.githubusercontent.com/80358062/128734895-6e202122-b435-493e-8d2a-39ad79ca3dfe.png)

![Screen Shot 2021-08-09 at 11 47 41 AM](https://user-images.githubusercontent.com/80358062/128734965-60ea50a0-208c-449c-8113-2de10e3f3aa3.png)


This means we can bucket the values that appear less than 10,000 and 1800 times, replace the column within the dataframe, and check if the binning was successful.
After generating a categorical variable list we applied OneHotEncoder which allows the algorithm to have a more nuanced understanding. Merging the new with the old and then dropping the old was the next step. Splitting the features and the target array was next. We determined that IS_SUCCESSFUL was the dependent variable or target of the model, and that any variable other than IS_SUCCESSFUL was our independent or feature arrays. This allows us to move into the training and testing.

### 2. Compiling, Training, and Evaluating the model

This part allows us to customize the neural network. A neural network is designed to calculate the weight of various data inputs and extract an output. A basic neural network was applied which parsed the input data using input,  hidden, and output layers. To determine the number of input layers we have to include the number of input features equal to the number of variables in the feature dataframe. We chose to have two hidden layers with 80 neurons and 30 neurons. The “relu” activation function was applied to the first and second hidden layer while the “sigmoid” activation function was applied to the output layer. Training and evaluating lead to an accuracy of 72 percent.

Building neural network
![Screen Shot 2021-08-09 at 11 49 05 AM](https://user-images.githubusercontent.com/80358062/128735171-1ccd0fe8-fdfb-4b8a-a93c-6e511cf948af.png)

Training

![Screen Shot 2021-08-09 at 11 50 00 AM](https://user-images.githubusercontent.com/80358062/128735298-b020370e-eccd-4552-b92b-bb3fe06a8627.png)

Evaluation

![Screen Shot 2021-08-09 at 11 50 27 AM](https://user-images.githubusercontent.com/80358062/128735373-b5b91e26-03b9-49ec-9610-e693d2006504.png)


### 3. Optimizing model to reach 75 percent accuracy

- My first attempt at optimizing the model was to add an additional layer. This lowered the accuracy.

![Screen Shot 2021-08-09 at 11 54 37 AM](https://user-images.githubusercontent.com/80358062/128736144-1b6e2908-54a9-4229-840c-8a8f40199be8.png)

Evaluation

![Screen Shot 2021-08-09 at 11 55 07 AM](https://user-images.githubusercontent.com/80358062/128736245-16751e66-d103-48a6-8870-ab29a4ec19c8.png)

- My second attempt was to drop more features that seemed unbeneficial to the decision process. I chose to drop EIN, NAME, USE_CASE, and SPECIAL_CONSIDERATIONS

![Screen Shot 2021-08-09 at 11 57 21 AM](https://user-images.githubusercontent.com/80358062/128736540-1afa5f4a-396b-4f1c-a6a9-764e0bb69e2d.png)

Evaluation

![Screen Shot 2021-08-09 at 11 57 56 AM](https://user-images.githubusercontent.com/80358062/128736655-e7d3bdf1-ff5a-412b-9259-7e9cf546f212.png)

- Attempt number three was a mixture of these steps. I decided to keep the EIN column and dropped NAME and SPECIAL_CONSIDERATIONS.

![Screen Shot 2021-08-09 at 11 59 26 AM](https://user-images.githubusercontent.com/80358062/128736895-e45a50c7-f722-4897-b7ae-ec8e0dbbc806.png)

I then added an additional layer and neurons

![Screen Shot 2021-08-09 at 12 00 20 PM](https://user-images.githubusercontent.com/80358062/128737016-850e442f-5afd-49c3-8120-524ea6a6b12b.png)

Evaluation

![Screen Shot 2021-08-09 at 12 00 44 PM](https://user-images.githubusercontent.com/80358062/128737076-ca1005ba-22b1-4190-9959-c262b23d9556.png)



