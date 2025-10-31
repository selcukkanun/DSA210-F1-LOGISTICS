# DSA 210 Project: Analysis of Logistics and The Car's Performance in F1
## Does Workload of Logistics in the F1 Affect The Teams' Performances and Reliability?

Subquestions:
1. Are DNFs more frequent when races occur on consecutive weekends?
2. Does traveling correlate with reduced performance especially pit stops and average laptimes compared to race winners laptime(percentage difference from the race winner’s average lap time)?

## Terminology 
Pit stops: In F1 in a general sense a pit stop is a pause for new tyres, repairs, mechanical adjustments, as a penalty, or any combination of the above.
Laptime: Laptime is the time interval that a car completed one circulation around the track.
DNF: DNF stands for 'Did Not Finish'. The reason might vary like mechanical error or driver error etc.
Mechanical Error: A type of error caused by the malfunction or breakdown of a car component.



## Motivation
F1 is among the one the most popular sports around the world and as a fan of this sport I was always fascinated by how are cars, crews and car parts are moving around the world, sometimes switching continents, from one week to another and still all the teams perform at the top under all that workload. 

This study will investigate whether the logistics and workload comes with it affect the F1 teams' performance throughout the racing weekends. Specifically, If the logistics and workload of the back to back weekends affect the teams performances by the laptimes and mechanical problems with the help of the data science methods.

## Hypothesis
Null Hypothesis (H₀): The workload of the logistics does not affect the F1 teams' performances and reliability.

Alternative Hypothesis (H₁): Teams perform worse and experience more mechanical issues during back-to-back weekends.

H₂: Teams with factories located farther from the race circuit performed worse during consecutive or long-distance race weekends.

## Data Sources

**Data Preparation:** Collect lap times, pit stops, DNFs, and race dates for the 2021–2024 seasons using the FastF1 and Jolpica APIs. Compare it within each other. Sort what is the cause of deviations in laptime, pitstop time (whether it is related to driver error or not) and collect the cause of DNFs.

For laptimes of each driver and DNFs: [FastF1 Library](https://theoehrly.github.io/Fast-F1/)

For pitstop times and DNFs: [Kaggle F1 Data](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020)

For race calendar and circuit coordinates: [Jolpica F1 API](https://api.jolpi.ca/)

For how are the things are moving: [DHL Information Page](https://inmotion.dhl/en/formula-1)

Custom metrics: I am planning to calculate the distances by getting the information from DHL page and calculate the distances for each transportation method (freight trains, trucks or freight planes) and estimate their times from each factory.


## Methodology:

1. **Create variables:**
   - `travel_distance_km`: distance teams travel between races (it varies whether if the team goes from the factory or from one race circuit to another)
   - `relative_laptime_diff`: team’s average lap time compared to the winner’s (as a % difference).  
   - `dnf_rate`: percentage of cars from a team that didn’t finish a race.  
   - `avg_pitstop_time`: average pit stop time per team.
   - `back_to_back_flag`: whether the race happened in the upcoming weekend.  

2. **Normalize performance:**
   -Since tracks are different I will be comparing lap times relatively to the race winner instead of raw laptimes.
   
3. **Comparision**

   -Compare how teams performed in the last week and the current week compared to the race winner. How much mistakes they made in terms of mechanical or DNFs.
   -Compare how teams with differently located factories performed compared to eachother.

4. **Look for correlations:**
   - Checking if higher traveling distance or continent changes correspond to worse relative performance.  
   - Observe whether shorter gaps between races lead to more DNFs.

5. **Conclusion:**
   - Determine if teams show measurable performance drops or reliability issues during back-to-back and high-travel races.
   - Determine if teams with furtherly located factories performed poorer.


## Expected Outcome
I expect to observe if the race is consecutive and long distance travel between races would result in slower average lap times and higher DNF rates.  
This would suggest that logistics and workload with back-to-back racings has an effect on car performance and reliability.
