# Group 3: DATA 226 Project 

## Project Overview
This project analyzes and visualizes SJSU King Library study room booking data to understand room utilization, demand trends, peak booking periods, and booking behavior under varying academic/operational conditions. The project uses **Python** for extraction/transformation, **Apache Airflow** for ETL orchestration, **PostgreSQL** as the warehouse, and **Tableau** for dashboarding.

## Main Files and Their Purpose

### Data Files
1. **tableau_dashboard/DWProject.twb**  
   - Tableau workbook containing final dashboard visualizations and interactive analysis.

2. **csv_txt_files/sjlibrary_bookings.csv**  
   - Raw/aggregated study room booking records scraped from the SJSU Library booking system.

3. **csv_txt_files/sjlibrary_completed_dates.txt**  
   - Tracks completed booking extraction dates to support resumable/incremental scraping.

4. **csv_txt_files/sjlibrary_completed_hours_weeks.txt**  
   - Tracks completed library-hours extraction weeks.

5. **csv_txt_files/sjlibrary_hours.csv**  
   - Library operating hours data by date/week.

6. **data_sources/Calendar23-24.pdf, Calendar24-25.pdf, Calendar25-26.pdf**  
   - Academic calendar PDFs used to derive instructional periods, breaks, holidays, exams, etc.

---

### Python Scripts
1. **bookings.py**  
   - Extracts booking data from the SJSU Library booking system.

2. **calendars.py**  
   - Parses academic calendar PDFs into structured academic-period data.

3. **hours.py**  
   - Extracts/scrapes library operating hours.

4. **transform.py**  
   - Cleans, joins, enriches, and transforms raw extracted data into warehouse-ready dimension/fact tables.

---

### Warehouse Output Tables
1. **dim_date**  
   - Date dimension with calendar, academic-period, and operational-condition attributes.

2. **dim_room**  
   - Room/resource dimension containing room metadata.

3. **dim_time**  
   - Time dimension containing hour/minute/part-of-day attributes.

4. **fact_bookings**  
   - Central fact table containing booking events and durations.

---

### Airflow / Infrastructure
1. **airflow_project/dags/etl_dag.py**  
   - Airflow DAG automating full ETL pipeline.

2. **airflow_project/config/airflow_config.yml**  
   - Airflow/environment configuration settings.

3. **docker-compose.yml**  
   - Docker container definitions for local Airflow/PostgreSQL environment.

---

## Analytical SQL Queries

1. **Least Utilized Library Resources.sql**  
   - Identifies the least-utilized rooms/resources based on total booked hours and booking frequency.

2. **Peak Study Room Demand.sql**  
   - Aggregates bookings by weekday and hour to identify peak demand periods.

3. **Study Room Booking Trends.sql**  
   - Tracks booking volume trends over time (monthly/temporal seasonality).

4. **Study Room Demand by Academic Context.sql**  
   - Compares booking demand across instructional days, exams, breaks, holidays, and other academic periods.

---

## Conclusion
This project builds an end-to-end data warehouse and analytics pipeline for SJSU library room booking data, from extraction through dashboard visualization. It enables actionable insights into room demand, temporal usage patterns, and operational planning.
