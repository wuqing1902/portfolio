# Project 2: File Permissions in Linux

## Project Overview
**Role Context:** Security Analyst / Linux System Administrator  
**Objective:** Perform file permission analysis and management to support a research team, identify unauthorized access, and apply appropriate restrictions to ensure system security.  
**Techniques Used:** `ls -la`, `chmod`, permission strings (rwx), octal notation (`700`), hidden file handling.

<br><br><br>

## Scenario
A research team has requested a security review of their Linux environment. I must:
- Review existing file and directory permissions.
- Identify violations of the principle of least privilege.
- Apply restrictions to remove unauthorized write access.
- Secure a hidden file and restrict directory access to the owner only.

<br><br><br>

## Investigation & Actions

### Step 1: Check File and Directory Details

**Command Used:**
```bash
ls -la
```

**Purpose:** List all files (including hidden files) with detailed permission, ownership, and file type information.

**Example Output (Based on Scenario):**
```bash
-rw-rw-rw- 1 researcher2 research 1234 project_k.txt
-rw-r----- 1 researcher2 research 1234 project_m.txt
-rw-rw-r-- 1 researcher2 research 1234 project_r.txt
-rw-rw-r-- 1 researcher2 research 1234 project_t.txt
-rw--w---- 1 researcher2 research 1234 .project_x.txt
drwx--x--- 2 researcher2 research 4096 drafts
```

**Finding:** Multiple files have overly permissive settings, particularly project_k.txt which allows write access to "others."

<br><br>

### Step 2: Describe the Permissions String
**Example Selected:** -rw-rw-r--

| Character Position | Meaning | Value |
|--------------------|---------|-------|
| 1 | File type | `-` (regular file) |
| 2-4 | User (owner) permissions | `rw-` (read & write) |
| 5-7 | Group permissions | `rw-` (read & write) |
| 8-10 | Others permissions | `r--` (read only) |

**Security Implication:** The group has write access, which may be acceptable for collaborative projects, but "others" having read access means anyone on the system can view this file.

<br><br>

### Step 3: Change File Permissions (Remove Others Write Access)
**Policy Requirement:** The organization does NOT allow "others" to have write access to any file.

**File Identified:** `project_k.txt`
**Current Permission:** `-rw-rw-rw-` (others had write permission)

**Command Used:**
```bash
chmod o-w project_k.txt
```

**Breakdown:**
- `chmod` → Change file permissions command
- `o-w` → Remove (`-`) write permission (`w`) from others (`o`)

**Result:**
```
Before: -rw-rw-rw-
After:  -rw-rw-r-- 
```

**Validation:** Others can now only read the file, not modify it. This aligns with organizational policy.

<br><br>

### Step 4: Change File Permissions on a Hidden File
File Identified: `.project_x.txt` (hidden file - denoted by leading dot)

Policy Requirement:
- NO write access for anyone
- Read access for user and group ONLY
- No access for others

Current Permission: `-rw--w----`

Command Used:
```bash
chmod ug+r,u-w,g-w,o-rwx .project_x.txt
```

Breakdown:

| Operation | Meaning |
|-----------|---------|
| `ug+r` | Add read permission to user and group |
| `u-w` | Remove write permission from user |
| `g-w` | Remove write permission from group |
| `o-rwx` | Remove read, write, and execute from others |

Result:
```
Before: -rw--w----
After:  -r--r-----
```

Validation:
- User can read (but not write) → `r--`
- Group can read (but not write) → `r--`
- Others have no access → `---`

This ensures the hidden file is protected from unauthorized modifications.

<br><br>

### Step 5: Change Directory Permissions
Directory Identified: `drafts`

Policy Requirement: Only the owner (`researcher2`) should have access to this directory.

Current Permission: `drwx--x---`

Command Used:
```bash
chmod 700 drafts
```

Breakdown (Octal Notation):

| Digit | Permission | Applied To |
|-------|------------|-------------|
| 7 | `rwx` (read, write, execute) | User (owner) |
| 0 | `---` (no permissions) | Group |
| 0 | `---` (no permissions) | Others |

Result:
```
Before: drwx--x--- (group could execute, others had no access)
After:  drwx------ (only owner has any access)
```

Validation: The owner can fully manage the directory. No other user (including group members) can list, enter, or modify contents. This is a strict access control suitable for sensitive drafts.

<br><br><br>

## Complete Permission Changes Summary
| File/Directory | Original Permission | Command Used | Final Permission |
|----------------|---------------------|--------------|------------------|
| `project_k.txt` | `-rw-rw-rw-` | `chmod o-w project_k.txt` | `-rw-rw-r--` |
| `.project_x.txt` | `-rw--w----` | `chmod ug+r,u-w,g-w,o-rwx .project_x.txt` | `-r--r-----` |
| `drafts` | `drwx--x---` | `chmod 700 drafts` | `drwx------` |

<br><br><br>

## Summary of Skills Demonstrated
| Skill | How Demonstrated |
|-------|------------------|
| Listing with Details | `ls -la` to view all files including hidden ones with full permissions |
| Reading Permission Strings | Interpreted `-rw-rw-r--` as user/group/others permissions |
| Removing Permissions (Symbolic) | `chmod o-w` to remove others' write access |
| Multiple Changes at Once | `chmod ug+r,u-w,g-w,o-rwx` for the hidden file |
| Octal Notation | `chmod 700` for directory restriction |
| Hidden File Handling | Identified and secured `.project_x.txt` |
| Directory Permissions | Secured drafts directory to owner-only access |

<br><br><br>

## Conclusion
This project demonstrates my ability to manage Linux file permissions as a security control. I can:
- Audit existing permissions using `ls -la`.
- Interpret 10-character permission strings to identify security violations.
- Apply principle of least privilege using both symbolic (`o-w`) and octal (`700`) `chmod` syntax.
- Secure hidden files and restrict directory access appropriately.
- Document permission changes with before/after validation.

These skills are essential for cybersecurity roles requiring Linux system administration, access control enforcement, and data protection.

