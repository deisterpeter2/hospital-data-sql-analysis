# Hospital Data Analysis (SQL)

## Project Overview

This project demonstrates core **SQL** skills through the analysis of hospital patient and operational data.

The project includes designing a relational database, loading and validating data, transforming data for analysis, and writing SQL queries that generate meaningful business insights. The analysis demonstrates SQL techniques commonly used by data analysts to answer operational and performance-related business questions.

---

## Business Problem

Hospitals generate large volumes of operational and patient data that can be used to improve efficiency, monitor performance, and support decision-making.

This project answers business questions related to patient volume, physician workload, department performance, and revenue using SQL.

---

## Tools Used

- SQL
- Relational Database
- SQL Queries
- Data Cleaning
- Data Transformation
- Data Analysis

---

## Project Objectives

### 1. Create and Populate a Relational Database

Design a relational database and populate it with hospital operational data.

**Deliverables**

- Database tables
- Primary and foreign key relationships
- Sample hospital data

---

### 2. Clean and Validate Imported Data

Prepare the imported data for analysis by identifying and correcting inconsistencies.

**Deliverables**

- Data validation
- Data cleaning
- Standardized values
- Improved data quality

---

### 3. Analyze Hospital Data

Write SQL queries to answer common operational and business questions.

**Deliverables**

- Patient analysis
- Department analysis
- Physician analysis
- Revenue analysis
- Admission trends

---

### 4. Demonstrate Advanced SQL Techniques

Use SQL features commonly expected in entry-level data analyst positions.

**Deliverables**

- Multi-table joins
- Window functions
- Common Table Expressions (CTEs)
- Aggregate calculations
- Ranking queries
- Data transformations

---

## SQL Concepts Demonstrated

- INNER JOIN
- Subqueries
- Common Table Expressions (CTEs)
- Aggregate Functions (`SUM`, `AVG`, `COUNT`)
- Window Functions
- Ranking Functions
- CASE Statements
- Date Functions
- Data Type Conversion (`CAST`, `CONVERT`)

---

## Business Questions Answered

This project demonstrates how SQL can answer important operational questions, including:

- What was the total revenue and number of visits for each department?
- For each doctor, how many distinct patients did they treat?
- For each department, what were the average satisfaction score and average wait times?
- Which doctors have the highest average satisfaction score (minimum 100 visits)?
- How do departments rank based on their total revenue within each department category?

---


## Skills Demonstrated

- SQL Database Design
- Relational Database Concepts
- Data Cleaning
- Data Validation
- Data Transformation
- Data Analysis
- Business Reporting
- Query Optimization
- Analytical Thinking
- Problem Solving

---

## Repository Structure

```
hospital-data-analysis-sql/
│
├── README.md
├── sql/
│   ├── Hospital-Create-Tables.sql
│   ├── Hospital-Insert-PatientVisits-Data.sql
│   ├── Hospital-Insert-Patient-Doctors-Data.sql
│   ├── Hospital-Insert-Dept-Treatment-Diagnosis-PayMethod-Data.sql
│   ├── Hospital-Data-Cleaning.sql
│   └── Hospital-Data-Analysis.sql
│
└── images/
    ├── Hospital-Data-ERD.png
    ├── Revenue-rank-by-dept.jpg
    ├── Dr-highest-satisfaction-score.jpg
    ├── Satisfaction-score-by-dept.jpg
    ├── Patient-volume-per-dr.jpg
    ├── Revenue-visits-per-dept.jpg

```

---

## Database Structure

The project uses a relational database consisting of multiple related tables representing:

- Patients
- Patient Visits
- Physicians
- Departments
- Diagnoses
- Treatments
- Payment Methods


```mermaid
erDiagram

    Dim_Patient ||--o{ PatientVisits : "PatientID"
    Dim_Doctor ||--o{ PatientVisits : "DoctorID"
    Dim_Department ||--o{ PatientVisits : "DepartmentID"
    Dim_Diagnosis ||--o{ PatientVisits : "DiagnosisID"
    Dim_Treatment ||--o{ PatientVisits : "TreatmentID"
    Dim_PaymentMethod ||--o{ PatientVisits : "PaymentMethodID"

    Dim_Patient {
        varchar PatientID PK
        varchar FirstName
        varchar LastName
        varchar Gender
        date DOB
        varchar CityStateCountry
    }

    Dim_Doctor {
        varchar DoctorID PK
        varchar FirstName
        varchar LastName
        varchar Gender
        integer ExperienceYears
    }

    Dim_Department {
        varchar DepartmentID PK
        varchar DepartmentName
        varchar DepartmentCategory
        varchar Specialization
        varchar HOD
    }

    Dim_Diagnosis {
        varchar DiagnosisID PK
        varchar DiagnosisName
    }

    Dim_Treatment {
        varchar TreatmentID PK
        varchar TreatmentName
    }

    Dim_PaymentMethod {
        varchar PaymentMethodID PK
        varchar PaymentMethod
    }

    PatientVisits {
        varchar VisitID PK
        varchar PatientID FK
        varchar DoctorID FK
        varchar DepartmentID FK
        varchar DiagnosisID FK
        varchar TreatmentID FK
        varchar PaymentMethodID FK
        date VisitDate
        time VisitTime
        date DischargeDate
        decimal BillAmount
        decimal InsuranceAmount
        integer SatisfactionScore
        integer WaitTimeMinutes
    }
```
> **Note:** The physical implementation stores patient visit records in separate tables (`PatientVisits_2020_2021`, `PatientVisits_2022_2023`, `PatientVisits_2024`, and `PatientVisits_2025`) to organize historical data. For clarity, the ERD presents these as a single logical `PatientVisits` fact table because all tables share the same structure and relationships.



---


