
## Objectives

- Investigate unsuccessful login attempts occurring after business hours.
- Retrieve login attempts associated with specific dates.
- Identify login attempts that did not originate in Mexico.
- Filter employee records by department and office location.
- Retrieve employees in either the Finance or Sales department.
- Identify employees outside the Information Technology department.

## Technical Implementation

### 1. Investigating failed login attempts after business hours

sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00'
  AND success = FALSE;


*Purpose:* Retrieve login attempts that occurred after 18:00 and were unsuccessful, helping narrow down records for further investigation.

### 2. Filtering login attempts by date

sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09'
   OR login_date = '2022-05-08';


*Purpose:* Retrieve login records from the two dates relevant to the investigation.

### 3. Identifying login attempts outside Mexico

sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';


*Purpose:* Exclude country values beginning with MEX, including values such as MEX and MEXICO, from the results.

### 4. Identifying Marketing employees in the East building

sql
SELECT *
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East-%';


*Purpose:* Retrieve Marketing employee records for offices whose names begin with East-, such as East-170 and East-320.

### 5. Retrieving Finance or Sales employees

sql
SELECT *
FROM employees
WHERE department = 'Finance'
   OR department = 'Sales';


*Purpose:* Retrieve employee records for either department to support the specified computer-update task.

### 6. Identifying employees outside Information Technology

sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';


*Purpose:* Retrieve employees whose department is not Information Technology.

## SQL Concepts Applied

- *SELECT* — specifies the data to retrieve.
- *FROM* — identifies the source table.
- *WHERE* — filters records according to conditions.
- *AND* — requires both conditions to be true.
- *OR* — allows either condition to be true.
- *NOT* — excludes records matching a condition.
- *LIKE* — matches a text pattern.
- *% wildcard* — matches zero or more characters.

## Security Relevance

SQL filtering helps security professionals narrow large sets of records to information relevant to an investigation. It can support the review of failed authentication attempts, time-based activity, geographic indicators, and employee records associated with access or endpoint-management tasks.

Filtering is an investigative step, not proof of malicious activity. The resulting records should be assessed alongside other available evidence.

## Key Learning Outcomes

Through this lab, I strengthened my ability to:

- Translate security requirements into SQL conditions.
- Combine multiple filters to retrieve targeted records.
- Use logical operators and wildcards effectively.
- Work with authentication-log and employee datasets.
- Document database queries and explain their security relevance.

## Tools and Technologies

- SQL
- Relational database tables
- log_in_attempts and employees datasets
- Cybersecurity investigation and filtering concepts

## Conclusion

This project strengthened my practical understanding of SQL as a data-retrieval skill for cybersecurity. It reinforced the importance of writing precise queries, applying logical conditions correctly, and using database results to support security-related decisions.

*Focus areas:* Cybersecurity | SQL | Security Log Analysis | Database Querying | Technical Documentation

#Cybersecurity #SQL #SecurityAnalysis #BlueTeam #CybersecurityPortfolio
