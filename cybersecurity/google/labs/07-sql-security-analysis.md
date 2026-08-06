# Lab 7: Databases and SQL – Security Analysis & Data Investigation

**Tools Used:** MariaDB SQL  
**Focus Area:** Database Querying | Data Filtering | Table Joins  
**Skills:** SELECT Queries | WHERE Filters | AND/OR/NOT Operators | INNER/LEFT/RIGHT JOINs | Security Data Analysis  

<br><br>

## Objective

Learn to query, filter, and join data from a relational database using SQL. This lab provides practical experience in retrieving and analyzing information for security purposes, including investigating login attempts, employee device assignments, and departmental data.

<br><br>

## 1. Scenario Overview

As a cybersecurity analyst, I need to:
- Determine which employee devices must be updated
- Investigate user login activity for unusual events
- Analyze relationships between employees, machines, departments, and login attempts

**Data Sources:**
- `machines` table – employee device information
- `employees` table – employee details and department assignments
- `log_in_attempts` table – user login activity records

<br><br>

## 2. Lab Activities Summary

| Activity | Focus | Key SQL Concepts |
|----------|-------|------------------|
| 1 | Basic queries & sorting | SELECT, FROM, ORDER BY |
| 2 | Filtering with conditions | WHERE, LIKE pattern matching |
| 3 | Date/time & numeric filters | >, <, >=, <=, BETWEEN |
| 4 | Multiple conditions | AND, OR, NOT operators |
| 5 | Combining tables | INNER JOIN, LEFT JOIN, RIGHT JOIN |

<br><br>

## 3. Activity 1: Perform a SQL Query

**Objective:** Return information on employee devices and examine login attempts with sorting.

### Sample Data Structure

**`machines` table:**

| device_id | email_client | operating_system | OS_patch_date |
|-----------|--------------|------------------|---------------|
| 101 | Outlook | OS 1 | 2023-01-10 |
| 102 | Gmail | OS 2 | 2022-12-15 |
| 103 | Thunderbird | OS 2 | 2022-12-20 |
| 104 | Outlook | OS 3 | 2023-02-01 |

**`log_in_attempts` table:**

| event_id | username | login_date | login_time | country | success |
|----------|----------|------------|------------|---------|---------|
| 1 | alice | 2022-05-08 | 09:00:00 | USA | 1 |
| 2 | bob | 2022-05-09 | 18:30:00 | CAN | 0 |
| 3 | charlie | 2022-05-10 | 06:30:00 | MEX | 1 |
| 4 | diana | 2022-05-11 | 20:15:00 | USA | 0 |

### SQL Queries Executed

| Query # | Purpose | SQL Statement |
|---------|---------|---------------|
| 1 | View all devices | `SELECT * FROM machines;` |
| 2 | View specific columns | `SELECT device_id, email_client FROM machines;` |
| 3 | View device specs | `SELECT device_id, operating_system, OS_patch_date FROM machines;` |
| 4 | Investigate login locations | `SELECT event_id, country FROM log_in_attempts;` |
| 5 | Check after-hours logins | `SELECT username, login_date, login_time FROM log_in_attempts;` |
| 6 | View all login attempts | `SELECT * FROM log_in_attempts;` |
| 7 | Sort by date | `SELECT * FROM log_in_attempts ORDER BY login_date;` |
| 8 | Sort by date then time | `SELECT * FROM log_in_attempts ORDER BY login_date, login_time;` |

### Key Learning: ORDER BY

```sql
-- Single column sort
ORDER BY login_date;

-- Multi-column sort (date first, then time)
ORDER BY login_date, login_time;
```


## 4. Activity 2: Filter a SQL Query
Objective: Apply filters to retrieve specific information about employees, machines, and departments.

### Sample Data
**`machines` table:**

| device_id	| operating_system | 
| --------- | ---------------- | 
| 101 |	OS 1 |
| 102 |	OS 2 |
| 103 |	OS 2 |
| 104 |	OS 3 |


**`employees` table:**

| employee_id | name | department | office | device_id |
| ----------- | ---- | ---------- | ------ | --------- |
| 1 | Alice | Finance | North-101 | 101 | 
| 2 | Bob | Sales | South-109 | 102 |
| 3 | Charlie | Marketing | East-170 | 103 |
| 4 | Diana	| IT | West-220 | 104 |


### SQL Queries Executed
| Query | Purpose | SQL Statement |
|-------|---------|---------------|
| 1 | View device columns | SELECT device_id, operating_system FROM machines; |
| 2 | Filter OS 2 devices | SELECT device_id, operating_system FROM machines WHERE operating_system = 'OS 2'; |
| 3 | Finance department | SELECT * FROM employees WHERE department = 'Finance'; |
| 4 | Sales department | SELECT * FROM employees WHERE department = 'Sales'; |
| 5 | Specific office | SELECT * FROM employees WHERE office = 'South-109'; |
| 6 | South building (pattern) | SELECT * FROM employees WHERE office LIKE 'South-%'; |


### Key Learning: LIKE Pattern Matching
| Pattern | Meaning | Example Match |
|---------|---------|---------------|
| 'South-%' | Starts with "South-" | South-109, South-205 |
| '%East%' | Contains "East" | North-East, East-170 |
| '%109' | Ends with "109" | South-109, North-109 |


## 5. Activity 3: Apply More Filters in SQL
Objective: Filter data by dates, times, and numeric values using operators.

### **Sample Data:** `log_in_attempts`
| event_id | username | login_date | login_time | success | country |
|----------|----------|------------|------------|---------|---------|
| 100 | Alice | 2022-05-08 | 08:30:00 | 1 | USA |
| 101 | Bob | 2022-05-09 | 06:45:00 | 0 | CAN |
| 102 | Charlie | 2022-05-10 | 07:15:00 | 1 | MEX |
| 103 | Diana | 2022-05-11 | 06:30:00 | 0 | USA |
| 104 | Bob | 2022-05-12 | 08:00:00 | 1 | USA |


### SQL Queries Executed
| Filter Type | SQL Statement | Result Count |
|-------------|---------------|--------------|
| Date > value | WHERE login_date > '2022-05-09' | 3 rows |
| Date >= value | WHERE login_date >= '2022-05-09' | 4 rows |
| Date range | WHERE login_date BETWEEN '2022-05-09' AND '2022-05-11' | 3 rows |
| Time < value | WHERE login_time < '07:00:00' | 2 rows |
| Time range | WHERE login_time BETWEEN '06:00:00' AND '07:00:00' | 2 rows |
| Numeric >= | WHERE event_id >= 100 | 5 rows |
| Numeric range | WHERE event_id BETWEEN 100 AND 150 | 5 rows |


### Key Learning: Comparison Operators
| Operator | Meaning | Use Case |
|----------|---------|----------|
| > | Greater than | After a specific date |
| >= | Greater than or equal | On or after a date |
| < | Less than | Before a specific time |
| <= | Less than or equal | On or before |
| BETWEEN | Inclusive range | Date or numeric ranges |


## 6. Activity 4: Filter with AND, OR, and NOT
Objective: Apply multiple conditions using logical operators.

### Sample Data
#### **`log_in_attempts` table:**

| event_id | username | login_date | login_time | success | country |
|---------|----------|------------|------------|---------|---------|
| 100 | Alice | 2022-05-08 | 08:30:00 | 1 | USA |
| 101 | Bob | 2022-05-09 | 19:00:00 | 0 | CAN |
| 102 | Charlie | 2022-05-10 | 17:15:00 | 1 | MEX |
| 103 | Diana | 2022-05-11 | 20:30:00 | 0 | USA |
| 104 | Eve | 2022-05-12 | 16:00:00 | 1 | MEX |

#### **`employees` table:**

| emp_id | username | department | office |
|--------|----------|------------|--------|
| 1 | Alice | Finance | East-170 |
| 2 | Bob | Sales | South-109|
| 3 | Charlie | Marketing | East-320 |
| 4 | Diana | Information Technology | West-205 |
| 5 | Eve | Marketing | East-170 |


### SQL Queries Executed
| Query | Logical Operator | SQL Statement | Security Relevance |
|------|------------------|----------------|--------------------|
| 1 | AND | WHERE login_time > '18:00' AND success = 0 | Failed after-hours logins |
| 2 | OR | WHERE login_date = '2022-05-08' OR login_date = '2022-05-09' | Suspicious date range |
| 3 | NOT | WHERE NOT country LIKE 'MEX%' | Exclude specific country |
| 4 | AND | WHERE department = 'Marketing' AND office LIKE 'East-%' | Dept in specific building |
| 5 | OR | WHERE department = 'Finance' OR department = 'Sales' | High-value departments |
| 6 | NOT | WHERE NOT department = 'Information Technology' | All except IT |


### Key Learning: Logical Operator Truth Table
| Condition A | Condition B | A AND B | A OR B | NOT A |
|-------------|-------------|---------|--------|-------|
| TRUE | TRUE | TRUE | TRUE | FALSE |
| TRUE | FALSE | FALSE | TRUE | FALSE |
| FALSE | TRUE | FALSE | TRUE | TRUE |
| FALSE | FALSE | FALSE | FALSE | TRUE |


## 7. Activity 5: Complete a Join
Objective: Use INNER JOIN, LEFT JOIN, and RIGHT JOIN to combine tables.

### Sample Data
#### **`employees` table:**

| emp_id | username | department | device_id |
|--------|----------|------------|-----------|
| 1 | Alice | Finance | 101 |
| 2 | Bob | Sales | 102 |
| 3 | Charlie | Marketing | 103 |
| 4 | Diana | IT | NULL |
| 5 | Eve | Marketing | 104 |

#### **`machines` table:**

| device_id | device_name | operating_system |
|-----------|-------------|------------------|
| 101 | Laptop-A | OS 1 |
| 102 | Laptop-B | OS 2 |
| 103 | Laptop-C | OS 2 |
| 105 | Laptop-E | OS 1 |

#### **`log_in_attempts` table:**

| event_id | username | login_date | login_time | success | 
| -------- | -------- | ---------- | ---------- | ------- | 
| 100 | Alice | 2022-05-08 | 08:30:00 |	1 |
| 101 | Bob | 2022-05-09 | 19:00:00 | 0 |
| 102 | Charlie | 2022-05-10 | 17:15:00 | 1 |
| 103 | Eve | 2022-05-11 | 20:30:00 | 0 |


### Join Results Summary
| Join Type | SQL Statement | Rows Returned | What It Shows |
|-----------|---------------|---------------|---------------|
| INNER JOIN | machines INNER JOIN employees ON machines.device_id = employees.device_id | 3 | Only matched records |
| LEFT JOIN | machines LEFT JOIN employees ON machines.device_id = employees.device_id | 4 | All machines + matches |
| RIGHT JOIN | machines RIGHT JOIN employees ON machines.device_id = employees.device_id | 5 | All employees + matches |
| INNER JOIN login | employees INNER JOIN log_in_attempts ON employees.username = log_in_attempts.username | 4 | Employees with login records |


### Key Learning: JOIN Types Visualized
| Join Type  | Result |
|------------|--------|
| INNER JOIN | Only rows with matches in both tables |
| LEFT JOIN | All left + matched right (NULL if no match) |
| RIGHT JOIN | All right + matched left (NULL if no match) |

#### INNER JOIN: 
| A | B | 
| ✓ | ✓ |
| ✓ | ✓ |

#### LEFT JOIN: 
| A | B | 
| ✓ | ✓ |
| ✓ | ✓ |
| ✓ | NULL |

#### RIGHT JOIN:
| A | B | 
| ✓ | ✓ |
| ✓ | ✓ |
| NULL | ✓ |




## 8. Security Applications of SQL
| Security Task | SQL Technique | Example Use Case |
|---------------|---------------|------------------|
| Incident investigation | WHERE filters | Find failed logins after hours |
| User behavior analysis | ORDER BY | Identify unusual login patterns |
| Asset management | JOIN | Match employees to devices |
| Compliance reporting | SELECT + filters | Generate audit reports |
| Anomaly detection | BETWEEN | Detect off-hours logins |
| Department isolation | AND / OR | Focus on sensitive departments |


## 9. Skills Demonstrated
| Skill | Application in Lab |
|-------|--------------------|
| SELECT queries | Retrieved specific columns |
| WHERE filters | Filtered based on conditions |
| Comparison operators | Used >, <, >=, <=, BETWEEN |
| Logical operators | Used AND, OR, NOT |
| Pattern matching | Used LIKE with % |
| Sorting | Used ORDER BY |
| Table joins | INNER, LEFT, RIGHT JOIN |
| Security data analysis | Investigated login anomalies |


## 10. Reflection
This lab provided hands-on experience with SQL for security analysis purposes. Key takeaways:

- SELECT statements form the foundation of data retrieval – knowing which columns to query saves time and reduces noise
- WHERE filters are essential for narrowing down security investigations (e.g., failed logins, specific time ranges)
- Logical operators (AND, OR, NOT) enable complex investigations that combine multiple conditions
- JOINs are critical for understanding relationships between entities (employees → devices → login attempts)
- ORDER BY helps identify patterns chronologically, which is crucial for incident timelines

Demonstrates: Practical SQL proficiency for security monitoring, incident investigation, and asset management.

## 11. Appendix: Key Terminology
	
| Term | Meaning |
|------|---------|
| SELECT | SQL statement to retrieve data from a database |
| FROM | Specifies which table to query |
| WHERE | Filters rows based on conditions |
| ORDER BY | Sorts results by specified columns |
| LIKE | Pattern matching with wildcards (%) |
| BETWEEN | Filters within an inclusive range |
| AND | Requires both conditions to be true |
| OR | Requires at least one condition to be true |
| NOT | Excludes rows matching the condition |
| INNER JOIN | Returns only matching rows from both tables |
| LEFT JOIN | Returns all rows from left table + matches from right |
| RIGHT JOIN | Returns all rows from right table + matches from left |
| Wildcard (%) | Matches any character(s) in LIKE patterns |

## 12. SQL Quick Reference Card
```sql
-- Basic query
SELECT column1, column2 FROM table_name;

-- Filtering
SELECT * FROM table_name WHERE condition;

-- Pattern matching
SELECT * FROM employees WHERE office LIKE 'East-%';

-- Date/time filtering
SELECT * FROM logins WHERE login_date > '2023-01-01';

-- Multiple conditions
SELECT * FROM logins WHERE login_time > '18:00' AND success = 0;

-- Sorting
SELECT * FROM logins ORDER BY login_date DESC;

-- Inner join
SELECT * FROM table1 INNER JOIN table2 ON table1.key = table2.key;

-- Left join
SELECT * FROM table1 LEFT JOIN table2 ON table1.key = table2.key;
```

