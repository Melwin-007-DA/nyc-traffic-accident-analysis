# Project Status & Current Progress

### Where We Are Right Now: 75% Done
We have finished all of our backend data cleaning, setup, and our main charts. The core foundation of our dashboard is officially complete, putting us right at the 75% mark for the project.

---

### What We Have Finished So Far

#### Phase 1: Cleaning and Preparing the Data
* **Choosing the Dataset:** We locked down the official New York City car crash data specifically from January through August 2020.
* **Cleaning It Up:** We deleted broken rows, blank spaces, and messed-up location coordinates so they wouldn't ruin our averages.
* **Creating New Columns:** We used Power Query to split raw crash timestamps into clean, separate columns for the exact hour and day name. This is what lets us track precisely what time crashes happen.

#### Phase 2: Building our First Main Charts
* **Timeline Trends:** We built a month-over-month line chart that shows the massive drop-off in crashes during the April lockdown, followed by the summer climb back up.
* **Borough Breakdown:** We mapped out a donut chart that shows over 60% of all NYC crashes are heavily crowded into just two boroughs: Brooklyn and Queens.
* **Dangerous Streets:** We set up a bar chart to see specific roads, which proved that crashes heavily cluster on fast highways like the Belt Parkway rather than local neighborhood streets.

---

### What We Are Working On Next (The Final 25%)

* **Building the Time Heatmap:** We are setting up the color logic on our daily time grid. This will use a red color gradient to make the peak danger hours pop out instantly.
* **Finding the Root Causes:** We are building comparative charts to study driver behaviors. This will separate everyday distractions from high-speed fatal accidents so we can officially test the "Rush Hour Myth."
* **Connecting the Pages:** We are linking all of our sheets together using cross-filtering. That way, if someone clicks on a specific borough or street, the entire dashboard will instantly update to show the exact crash hours for that location.
