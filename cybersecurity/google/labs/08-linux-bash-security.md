# Lab 8: Linux Commands in the Bash Shell

**Tools Used:** Bash Shell | Linux Command Line  
**Focus Area:** System Navigation | File Management | User Administration | Permissions | Log Analysis   
**Skills:** pwd, ls, cd, cat, head, grep, mkdir, mv, rm, touch, nano, chmod, useradd, usermod, userdel, groupdel, man, whatis, apropos  

<br><br>

## Objective

Develop foundational Linux Bash skills for security analysis, including navigating directories, managing files, filtering data, controlling permissions, administering users, and accessing command-line help.

<br><br>

## 1. Scenario Overview

As a cybersecurity analyst working in a Linux environment, I need to:
- Navigate the file system to locate logs and reports
- Filter and search files for specific security events
- Create, move, and delete files and directories
- Manage file permissions to enforce access control
- Add and remove users and groups
- Find help for unfamiliar commands

<br><br>

## 2. Lab Activities Summary

| Activity | Focus | Key Commands | Security Relevance |
|----------|-------|--------------|-------------------|
| 1 | Finding files & navigation | pwd, ls, cd, cat, head | Locating logs and investigating file contents |
| 2 | Filtering with grep | grep, pipe (\|) | Searching logs for errors or specific users |
| 3 | Managing files | mkdir, mv, rm, touch, nano | Organizing evidence and cleaning up files |
| 4 | Managing permissions | chmod, ls -la | Restricting access to sensitive files |
| 5 | User management | useradd, usermod, chown, userdel | Controlling system access and ownership |
| 6 | Getting help | man, whatis, apropos | Discovering commands and options |

<br><br>

## 3. Activity 1: Find Files with Linux Commands

**Objective:** Navigate directories, locate files, and read file contents.

### Command Reference

| Command | Purpose | Example |
|---------|---------|---------|
| `pwd` | Print working directory | `pwd` → `/home/analyst` |
| `ls -l` | List files with details | Shows permissions, owner, size, date |
| `cd [directory]` | Change directory | `cd /home/analyst/reports` |
| `cat [file]` | Display entire file | `cat Q1_added_users.txt` |
| `head -n [number] [file]` | Show first N lines | `head -n 10 server_logs.txt` |

### Commands Executed
```bash
# Navigate to reports directory and examine users
cd /home/analyst/reports
cd users
ls
cat Q1_added_users.txt

# Navigate to logs and preview content
cd /home/analyst/logs
ls
head -n 10 server_logs.txt
```

### Security Application
| Task	| Command | Purpose |
|-------|---------|---------|
| Locate log files | cd /var/log | Access system logs |
| Preview large logs | head -n 50 auth.log | Check recent authentication attempts |
| Read configuration | cat /etc/passwd | View user accounts |

<br><br>

## 4. Activity 2: Filter with grep
**Objective:** Use grep and piping to search for specific information.

### Command Reference
| Command | Purpose | Example | 
|---------|---------|---------|
| grep "pattern" [file] | Search for pattern in file | grep "error" server_logs.txt |
| command \| grep "pattern" | Pipe output to grep | ls \| grep "Q1" |


### Commands Executed
```bash
# Search for errors in logs
cd /home/analyst/logs
grep "error" server_logs.txt

# Find files with specific patterns
cd /home/analyst/reports/users
ls | grep "Q1"
ls | grep "access"

# Search for specific users
grep "jhill" Q2_deleted_users.txt
grep "Human Resource" Q4_added_users.txt
```


### Security Application
| Task | Command | Purpose | 
|------|---------|---------|
| Find failed logins | grep "Failed password" /var/log/auth.log | Investigate brute force attempts |
| Search by IP | grep "192.168.1.100" access.log | Track specific attacker |
| Exclude patterns | grep -v "success" login.log | Find only failures |
| Count matches | grep -c "error" server_logs.txt | Quantify issues |


### grep Options Reference
| Option | Meaning | Use Case |
|--------|---------|----------|
| -i | Case insensitive | Search without case sensitivity |
| -v | Invert match | Exclude matching lines |
| -c | Count | Count occurrences |
| -n | Show line numbers | Locate exact position |
| -r | Recursive | Search directories |

<br><br>

## 5. Activity 3: Manage Files with Linux Commands
**Objective:** Create, move, remove files and directories, and edit files using nano.

### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `mkdir [dir]` | Create directory | `mkdir /home/analyst/logs` |
| `rm [file]` | Remove file | `rm tempnotes.txt` |
| `rm -r [dir]` | Remove directory recursively | `rm -r /home/analyst/temp` |
| `mv [source] [dest]` | Move/rename file | `mv Q3patches.txt /home/analyst/reports` |
| `touch [file]` | Create empty file | `touch tasks.txt` |
| `nano [file]` | Edit file | `nano tasks.txt` |
| `clear` | Clear terminal screen | `clear` |


### Commands Executed
```bash
# Create and remove directories
mkdir /home/analyst/logs
rm -r /home/analyst/temp

# Move and delete files
mv /home/analyst/notes/Q3patches.txt /home/analyst/reports
rm /home/analyst/notes/tempnotes.txt

# Create and edit file
touch /home/analyst/notes/tasks.txt
nano /home/analyst/notes/tasks.txt
cat /home/analyst/notes/tasks.txt
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Create evidence directory | `mkdir incident_2024` | Organize investigation files |
| Move suspicious file | `mv suspect_file /quarantine/` | Isolate potential malware |
| Remove sensitive temp files | `rm -r /tmp/sensitive_data` | Secure data cleanup |
| Create case notes | `touch case_notes.txt && nano case_notes.txt` | Document findings |

<br><br>

## 6. Activity 4: Manage Authorization
**Objective:** Examine and modify file and directory permissions.

### Permission Structure
-rw-r--r-- 1 owner group size date filename
│││││││││
│││└─┴─┴─┴─ Other permissions (read/write/execute)
││└─────── Group permissions
│└──────── Owner permissions
└───────── File type (-=file, d=directory)


| Permission | Symbol | Numeric Value | Meaning |
|------------|--------|---------------|---------|
| Read | r | 4 | View contents |
| Write | w | 2 | Modify contents |
| Execute | x | 1 | Run as program |



### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `ls -la` | List all files with permissions | `ls -la` |
| `chmod [permissions] [file]` | Change file permissions | `chmod o-w project_k.txt` |


### Permission Formats
| Format | Example | Meaning |
|--------|---------|---------|
| Symbolic | `chmod o-w file.txt` | Remove write for others |
| Symbolic | `chmod go-rw file.txt` | Remove read/write for group and others |
| Symbolic | `chmod ug=r file.txt` | Set owner and group to read-only |
| Numeric | `chmod 755 file.txt` | Owner:rwx, Group:r-x, Other:r-x |


### Commands Executed
```bash
cd /home/researcher2/projects
ls -la

# Remove write permission for others
chmod o-w project_k.txt

# Restrict group permissions
chmod go-rw project_m.txt

# Adjust hidden file permissions
chmod ug=r .project_x.txt

# Remove execute permission for group on directory
chmod g-x drafts
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Check file permissions | `ls -la sensitive_file.txt` | Verify access restrictions |
| Remove world read | `chmod o-r /etc/shadow` | Protect password hashes |
| Make script executable | `chmod +x scan.sh` | Allow script execution |
| Restrict directory access | `chmod 700 /home/analyst/private` | Only owner can access |

<br><br>

## 7. Activity 5: Add and Manage Users with Linux Commands
**Objective:** Add, modify, and delete users and groups.

### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `sudo useradd [username]` | Add new user | `sudo useradd researcher9` |
| `sudo usermod -g [group] [user]` | Set primary group | `sudo usermod -g research_team researcher9` |
| `sudo usermod -a -G [group] [user]` | Add to secondary group | `sudo usermod -a -G sales_team researcher9` |
| `sudo chown [user] [file]` | Change file owner | `sudo chown researcher9 project_r.txt` |
| `sudo userdel [username]` | Delete user | `sudo userdel researcher9` |
| `sudo groupdel [groupname]` | Delete group | `sudo groupdel researcher9` |


### User vs Group Types
| Type | Description | Example |
|------|-------------|---------|
| Primary group | Default group for user's files | research_team |
| Secondary group | Additional group membership | sales_team |
| System user | Service account (no login) | www-data |


### Commands Executed
```bash
# Add new user
sudo useradd researcher9

# Set primary group
sudo usermod -g research_team researcher9

# Change file ownership
sudo chown researcher9 /home/researcher2/projects/project_r.txt

# Add to secondary group
sudo usermod -a -G sales_team researcher9

# Delete user and group
sudo userdel researcher9
sudo groupdel researcher9
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Create auditor account | `sudo useradd auditor` | Temporary investigation access |
| Remove departed employee | `sudo userdel -r jsmith` | Revoke access immediately |
| Change file ownership | `sudo chown newadmin config.ini` | Transfer responsibility |
| Verify group membership | `groups researcher9` | Check user's groups |

<br><br>

## 8. Activity 6: Get Help in the Command Line
**Objective:** Use man, whatis, and apropos to discover commands and options.

### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `whatis [command]` | Short description | `whatis cat` → "concatenate files and print" |
| `man [command]` | Manual page | `man cat` (full documentation) |
| `apropos [keyword]` | Search commands by keyword | `apropos "create new group"` |


### Commands Executed
```bash
# Get short descriptions
whatis cat
whatis rm
whatis rmdir

# Read manual pages
man cat
man useradd

# Search for commands by keyword
apropos "first part file"
apropos "create new group"
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Find log viewing command | `apropos "view log"` | Discover tail, less, journalctl |
| Learn chmod syntax | `man chmod` | Understand permission options |
| Check command purpose | `whatis journalctl` | Quick command description |

<br><br>

## 9. Linux Command Quick Reference Card
### Navigation & File Management
```bash
pwd                    # Show current directory
ls -la                 # List all files with details
cd /path/to/dir        # Change directory
cat file.txt           # Display entire file
head -n 20 file.txt    # Show first 20 lines
tail -n 20 file.txt    # Show last 20 lines
```


### File Operations
```bash
mkdir new_dir          # Create directory
rm file.txt            # Delete file
rm -r directory        # Delete directory recursively
mv source destination  # Move or rename
cp source destination  # Copy file
touch newfile.txt      # Create empty file
nano file.txt          # Edit file
```


### Searching & Filtering
```bash
grep "pattern" file.txt          # Search in file
grep -i "pattern" file.txt       # Case insensitive
grep -v "pattern" file.txt       # Exclude pattern
ls | grep "keyword"              # Pipe to filter
```

### Permissions
```bash
ls -la                 # View permissions
chmod 755 file.txt     # Numeric: rwxr-xr-x
chmod u+x file.txt     # Add execute for owner
chmod go-rw file.txt   # Remove r/w for group/others
chown user:group file  # Change owner:group
```

### User Management (requires sudo)
```bash
sudo useradd username           # Add user
sudo userdel -r username        # Delete user with home dir
sudo usermod -aG group username # Add to secondary group
sudo groupadd groupname         # Create group
sudo groupdel groupname         # Delete group
```

### Getting Help
```bash
whatis command         # One-line description
man command            # Full manual
command --help         # Short help (many commands)
apropos keyword        # Search commands by keyword
```

<br><br>

## 10. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| Directory navigation | pwd, cd, ls to locate logs and reports |
| File content inspection | cat, head to read user lists and logs |
| Pattern searching | grep with piping to filter files and content |
| File management | mkdir, mv, rm, touch, nano for organizing evidence |
| Permission management | chmod, ls -la to restrict access |
| User administration | useradd, usermod, chown, userdel for access control |
| Command discovery | man, whatis, apropos to find help |

<br><br>

## 11. Reflection
This lab provided comprehensive hands-on experience with essential Linux Bash commands. Key takeaways:

- Navigation and file inspection (pwd, cd, ls, cat, head) are foundational for locating and examining logs during incident investigation
- grep with piping enables efficient searching through large log files – critical for identifying specific events like failed logins or error patterns
- File management commands (mkdir, mv, rm, touch, nano) help organize investigation artifacts and document findings
- Permission management (chmod, ls -la) ensures sensitive files are protected according to the principle of least privilege
- User administration (useradd, usermod, userdel) is essential for onboarding/offboarding and maintaining proper access control
- Help commands (man, whatis, apropos) enable self-sufficient learning and discovery of new commands

Demonstrates: Practical Linux proficiency for security monitoring, incident investigation, log analysis, and system administration.

<br><br>

## 12. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Bash | Bourne Again SHell – default Linux command-line interpreter |
| Directory | Linux term for folder |
| Piping (\|) | Sends output of one command as input to another |
| grep | Global Regular Expression Print – searches for patterns |
| Permission | Access control setting (read, write, execute) |
| Owner | User who owns a file/directory |
| Group | Collection of users with shared permissions |
| chmod | Change mode – modifies permissions |
| sudo | Superuser do – executes command with elevated privileges |
| Home directory | User's personal directory (/home/username) |
| Manual page | Built-in documentation for Linux commands |

<br><br>

## 13. Common Security Scenarios & Linux Commands
| Scenario | Linux Command |
|----------|---------------|
| Investigate failed SSH logins | `grep "Failed password" /var/log/auth.log` |
| Find large log files | `find /var/log -size +100M` |
| Monitor live log | `tail -f /var/log/syslog` |
| Check disk space | `df -h` |
| Find files owned by user | `find /home -user jsmith` |
| Count unique IPs in log | `grep "Failed" auth.log \| awk '{print $11}' \| sort \| uniq -c` |
| Backup directory | `cp -r /important/data /backup/` |

