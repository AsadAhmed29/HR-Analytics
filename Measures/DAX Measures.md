# Employee Attrition Analysis - DAX Measures  

This document contains all the DAX measures used for the Employee Attrition Analysis dashboard.  

---

```DAX
-- % Attrition Rate
% Attrition Rate = DIVIDE([InactiveEmployees], [TotalEmployees])

-- % Attrition Rate Date
% Attrition Rate Date = DIVIDE([InactiveEmployeesDate], [TotalEmployeesDate])

-- Total Employees
TotalEmployees = DISTINCTCOUNT(DimEmployee[EmployeeID])

-- Total Employees by Date
TotalEmployeesDate = 
CALCULATE (
    [TotalEmployees],
    USERELATIONSHIP ( DimEmployee[HireDate], DimDate[Date] )
)

-- Active Employees
ActiveEmployees = CALCULATE([TotalEmployees], FILTER(DimEmployee, DimEmployee[Attrition] = "No"))

-- Inactive Employees
InactiveEmployees = CALCULATE([TotalEmployees], FILTER(DimEmployee, DimEmployee[Attrition] = "Yes"))

-- Inactive Employees by Date
InactiveEmployeesDate = CALCULATE([InactiveEmployees], USERELATIONSHIP(DimEmployee[HireDate], DimDate[Date]))

-- Environment Satisfaction
EnvironmentSatisfaction = 
CALCULATE (
    MAX ( FactPerformanceRating[EnvironmentSatisfaction] ),
    USERELATIONSHIP ( FactPerformanceRating[EnvironmentSatisfaction], DimSatisfiedLevel[SatisfactionID] )
)

-- Job Satisfaction
JobSatisfaction = MAX(FactPerformanceRating[JobSatisfaction])

-- Relationship Satisfaction
RelationshipSatisfaction = 
CALCULATE (
    MAX ( FactPerformanceRating[RelationshipSatisfaction] ),
    USERELATIONSHIP ( FactPerformanceRating[RelationshipSatisfaction], DimSatisfiedLevel[SatisfactionID] )
)

-- Work-Life Balance
WorkLifeBalance = 
CALCULATE (
    MAX ( FactPerformanceRating[WorkLifeBalance] ),
    USERELATIONSHIP ( FactPerformanceRating[WorkLifeBalance], DimSatisfiedLevel[SatisfactionID] )
)

-- Average Salary
AverageSalary = AVERAGE(DimEmployee[Salary])

-- Last Review Date
LastReviewDate = 
IF (
    MAX ( FactPerformanceRating[ReviewDate] ) = BLANK (),
    "No Review Yet",
    MAX ( FactPerformanceRating[ReviewDate] )
)

-- Next Review Date
NextReviewDate = 
VAR reviewOrHire =
    IF (
        MAX ( FactPerformanceRating[ReviewDate] ) = BLANK (),
        MAX ( DimEmployee[HireDate] ),
        MAX ( FactPerformanceRating[ReviewDate] )
    )
RETURN
    reviewOrHire + 365

-- Manager Rating
ManagerRating = 
CALCULATE (
    MAX ( FactPerformanceRating[ManagerRating] ),
    USERELATIONSHIP ( FactPerformanceRating[ManagerRating], DimRatingLevel[RatingID] )
)

-- Self Rating
SelfRating = 
CALCULATE (
    MAX ( FactPerformanceRating[SelfRating] ),
    USERELATIONSHIP ( FactPerformanceRating[SelfRating], DimRatingLevel[RatingID] )
)
