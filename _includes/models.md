# Prediction Models

We will try two methods in order to predict the number of friends that a specific user will gain or lose during the data collection period: 
1. A model using the social scores and the travel scores that we have computed above  
2. A model only using the check-ins of the users to determine the similarity between them

First of all we divide our data into a training set containing 80% of the users (45618 users), and a testing set containing 20% of the users (11405 users).  
We then train our models on the training data, and predict the number of friends gained for the users in the testing set.

Let's talk about the first model. After having computed social and traveler scores for every user in our training set, we normalise the scores and we use them to train a **linear regression model**. We then use this model to predict the number of friends gained for each user in the testing set, and we compare that value to the real number of friends gained. The figure below is a plot of the residual, or the subtraction of the predicted friendship gain and the true friendship gain.

{% include regression_model.html %}

We can see that with this simple regression model, the results already look pretty promising! In fact **in 35% of the cases, we were able to determine with an error of less than 1 friends, the number of friends that a user has gained or lost**. 

Now what if we only use the the check-ins of the users in the testing set to determine to which user in the training set they are the most similar to? 

For the second model, we use a similarity measurement technique between the users and then use this to predict how a user's friendships have evolved.  
In this case, for each user in the testing set, we determine the 5 most similar users in the training set by using **cosine similarity**, taking only into account the frequency at which the users go to a specific location. With this information, we then determine which users are the most similar. The difference between the predicted number of friends and the real number of friends (aka the residual) can be seen in the density plot below. 

{% include cosine_model.html %}

Clearly, this method works a lot better than the model using the social and traveler scores of the users, which is something we were not expecting at all! In **60% of the cases, we are able to predict the number of friends a person will make (with an error of only 1 friend)** simply by looking at the users to which this person is most similar. This clearly proves that users that go to similar places are similar in behaviour, and are most likely to make the same number of friends. 



