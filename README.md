# NYC Traffic Accident Analysis: Testing the "Rush Hour Myth" (Jan–Aug 2020)

## Project Overview
This data analytics project uses New York City car crash data to study traffic safety patterns in Power BI. Our main goal is to test the "Rush Hour Myth"—the common belief that the morning and evening commuter rush hours are always the most dangerous times to drive simply because the roads are packed with cars. 

By looking at data from January through August 2020, we can compare normal traffic months against the unique, empty-road months caused by the COVID-19 lockdowns. This helps us see if drivers are actually more dangerous when they are stuck in gridlock, or when they have wide-open roads to speed.

## What We Found So Far (75% Milestone)
* **Macro Timeline Trends:** Our line chart shows a massive drop-off in April 2020 where crashes hit an all-time low (under 2,000) because lockdowns emptied the streets. By July and August, numbers steadily climbed back up toward 4,000 as things opened up.
* **Borough Breakdown:** Our donut chart shows that accidents are not spread out evenly. Over 60% of all NYC traffic collisions are heavily crowded into just two boroughs: Brooklyn (37%) and Queens (24.6%).
* **Dangerous Streets:** Our bar chart proves that danger follows speed. Drivers are much more likely to crash on fast, busy multi-lane highways than on local city streets, with the Belt Parkway emerging as the single most dangerous road (250+ crashes).

## Data Engineering & Tools
* **Platform:** Power BI Desktop / Power Query
* **Data Cleaning:** Filtered the dataset down to our 8-month window, removed broken rows, and cleaned up messed-up location coordinates.
* **New Columns Built:** Split the raw crash timestamps into clean, separate columns for the exact Hour and Day Name so we can see precisely what time of day crashes happen.

## What is Left to Build (The Final 25%)
1. **Building the Time Heatmap:** Setting up conditional formatting on our 24-hour time grid using a red color gradient to make peak danger hours pop out instantly.
2. **Finding the Root Causes:** Building comparative charts to look at driver behaviors. This will separate everyday distractions from high-speed fatal accidents so we can officially test our main hypothesis.
3. **Connecting the Pages:** Linking all of our sheets together using cross-filtering so that clicking a borough or street automatically updates the time charts across the whole dashboard.
