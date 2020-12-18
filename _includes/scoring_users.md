# Scoring Users

To create our prediction model, we need to give each check-in a certain *Checkin Social Score*: we want to know how social a check-in is! 
Indeed giving a social score to the 3,430,171 different venues is hard work. Giving a social score to the 506 unique proposed categories is slightly easier, but also
not the best idea. Remember the Foursquare hierarchy? We can use the level 1 category to group all checkins into one of 275 categories now. 
Our social score is based on two main ideas, first of all that some places are less social than others, obviously a post office is less social than a nighclub. We 
define a coefficient for each level 0 category, reflecting how social this category is (in general).

| N° |       Level 0 category      | Coefficient |
|:--:|:---------------------------:|:-----------:|
|  0 |        Nightlife Spot       |     1.5     |
|  1 | Proffesional & Other Places |     1.1     |
|  2 |     College & University    |     1.3     |
|  3 |             Food            |     1.3     |
|  4 |        Shop & Service       |     1.0     |
|  5 |      Travel & Transport     |     1.2     |
|  6 |          Residence          |     1.1     |
|  7 |    Outdoors & Recreation    |     1.4     |
|  8 |     Arts % Entertainment    |     1.3     |
|  9 |            Event            |     1.5     |
| 10 |            Other            |     1.0     |
