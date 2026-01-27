# Bandit Level 12 → Level 13

## Goal
Read the password for the next level from the file `data.txt`,
which is a hexdump of a file that has been repeatedly compressed.


## What I did
- Created a temporary working directory in `/tmp`
- Copied `data.txt` into the workspace
- Converted the hexdump back into a binary file
- Identified file types using `file`
- Renamed files based on file type identified by `file`
- Decompressed gzip and bzip2 layers
- Extracted tar archives
- Repeated the process until a readable file appeared
- Read the final file to obtain the password


## Command
- `cp ~/data.txt .`
- `xxd -r data.txt > data.bin`
- `file data.bin`
- `mv data.bin data.gz`
- `gunzip -c data.gz > output1`
- `bzip2 -dc output1 > output2`
- `bunzip2 -c output2 > output3`
- `gzip -dc output3 > output4`
- `tar -tf output4`
- `tar -xf output4`
- `cat final_file`


## Reading Notes

1&#41; Hexdump restoration with `xxd`

The file `data.txt` contains hexadecimal text, not real binary data.
`xxd -r` converts the hexdump back into its original binary format.

| Option | Meaning  | Description                 |
|--------|----------|-----------------------------|
| -r     | Reverse  | Hex to binary conversion    |


2&#41; File identification with `file`

The `file` command identifies file types based on file content rather than filename.
It was used at every stage to determine the next action.


3&#41; Stream output with `-c`

Many compression tools support the `-c` option.

| Option | Meaning | Description                       |
|--------|---------|-----------------------------------|
| -c     | stdout  | Output to standard output stream  |

Using `-c` prevents automatic file creation and allows manual filename control.

Example usage:
- `gunzip -c file.gz > file`
- `bunzip2 -c file.bz2 > file`


4&#41; Gzip and Bzip2 decompression

Gzip and bzip2 are compression tools.

| Tool   | Decompress Option | Description            |
|--------|-------------------|------------------------|
| gzip   | -d / -dc          | Decompress gzip files  |
| bzip2  | -d / -dc          | Decompress bzip2 files |

Stream mode (`-dc`) preserves original files.


5&#41; Tar archive handling

The `tar` command is used to archive multiple files.

| Option | Meaning  | Description            |
|--------|----------|------------------------|
| -c     | Create   | Create archive         |
| -x     | Extract  | Extract archive        |
| -t     | List     | List archive contents  |
| -f     | File     | Specify archive file   |

The `-t` option was used before extraction to inspect contents safely.


6&#41; Recursive extraction workflow

This level requires repeating the following process:

- Identify file type with `file`
- Decompress or extract accordingly
- Verify output
- Repeat until readable text appears


## Mastery Check
- [x] Can restore binary files using `xxd -r`
- [x] Can identify file types using `file`
- [x] Understands stream output with `-c`
- [x] Can copy files using `cp`
- [x] Can rename files using `mv`
- [x] Can decompress gzip and bzip2 files
- [x] Can inspect and extract tar archives safely
