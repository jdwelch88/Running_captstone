# Running_captstone

Running data - For Capstone

## Project Proposal
Do males and females need to be offered different allocations of time to finish an ultra marathon race due to elevation?
Does distance, elevation, and age affect running performance?


## Background & Motivation
As an avid runner, ultra marathon running is a passion of mine.  Ultra Marathon running is a particularly unique sporting event that requires endurance and stamina as well as proper training. Ultra Marathon running is particularly interesting when attempting to look at the data for races across multiple variables as to why others run better or worse.

## Data

Data was downloaded from Kaggle.com (https://www.kaggle.com/datasets/aiaiaidavid/the-big-dataset-of-ultra-marathon-running)

I cleaned the data to only pull the top 100 Ultra Marathon events by most participants in the United states.  I had to individually add the average state elevation of each race which included 25 states.


 - Years of data range from 1963 - 2022.
 - There are 424,114 rows of data.
 - Age Range is from 17 to 62 years old.
 - 128,168 unique runners.
 - 86,727 individual male runners. 41,480 individual female runners.
 - Distances range from 26.2 Miles to 100 Miles.
 - Average State elevations range from 469 feet to 6800 feet.

Data to Focus on for features: Gender, Age, Average State Elevation (feet), and distance (miles).
Target data: mph (average race pace)

To make this more focused to the military I am choosing high and low elevations of unique military bases.


## Hypothesis
I had four individual null hypothesis ran in regards to my data to understand if it affects my target data or not (average race pace).

### Null Hypothesis
    - Gender does not signficantly affects average race pace.
    - Age does not significantly affects average race pace.
    - Average State Elevation does not affects average race pace.
    - Distance does not affects average race pace.
In all of my hypothesis above I failed to reject all my null hypothesis meaning all data had significant affects on my data.


## Results

- Average Race Paces in Virginia for 31 mile runs
#### ![Average Race Paces in Virginia for 31 mile runs](Images/real_avg_race_pace_virginia.png)



### Present key insights
    - The data attempts to predict average race pace by gender, elevation, and distance of a race.
    - Males generally run faster than females on average.
    - Elevation, age, gender, and distance affect average race pace.
    - Races below marathons may be skewed due to not having data for those distances.  Adding more data to those lower distances can increase the accuracy of the predicted model.
    

### Tell us what you recommend
- Recommend gathering racing data at distances shorter than 26 miles.

### Tell us what future areas you might want/need to study
- Consider studying Terrain type of events, i.e. desert, mountain, forest, beach and seasons to see if that affects runners performance.  See if adding weight and height can affect if possible.


## Contributing
To contribute to this project, continue to add where to find pertinent data about each race to enhance further exploration of data analysis of Ultra Marathon Running.  Continue to provide race data from races ranging from 2 to 13 miles for better predictions.

## License
This project is licensed under the GPL-3.0 License.

## Contact

- Author - Justin Welch
- GitHub - https://github.com/jdwelch88