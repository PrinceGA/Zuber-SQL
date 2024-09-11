# Zuber-SQL-Project
# File Title: The Zuber Database

This project is part of the TripleTen Business Intelligence Analytics Program. It is an independent project designed to showcase what I have learned in SQL. The purpose was to analyze various aspects of taxi rides in Chicago to uncover patterns and insights.

### Table of Contents
| File Number | Title | Description |
| :-----------: | ----------- |----------- |
| 1 | README.md | This current page with all relevant information about the project, just past the Table of contents. |
| 2 | [Requirements.txt] | A simple .txt file with the provided project requirements as provided by TripleTen. |
| 3 | [Table Scheme.png] | A .png file showing the relationships between tables used in this project. |

| Section Title | Description |
| ----------- |----------- |
| DATA | Describes the source of data, included files, tables, and fields. |
| Description | Describes the final product's purpose, software, format, and included visuals. |
| Assumptions | Describes assumptions to include given by TripleTen and assumptions made based on the data and task. |
| Process | A general outline of how this project formed from start to finish. |
| Findings | Insights learned from the data analysis. |
| Project Querries |Lists and describes the specific SQL queries used for data extraction and analysis to investigate ride patterns, weather impact, and popular taxi companies. |

### Data
A database with info on taxi rides in Chicago provided by TripleTen:
- `'neighborhoods'` table: data on city neighborhoods
    - `'name'`: name of the neighborhood
    - `'neighborhood_id'`: neighborhood code
- `'cabs'` table: data on taxis
    - `'cab_id'`: vehicle code
    - `'vehicle_id'`: the vehicle's technical ID
    - `'company_name'`: the company that owns the vehicle
- `'trips'` table: data on rides
    - `'trip_id'`: ride code
    - `'cab_id'`: code of the vehicle operating the ride
    - `'start_ts'`: date and time of the beginning of the ride (time rounded to the hour)
    - `'end_ts'`: date and time of the end of the ride (time rounded to the hour)
    - `'duration_seconds'`: ride duration in seconds
    - `'distance_miles'`: ride distance in miles
    - `'pickup_location_id'`: pickup neighborhood code
    - `'dropoff_location_id'`: dropoff neighborhood code
- `'weather_records'` table: data on weather
    - `'record_id'`: weather record code
    - `'ts'`: record date and time (time rounded to the hour)
    - `'temperature'`: temperature when the record was taken
    - `'description'`: a brief description of weather conditions, e.g. "light rain" or "scattered clouds"

### Description:
- 5 Step SQL query.
- Exploratory data analysis and investigation of whether the duration of rides from the Loop to O'Hare International Airport changes on rainy Saturdays.

 #### Project Querries 

- Retrieve from the trips table all rides that started in the Loop (pickup_location_id: 50) on weekdays (Monday to Friday) and ended at Midway (dropoff_location_id: 66). Get the weather conditions for each ride by joining the weather_records table on the date and hour of the ride. Also, calculate the duration of each ride. Ignore rides for which data on weather conditions is not available.(![image](https://github.com/user-attachments/assets/a3e408e7-5a78-4042-b05a-41f0b1bae607)

- For November 1-7, 2017, the most popular taxi companies were Flash Cab and Taxi Affiliation Services. Find the number of rides for these two companies and name the resulting variable trips_amount. Join the rides for all other companies in the group "Other." Group the data by taxi company names. Name the field with taxi company names company. Sort the result in descending order by trips_amount.![image](https://github.com/user-attachments/assets/2916d956-6d15-4e7e-b862-3e9c5eaa48ca)

- For each hour, retrieve the weather condition records from the weather_records table. Using the CASE operator, break all hours into two groups: Bad if the description field contains the words rain or storm, and Good for others. Name the resulting field weather_conditions. The final table must include two fields: date and hour (ts) and weather_conditions.![image](https://github.com/user-attachments/assets/ccb356e8-78ed-422d-8f1a-e74fffe4fc65)

- For each day in November 2017, retrieve the total number of rides and the average duration of rides from the trips table. Additionally, classify each day as "High Demand" if the total number of rides exceeds 500 and "Low Demand" otherwise. Use the CASE operator to create this classification and name the resulting field demand_level. The final table should include the fields: date, total_rides, avg_duration, and demand_level. Sort the results by date in ascending order.![image](https://github.com/user-attachments/assets/be4f5f4d-5a84-4ec3-8ae7-1befc5c1da56)

- Retrieve from the trips table all rides that started at the Loop (pickup_location_id: 50) and ended at O'Hare (dropoff_location_id: 63) on any Saturday in November 2017. Get the weather conditions for each ride by joining with the weather_records table on the date and hour of the ride. Also, retrieve the duration of each ride. Ignore rides for which data on weather conditions is not available.![image](https://github.com/user-attachments/assets/e7b2ec41-a06b-46c9-9c49-f939bf766eb8)






### Assumptions:
- There isn't a direct connection between the trips table and weather_records table in the database.
- neighborhood_id is the Primary Key for the neighborhoods table.
- cab_id is the Primary Key for the cabs table.
- trip_id is the Primary Key for the trips table.
- record_id is the Primary Key for the weather_records table.

### Process:
Analyzed taxi rides by the company for specific dates, sorting by trip count.
Analyzed rides for companies containing specific keywords, grouping by company name.
Retrieved neighborhood IDs for O'Hare and Loop.
Categorized weather conditions by hour.
Retrieved Saturday rides from Loop to O'Hare, including weather and duration.
Sorted the results.

### Findings:
Weather Impact on Rides:

-By analyzing the rides that started in the Loop and ended at Midway on weekdays, it was observed that weather conditions varied significantly. This analysis provided insights into how different weather conditions might affect ride durations and frequency.
Popular Taxi Companies:

-Flash Cab and Taxi Affiliation Services were identified as the most popular taxi companies for the period of November 1-7, 2017. Flash Cab had the highest number of taxi rides.
The total number of rides for the group "Other" was significantly higher than each of the top companies separately.
Demand Classification:

-The analysis of daily ride demand in November 2017 showed clear patterns of high and low demand days. Days with more than 500 rides were classified as "High Demand", which helped in understanding peak usage periods.
Ride Patterns on Specific Routes and Days:

-Saturday rides from the Loop to O'Hare showed varying durations and were influenced by weather conditions. This analysis provided a deeper understanding of how external factors like weather can impact ride durations and frequency on specific days and routes.

These findings and processes provide a comprehensive overview of the ride patterns, popular taxi companies, and the impact of weather conditions on rides within the specified period and locations..
