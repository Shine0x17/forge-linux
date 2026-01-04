# Bandit Level 1

## Goal
Read the password for the next level from a file named `-`.


## What I did
- Listed files in the home directory
- Identified a file named `-`
- Confirmed that `cat -` reads from stdin
- Read the file using an explicit path


## Command
`cat ./-`


## Reading Notes


## Mastery Check
- [x] Can explain why `cat -` does not read the file named `-`
- [x] Can handle files with special names using explicit paths
