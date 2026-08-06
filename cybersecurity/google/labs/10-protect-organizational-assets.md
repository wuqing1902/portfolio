# Lab 10: Protect Organizational Assets

**Focus Area:** Data Protection | Encryption | Hashing | Access Control | Least Privilege  
**Standards Referenced:** NIST SP 800-53 (AC-6)  
**Skills:** Data Handling Policies | Encryption/Decryption | Hash Generation (SHA-256) | File Integrity Verification | RBAC | Account Lifecycle Management | MFA  

<br><br>

## Objective

Protect organizational data through secure handling practices, encryption, hashing, and access control improvements. This lab consists of four activities simulating real-world cybersecurity scenarios.

<br><br>

## 1. Lab Activities Summary

| Activity | Focus | Key Tools/Concepts | Security Relevance |
|----------|-------|-------------------|-------------------|
| 1 | Data handling & least privilege | NIST SP 800-53 AC-6, role-based access | Prevent data leaks |
| 2 | Decrypt encrypted messages | Caesar cipher, OpenSSL (AES-256-CBC) | Recover encrypted data |
| 3 | Create hash values | SHA-256, sha256sum, cmp | File integrity verification |
| 4 | Improve AAA (Authentication, Authorization, Accounting) | RBAC, MFA, account lifecycle | Access control enforcement |

<br><br>

## 2. Activity 1: Determine Appropriate Data Handling Practices

**Objective:** Analyze a data leak incident and recommend improvements using the principle of least privilege.

### Incident Summary

| Aspect | Details |
|--------|---------|
| **What happened** | Employee mistakenly shared entire folder of sensitive internal documents instead of limited materials |
| **Root cause** | Access to folder was not properly restricted or revoked after meeting |
| **Key failure** | Manager failed to remove access post-meeting; poor access control oversight |

### NIST SP 800-53: AC-6 - Least Privilege

| Aspect | Description |
|--------|-------------|
| **Purpose** | Ensure users are granted only minimum access necessary to perform tasks |
| **Key principle** | "Need-to-know" + "need-to-do" |
| **Implementation strategies** | Role-based access, time-bound access, regular access reviews |
| **Enhancements** | Privilege separation, parameterized access, monitoring privileged actions |

### Least Privilege Implementation Model

| Step | Process                  | Description                                      |
|------|--------------------------|--------------------------------------------------|
| 1    | User Request             | User requests access to a resource               |
| 2    | Role Evaluation          | System checks user's role/permissions            |
| 3    | Minimum Required Access  | Determine least privilege needed                 |
| 4    | Access Granted           | Only necessary access is provided                |
| 5    | Review & Revocation      | Periodic audit and removal of excess privileges  |


### Root Cause Analysis

| Cause Category | Specific Issue |
|----------------|----------------|
| **Policy** | No automatic access revocation |
| **Human** | Manager forgot to remove access |
| **Technical** | No time-based access controls |
| **Oversight** | No audit of folder permissions |

### Recommendations & Justification

| Recommendation | Implementation | Justification |
|----------------|----------------|---------------|
| Restrict access based on user roles | Implement RBAC | Ensures only authorized users view sensitive data |
| Automatically revoke access after defined period | Time-bound access controls | Reduces risk of forgotten permissions |
| Regular access reviews (monthly/quarterly) | Scheduled audits | Catches orphaned permissions |
| Enable access logging | Audit trails | Detect unauthorized access attempts |

<br><br>

## 3. Activity 2: Decrypt an Encrypted Message

**Objective:** Use Linux commands to decrypt encrypted data and recover hidden messages.

### Decryption Process Flow
| Step | Task | 
|------|------| 
| Step 1: | Navigate directories (ls, cd) |
| Step 2: | Read instructions (cat README.txt) |
| Step 3: | Find hidden files (ls -a) |
| Step 4: | Decrypt Caesar cipher (tr command) |
| Step 5: | Decrypt AES file (openssl) |
| Step 6: | View recovered content (cat) |


### Key Commands Reference

| Command | Purpose | Example |
|---------|---------|---------|
| `ls` | List directory contents | `ls` |
| `ls -a` | List all files (including hidden) | `ls -a` |
| `cat [file]` | Display file contents | `cat README.txt` |
| `cd [directory]` | Change directory | `cd caesar` |
| `tr [set1] [set2]` | Translate/transform characters | `tr "d-za-cD-ZA-C" "a-zA-Z"` |
| `openssl aes-256-cbc -d` | Decrypt AES-256-CBC | See below |
| `cat [file]` | View recovered content | `cat Q1.recovered` |

### Caesar Cipher Decryption

```bash
# Caesar cipher with left shift of 3
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
```

How it works:

| Cipher | Plaintext | Explanation |
|--------|-----------|-------------|
| d | a | Shift back by 3 |
| e | b | Shift back by 3 |
| f | c | Shift back by 3 |
| a | x | Wrap-around shift |	


OpenSSL AES-256-CBC Decryption
```bash
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```

| Parameter | Meaning |
|-----------|---------|
| `aes-256-cbc` | AES algorithm, 256-bit key, CBC mode |
| `-pbkdf2` | Password-Based Key Derivation Function 2 |
| `-a` | Base64 encode/decode |
| `-d` | Decrypt mode |
| `-in [file]` | Input encrypted file |
| `-out [file]` | Output decrypted file |
| `-k [password]` | Decryption password |


Commands Executed
```bash
# Navigate and explore
ls
cat README.txt
cd caesar
ls -a

# Decrypt Caesar cipher
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"

# Decrypt AES file
cd ~
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
cat Q1.recovered
```


Encryption Types Compared
| Type | Example | Strength | Use Case |
|------|---------|----------|----------|
| Classical cipher | Caesar cipher (shift) | Very weak | Historical/educational |
| Symmetric encryption | AES-256-CBC | Strong | Bulk data encryption |
| Asymmetric encryption | RSA | Strong | Key exchange, digital signatures |



Reflection - Activity 2
This activity strengthened understanding of encryption and decryption processes. It demonstrated how classical ciphers (Caesar) and modern encryption (AES-256-CBC) can be reversed using correct tools and commands, reinforcing the importance of protecting sensitive data.

<br><br>

## 4. Activity 3: Create Hash Values
**Objective:** Generate and compare hash values to verify file integrity.

| Hash Function Properties | Description |
|-------------------------|-------------|
| Deterministic | Same input always produces same hash |
| One-way | Cannot reverse hash to original input |
| Collision-resistant | Two different inputs unlikely to produce same hash |
| Avalanche effect | Small change in input → completely different hash |


SHA-256 Hash Example
```
Input: "Hello World"
SHA-256: a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e

Input: "Hello World " (added space)
SHA-256: 1a460c5b0ebcaf175154be8b5472fca1a8d5d80c7e32f72d1f68e6be4175a25a
```

Commands Executed
```bash
# Display file contents
cat file1.txt
cat file2.txt

# Generate SHA-256 hashes
sha256sum file1.txt
sha256sum file2.txt

# Save hashes to files
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash

# View saved hashes
cat file1hash
cat file2hash

# Compare hashes
cmp file1hash file2hash
```


Hash Comparison Visualization
- File 1 Process: file1.txt → sha256sum → file1hash  
- File 1 Process: file2.txt → sha256sum → file2hash  
- file1hash vs file2hash → cmp → "Different - No match"


Findings
| Observation | Implication |
|-------------|-------------|
| Files appeared identical when viewed with cat | Human-readable content was the same |
| Hash values were different | Hidden differences exist (whitespace, line endings, metadata) |
| cmp reported files differ | Security tool detected tampering |


Why Hashes Differ for Seemingly Identical Files
| Hidden Difference | Example |
|------------------|---------|
| Whitespace | Trailing space, tab vs. space |
| Line endings | LF (Unix) vs. CRLF (Windows) |
| Encoding | UTF-8 vs. ASCII |
| Hidden characters | Null bytes, special characters |
| Metadata | File timestamps (some hash algorithms include) |


Integrity Verification Workflow
Original File → sha256sum → Original Hash  
Received File → sha256sum → New Hash  

Original Hash vs New Hash → Compare  
Result:  
- Match → Intact 
- Mismatch → Tampered 


Reflection - Activity 3
This activity highlighted the importance of hashing for ensuring data integrity. It showed how security professionals can detect even the smallest modifications to files, which is critical for identifying tampering or malicious changes.

Key takeaway: Even a single character difference (including invisible characters) produces a completely different hash value.

<br><br>

## 5. Activity 4: Improve Authentication, Authorization, and Accounting (AAA)
**Objective:** Analyze an access control incident and recommend improvements.

Incident Data
Employee Record:

Name	Role	Status	Authorization	IP Address	End Date
Robert Taylor Jr.	Legal attorney	Contractor	Admin	152.207.255.255	12/27/2019
Log Evidence:
```
Event Type: Information
Date: 10/03/2023
Time: 8:29:57 AM
User: Legal\Administrator
IP Address: 152.207.255.255
Action: Payroll event added (FAUX_BANK)
```


### Incident Timeline

| Date | Event Description | Notes |
|------|-------------------|-------|
| 2019-12-27 | Contractor contract ends                               | Account should be deactivated   |
| 2023-10-03 | Payroll event executed using same account              | Unauthorized / suspicious use   |
| Current    | Account still active with admin privileges             | Critical security risk ⚠️       |


Issues Identified
| # | Issue | Severity | Risk |
|---|-------|----------|------|
| 1 | Contractor account active 4 years after contract end | 🔴 Critical | Unauthorized access |
| 2 | User had administrative privileges | 🔴 Critical | Excessive permissions |
| 3 | No automatic account expiration | 🟠 High | Orphaned accounts |
| 4 | Payroll action from non-payroll role | 🔴 Critical | Segregation of duties violation |


Account Lifecycle Management Gaps

| Lifecycle Stage | Status | Description |
|-----------------|--------|-------------|
| Provisioning | ✓ | Account created |
| Active | ✓ | Account in use |
| Review | ✗ | No periodic review |
| De-provisioning | ✗ | Account never removed |


Recommendations
| Priority | Recommendation | Implementation | MITRE ATT&CK Mapping |
|----------|---------------|----------------|----------------------|
| Critical | Implement automatic account expiration | Set end date in identity management system | T1078 - Valid Accounts |
| Critical | Apply RBAC with limited privileges | Legal attorneys should not have payroll access | T1098 - Account Manipulation |
| High | Enable MFA for all admin accounts | Require second factor for sensitive actions | T1557 - Man-in-the-Middle |
| High | Conduct quarterly access reviews | Automated certification campaigns | TA0006 - Credential Access |
| Medium | Enable logging for all admin actions | SIEM integration | TA0007 - Discovery |


Least Privilege Applied to Robert Taylor Jr.
| Before | After |
|--------|-------|
| Legal\Administrator | Legal\Legal_Reviewer |
| Access to payroll system | Access to legal documents only |
| Admin privileges | Read-only for most systems |
| Active indefinitely | Account expires with contract |


Reflection - Activity 4
This activity highlighted the importance of proper account lifecycle management and access control enforcement. Retaining active accounts for former employees and granting excessive privileges significantly increases security risks.

Key takeaways:
- Accounts must be de-provisioned immediately upon employment termination
- Administrative privileges should be rare and tightly controlled
- Segregation of duties prevents single-user abuse
- Regular access reviews catch orphaned accounts

<br><br>

## 6. AAA Framework Summary
| Component | Definition | Controls Implemented |
|-----------|------------|----------------------|
| Authentication | Verifying user identity | MFA, strong passwords |
| Authorization | Determining access rights | RBAC, least privilege |
| Accounting | Tracking user actions | Logging, audit trails |


Security Controls Comparison
| Control | Before Incident | After Recommendations |
|---------|-----------------|----------------------|
| Account expiration | Manual (forgotten) | Automatic |
| Access reviews | None | Quarterly |
| MFA | Not enabled | Required for admin |
| Privilege level | Admin (excessive) | Role-appropriate |
| Segregation of duties | Violated | Enforced |

<br><br>

## 7. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| Least privilege implementation | Analyzed data leak; recommended role-based restrictions |
| NIST framework application | Applied NIST SP 800-53 AC-6 |
| Encryption/decryption | Used Caesar cipher and AES-256-CBC decryption |
| Hash generation | Generated SHA-256 hashes with sha256sum |
| File integrity verification | Compared hashes using cmp |
| Access control analysis | Identified unauthorized payroll access |
| Account lifecycle management | Recommended automatic expiration |
| Security control recommendations | Proposed MFA, RBAC, access reviews |

<br><br>

## 8. Tools and Concepts Used
| Tool/Concept | Application |
|--------------|-------------|
| NIST SP 800-53 AC-6 | Least privilege framework |
| Caesar cipher | Classical encryption decryption |
| OpenSSL (AES-256-CBC) | Modern symmetric decryption |
| SHA-256 | Cryptographic hashing |
| sha256sum | Linux hash generation |
| cmp | File comparison |
| RBAC | Role-based access control |
| MFA | Multi-factor authentication |
| AAA framework | Authentication, Authorization, Accounting |

<br><br>

## 9. Reflection - Full Lab
This lab provided practical experience in securing data through multiple approaches: data handling policies, encryption, hashing, and access control mechanisms.

Key takeaways from each activity:

| Activity | Key Insight |
|----------|--------------|
| Activity 1 | Least privilege requires both policy AND technical enforcement |
| Activity 2 | Encryption is reversible with proper keys/tools |
| Activity 3 | Hashes detect invisible tampering (whitespace, encoding) |
| Activity 4 | Account lifecycle management is often the weakest link |
| Demonstrates | Practical data protection skills including encryption, hashing, access control, and security policy implementation. |

<br><br>

## 10. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Least Privilege | Users get minimum access necessary for their role |
| NIST SP 800-53 | Security and privacy controls catalog |
| Caesar cipher | Classical substitution cipher shifting letters |
| AES-256-CBC | Advanced Encryption Standard, 256-bit key, Cipher Block Chaining mode |
| OpenSSL | Open-source cryptography toolkit |
| SHA-256 | Secure Hash Algorithm (256-bit output) |
| Hash | Fixed-size output from hash function |
| cmp | Linux command to compare files byte by byte |
| RBAC | Role-Based Access Control |
| MFA | Multi-Factor Authentication |
| AAA | Authentication, Authorization, Accounting |
| Segregation of duties | Single user cannot perform conflicting actions |
| Orphaned account | Active account without a valid user |

<br><br>

## 11. Command Quick Reference
Encryption/Decryption
```bash
# Generate SHA-256 hash
sha256sum filename.txt

# Compare files
cmp file1 file2

# Caesar cipher decryption (left shift 3)
cat encrypted.txt | tr "d-za-cD-ZA-C" "a-zA-Z"

# AES-256-CBC decryption
openssl aes-256-cbc -pbkdf2 -a -d -in encrypted.aes -out decrypted.txt -k password

# AES-256-CBC encryption
openssl aes-256-cbc -pbkdf2 -a -e -in plaintext.txt -out encrypted.aes -k password
```


File Navigation
```bash
ls -a          # List all files including hidden
cat file.txt   # Display file contents
cd directory   # Change directory
```
