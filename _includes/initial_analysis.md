# Initial Analysis

First, let's talk about our data. As previously mentionned, we are using data from *Foursquare* which includes long-term global-scale check-in 
data collected from Foursquare (about 22 months from April 2012 to January 2014), and also two snapshots of user 
social networks before and after the check-in data collection period. After preprocessing, the check-in dataset contains 
19,306,111 checkins by 71,188 users in 3,430,171 venues. The social network data contains 363,704 old and 607,333 new friendships.

Let's find out where all of these beautiful users live! We adopt the same method as proposed in *Friendship and Mobility: User Movement in 
Location-Based Social Networks* by Jure Leskovec & al. [1]. We divide the world into 25km by 25km cells, we then determine the cell with the 
most check-ins for each user.

The average location of check-ins within this cell is defined as a user's home. This method has proven to be 80% accurate in [1]. 

We can have a look at user home locations as well as check-in locations by country in the figure below.

{% include homes_and_checkins_plot.html %}

By selecting **Number of Homes** in the dropdown menu, we can see that the users living in the United States and in Brasil are the ones who use the Foursquare
application the most. In Europe, Asia, and Australia, there is also a large amount of users checking in on the application, whereas in Africa some countries don't have any user homes in at all. Selecting **Number of check-ins** shows us a similar trend, however more countries are filled out this time.

Let's dig a little deeper by looking at the 20 countries with the most users and figure out how the check-ins in these countries compare. 

{% include top_20_plot.html %}

We observe a general correlation between the amount of homes per country and check-ins per country. The big exception here, that has a larger check-in number compared to other top countries as apposed to homes. Indeed japan is a very attractive country for tourists with over 30 million visitors a year, which would explain the large number of check-ins.

Foursquare defines a category hierarchy of multiple levels. Indeed each venue has a category, with perhaps a superior caterior, or even another 
uperior category! We define 5 category levels (0 to 5) with 0 being the most general. Let us look at the distribution of check-ins within each of 
the level 0 categories to get an idea on what our Foursquare users are up to.

{% include category_plot.html %}

Cleary the users love to eat!
