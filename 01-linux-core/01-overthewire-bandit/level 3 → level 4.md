# Bandit Level 3 → Level 4

## Goal
Read the password for the next level from a hidden file in the `inhere` directory.


## What I did
- Listed files including hidden files
- Identified a hidden file starting with dots


## Command
`ls -la`  
`cat ...Hiding-From-You`


## Reading Notes
- Files starting with `.` are hidden by default.
- `ls` lists directory contents but does not show hidden files.
- `ls -a`
  - `-a` (all): include hidden files starting with `.`.
- `ls -l`
  - `-l` (long): display detailed file information (permissions, owner, size).
- `ls -la`
  - Combination of `-l` and `-a`: show all files with detailed information.
- Filenames can begin with multiple dots and are still treated as valid filenames.
- Quoting a filename prevents the shell from misinterpreting special characters.


## Mastery Check
- [x] Can list hidden files using `ls -a`
- [x] Can identify hidden files by naming convention
- [x] Can safely read files with unusual names
