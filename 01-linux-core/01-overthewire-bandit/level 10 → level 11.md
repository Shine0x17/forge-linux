# Bandit Level 10 → Level 11

## Goal
Read the password for the next level from the file `data.txt`,
which contains Base64 encoded data.


## What I did
- Confirmed that `data.txt` exists in the home directory
- Checked the contents of the file to determine its encoding format
- Identified the data as Base64-encoded based on its character set and padding
- Decoded the file using the `base64` command
- Retrieved the plaintext password from the decoded output


## Command
`ls`  
`head data.txt`  
`base64 -d data.txt`


## Reading Notes
- `data.txt` contains a single line composed entirely of printable ASCII characters.
- The character set (`A–Z`, `a–z`, `0–9`, `+`, `/`) and trailing `=` padding are strong indicators of Base64 encoding.
- Base64 is a binary-to-text encoding scheme used to safely represent binary data in text-only environments.
- Base64 is not an encryption method and provides no confidentiality.
- Base64 encoding converts input data in 3-byte (24-bit) blocks into 4 encoded characters.
- Each encoded character represents 6 bits, resulting in an approximate 33% increase in data size.
- Base64 output length is always a multiple of 4 characters.
- Padding characters are added when the input length is not a multiple of 3 bytes.
  - A single `=` indicates that the input ended with 2 remaining bytes.
  - Two `=` characters indicate that the input ended with 1 remaining byte.
- Padding characters do not represent actual data and are discarded during decoding.
- The `base64` command performs encoding by default.
- The `-d` option explicitly instructs the `base64` command to decode Base64-encoded input.

| `base64` option | Meaning | Description |
|-----------------|---------|-------------|
| (none)          | Encode  | Encodes input data into Base64 (default behavior) |
| `-d`            | Decode  | Decodes Base64-encoded data back to its original form |
| `-w N`          | Wrap    | Wraps encoded output lines at N characters (GNU coreutils) |
| `-i`            | Ignore  | Ignores non-Base64 characters during decoding |

- `head` is useful for inspecting the structure of a file before reading it entirely.
- By default, `head` outputs the first 10 lines of a file.
- `head` is commonly used during the initial inspection phase to determine file structure or encoding.

| `head` option | Meaning | Description |
|---------------|---------|-------------|
| (none)        | Default | Outputs the first 10 lines of a file |
| `-n N`        | Lines   | Outputs the first N lines of the file |
| `-c N`        | Bytes   | Outputs the first N bytes of the file |
| `-q`          | Quiet   | Suppresses file name headers when processing multiple files |
| `-v`          | Verbose | Always prints file name headers |


## Mastery Check
- [x] Can recognize Base64-encoded data by its character set and padding
- [x] Understands the purpose of Base64 padding characters
- [x] Understands the difference between encoding and encryption
- [x] Can decode Base64 data using the `base64` command
- [x] Understands why Base64-encoded data is larger than the original
