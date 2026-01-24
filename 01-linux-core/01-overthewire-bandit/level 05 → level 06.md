# Bandit Level 5 → Level 6

## Goal
Read the password for the next level from a file located somewhere under the `inhere` directory.  
The file must meet all of the following conditions:
- Human-readable
- Exactly 1033 bytes in size
- Not executable


## What I did
- Used `find` to recursively search all subdirectories
- Filtered files by exact size and execution permission
- Verified the file type using `file`


## Command
- `find . -type f -size 1033c ! -executable`
- `file ./maybehere07/.file2`
- `cat ./maybehere07/.file2`


## Reading Notes

1&#41; File type filtering with `-type`

The `-type` option filters results based on file type.

| Option | Meaning           | Description                          |
|-------|-------------------|--------------------------------------|
| f      | Regular file      | Normal files (text or binary)        |
| d      | Directory         | Folder                               |
| l      | Symbolic link     | Symlink                              |
| c      | Character device  | Character-based device file          |
| b      | Block device      | Block-based device (disk)            |
| p      | Named pipe (FIFO) | FIFO / inter-process communication   |
| s      | Socket            | Network socket file                  |

In this level, `-type f` was used because the password is stored in a regular file, not in a directory or special file.

2&#41; File size filtering with `-size`

The `-size` option filters files by their size.

| Unit | Meaning | Description                       |
|-----|---------|-----------------------------------|
| c    | Bytes   | Exact byte size (most precise)    |
| k    | KB      | 1024 bytes                        |
| M    | MB      | 1024 KB                           |
| G    | GB      | 1024 MB                           |
| —    | Blocks  | 512-byte blocks (default)         |

Examples:
- `-size 1033c`  → exactly 1033 bytes  
- `-size +1033c` → greater than 1033 bytes  
- `-size -1033c` → less than 1033 bytes  
  
3&#41; Executable permission filtering

| Expression     | Meaning                |
|---------------|------------------------|
| -executable   | File is executable     |
| ! -executable | File is NOT executable |
| -readable     | File is readable       |
| -writable     | File is writable       |
  
Key takeaway:
- `find` searches recursively by default.
- Conditions like type, size, and permissions enable precise filtering.


## Mastery Check
- [x] Understands that `find` searches subdirectories recursively by default
- [x] Can filter files by type using `-type`
- [x] Can filter files by exact byte size using `-size`
- [x] Understands the meaning of `! -executable`
- [x] Can translate problem conditions directly into `find` options
