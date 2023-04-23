# Deep Learning Challenge Report
## Overview
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. The challenge develops a deep learning model that can predict whether applicants will be successful if funded by Alphabet Soup. The model is trained on the metadata of more than 34,000 organisations that have received funding from Alphabet Soup over the years.

## Results
### Data Preprocessing
The data needs to be preprocessed so that it can be input into the deep learning model. Categorical variables are transformed into numerical variables via one hot encoding and binning. The data is then split into a training set and a testing set. Both sets are then scaled.

IS_SUCCESSFUL is the target of the model. This tells us whether a funded organisation is successful in its venture and thus whether Alphabet Soup's money was used effectively.

The following variables are the features for the model:
* APPLICATION_TYPE - application type categorised by Alphabet Soup
* AFFILIATION - affiliated sector of industry
* CLASSIFICATION - classification of the organisation by the government
* USE_CASE - use case for funding
* ORGANIZATION - organisation type
* STATUS - active status
* INCOME_AMT - income classification
* SPECIAL_CONSIDERATIONS - special considerations for an application
* ASK_AMT - funding amount requested

The following variables are removed from the input data because they are neither targets nor features as they are non-beneficial ID columns:
* EIN
* NAME

### Compiling, Training, and Evaluating the Model

After several optimisation attempts, I selected 2 hidden layers, the first of which has 86 neurons (twice the number of input features) and the second of which has 30 neurons (less than half of the number of neurons in the first hidden layer). All hidden layers use the relu function and the output layer uses the sigmoid function. I was not able to achieve the target model performance of 75% accuracy despite having attempted several times to increase the model performance. The general rule is that having more hidden layers and neurons and different activation functions give better accuracy. But in this case having more hidden layers and neurons and changing activation functions still gave similar, slightly worse accuracy score and so I reverted to the original model with lesser hidden layers and neurons since it is better to use less computational resources for the same performance.

Steps taken to increase model performance
* Before optimisation, there are 2 hidden layers, the first of which has 86 neurons (twice the number of input features) and the second of which has 30 neurons (less than half of the number of neurons in the first hidden layer). All hidden layers use the relu function and the output layer uses the sigmoid function. Epoch number is 100. Loss: 0.5555844306945801, Accuracy: 0.7267638444900513
<img width="380" alt="image" src="https://user-images.githubusercontent.com/115685811/233821784-edce9580-5575-4b51-aa2c-fa121d0037ae.png">
<img width="416" alt="image" src="https://user-images.githubusercontent.com/115685811/233821805-8d703354-6e26-4861-b4ea-aaa8df02edb1.png">

* In my first attempt to optimise, I added the number of neurons of the first layer to 129 (3 times the number of input features) and of the second layer to 50 neurons. I also plotted the loss graph to determine the optimal number of epochs. Loss: 0.5592455863952637, Accuracy: 0.726064145565033. Loss and accuracy worsened slightly. The loss graph flattens at 90-100 epochs. So 100 is an optimal number of epoch.
<img width="380" alt="image" src="https://user-images.githubusercontent.com/115685811/233821758-47ee1d1a-ed78-4a44-ba57-5175d3eba536.png">
<img width="420" alt="image" src="https://user-images.githubusercontent.com/115685811/233821915-0a90998a-6aa3-4578-8633-4a8154e89deb.png">
<img width="417" alt="image" src="https://user-images.githubusercontent.com/115685811/233821947-3f6c91cf-8588-42a4-8db9-507a1260d620.png">

* In my second attempt, I added a third layer with 30 neurons using a relu function and increased the neurons in the second layer to 75. Loss: 0.5669000744819641, Accuracy: 0.7241982221603394. Loss and accuracy worsened slightly further. The loss graph fluctuates a little more but still flattens at 90-100 epochs. So 100 is an optimal number of epoch.
<img width="385" alt="image" src="https://user-images.githubusercontent.com/115685811/233821337-5b355532-95ed-4407-ae92-bb2e7f1270eb.png">
<img width="418" alt="image" src="https://user-images.githubusercontent.com/115685811/233821665-1224d800-bd49-46cd-ad97-c1f417c57bbc.png">
<img width="415" alt="image" src="https://user-images.githubusercontent.com/115685811/233821725-9c24c968-244b-476f-bbbe-7caf7ff12e78.png">

* In my third attempt, I added a fourth layer with 40 neurons using sigmoid function and increased the neurons in the second layer to 100 and the third layer to 75. Loss: 0.5611671209335327, Accuracy: 0.7262973785400391. Loss improved a little and accuracy worsened slightly further. The loss graph fluctuates even a little more but still sort of flattens at 90-100 epochs. So 100 is an optimal number of epoch.
<img width="385" alt="image" src="https://user-images.githubusercontent.com/115685811/233822015-c9bb4e6e-72e8-424a-9818-417b91391989.png">
<img width="416" alt="image" src="https://user-images.githubusercontent.com/115685811/233822414-2d8052a6-3025-4ad2-a7e5-75038868d8b6.png">
<img width="416" alt="image" src="https://user-images.githubusercontent.com/115685811/233822442-e9decdc8-f297-4935-939d-8870d1bd3752.png">

* Since having more hidden layers and neurons and changing activation functions still gave similar, slightly worse accuracy score and so I reverted to the original model with lesser hidden layers and neurons since it is better to use less computational resources for the same performance.

## Summary
