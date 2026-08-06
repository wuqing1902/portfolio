# Lab 16: Automate Cybersecurity Tasks with Python

**Focus Area:** Security Automation | Scripting | Log Analysis | File Processing  
**Tools Used:** Python 3  
**Skills:** Functions | Conditional Logic | Loops | File Operations | Regular Expressions | Data Parsing  

<br><br>

## Objective

Demonstrate understanding and practical application of Python concepts for cybersecurity, including automation, data parsing, conditional logic, iterative statements, and file operations – essential skills for log analysis, threat detection, and system monitoring.

<br><br>

## 1. Module Structure

| Section | Concepts Covered | Cybersecurity Application |
|---------|-----------------|--------------------------|
| 1 | Comments, functions, conditionals, loops | Login attempt validation, access control |
| 2 | User-defined functions, built-in functions, imports | Reusable security tools, data analysis |
| 3 | String/list methods, regex, concatenation | Log parsing, pattern matching |
| 4 | File operations, parsing | Allow list updates, log processing |

<br><br>

## 2. Section 1: Python Fundamentals

**Concepts:** Comments, Functions, Conditional Statements, Iterative Statements

### Comments

```python
# Single-line comment - explains code purpose
"""
Multi-line comment / Docstring
Used for function documentation
"""
```

### Conditional Statements (if, elif, else)
| Keyword | Purpose | Cybersecurity Use Case |
|---------|---------|----------------------|
| `if` | Execute if condition true | Check if login attempts exceeded limit |
| `elif` | Else-if chain | Multi-condition user role checks |
| `else` | Execute if no conditions true | Default deny access |
| `and` | Both conditions true | Username AND IP match |
| `or` | At least one condition true | Admin OR manager access |
| `not` | Negate condition | NOT on blocklist |

```python
# Login validation example
if username == "bmoreno" and login_attempts < 5:
    print("Access granted")
elif status == 500:
    print("Server error - log this incident")
else:
    print("Access denied - unauthorized user")
```


### Iterative Statements (for, while)
| Loop Type | Use Case | Example |
|-----------|----------|---------|
| `for` | Iterate through known sequence | Process list of users |
| `while` | Loop until condition changes | Retry login attempts |
| `break` | Exit loop early | Stop after finding threat |
| `continue` | Skip to next iteration | Skip whitelisted IPs |

```python
# Iterate through user list
for user in ["bmoreno", "tshah", "elarson"]:
    print(f"Checking logs for: {user}")

# Track login attempts
while login_attempts < 5:
    login_attempts += 1
    print(f"Attempt {login_attempts} of 5")
```

### User-Defined Functions
```python
def calculate_fails(total_attempts, failed_attempts):
    """Calculate failure percentage for security metrics"""
    fail_percentage = failed_attempts / total_attempts
    return fail_percentage

# Function call
failure_rate = calculate_fails(50, 5)
print(f"Failure rate: {failure_rate * 100}%")
```


### Built-in Functions
| Function | Purpose | Example | Output |
|----------|---------|---------|--------|
| `print()` | Display output | `print("Alert!")` | Alert! |
| `type()` | Get data type | `type(True)` | `<class 'bool'>` |
| `range()` | Generate sequence | `range(1, 10)` | 1-9 |
| `max()` | Find maximum | `max(10, 15, 5)` | 15 |
| `min()` | Find minimum | `min(10, 15, 5)` | 5 |
| `sorted()` | Sort sequence | `sorted([10, 15, 5])` | [5, 10, 15] |

### Importing Modules
```python
# Import entire module
import statistics

# Import specific functions
from statistics import mean, median

# Usage
data = [10, 20, 30, 40, 50]
print(mean(data))    # 30
print(median(data))  # 30
```


## 3. Section 2: Functions and Modules
Concepts: User-defined Functions, Built-in Functions, Importing Modules

### Function Design Pattern
```python
def function_name(parameters):
    """Docstring describing function"""
    # Function body
    return output_value
```


### Cybersecurity Function Examples
```python
# Validate login credentials
def validate_login(username, password_hash, attempts):
    if attempts >= 5:
        return "Account locked"
    elif username in allowed_users and verify_hash(password_hash):
        return "Access granted"
    else:
        return "Access denied"

# Calculate threat score
def calculate_threat_score(failed_logins, suspicious_ports, anomaly_score):
    return (failed_logins * 2) + (suspicious_ports * 3) + (anomaly_score * 5)
```


## 4. Section 3: Strings, Lists, and Regular Expressions
Concepts: String Methods, List Methods, Regular Expressions, Advanced Syntax

### String Methods
| Method | Purpose | Example | Output |
|--------|---------|---------|--------|
| `.upper()` | Convert to uppercase | `"security".upper()` | `"SECURITY"` |
| `.lower()` | Convert to lowercase | `"SECURITY".lower()` | `"security"` |
| `.index()` | Find position | `"security".index("c")` | 2 |

### List Methods
| Method | Purpose | Example |
|--------|---------|---------|
| `.append()` | Add to end | `username_list.append("btang")` |
| `.insert()` | Insert at index | `username_list.insert(2, "wjaffrey")` |
| `.remove()` | Remove first match | `username_list.remove("elarson")` |
| `.index()` | Find position | `username_list.index("tshah")` |


```python
# User list management (access control)
username_list = ["elarson", "fgarcia", "tshah"]
username_list.insert(2, "wjaffrey")  # Add new hire
username_list.remove("elarson")      # Remove departed employee
username_list.append("btang")        # Add contractor
print(username_list.index("tshah"))  # Find user position
```

### String and List Operations
| Operation | Syntax | Example | Result |
|-----------|--------|---------|--------|
| Concatenation | `+` | `"IT" + "nwp12"` | `"ITnwp12"` |
| Bracket notation | `[]` | `users[2]` | Third element |
| Slicing | `[start:end]` | `"security"[0:4]` | `"secu"` |


### Regular Expressions (re module)
| Pattern | Meaning | Example Match |
|---------|---------|---------------|
| `\w` | Word character (a-z, A-Z, 0-9, _) | a, Z, 9, _ |
| `\d` | Digit (0-9) | 0, 1, 2 |
| `.` | Any character (except newline) | a, , ! |
| `\s` | Whitespace | space, tab, newline |
| `+` | One or more | `\w+` = one or more word chars |
| `*` | Zero or more | `\d*` = zero or more digits |
| `{}` | Exact count | `\d{3}` = exactly 3 digits |


```python
import re

# Extract words from log entry
words = re.findall(r"\w+", "a53-32c .E")
print(words)  # ['a53', '32c', 'E']

# Extract all digits from IP address log
digits = re.findall(r"\d", "a53-32c .E")
print(digits)  # ['5', '3', '3', '2']

# Extract IP addresses from log
log_line = "Failed login from 192.168.1.100"
ip_addresses = re.findall(r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", log_line)
print(ip_addresses)  # ['192.168.1.100']
```


## 5. Section 4: File Operations and Parsing
Concepts: File Operations, Parsing (.split(), .join())

| Mode | Description | Use Case |
|------|-------------|----------|
| `"r"` | Read (default) | Read log files |
| `"w"` | Write (overwrites) | Create allow list |
| `"a"` | Append (adds to end) | Add to audit log |
| `"x"` | Exclusive creation | Create new file |


```python
# Reading a file
with open("login_attempts.txt", "r") as file:
    file_text = file.read()
    print(file_text)

# Appending to a log file
with open("access_log.txt", "a") as file:
    file.write("jrafael - login success - 2024-01-15\n")

# Writing a new allow list
with open("allow_list.txt", "w") as file:
    file.write("elarson,bmoreno,tshah")
```


### Parsing with .split() and .join()
| Method | Purpose | Example |
|--------|---------|---------|
| `.split()` | String → List | `"a,b,c".split(",")` → `['a','b','c']` |
| `.join()` | List → String | `",".join(['a','b','c'])` → `"a,b,c"` |


```python
# Parse comma-separated allow list
approved_users = "elarson,bmoreno,tshah".split(",")
print(approved_users)  # ['elarson', 'bmoreno', 'tshah']

# Parse space-separated removed users
removed_users = "wjaffrey jsoto abernard".split()
print(removed_users)  # ['wjaffrey', 'jsoto', 'abernard']

# Rebuild allow list as string
approved_users_string = ",".join(["elarson", "bmoreno", "tshah"])
print(approved_users_string)  # "elarson,bmoreno,tshah"
```


## 6. Cybersecurity Script Examples
Example 1: Update Allow List
```python
# Remove IP addresses from allow list
def update_allow_list(allow_list_file, remove_list_file):
    # Read current allow list
    with open(allow_list_file, "r") as file:
        allow_list = file.read().split()
    
    # Read IPs to remove
    with open(remove_list_file, "r") as file:
        remove_list = file.read().split()
    
    # Remove matching IPs
    for ip in remove_list:
        if ip in allow_list:
            allow_list.remove(ip)
    
    # Write updated allow list
    with open(allow_list_file, "w") as file:
        file.write("\n".join(allow_list))
    
    return allow_list

# Usage
updated_list = update_allow_list("allow_list.txt", "remove_list.txt")
```


### Example 2: Analyze Login Attempts
```python
# Analyze failed login attempts from log file
def analyze_failed_logins(log_file, threshold=5):
    failed_attempts = {}
    
    with open(log_file, "r") as file:
        for line in file:
            if "Failed password" in line:
                # Extract username using regex
                import re
                match = re.search(r"for user (\w+)", line)
                if match:
                    username = match.group(1)
                    failed_attempts[username] = failed_attempts.get(username, 0) + 1
    
    # Flag accounts exceeding threshold
    suspicious = {user: count for user, count in failed_attempts.items() 
                  if count >= threshold}
    
    return suspicious

# Usage
suspicious_accounts = analyze_failed_logins("auth.log", threshold=5)
print(f"Suspicious accounts: {suspicious_accounts}")
```


### Example 3: Parse HTTP Log
```python
# Extract IP addresses and status codes from web log
def parse_web_log(log_file):
    import re
    ip_pattern = r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"
    status_pattern = r'" (\d{3}) '
    
    requests = []
    
    with open(log_file, "r") as file:
        for line in file:
            ip = re.findall(ip_pattern, line)
            status = re.findall(status_pattern, line)
            
            if ip and status:
                requests.append({
                    "ip": ip[0],
                    "status": int(status[0])
                })
    
    # Count errors (4xx, 5xx)
    errors = [r for r in requests if r["status"] >= 400]
    
    return {
        "total_requests": len(requests),
        "error_count": len(errors),
        "error_rate": len(errors) / len(requests) if requests else 0
    }

# Usage
stats = parse_web_log("access.log")
print(f"Error rate: {stats['error_rate'] * 100}%")
```


## 7. Python-Cybersecurity Mapping
| Python Concept | Cybersecurity Application |
|----------------|--------------------------|
| Conditional statements | Access control decisions, alert thresholds |
| Loops (for, while) | Processing log files, iterating through user lists |
| Functions | Reusable threat detection modules |
| File operations | Reading/writing allow lists, audit logs |
| Regular expressions | Extracting IPs, usernames, timestamps from logs |
| String methods | Normalizing log entries (`.upper()`, `.lower()`) |
| List methods | Managing user/IP allow/block lists |
| `.split()` / `.join()` | Parsing CSV logs, formatting output |


## 8. Skills Demonstrated
| Skill | Application |
|-------|-------------|
| Conditional logic | Login validation, access control decisions |
| Iterative processing | Looping through user lists, log entries |
| Function creation | Reusable security analysis tools |
| File I/O | Reading/writing allow lists, audit logs |
| Regular expressions | Pattern matching in log files |
| Data parsing | Splitting/joining strings for data extraction |
| Module imports | Using statistics, re modules |


## 9. How to Run Python Scripts
### Prerequisites
- Python 3 installed (python --version to verify)
- Script files in same directory as input files

### Execution Commands
```bash
# Basic execution
python filename.py

# With input redirection
python parse_logs.py < access.log

# With arguments (advanced)
python analyze_threats.py --threshold 5 --input auth.log
Example Workflow
bash
# Navigate to project folder
cd /home/analyst/python_scripts

# Run allow list update script
python update_allow_list.py

# Run log analysis script
python analyze_failed_logins.py
```


## 10. Python Quick Reference Card
### Conditionals
```python
if condition:
    action
elif other_condition:
    other_action
else:
    default_action
```


### Loops
```python
for item in sequence:
    process(item)

while condition:
    action
    update_condition
```


### Functions
```python
def function_name(param1, param2):
    result = param1 + param2
    return result
```


### File Operations
```python
with open("file.txt", "r") as f:
    content = f.read()

with open("file.txt", "w") as f:
    f.write("data")
```


### Regex Patterns
```python
import re
re.findall(r"\d+", text)     # All digits
re.findall(r"\w+", text)     # All words
re.findall(r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", text)  # IP addresses
```


### String/List Operations
```python
text.upper()                 # Uppercase
text.lower()                 # Lowercase
text.split(",")              # Split by comma
",".join(list)               # Join with comma
list.append(item)            # Add to end
list.remove(item)            # Remove item
```


## 11. Reflection
This module helped consolidate fundamental Python concepts while applying them to cybersecurity-related scenarios.

### Key takeaways:

| Concept | Insight |
|---------|---------|
| Conditional logic | Essential for access control and alert thresholds |
| Loops | Enable processing of large log files efficiently |
| Functions | Promote code reuse for security tools |
| File operations | Critical for updating allow lists and audit logs |
| Regular expressions | Most powerful tool for log parsing |
| String/list methods | Simplify data normalization and management |


### Confidence gained:
- Automating routine security tasks
- Building scripts for incident response
- Parsing logs to extract Indicators of Compromise (IoCs)

Demonstrates: Python proficiency for security automation, log analysis, and operational efficiency.

## 12. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Syntax | Rules governing code structure |
| Function | Reusable block of code |
| Parameter | Input passed to function |
| Return value | Output from function |
| Conditional | Code that executes based on conditions (if/else) |
| Iteration | Repeating code (loops) |
| List | Ordered, mutable collection |
| String | Sequence of characters |
| Regex | Pattern matching language |
| Parse | Extract information from data |
| File I/O | Reading from/writing to files |


## 13. Next Steps for Python in Cybersecurity
| Skill Area | Learning Path |
|------------|---------------|
| Log analysis | Parse syslog, auth.log, web server logs |
| Network automation | Use socket library for port scanning |
| API integration | Query VirusTotal, Shodan via REST APIs |
| Forensics | Parse PCAP files with scapy |
| Incident response | Build automated triage scripts |
| Threat hunting | Process large datasets with pandas |

