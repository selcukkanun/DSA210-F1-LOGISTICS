# DSA 210 Project: Analysis of Champion Drivers and Their Specific Features
## Does Being a World Driver Champion correlates with wet race performances and outperforming teammates?

## Terminology 
Wet Races: It means during the race the rain affected the track.

Dry Races: No rain during the races or the rain didn't affected the rain.

WDC: World Driver Champion.

Grid: It refers to the whole drivers during a race or season.


## Motivation
F1 is among the one the most popular sports around the world and as a fan of this sport I always wondered what metric makes a champion a champion.

In this project I will try to investigate metrics that affect championship rates. More specifically, does outperforming your teammate show correlation with being a champion and does being a good driver in wet show correlation with being a champion. I would consider these two since drivers who share the same car could perform similarly and I believe it is the most important metric for a champion to outperform their teammate because basically the drivers who share a team also share a car so they are in equal conditions. Also wet races always believed to measure the driving ability more so I'd be checking if being better in wet correlates with being a champion furthermore being more champion.

## Hypothesis
Null Hypothesis (H₀): Being World Driver Champion (WDC)  has no effect on how much they outperform their teammate.

Alternative Hypothesis (H₁): Being a WDC means outperforming your teammates more across the career.

Sub Hypothesis (H₁): Being more WDC means outperforming your teammates more across the career. (more championship more outperforming)

Alternative Hypothesis No.2 (H₂): Champion drivers perform better in wet conditions than non-champions, and more championships correlates with more win-rate in wet races.

## Data Sources

**Data Preparation:** Collect lap times, pit stops, DNFs, and race dates for the 2021–2024 seasons using the FastF1 and Jolpica APIs. Compare it within each other. Sort what is the cause of deviations in laptime, pitstop time (whether it is related to driver error or not) and collect the cause of DNFs.

For race results, race calendar, driver names: [Kaggle F1 Data](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020)

For weather data: [Kaggle F1 Weather Data](https://www.kaggle.com/datasets/mariyakostyrya/formula-1-weather-info-1950-2024)

For number of championships:[Wikipedia F1 page](https://en.wikipedia.org/wiki/List_of_Formula_One_World_Drivers%27_Champions)

Custom metrics: I double checked the weather data to make sure whether the rain affected the race or not. I come up with a full list of wet races between 1985-2024 simply by checking them one by one. Then compared to the other online sources like reddit pages.

## Methodology For Alternative Hypothesis 1:

1. **Get all race data with wet race information:**

   -I merged all the result results.csv and used the wet race dictionary to tag them as wet races.

2. **Get the merged finishing positions for all races and each driver:**

   -I merged all the results for all races and each driver and also added the driver name and constructor name so if they share the same constructor in the same race then these drivers are teammates.
   
3. **Calculations:**

   -I used the the merged data set to calculate for whether a driver beat their teammate or not for each race by simply comparing finishing positions for each race.

   -Then I calculated total number of times they beat their teammate and divided it with total number of races they went on.

   -I applied minimum 5 races limit since driver who had less than 5 races most probably weren't good enough to stay on F1 for even a full season. So basically cleared out outliers but didn't want to lost limited number of drivers.

    -Group the champions and non-champion drivers using the dictionary of WDCs. Then in order to compare these 2 groups I applied Mann-Whitney U test and calculate p_value.

   -Apply pearson and spearman correlation tests to see whether there is a direct relationship between number of WDC and outperforming your teammate more (without including non-champion drivers).

5. **Look for correlations:**

   - Checking if WDC drivers outperformed their teammate more than non-champion drivers. 

   - Checking if higher number of championship meant more races outperforming your teammate.  

   - Observe whether it applied amongst the only championships too. If it does then there is a real correlation.

7. **Conclusion:**

   - Determine if there is a real correlation or not by using the all p_values from each test applied(Spearman, Mann-Whitney U test, Pearson).


9. **Outcome for hypothesis 1:**

   - I have observed there is a real relationship between being a champion and outperforming your teammate. Also it correlates with more number of championships meant more percentage of races you outperform your teammate.

## Methodology For Alternative Hypothesis 2:

1.**Getting the data:**
   
   - Using the already merged dataset in hypothesis 1.
   
2.**Calculations:**
   
   - Simply calculating the number of wins for each driver in wet races. If they finished in position "1" they won the race and applying it to only wet races.
   
   - Calculate wet win rates for each driver.
   
   - Compare champion and non-champion drivers.
   
3.**Look for correlations:**
   
   - Simply apply Pearson, Spearman correlations and t_test. (Applied jittering here since there was a lot of driver who have no championship)
   
   - Check for p_values for each test
   
   - Apply each test only to the champion driver and read the values again.
   
4.**Conclusion** 
   
   - Determine if there is a real correlation or not by using the all p_values.

## Methodology For further works:
   
   - Could apply machine learning models to calculate possible new champions in the current grid.
   
   - Could detect which drivers could've been a wdc in the best.

## Further Works:

-I expect to predict who are the possible candidates for new champions for 2025 by simply comparing how they outperformed their teammates and how much they won in wet races across their careers. 

-I plan to get a list of drivers who was champion level driver but couldn't win any championship.
