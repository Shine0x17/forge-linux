# Bandit Level 4 → Level 5

## Goal
Read the password for the next level from the only human-readable file
in the `inhere` directory.


## What I did
- Listed all files in the `inhere` directory
- Checked each file’s type using the `file` command
- Identified the only file marked as ASCII text


## Commands
`file ./*`
`cat ./-file07`


## Reading Notes
- Filenames starting with `-` can be misinterpreted as command options.
- Prefixing filenames with `./` prevents option parsing issues.
- The `file` command determines file type based on content, not filename.
- `ASCII text` indicates a human-readable file.
- Wildcards like `*` expand to all files in a directory.
- `./*` is safer than `*` when filenames start with `-`.
- The `--` argument explicitly marks the end of command options.


## Mastery Check
- [x] Can analyze file types using the `file` command
- [x] Understands why `./` is required for filenames starting with `-`
- [x] Can identify human-readable files among binary data
