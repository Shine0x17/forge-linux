# Bandit Level 2 → Level 3

## Goal
Read the password for the next level from a file with spaces in its name
and use it to log in to bandit3 via SSH.

## What I did
- Found a file named `--spaces in this filename--`
- Tried to read the file and encountered an option parsing error
- Used the correct path to indicate it is a file, not an option

## Command
`cat ./--spaces\ in\ this\ filename--`  
`cat "./--spaces in this filename--"`

## Reading Notes
- The shell splits command input by spaces.
- Filenames can start with `--`, which may be mistaken for command options.
- Prefixing a filename with `./` makes it clear that it is a file path.
- Quotation marks prevent spaces from splitting filenames.
- `cat` displays the contents of a file.

## Mastery Check
- [x] Can handle filenames with spaces
- [x] Can handle filenames starting with `--`
- [x] Understands the difference between quoting and option parsing

