# Ultra Marathon Running

Predicting Ultra Marathon Race Pace: A Gender, Elevation, Age, and Distance Analysis

## Project Proposal to predict Race Pace based on specific variables
Do males and females need different time allocations to finish an ultra marathon race due to elevation?
How do distance, elevation, age, and elevation affect running performance?

A caveat to the data is that we already know average race pace, however, can we predict average race pace given specific variables?

## Background & Motivation
As an avid runner, ultra marathon running is a passion of mine.  Ultra Marathon running is a particularly unique sporting event that requires endurance and stamina as well as proper training. Ultra Marathon running is particularly interesting when attempting to look at the data for races across multiple variables as to why others run better or worse.

Military members may live in different altitude areas, which could impact their performance. By analyzing data based on gender, age, and altitude, we can determine if training protocols need to be adjusted for optimal performance.

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

To make this more focused to the military I am choosing high and low elevations of unique military bases.  Fort Eisenhower versus Fort Carson.

- To see how my data was manipulated and transformed please look in the data folder at UM_data_top_100.csv. 
- To see how the data was cleaned check the cleaning_data.ipynb
- My initial hypothesis testing was conducted in running_hypothesis.ipynb (most information discarded for my main analysis)
- My full analysis was conducted in all_100_running_hypothesis.ipynb
- My full regression analysis for my predictive model was conducted in the box_cox.ipynb
- I have one notebook checking how seasons affect running data in the adding_seasonal_data.ipynb (discarded for my main analysis)

## Hypothesis
I had four individual hypotheses ran in regards to my data to understand if it affects my target data or not (average race pace).

### Hypothesis
    - Gender significantly affects average race pace.
    - Age significantly affects average race pace.
    - Average State Elevation significantly affects average race pace.
    - Distance significantly affects average race pace.
In all of my hypotheses above, all statements were in fact true in regards to my data when comparing race pace.

## MVP

- Convert data to specific units (integers or floats) instead of strings as they are continuous.

- Set gender data to binary values (0 for females, 1 for males).

- Compare linear regression, log model transformation, and other regression models to determine the best model for analysis.

- Use the best model to perform a predictive analysis on average race pace from the selected features.


## Analysis

- Initial Pair Plot Analysis is showing distribution of variables between males (1) and females (0).
- The pair plot likely shows that race pace generally decreases with increasing age for both genders.
- The plots show a distinct separation between the race paces of males and females, with males generally having faster paces.
- The rate at which race pace decreases with age might differ between males and females. This can be observed if the lines for males and females have different slopes.
- The age distribution for both genders might show that certain age groups have more data points, which could affect the model's estimates.

#### ![Pair plot of features](Images/pair_plot_features.png)

- Average Race Paces in Virginia and Colorado for 31 mile runs
    - Comparison of race data at 489 feet (Virginia) vs. 6800 feet (Colorado).

    - The data indicates that gender, age, and elevation impact running performance.

    - Outliers are accounted for by taking the average race pace, which provides a more reliable comparison.

#### ![Average Race Paces in Virginia for 31 mile runs](Images/real_avg_race_pace_virginia.png)
#### ![Average Race Paces in Colorado for 31 mile runs](Images/real_avg_race_pace_colorado.png)


## Regression Analysis
- When conducting the regression analysis, Linear regression was first tested.  The residuals plot of predicted values show a cone shape showing heteroscedasticity and plots of predicted vs actual values shows invalid predictions.  A Box Cox transformation was ultimately used due to it's homoscedasticity in the residuals and analysis of the predicted values versus the actual values.  Real data versus predicted data is compared from race paces versus age to show how each model compared to each other.  Multiple models were tested, however, the box cox transformation made the best estimate of predictions for analysis.

### Linear Regression

Upon first utilizing the Linear Regression model, it was utilized due to my target data being a continuous set of data.
- Calculated Mean Squared Error: 0.927758784169388

- The Linear Regression plot of the residuals below shows a heteroscedastic model, implying that my model might not be able to be accurate.  It shows a cone shape and the shape should be more homoscedastic.  This implies as the values go up for my prediction the less accurate they may be.

#### ![Linear Regression Residuals Plot](Images/linear_reg_plot.png)

- In this model of the linear regression predictions we see that our predicted values of the average race pace are linear compared to the actual values.  This will show inconsistent results and ultimately show improper analysis fo the data. The thought process behind using another method is to find a transformation or regression model that will show more accurate results.

#### ![Linear Regression Fit](Images/Linear_Reg_fit.png)

### Box Cox Transformation

A box cox transformation with an xgboost regressor was used for this predictive model ultimately. It gives normality of residuals, more constant variance (Homoscedasticity, better fit, and reduced MSE).

    - XGBoost Regressor improves predictions by handling complex relationships, ranking feature importance, and preventing overfitting.

    - Combining Box-Cox transformation normalizes data, ensuring constant variance and improved model fit.

    - This approach significantly reduced prediction errors, enhancing the accuracy and reliability of race pace predictions.

The data becomes more normally distributed and has constant variance. The resulting linear regression model meets the assumptions better, leading to more accurate and reliable predictions.

- Calculated Mean Squared Error: 0.012979636721184285
- The calculated MSE was better than the linear regression and log transformation.  This method was more effective at minimizing the descrepancies between actual and predicted race paces.

- When looking at the residuals plot we see the plot is more homoscedastic compared to the other residual plots for the linear regression models and log transformation.  How does the data look now compared to the fit of data to the predictions?

#### ![Linear Regression with Box Cox Transformation](Images/box_cox_res_plot.png)

- The model created a better fit of the data.  Ultimately allowing the analysis of predicted paces fitting better.  There is now significant improvement to the accuracy and reliability compared to using untransformed linear regression.

#### ![Linear Regression with Box Cox Transformation](Images/box_cox_trans_fit.png)

## Predicted Outcomes

- The predictive outcomes of running pace show predicted race paces in miles per hour for males versus females at a low elevation (Fort Eisenhower at 446 feet) versus a high elevation (Fort Carson at 5680 feet). The age range is from 17 to 62 years old.

- The first model shows racers running a 31 mile race and gives predicted average race pace.  The average difference between the average pace for males and females at low altitude are 0.42 mph and 0.51 mph at high altitude. The average difference gap is wide for this race distance.  Males generally run faster than females and as age increases the pace decreases.  Males and females run faster on average at lower altitudes in their late twenties while they run faster at higher altitudes in their mid twenties.

#### ![Predicted pace for 31 miles](Images/31_mile_pred.png)

- The second model shows racers running a 50 mile race and gives predicted average race pace.  The average difference between the average pace for males and females at low altitude are 0.33 mph and 0.21 mph at low altitude.  The average difference gap did get more narrow. The trends are the same as 31 mile distances for ages and altitude for how fast they run on average.

#### ![Predicted pace for 50 miles](Images/50_mile_pred.png)

- The third model shows racers running a 100 mile race and gives predicted average race pace. The average difference between the average pace for males and females at low altitude are 0.20 and 0.21 mph at high altitude.  The trends are the same as the 31 mile distances and 50 mile distances.  The average difference in race pace is more narrow suggesting that it is equally difficult to run an extremely long race for both males and females, potentially showing the need for stamina and endurance as well as physiological capabilities. However, we can see the average difference get smaller and the race paces narrow as the distances increase. The fastest average pace for males and females at low altitude are in their late twenties to early thirties and at high altitude their faster paces is in their early to mid twenties.

#### ![Predicted pace for 100 miles](Images/100_mile_pred.png)

### Key Insights and Conclusion

All factors in my features affect a runner's average pace: gender, distance, age, and elevation.

- Consistent trend that Males maintain higher paces at all distances, elevation, and age.
- The average difference of males vs female paces narrows at longer distances, indicating similar endurance capacities for ultra-distances, and as distance increases the pace decreases.
- Both genders generally show peak performance in their twenties with pace declining with age.
- Males and females run faster, on average, in their late twenties to early thirties at lower elevation. They run faster, on average, in their early to mid twenties at higher elevation.

Runners should be given different allocations of time to finish a race based off of elevation, distance, gender, and age.  Coaches and athletes can utilize this data to create flexible training regimes for runners based off elevation, gender, age, and distance they are training for.


### Recommendations
- Gather racing data at distances shorter than 26 miles. Investigate where racers come from regarding different altitudes. Are they already acclimated to high altitude?

- Runners should be given different allocations of time to finish a race based on elevation, distance, gender, and age.

- Examine how seasonal data affects runners' times.

- Check cardio event results in the Army Combat Fitness Test for Fort Eisenhower versus Fort Carson to see if elevation concerns training. Compare initial acclimation versus fully acclimated states.

### Future areas of study
- Study terrain types (desert, mountain, forest, beach) and seasons to see their impact on runners' performance. Consider adding weight and height as factors if possible.

- Analyze the ACFT two-mile run for each age group of males versus females at Fort Carson and Fort Eisenhower. Include height and weight data.

## Contributing
To contribute to this project, please continue to add pertinent data about each race to enhance further exploration of ultra marathon running data analysis. Provide race data from races ranging from 2 to 13 miles for better predictions.

## License
This project is licensed under the GPL-3.0 License.

## Contact

- Author - Justin Welch
- GitHub - https://github.com/jdwelch88
