
In 2020, zenith year for social media (until 2021), the WorldWideWeb proliferates with personalities, showing off their incredible life online and seeking for followers as much as forty-niners were looking for nuggets during the California Gold Rush. Many of the social media users have used at least once an analytical app to manage their virtual activity and visualise statistics about their posts and friends. One in particular can end friendships: it indicates which of your online friends has deleted you from its friend's list. It is heartbreaking to discover that one of your close friend estimated that you were not worth to follow anymore, and decided to cancel your virtual friendship.


It is almost impossible to precisely forecast the creation and deletion of particular social media friendships. Indeed it depends on too many real-life factors, including who you speak too, and who you meet (even randomly in a connection-free area, making impossible to use geo-localisation as prediction tool). Nevertheless we believe that with the appropriate dataset, it must be possible to predict the global dynamic of friendships over a certain period.

Throughout this study, we used data from the social network Foursquare to build and train prediction models in order to predict wheither friendships will be created or deleted in the future.

{% include Foursquare_logo.html %}


Foursquare is a location-based social network which database gathers 13+ billion check-ins, used by developers around the globe for localisation purposes. A **check-in** occurs when a user communicates its position, associated with a location category like bakery shops, boats, clubs,... In this case the check-in is considered as a **venue**.

We extracted a fraction of this database used in several papers exploring multiple aspects of the friendships between users. We base our analysis on these dataset.
