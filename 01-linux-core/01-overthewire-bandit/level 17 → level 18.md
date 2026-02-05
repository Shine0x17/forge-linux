# Bandit Level 17 → Level 18

## Goal
Find the password for the next level by comparing two files: passwords.old and passwords.new.
The correct password is the only line that has been changed between them.


## What I Did
- Used diff to compare passwords.old and passwords.new
- Identified the changed line in the new file
- Extracted the new password


## Command
- `diff passwords.old passwords.new`


## Reading Notes
- File Comparison
  - This level required comparing two similar files to find a single changed line.
  - Only the modified line in `passwords.new` contained the correct password.

- diff Output Interpretation
  - Lines starting with `<` exist only in the first file (passwords.old).
  - Lines starting with `>` exist only in the second file (passwords.new).
  - The format `42c42` indicates that line 42 was changed.

- File Management
  - Linux file names are case-sensitive.

| diff Command Structure | Meaning |
|------------------------|---------|
| diff file1 file2 | Compare two files |
| diff [option] file1 file2 | Compare files with options |

| `diff` option | Meaning | Description |
|-------------|---------|-------------|
| -u | Unified | Show unified diff format |
| -y | Side by side | Display files in two columns |
| -q | Quiet | Show only whether files differ |
| -w | Ignore space | Ignore whitespace |
| -i | Ignore case | Ignore uppercase/lowercase |

| diff type | Meaning | Description |
|-----------|---------|-------------|
| c | Change | An existing line was modified |
| a | Add | A new line was added |
| d | Delete | An existing line was removed |

Example:  
`42c42`  → Line 42 was changed  
`5a6`    → A new line was added at line 6  
`8d7`    → Line 8 was deleted


## Mastery Check
- [x] Can compare files using diff
- [x] Can interpret < and > symbols
- [x] Can understand change information like 42c42
