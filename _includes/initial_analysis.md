# Initial Analysis

First, let's talk about our data. As previously mentionned, we are using data from *Foursquare* which includes long-term global-scale check-in 
data collected from Foursquare (about 22 months from April 2012 to January 2014), and also two snapshots of user 
social networks before and after the check-in data collection period. After preprocessing, the check-in dataset contains 
19,306,111 checkins by 71,188 users in 3,430,171 venues. The social network data contains 363,704 old and 607,333 new friendships.

Let's find out where all of these beautiful users live! We adopt the same method as proposed in *Friendship and Mobility: User Movement in 
Location-Based Social Networks* by Jure Leskovec & al. [1]. We divide the world into 25km by 25km cells, we then determine the cell with the most check-ins for each user.
The average location of check-ins within this cell is defined as a user's home. This method has proven to be 80% accurate in [1]. 

We can have a look at user home locations as well as check-in locations by country in the figure below.

{% include homes_and_checkins.html %}
