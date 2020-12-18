# Scoring Users

To create our prediction model, we need to give each check-in a certain *Checkin Social Score*: we want to know how social a check-in is! 
Indeed giving a social score to the 3,430,171 different venues is hard work. Giving a social score to the 506 unique proposed categories is slightly easier, but also
not the best idea. Remember the Foursquare hierarchy? We can use the level 1 category to group all checkins into one of 275 categories now. 
Our social score is based on two main ideas, first of all that some places are less social than others, obviously a post office is less social than a nighclub. We 
define a coefficient **C** for each level 0 category, reflecting how social this category is (in general).

|       Level 0 category      | Coefficient |
|:---------------------------:|:-----------:|
|        Nightlife Spot       |     1.5     |
| Proffesional & Other Places |     1.1     |
|     College & University    |     1.3     |
|             Food            |     1.3     |
|        Shop & Service       |     1.0     |
|      Travel & Transport     |     1.2     |
|          Residence          |     1.1     |
|    Outdoors & Recreation    |     1.4     |
|     Arts % Entertainment    |     1.3     |
|            Event            |     1.5     |
|            Other            |     1.0     |

Second of all, we want to know if a check-in was performed during the peak hours of the venue category. For this we use level 1 categories to be slightly more precise in our categorisation. If a check-in is within the venue's peak hours, we give it a score of **S_peak = 2**, if it isnt we give it **S_peak = 2**. Each check-in can now get a social score by multiplying the coefficient with the peak hour score: **S = C*S_peak = 2**.

Right, we have now given the check-ins social scores but not the users. We therefore give each user an individual social score that is equals to the mean value of **S** for each of their check-ins.

But we're not done here... We also give each user two travel scores! We want to see if mobility influences friendships, therefore we can't leave out travelling.
First we notice that our friends at Foursquare have given us a level 0 category named *Travel & Transport*, our first travel score **T_category** is defined as the fraction of check-ins within this category over the total number of check-ins. Our second travel score **T_distance** uses a more scientific approach. By looking at the distribution of check-in distances from home. We see that the distribution follows a power law with a dip between 70 and 200km from home. We therefore use the upper value of 200km to define whether a check-in should be considered a *Travel* or not. We define **T_distance** as the fraction of *Travel* check-ins (further than 200km from home) over the total numver of check-ins.

The figure below shows three user's with a high **T_distance** score in orange, and a low **T_distance** in purple. We can clearly see that our definition illustrates how far and how often a user with a high **T_distance** travels.

{% include travel_plot.html %}
