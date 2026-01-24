# Bandit Level 9 → Level 10

## Goal
Read the password for the next level from the file `data.txt`,
where the password is stored in one of the few human-readable strings
and is preceded by several `=` characters.


## What I did
- Observed that `data.txt` is not a plain text file and contains binary data
- Used `strings` to extract human-readable strings from the file
- Noticed that most extracted strings are meaningless fragments
- Used `grep` to filter only strings containing `=` characters
- Refined the filter to match strings with multiple consecutive `=` characters
- Identified the final string containing the actual password


## Command
- `strings data.txt`  
- `strings data.txt | grep "="`  
- `strings data.txt | grep "==="`  
- `find . -type f -exec strings -f {} \;`


## Reading Notes
- `data.txt` contains binary data, so `cat` produces unreadable output.
- `strings` scans a file byte by byte and extracts sequences of
  **printable ASCII characters**.
- A string is defined as **printable characters that appear consecutively**
  without interruption by non-printable bytes.
- By default, `strings` outputs sequences that are at least 4 characters long.
- The problem hint specifies that the password is preceded by **several `=` characters**.
- Using `grep "="` filters strings containing `=`, but includes many irrelevant results.
- Using `grep "==="` more accurately reflects the problem condition and significantly narrows down the candidates.
- `strings` can accept multiple files as input, but it does not traverse directories recursively.
- `find . -type f` searches for all regular files starting from the current directory, including subdirectories.
- `-exec strings -f {} \;` runs `strings` on each discovered file and prefixes each extracted string with its source filename.

| `strings` option | Meaning              | Description                                                   |
|------------------|----------------------|---------------------------------------------------------------|
| (none)           | Default behavior     | Extracts printable strings of at least 4 characters           |
| `-n N`           | Minimum length       | Outputs only strings with at least N consecutive characters   |
| `-a`             | All                  | Scans the entire file regardless of file format               |
| `-f`             | Filename prefix      | Prefixes each string with its source filename                 |
| `-t x`           | Offset (hex)         | Displays the byte offset (hexadecimal) of each string         |
| `-t d`           | Offset (decimal)     | Displays the byte offset (decimal) of each string             |
| `-e s`           | ASCII encoding       | Interprets data as single-byte ASCII (default)                |
| `-e l`           | UTF-16 little-endian | Interprets data as UTF-16 little-endian encoded strings       |
| `-e b`           | UTF-16 big-endian    | Interprets data as UTF-16 big-endian encoded strings          |


## Mastery Check
- [x] Understands why `cat` is not suitable for binary files
- [x] Understands what a human-readable string is in binary data
- [x] Can use `strings` to extract printable character sequences
- [x] Can translate problem hints into filtering conditions
- [x] Can use `grep` to narrow down relevant output
- [x] Understands the concept of consecutive printable characters
