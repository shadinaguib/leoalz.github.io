
## I - Introduction to the Data


Although our dataset has previously been wrangled and cleaned, we still have to apply a few modifications in able to perform our analysis. We created new datasets to be used in the creation of our prediction models and all of the steps leading up this. We now introduce the datasets to be used, we will then modify them and finally export new '.csv' files for analyis.


### I.1 - The Data

Our extension considers data from a location-based social networks: Foursquare. The datasets are available in the `data` directory pushed to the same GitHub repo as this notebook. This directory contains four '.txt' files and are described below.

#### Friendship network data

* `dataset_WWW_friendship_old.txt` : Friendship network of Foursquare users in April 2012 (list of all friends of all users on the social media).

* `dataset_WWW_friendship_new.txt.gz` Friendship network of Foursquare users in January 2014, 22 months later.


Example:
~~~
[user]      [friendship]
15          595326
19          54
19          1061
...         ...
~~~


#### Anonymised check-in data

* `dataset_WWW_Checkins_anonymized.txt` Time and venue ID of check-ins made by Foursquare users. Each venue ID corresponds to a physical place, linked to a category in Foursquare database (e.g. venue Asmalı Mescit is in the parent category Neighborhood). The check-in time is displayed in GMT with the offset for the correct time zone.

Example:
~~~
[user]  [venue_ID]                 [checkin_time]                    [offset]
822121  4b4b87b5f964a5204a9f26e3   Tue Apr 03 18:00:07 +0000 2012    -420
208842  4b4606f2f964a520751426e3   Wed Apr 04 11:32:47 +0000 2012    120
113817  3fd66200f964a52000e71ee3   Fri Apr 06 21:30:23 +0000 2012    -300
...     ...                        ...                               ...
~~~


#### Venue information data

* `raw_POIs.txt` Venue category and location information of venue IDs for our Foursquare extracted dataset.

Example:
~~~
[venue_ID]                 [latitude]     [longitude]     [category]           [country_code]
4b4b87b5f964a5204a9f26e3   40.729209	  -73.998753      Mall                 US
4b4606f2f964a520751426e3   36.309536      -119.31340      Asian Restaurant     MX
3fd66200f964a52000e71ee3   -34.28493	  65.3134064      Library              FR
...                        ...            ...             ...                  ...
~~~

## I.2 -


## Estimation of the distance threshold

We will try few methods to differenciate Travelers and Residents:

- The *first method* is a comparison between the threshold and the average of distances per-user.
- In the **second** method, we look at the fraction of checkins farther than the threshold. Then we compare this fraction to a variable percentage.
- The ***third*** consists in a Kernel Density estimation to group users separately.

To this end we have to establish a threshold distance value to compare the distances to.
A method to estimate the optimal limit can be to use the density curve of distances between friends' homes and search for when checkins are far from homes.  
We saw that between $100km$ and $450km$, the probability of having a friend is stable. The kink at the greater edge of the plateau shows a quick and sharp drop of the density curve.  


{% include homes_plot.html %}

One can conclude that users do not have a lot of friends living farther than $450km$.  
In our case, we consider the $450km$ kink as the threshold value to define users as Travelers or Resident in the first two methods.
