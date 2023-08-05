# deep-learning-challenge

# Overview
The general purpose of this model is to determine whether or not a applicant for funding will be successful in thier goals. The model uses the data from previous applicants who were either successful or not successful. The model takes this data to learn what it takes for an applicant to be succesful. 

# Results

* ## Data Preprocessing
  * The target variable is for the model is the vairable that looks at whether or not a particular applicant was sucessful. After the model trains on the features it then compares to the data as to whether or not that applicant was successful. 
  * The feature variables for the initial model included; APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT. When the model uses these features to learn about the particular applicant it is then able to compare to the target variable to see if it had predicted correctly. 
  * Initially the two variable that were removed were the EIN and NAME. These removed under the assumption that they would not help the model train. 

* ## Compiling, Training, and Evaluating the Model 
  * In my initial model I used two layers plus the output layer with 10 neurons in the first two layers. For the activation functions I used relu in the first two layers and sigmoid in the output layer. For loss I used binary_crossentropy and for optimaztion I used adam. I decided to go with these hyperparameters because I got the best results in my initial model with them after trying different variations with different hyperparameters. 
  * The initial model did okay, it was able to predict correctly with an accuracy rate 72.5% and a loss rate of .55. I felt this was satisfactory for the initial model as the accuracy was above 70%.
  * With an accuracy rate of 72% in my initial model I wanted to see if I could tune the model to get better accuracy. So my first attempt at optimizing the model I created a function that utilized keras tuner. I did this to find the most optimal hyperparameters. After getting what keras tuner told me were the best hyperparameters, which were, 5 layers with the activation function tanh and the number of nuerons for each layer were hidden_nodes_layer1 =  59, hidden_nodes_layer2 = 11, hidden_nodes_layer3 = 25, hidden_nodes_layer4 = 71, hidden_nodes_layer5 = 65, and the output layer with the activation function sigmoid. For the loss function I used mse and for optimaztion I used sgd. With my first attempt at optimaztion I was able to get an accuracy score of 72.3%, so lower than my initial model.
I then decided to try again at optimizing the model, and I tried many many things, but what made the biggest difference was to add a column back into the feature variable. I added the NAME column back in and split it into buckets. When I ran the optimizing function I instantly saw a large increase in the model's accuracy. With the optimized hyper parameters of, hidden_nodes_layer1 =  97, hidden_nodes_layer2 = 11, hidden_nodes_layer3 = 25, hidden_nodes_layer4 = 11, and the relu activation function for the hidden layers and sigmoid for the output layer. The loss function was mse and the optimizer was rmsprop. With this model I was able to get a 79% accuracy and a loss of .14. 

* ## Summary

  * With and accuracy score of nearly 80%,  I am confident that my optimized model will be able to accurately predict which applicants would be successful if they were funded by Alphabet Soup. Another model that could potentially be able to predict with better accuracy would be the tensorflow decision forest. That is because it what is called a boosted model, where the model is continously learning from its previous mistakes so that it can continue to be able to predict more accurately in the future. 
