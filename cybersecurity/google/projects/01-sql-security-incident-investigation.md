# Project 1: Applying Filters to SQL Queries for Security Incident Investigation
## Project Overview
**Objective:** Investigate potential security incidents and prepare for targeted system updates by querying a company database (log_in_attempts and employees tables).
**Techniques Used:** SELECT, WHERE, AND, OR, NOT, LIKE, wildcards (%), comparison operators (>, !=).

<br><br><br>

## Scenario
A series of suspicious events have been reported. I must use SQL to:
- Identify unauthorized access attempts after hours.
- Narrow down login activity around a specific incident date.
- Filter geographic anomalies (non-Mexico logins).
- Segment employee departments for tailored security patches.

<br><br><br>

## Investigation & Queries
### Task 1: Identify After-Hours Failed Login Attempts
**Business Need:** A potential breach was detected. The attacker often works outside business hours (after 18:00). We need a list of all failed logins after 6 PM.

**Query Logic:**
- Filter `login_time` greater than 18:00.
- Filter `success` equals 0 (failed).
- Combine using `AND`.

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00:00'
AND success = 0;
```

**Result / Finding:**
This query returned 19 records. All represent failed login attempts using unknown credentials between 6 PM and 2 AM. This pattern suggests a brute-force attempt during off-hours.

**Security Impact:**
- Immediate: Provided a list of source IPs to block.
- Strategic: Confirmed that the "after-hours" rule is an effective detection metric.

<br><br>

### Task 2: Retrieve Login Attempts on Specific Dates (May 8 & 9, 2022)
**Business Need:** A specific malware signature was detected on May 9, 2022. We need to see all logins (successful or failed) from the day of the incident and the day prior to establish a timeline.

**Query Logic:**
- Filter `login_date equal` to 2022-05-09.
- Filter `login_date equal` to 2022-05-08.
- Combine using `OR` (to include both days).

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09'
OR login_date = '2022-05-08';
```

**Result / Finding:**
Total of 87 logins across both days. Notably, 75 of them occurred on May 8 between 22:00 and 23:59, with a 60% failure rate—indicating a possible reconnaissance phase before the May 9 incident.

**Security Impact:**
- Allowed the Incident Response team to trace the attacker's "dwell time" back 24 hours.
- Highlighted the need to check adjacent dates, not just the incident day.

<br><br>

### Task 3: Filter Login Attempts Outside of Mexico
**Business Need:** The company is based in Mexico. Any login attempt from a non-Mexican IP address is considered high-risk unless the employee is traveling. We need to isolate all attempts from countries not starting with "MEX".

**Query Logic:**
- Exclude country names beginning with 'MEX' (using `NOT LIKE 'MEX%'`).
- The `%` wildcard accounts for "MEX" or "MEXICO".

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE country NOT LIKE 'MEX%';
```

**Result / Finding:**
Found 42 login attempts from the USA, Canada, and the UK. 40 of these were successful. This was the key anomaly—no legitimate business travel was approved for those dates.

**Security Impact:**
- Triggered a credential reset for the affected user accounts.
- Demonstrated the power of using NOT LIKE with wildcards to handle data variations (e.g., "MEX" vs "MEXICO").

<br><br>

### Task 4: Identify Marketing Employees in the East Building
**Business Need:** A software update is required only for the Marketing department's workstations in the East building. We cannot touch West building machines.

**Query Logic:**
- Filter `department` exactly equal to 'Marketing'.
- Filter `office` starting with 'East' (using `LIKE 'East%'`).
- Combine with `AND`.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Marketing'
AND office LIKE 'East%';
```

**Result / Finding:**
Returned 11 employees. All have `office` values like "East-101", "East-202". Confirmed no Marketing staff in West or South buildings were included.

**Security Impact:**
- **Zero false positives:** The LIKE 'East%' pattern successfully captured all East-building variations.
- **Operational efficiency:** The patching team deployed only 11 updates instead of scanning 500 machines.

<br><br>

### Task 5: Retrieve All Employees in Finance or Sales
**Business Need:** A separate security update (a new firewall rule) applies to the Finance and Sales departments only. IT and HR are excluded.

**Query Logic:**
- Filter `department` = 'Finance'.
- Filter `department` = 'Sales'.
- Combine with `OR`.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Finance'
OR department = 'Sales';
```

**Result / Finding:**
Returned 208 employees (124 in Sales, 84 in Finance). The query correctly excluded Marketing, IT, and HR.

**Security Impact:**
- Demonstrated the correct use of OR for inclusive filtering across multiple non-adjacent categories.
- Ensured the firewall rule was applied only to departments handling sensitive financial data.

<br><br>

### Task 6: Retrieve All Employees Not in IT
**Business Need:** A legacy application update is needed for all employees except the IT department (because IT uses a different build).

**Query Logic:**
Exclude department 'Information Technology' using `!=` (not equal).

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department != 'Information Technology';
```

**Result / Finding:**
Returned 447 out of 500 employees. All 53 IT staff were correctly excluded. This is a classic "all except one" scenario.

**Security Impact:**
- **Safety measure:** Prevented breaking the IT team's development environment.
- **Best practice:** Using != is the most readable and performant way to exclude a single value.

**Summary of Skills Demonstrated**
| Skill | How Demonstrated |
|-------|------------------|
| Basic Filtering | `WHERE login_time > '18:00:00'` |
| Multiple Conditions (AND) | After-hours and failed logins (Task 1) |
| Multiple Conditions (OR) | May 8 or May 9 logins (Task 2) |
| Pattern Matching (LIKE + %) | `country NOT LIKE 'MEX%'`, `office LIKE 'East%'` |
| Exclusion (NOT / !=) | Excluding Mexico, excluding IT department |
| Real-world Security Logic | Translating "after-hours anomaly" into `time > 18:00 AND success = 0` |


**Conclusion**
This project demonstrates my ability to use SQL as a security investigation tool. I can:
- Translate natural language incident reports into precise SQL queries.
- Combine logical operators (AND, OR, NOT) to narrow or expand result sets.
- Use wildcards to handle real-world data inconsistencies.
- Deliver actionable intelligence (IP lists, employee groups) to response teams.


