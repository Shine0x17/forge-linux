# Bandit Level 6 → Level 7

## Goal
Read the password for the next level from a file that:
- is owned by user bandit7
- is owned by group bandit6
- is exactly 33 bytes in size


## What I did
- Moved to the root directory to search the entire filesystem
- Used `find` to locate files by owner, group, and size
- Suppressed permission error messages during the search
- Identified the target file matching all conditions
- Read the file to obtain the password


## Command
- `find . -user bandit7 -group bandit6 -size 33c 2>/dev/null`  
- `cat /var/lib/dpkg/info/bandit7.password`


## Reading Notes
- `find` searches files recursively starting from a given directory.
- `-user` filters files by owner.
- `-group` filters files by group.
- `-size 33c` matches files with an exact size of 33 bytes (`c` = bytes).
- Searching from `/` causes many permission errors.
- Linux programs use separate file descriptors:
  - `0` (stdin): standard input
  - `1` (stdout): standard output
  - `2` (stderr): standard error
- `2>/dev/null` redirects error output (stderr) to discard permission error messages.
- Standard output and error output are separate streams in Linux.


## Mastery Check
- [x] Can search the entire filesystem using `find`
- [x] Can filter files by owner, group, and size
- [x] Understands why permission errors occur and how to suppress them
- [x] Can locate and read a file based on metadata conditions
