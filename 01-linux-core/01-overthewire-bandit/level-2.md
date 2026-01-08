# Bandit Level 2

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
- cat reads files or standard input (stdin) and prints them to stdout.
- stdin is the default input stream of a program (usually the keyboard).
- `-` is a conventional placeholder meaning stdin, not a special character.
- `cat -` reads from stdin.
- `cat ./-` reads a file literally named -.
- Prefixing with `./` forces interpretation as a filename, not stdin.
- SSH does not read passwords from stdin by default (security design).
- Password automation via stdin is a concept-level topic and can be skipped for now.


## Mastery Check
- [x] Can explain why `cat -` does not read the file named `-`
- [x] Can handle files with special names using explicit paths
 