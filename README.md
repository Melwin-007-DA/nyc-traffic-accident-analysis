# NYC Traffic Accident Analysis: Testing the "Rush Hour Myth" (Jan–Aug 2020)

## Project Overview
[cite_start]This data analytics project uses New York City car crash data to study traffic safety patterns in Power BI[cite: 2, 12]. [cite_start]Our main goal is to test the **"Rush Hour Myth"**—the common belief that the morning and evening commuter rush hours are always the most dangerous times to drive simply because the roads are packed[cite: 3, 6]. 

[cite_start]By looking at data from January through August 2020, we can compare normal traffic months against the unique, empty-road months caused by the COVID-19 lockdowns[cite: 3, 22]. [cite_start]This helps us see if drivers are actually more dangerous when they are stuck in gridlock, or when they have wide-open roads to speed[cite: 7].

## What We Found So Far (75% Milestone)
* [cite_start]**Macro Timeline Trends:** Our line chart shows a massive drop-off in April 2020 where crashes hit an all-time low (under 2,000) because lockdowns emptied the streets[cite: 22]. [cite_start]By July and August, numbers steadily climbed back up toward 4,000 as things opened up[cite: 23].
* [cite_start]**Borough Breakdown:** Our donut chart shows that accidents are not spread out evenly[cite: 30]. [cite_start]Over 60% of all NYC traffic collisions are heavily crowded into just two boroughs: Brooklyn (37%) and Queens (24.6%)[cite: 31].
* [cite_start]**Dangerous Streets:** Our bar chart proves that danger follows speed[cite: 37]. [cite_start]Drivers are much more likely to crash on fast, busy multi-lane highways than on local city streets, with the Belt Parkway emerging as the single most dangerous road (250+ crashes)[cite: 35, 38].

## Data Engineering & Tools
* **Platform:** Power BI Desktop / Power Query
* [cite_start]**Data Cleaning:** Filtered the dataset down to our 8-month window, removed broken rows, and cleaned up messed-up location coordinates[cite: 16, 17].
* [cite_start]**New Columns Built:** Split the raw crash timestamps into clean, separate columns for the exact Hour and Day Name so we can see precisely what time of day crashes happen[cite: 18].

## 🚀 What is Left to Build (The Final 25%)
1. [cite_start]**Building the Time Heatmap:** Setting up conditional formatting on our 24-hour time grid using a red color gradient to make peak danger hours pop out instantly[cite: 43].
2. [cite_start]**Finding the Root Causes:** Building comparative charts to look at driver behaviors[cite: 44]. [cite_start]This will separate everyday distractions from high-speed fatal accidents so we can officially test our main hypothesis[cite: 44].
3. [cite_start]**Connecting the Pages:** Linking all of our sheets together using cross-filtering so that clicking a borough or street automatically updates the time charts across the whole dashboard[cite: 45].
