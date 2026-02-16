PROJECT TITLE
healthcare-appointments-sql-project

PROJECT OBJECTIVE
This project analyzes a healthcare appointments dataset using MySQL.
The goal is to explore appointment trends, no-show rates, doctor workload, and generate business insights. 

DATA DESCRIPTION
The dataset contains the following columns:  appointment_id, patient_id, doctor_id, appointment_date, appointment_time, reason_for_visit, status

SECTION 1: DATA CLEANING

- Trimmed spaces from text columns
- Standardized status
- Checked for duplocates
- Checked null values
- Removed rows with critical NULLs
- Joined date and time column tables together

SECTION 2: EXPLORATORY ANALYSIS
- Counted total rows and columns
- Counted total appointments
- Counted distinct patients and doctors
- Counted reasons for visit and status values
- Analyzed status distribution
- Analyzed appointments per month
- Analyzed appointments per doctor
- Analyzed appointments per doctor per month
- Analyzed cancellation rate per month
- Analyzed No-show rate per doctor
- Analyzed most common reason_for_visit
- Analyzed top 5 busiest doctors
- Analyzed patients with more than 3 appointments
- Analyzed doctor with highest no-show count
- Analyzed monthly apppointments trend
- Analyzed ranking of  doctors by total appointments


BUSINESS QUESTIONS AND INSIGHTS
1. Which doctor handles the most appointments?
  SELECT doctor_id, COUNT(*) AS total_appointments
  FROM appointments
  GROUP BY doctor_id
  ORDER BY total_appointments DESC
  LIMIT 1;
Insight:
Doctor with id D005 has the highest workload, suggesting possible scheduling imbalance.

2. What is the overall no-show rate?
  SELECT 
    ROUND(SUM(CASE WHEN status = 'No-show' THEN 1 ELSE 0 END) * 100.0 
    / COUNT(*), 2) AS no_show_rate
  FROM appointments;
Insight:
The no-show rate is 26%, indicating potential revenue loss.

3. Which month has the highest appointments?
  SELECT 
      DATE_FORMAT(appointment_date, '%Y-%m') AS month,
      COUNT(*) AS total_appointments
  FROM appointments
  GROUP BY month
  ORDER BY month;
Insight:
The first month recorded the highest patient volume.




