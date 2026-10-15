# 🏥 Medical Data Analysis Using SQL

## 📌 Project Overview

This project focuses on analyzing medical data using **MySQL** to retrieve useful information from patient records, hospital admissions, doctors, and province data.

The project includes practical SQL queries that demonstrate data filtering, aggregation, joins, subqueries, string functions, date functions, grouping, and sorting.

## 🎯 Project Objectives

- Analyze patient demographics such as gender, birth date, height, weight, and city.
- Retrieve patient records using specific conditions.
- Explore hospital admissions and diagnoses.
- Identify frequently reported allergies and repeated diagnoses.
- Combine patient, doctor, and province information using joins.
- Practice SQL problem-solving with healthcare-related data.

## 🗂️ Database Structure

**Database name:** `project_medical_data_history`

| Table | Description |
|---|---|
| `patients` | Patient details, including names, gender, birth date, city, province, allergies, height, and weight. |
| `admissions` | Admission and discharge dates, diagnoses, patient IDs, and attending doctor IDs. |
| `doctors` | Doctor details, including names and specialties. |
| `province_names` | Province IDs and their full names. |

## 🛠️ Tools and Technologies

- **Database:** MySQL
- **Query language:** SQL
- **SQL environment:** MySQL Workbench
- **Version control:** Git and GitHub

## 📚 SQL Concepts Practiced

- **Filtering:** `WHERE`, `IN`, `BETWEEN`, `LIKE`, `IS NULL`, `IS NOT NULL`
- **Aggregation:** `COUNT()`, `SUM()`, `MAX()`, `MIN()`
- **Grouping:** `GROUP BY`, `HAVING`
- **Sorting and uniqueness:** `ORDER BY`, `DISTINCT`
- **Joins and set operations:** `JOIN`, `UNION ALL`
- **String functions:** `CONCAT()`, `UPPER()`, `LOWER()`, `LENGTH()`
- **Date functions:** `YEAR()`, `DAY()`
- **Null handling:** `COALESCE()`
- **Subqueries and calculations:** scalar subqueries, `FLOOR()`, and arithmetic expressions

## 🔍 Analysis Tasks

The SQL script contains queries to:

1. Retrieve male patients and patients without recorded allergies.
2. Find patients whose first names begin with a particular letter.
3. Filter patients by weight, height, and birth year.
4. Display patients with their full province names.
5. Calculate the total number of admissions.
6. Find admissions where admission and discharge occurred on the same day.
7. Identify patients admitted multiple times for the same diagnosis.
8. Count patients by city and sort cities by patient count.
9. Analyze allergy frequency while excluding `NULL` values.
10. Count male and female patients in a single result row.
11. Group patients into weight bands.
12. Find patients diagnosed with Epilepsy who were attended by a doctor named Lisa.
13. Calculate the weight difference for patients with the last name Maroni.
14. Analyze admissions by day of the month.
15. Combine patient and doctor names into one result set with role labels.

## 💡 Sample SQL Queries

### 1. Count Male and Female Patients

```sql
SELECT
    SUM(gender = 'M') AS male_patients,
    SUM(gender = 'F') AS female_patients
FROM patients;
```

Counts male and female patients and displays both totals in one row.

### 2. Retrieve Patients and Their Province Names

```sql
SELECT
    p.first_name,
    p.last_name,
    pn.province_name
FROM patients AS p
JOIN province_names AS pn
    ON p.province_id = pn.province_id;
```

Combines patient records with province names using an `INNER JOIN`.

### 3. Find Repeated Diagnoses

```sql
SELECT
    patient_id,
    diagnosis,
    COUNT(*) AS admission_count
FROM admissions
GROUP BY patient_id, diagnosis
HAVING COUNT(*) > 1;
```

Finds patients who have multiple admission records for the same diagnosis.

### 4. Count Patients by City

```sql
SELECT
    city,
    COUNT(*) AS total_patients
FROM patients
GROUP BY city
ORDER BY total_patients DESC, city ASC;
```

Counts patients in each city, sorting by patient count from highest to lowest and then by city name.

### 5. Group Patients by Weight

```sql
SELECT
    FLOOR(weight / 10) * 10 AS weight_group,
    COUNT(*) AS total_patients
FROM patients
GROUP BY weight_group
ORDER BY weight_group DESC;
```

Groups weights into bands such as 100–109, 110–119, and 120–129.

## 📈 Key Learnings

- Writing SQL queries to retrieve and filter healthcare data.
- Summarizing records using aggregate functions.
- Combining related tables using joins.
- Handling missing values with `IS NULL` and `COALESCE()`.
- Working with dates and strings.
- Using subqueries and `HAVING` to answer more complex questions.
- Grouping and sorting records to identify patterns.

## 🚀 How to Run the Project

1. Install and open MySQL Workbench or another MySQL client.
2. Import or create the database and required tables.
3. Select the database:

   ```sql
   USE project_medical_data_history;
   ```

4. Confirm that the tables are available:

   ```sql
   SHOW TABLES;
   ```

5. Open the SQL script containing the project queries.
6. Run each query and review the results.

> **Note:** The database and table structures must be imported or created before running the queries. This repository's SQL script should contain the analysis queries unless schema and sample data are added separately.

## 📁 Suggested Repository Structure

```text
medical-data-analysis-sql/
├── README.md
└── medical_data_analysis.sql
```

## 🏷️ Skills Demonstrated

`MySQL` · `SQL` · `Data Analysis` · `Filtering` · `Aggregation` · `Joins` · `Subqueries` · `Data Grouping` · `Date Functions` · `String Functions`

## 📌 Project Status

Hands-on SQL learning project covering fundamental and intermediate SQL concepts.
