# SQL Case Study: Investigating Security Incidents through Filtering

## Project Overview
In this lab, I acted as a Security Analyst investigating a recent security incident. I used SQL to filter through organizational login logs to identify suspicious patterns, specifically focusing on login attempts made outside of business hours and tracking specific event IDs.

## Scenario
The goal was to gather actionable intelligence about login attempts by filtering data based on dates, times, and event IDs. This process is crucial for incident response to narrow down when an unauthorized access might have occurred.

## Tools Used
* **MariaDB Shell** (SQL)
* **Organizational Database** (`log_in_attempts` table)

## Key Tasks & Technical Implementation

### 1. Filtering by Specific Dates
To investigate activity following a reported incident on May 9th, 2022, I queried all login attempts after that date.

<img width="673" height="335" alt="image" src="https://github.com/user-attachments/assets/f0e4e93c-6919-446f-8344-82072dfd6af0" />

Result: Identified 125 login attempts that required further review.

### 2. Narrowing Down a Date Range
To focus on a specific window of time (between May 9th and May 11th), I used the BETWEEN and AND operators.

<img width="671" height="376" alt="image" src="https://github.com/user-attachments/assets/62bf7c6a-2d7d-4e8f-be30-9fbeec177e56" />

### 3. Analyzing After-Hours Activity
Typical work hours begin at 07:00:00. I filtered for all login attempts made before this time to identify potential unauthorized access by users outside of standard shifts.

-- Finding logins between 06:00:00 and 07:00:00
<img width="673" height="373" alt="image" src="https://github.com/user-attachments/assets/7511637f-2246-4aa2-81b1-2be89b488805" />

Insights: Discovered that the earliest login attempt occurred at 06:03:41, which was flagged for investigation.

### 4. Investigating by Event ID
To streamline the report, I selected only specific fields (event_id, username, login_date) for events with IDs ranging from 100 to 150.

<img width="672" height="367" alt="image" src="https://github.com/user-attachments/assets/f258e133-d812-4b08-8066-c58aeecc51ec" />


### Results & Insights:
- **Operational Efficiency:** Using numeric and date operators allowed me to filter thousands of records into small, manageable lists of suspicious activity.
- **Security Auditing:** By isolating logins outside of business hours, I was able to identify specific usernames (e.g., eraab, tmitchel) that were active during unusual times.
- **Incident Response:** This structured querying approach is essential for timelines during a post-incident analysis.


*Note: This lab was completed as part of the Google Cybersecurity Professional Certificate.*
