# Employee Attrition Analysis - Power BI Project

## Introduction  
This Power BI project focuses on analyzing employee attrition and key performance indicators (KPIs) to help HR departments identify trends and make informed decisions. The report is divided into four interactive pages:

- **Overview**  
- **Demographics**  
- **Performance Tracker**  
- **Attrition Analysis**  

Each page serves a specific purpose, enabling users to gain insights into the workforce, monitor employee performance, and understand the drivers of attrition.

## Data Model Overview  
The data model is built on a star schema, ensuring optimal performance for analytical queries. The relationships and tables are as follows:

### FactPerformanceRating  
- Central fact table containing employee performance metrics like job satisfaction, manager rating, and relationship satisfaction.  
- Connected to dimension tables through keys like EmployeeID, RatingID, and SatisfactionID.

### DimEmployee  
- Core employee information, such as age, department, education, business travel frequency, and attrition status.  
- Acts as a primary source for demographic and employee-related filters.

### DimDate  
- Date dimension table with fields like day name, month name, and year, enabling time-based analysis.

### DimEducationLevel  
- Details employees' education levels (e.g., Bachelor’s, Master’s, etc.).

### DimRatingLevel  
- Contains mapping for performance rating levels.

### DimSatisfiedLevel  
- Defines satisfaction levels linked to the employee satisfaction metrics.

### Measures  
- Calculated fields include:  

**Key Note:** All relationships are either one-to-many or many-to-one, ensuring efficient cross-filtering for visuals.

## Page Breakdown

### 1. Overview  
**Purpose:** Provides a high-level summary of employee statistics and attrition rates.  
**Key Features:**  
- Total number of employees and attrition percentage.  
- Active employees at the company across departments.  
- Hierarchical Tree Map showing job role density in departments.

---

### 2. Demographics  
**Purpose:** Offers an overview of the workforce's demographic details.  
**Key Features:**  
- Age distribution.  
- Employees' marital status.  
- Gender breakdown.  
- Employee ethnicity and their average salaries.  

This page enables HR teams to understand employee diversity and identify demographic trends.

---

### 3. Performance Tracker  
**Purpose:** Tracks individual employee performance over time.  
**Key Features:**  
- **Employee Selector:** Filter to choose an employee for detailed performance insights.  
- **Performance Timeline:**  
  - Line charts displaying trends over the past four years for:  
    - Job Satisfaction  
    - Self Rating  
    - Manager Rating  
    - Relationship Satisfaction  
    - Environment Satisfaction  
    - Work-Life Balance  
- **Key Dates:**  
  - Start Date: Date of joining.  
  - Last Review Date: Most recent performance review.  
  - Next Review Date: Scheduled review date.

This page provides a comprehensive view of an employee's performance journey, helping managers identify potential issues or achievements.

---

### 4. Attrition Analysis  
**Purpose:** Analyzes attrition trends across various dimensions to identify patterns and risk factors.  
**Key Features:**  
- **Attrition Rate by Department and Role:** Column chart showing attrition percentages for each department and role.  
- **Attrition by Hire Date:** Line chart tracking attrition trends over hire dates.  
- **Attrition by Business Travel Frequency:** Combined column and line charts showing attrition rates for employees with different travel requirements.  
- **Attrition by Overtime Requirement:** Column chart highlighting the impact of overtime work on attrition.  
- **Attrition by Tenure:** Visualizes attrition trends based on employees' tenure at the company.

This page equips decision-makers with actionable insights into the root causes of employee attrition.
