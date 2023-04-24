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

After several optimisation attempts, the best model is the one which has 2 hidden layers, the first of which has 86 neurons (twice the number of input features) and the second of which has 30 neurons (less than half of the number of neurons in the first hidden layer). All hidden layers use the relu function and the output layer uses the sigmoid function. I was not able to achieve the target model performance of 75% accuracy despite having attempted several times to increase the model performance. The general rule is that having more hidden layers and neurons and having activation functions of the hidden layers more complex than that of the output layer give better accuracy. But in this case doing so still gave virtually the same accuracy score. So the pre-optimisation model with the least hidden layers and neurons and with the least complex activation functions in the hidden layers is still the best model since it is better to use less computational resources for the same performance.

Steps taken to increase model performance
* Before optimisation, there are 2 hidden layers, the first of which has 86 neurons (twice the number of input features) and the second of which has 30 neurons (less than half of the number of neurons in the first hidden layer). All hidden layers use the relu function and the output layer uses the sigmoid function. Epoch number is 100. Loss is 0.5569349527359009 and accuracy is 0.7271137237548828
<img width="388" alt="image" src="https://user-images.githubusercontent.com/115685811/233846239-0308276a-ce49-4722-a51d-e23c10443d06.png">
<img width="417" alt="image" src="https://user-images.githubusercontent.com/115685811/233846263-35f55de2-d1f3-47ae-8855-3cc9db01edd0.png">

* In my first attempt to optimise, I added the number of neurons of the first layer to 129 (3 times the number of input features) and of the second layer to 50 neurons. I also plotted the loss graph to determine the optimal number of epochs. Loss and accuracy worsen slightly. The loss graph flattens at 90-100 epochs. So 100 is an optimal number of epoch.
<img width="386" alt="image" src="https://user-images.githubusercontent.com/115685811/233838041-681778f2-b679-41bd-94a4-51711b6af45a.png">
<img width="420" alt="image" src="https://user-images.githubusercontent.com/115685811/233821915-0a90998a-6aa3-4578-8633-4a8154e89deb.png">
<img width="417" alt="image" src="https://user-images.githubusercontent.com/115685811/233821947-3f6c91cf-8588-42a4-8db9-507a1260d620.png">

* In my second attempt, I added a third layer with 30 neurons using a relu function and increased the neurons in the second layer to 75. Loss and accuracy worsen slightly further. The loss graph fluctuates a little but still flattens at 90-100 epochs. So 100 is an optimal number of epoch.
<img width="385" alt="image" src="https://user-images.githubusercontent.com/115685811/233821337-5b355532-95ed-4407-ae92-bb2e7f1270eb.png">
<img width="418" alt="image" src="https://user-images.githubusercontent.com/115685811/233821665-1224d800-bd49-46cd-ad97-c1f417c57bbc.png">
<img width="415" alt="image" src="https://user-images.githubusercontent.com/115685811/233821725-9c24c968-244b-476f-bbbe-7caf7ff12e78.png">

* In my third attempt, I added a fourth layer with 40 neurons using relu function, increased the neurons in the second layer to 100 and the third layer to 75 and changed the activation functions of the first two hidden layers to tanh function and of the third hidden layer to leaky relu function. Loss and accuracy improves a little compared to those in the previous attempt. The loss graph flattens at 90-100 epochs. So 100 is an optimal number of epoch.
<img width="386" alt="image" src="https://user-images.githubusercontent.com/115685811/233839761-3857e10b-c8f7-4bad-9d70-0edad8f488f5.png">
<img width="417" alt="image" src="https://user-images.githubusercontent.com/115685811/233839786-f25fe40a-f581-40c3-adb8-947835fd78ba.png">
<img width="417" alt="image" src="https://user-images.githubusercontent.com/115685811/233839808-edbe51ea-4fc9-40e3-977c-f6bd5bf8d92c.png">

## Summary
The pre-optimisation model has a loss of 0.5569349527359009 and an accuracy of 0.7271137237548828 while the model with the most number of neurons and hidden layers and with activation functions in the hidden layers more complex than that in the output layer has a loss of 0.5656967759132385 and an accuracy of 0.7257142663002014. The general rule is that having more hidden layers and neurons and having activation functions in the hidden layers more complex than that in the output layer give better accuracy. But in this case doing so still gave virtually the same accuracy score. So the pre-optimisation model with the least hidden layers and neurons and with the least complex activation functions in the hidden layers is still the best model since it is better to use less computational resources for the same performance.

Random forest could be used to solve this classification problem as well. The reason is that random forest is made up of decision trees which are easy to audit. This is important in this problem since there is a need to justify whether to grant funds to a particular organisation. Also, random forest can map non-linear relationships and the dataset in this problem may have non-linear relationships.
