# Bandit Level 7 → Level 8

## Goal
Read the password for the next level from the file `data.txt`,
where the password is stored next to the word `millionth`.


## What I did
- Observed that `data.txt` contains many lines formatted as key–value pairs
- Used `grep` to find the line containing the word `millionth`
- Verified that the password is located on the same line
- Used `awk` with a pipe to extract only the password field


## Command
`grep "millionth" data.txt`  
`grep "millionth" data.txt | awk '{print $2}'`


## Reading Notes
- `grep` searches files line by line and outputs entire lines that match a string.
- Each line in `data.txt` follows a `[keyword] [value]` structure.
- The password is stored on the same line as the keyword `millionth`.
- The pipe (`|`) passes the output of one command as input to another.
- `awk` splits each input line into fields based on whitespace.
  - `$1` refers to the first field (keyword).
  - `$2` refers to the second field (password).
- `{print $2}` outputs only the second field.
- Single quotes are required so the shell does not interpret `$2` before `awk`.


## Mastery Check
- [x] Can locate specific lines in a large file using `grep`
- [x] Understands that `grep` operates on full lines
- [x] Can use pipes to chain commands together
- [x] Can extract specific fields using `awk`
- [x] Understands the role of `{}` and single quotes in `awk`
