# NYC Traffic Accident Analysis — Testing the Rush Hour Myth

A data analytics project testing a common assumption — that rush hour is the most dangerous time to drive — against 75,896 real NYPD-reported collisions in New York City (January–August 2020).

## Table of Contents

- [Overview](#overview)
- [Research Questions](#research-questions)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Tools & Technologies](#tools--technologies)
- [Team](#team)
- [Limitations](#limitations)


## Overview

Most people assume mornings and evenings are the most dangerous times to drive, simply because the roads are full. This project tests that assumption against real crash data instead of taking it at face value, by separating two questions that are usually blurred together:

- **Volume** — which hours produce the most crashes?
- **Severity** — which hours produce the deadliest crashes?

These two measures turn out to point in different directions, which is the central finding of the project: rush hour has only marginally more crashes than the rest of the day, but crashes outside rush hour are **more than twice as likely to be fatal**.

## Research Questions

This project answers four guiding questions:

| # | Question |
|---|---|
| RQ1 | Compare the % of total accidents by month. Do you notice any seasonal patterns? |
| RQ2 | Break down accident frequency by day of week and hour of day. When do accidents occur most frequently? |
| RQ3 | On which particular street were the most accidents reported? What % of all reported accidents does that represent? |
| RQ4 | What was the most common contributing factor overall (Vehicle 1)? What about for fatal accidents specifically? |

## Dataset

- **Source:** [NYC Open Data — Motor Vehicle Collisions (Crashes)](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95), NYPD-reported
- **Time window:** January 1 – August 30, 2020
- **Raw size:** 75,896 rows × 29 columns
- **Cleaned size:** 75,896 rows × 35 columns (6 engineered columns added; see [Methodology](#methodology))
- **Unit of analysis:** one row = one reported collision


## Methodology

The project has two phases: cleaning the raw data in Python, then modeling and visualizing it in Power BI. 

### Phase 1 — Data cleaning (Python / pandas)

1. Removed duplicate `COLLISION_ID` records (0 found)
2. Parsed `CRASH DATE` / `CRASH TIME` into real date-time values
3. Extracted an `Hour` column (0–23)
4. Extracted `DayName` and an `IsWeekend` flag
5. Built an `IsRushHour` flag (weekday 7–9 AM and 4–7 PM)
6. Built `IsInjury` and `IsFatal` severity flags
7. Dropped rows with unparseable date/time (0 dropped)
8. Handled missing `BOROUGH` (34.4% blank) by labeling as `"Unknown"` rather than deleting, and excluding it only from borough-specific charts
9. Standardized `ON STREET NAME` (trimmed, upper-cased) to avoid double-counting the same street
10. Filled 311 truly blank `CONTRIBUTING FACTOR VEHICLE 1` values with `"Unspecified"`

### Phase 2 — Power BI (data model & visuals)

- Corrected data types on import (date, whole number, boolean) so sorting, filtering, and legends behave correctly
- Fixed day-of-week sort order with a `WEEKDAY()` helper column and **Sort by Column**
- Built three DAX measures:
  ```dax
  Total Crashes = COUNTROWS(nyc_collisions_cleaned)

  Injury Rate = DIVIDE(
      CALCULATE(COUNTROWS(nyc_collisions_cleaned), nyc_collisions_cleaned[IsInjury] = TRUE),
      [Total Crashes]
  )

  Fatal Rate = DIVIDE(
      CALCULATE(COUNTROWS(nyc_collisions_cleaned), nyc_collisions_cleaned[IsFatal] = TRUE),
      [Total Crashes]
  )
  ```
- Built four core visuals: an hour × day-of-week heatmap (conditional formatting), an hourly crash-volume bar chart (rush hour highlighted), a dual-axis line chart of injury rate vs. fatal rate by hour, and a borough breakdown donut chart

## Key Findings

- **Seasonal pattern (RQ1):** crashes fell 71% in April 2020 during COVID lockdown, then rebounded steadily through August.
- **Timing (RQ2):** crash volume climbs gradually through the day, peaking around 4–5 PM; the noon–6 PM block is the heaviest window on every day of the week, not just weekdays.
- **The core test:** rush hour has only ~7% more crashes per hour than the rest of the day. Injury rates are nearly identical between rush and non-rush hours — but a non-rush-hour crash is **more than twice as likely to be fatal** (0.21% vs. 0.10%). Fatal-rate risk peaks between 3–5 AM, exactly when total crash volume is lowest.
- **Most dangerous street (RQ3):** the Belt Parkway, with 1,254 crashes — 1.65% of all reported collisions citywide, 66% more than the second-highest street. Every entry in the top 10 is a highway or parkway.
- **Contributing factors (RQ4):** Driver Inattention/Distraction is the top cause overall (25.6%) and is nearly identical rush vs. non-rush. But among the 143 fatal crashes specifically, **Unsafe Speed** ties as the top cause (23.8%) — nearly 7x its 3.6% share of crashes overall.

**Verdict:** the rush hour myth is true on raw numbers, but backwards on outcomes.

## Tools & Technologies

- **Python** (pandas) — data cleaning and feature engineering
- **Power BI Desktop** — data modeling, DAX measures, dashboard visuals
- **PowerPoint** — final presentation deck

## Team

| Name | Role |
|---|---|
| Aditya | Data Engineer — cleaned the data and set up the time filters |
| Melwin | Trend Analyst — built the month timeline and location charts |
| Kavya | Visual Architect — designed the final layout and heatmap templates |
| Shravan | Data Investigator — prepped the final slides and cause analysis |
| Mariyamol | Data Analyst — supported trend analysis and cause investigation |

## Limitations

- **No exposure data:** the analysis measures crash counts, not risk per mile driven, so it cannot say an hour is riskier *per driver* — only that it produces more or fewer, and more or less severe, crashes.
- **2020 was not a typical year:** COVID-19 stay-at-home orders emptied roads for months; absolute crash counts should not be read as a normal year's baseline, though hour-of-day shape is likely still informative.
- **Self-reported contributing factor:** 26.4% of records list "Unspecified," and the remaining categories rely on officer judgment at the scene rather than independently verified causes.
- **Borough gaps:** just over a third of records had no borough recorded; these were excluded only from borough-specific charts, not from the time-based findings.


