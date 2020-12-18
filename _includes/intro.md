# Introduction

In 2020, zenith year for social media, the WorldWideWeb proliferates with celebrities and influencers, showing off their incredible life online and seeking for followers as much as forty-niners were looking for nuggets during the California Gold Rush. Many of the social media users have used an analytical app at least once to manage their virtual activity and visualise statistics about their posts and friends. One in particular can end friendships: indeed these apps can indicate which of your online friends has deleted you from their friend's list, or even unfollowed you. It is heartbreaking to discover that one of your close friends thought that you were not worth following anymore, and decided to cancel your virtual friendship.


It is almost impossible to precisely forecast the creation and deletion of particular social media friendships. Indeed it depends on too many real-life factors, including who you speak too, and who you meet, even randomly in a connection-free area. These factors making it difficult to use geo-localisation as friendship prediction tools. Nevertheless we believe that with the appropriate dataset, it must be possible to predict (or get close to) if a user will make or break friendships over a certain period.

Throughout this study, we used data from the social network *Foursquare* to build and train two different prediction models in order to determine whether friendships will be created or deleted a 22 month time period.

Foursquare is a location-based social network which database gathers 13+ billion check-ins, used by developers around the globe for localisation purposes. A **check-in** occurs when a user communicates their position, associated with a location category like a bakery, shops, boats, clubs, etc. We extracted a fraction of this database used in several papers exploring multiple aspects of friendship and mobility, and we will base our analysis on this dataset.

---
