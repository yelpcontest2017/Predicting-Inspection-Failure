# Joshua Ashkinaze 
# Oberlin College

# Project Overview

How much signal and how much noise is in a Yelp review rant about cleanliness or bad service? I used Yelp resteraunt reviews and information to try to predict whether a resteraunt will fail food safety inspections. To do so, I used Toronto's DineSafe resteraunt inspection data and Yelp's 2017 academic challenge dataset. After matching the inspection data with Yelp resteraunts and reviews, I built a model predicting whether a resteraunt will pass its next inspection. 

The classification proved to be difficult, but it was a fun project. Here, I'll walk through my process and results. 

And if anyone has any ideas for how to improve the model, feel free to contact me at jashkina@oberlin.edu. The project has practical importantce for consumers to consumers if we think food safety inspections provide a (rather crude) proxy for dysfunction and uncleanliness. For public health officials, a model that predicts whether a resteraunt will fail inspections is useful for prioritizing which establishments to inspect. 



# Descriptive Analysis
## Inspections

There were 1706 restaurants in the dataset, and 2708 inspection instances. But the classes were highly imbalanced ![imbalanced](https://github.com/yelpcontest2017/Predicting-Inspection-Failure/blob/master/inspection_dist.png?) because only about 20% (561) of inspections resulted in failure. Although failure rates did not differ by price point, one surprising difference was how the distribution of _stars_ was opposite of what one would expect. 

![imbalanced](https://github.com/yelpcontest2017/Predicting-Inspection-Failure/blob/master/stars_fail.png?)
![imbalanced](https://github.com/yelpcontest2017/Predicting-Inspection-Failure/blob/master/stars_pass.png?)

We might think the star distribution of resteraunts who failed inspections would be more left skewed than those who didn't, but this isn't the case. It looks like we really need to turn to the more in-depth feature and text data for some insight. 

## Yelp Data
After one-hot encoding the categorical features, we can take a very specific look at what contributes to the liklihood a resteraunt will fail inspections. This makes First, 
<

| Feature Name | Chi2 | |:-----------------------------:|:---------:| | attributes.NoiseLevel_quiet | 8.929125 | | categories.Butcher | 7.654189 | | categories.Halal | 7.379606 | | categories.Hawaiian | 7.713115 | | categories.Hotels | 6.938719 | | categories.Hotels & Travel | 7.393479 | | neighborhood_Chinatown | 7.847233 | | neighborhood_Etobicoke | 11.147838 | | neighborhood_Willowdale | 7.723131 | | inspection.InspectionNumber_6 | 6.793666 |
