# Bandit Level 11 → Level 12

## Goal
Read the password for the next level from the file `data.txt`,
where all lowercase (a–z) and uppercase (A–Z) letters have been rotated by 13 positions.


## What I did
- Displayed the contents of `data.txt` to inspect the encoded text
- Recognized the transformation pattern as ROT13
- Used `tr` to translate all alphabetic characters by 13 positions
- Retrieved the decoded output containing the password


## Command
- `cat data.txt`  
- `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`


## Reading Notes

1&#41; ROT13 overview

ROT13 is a simple letter substitution cipher that shifts each alphabetic character
13 positions forward in the alphabet.

- The English alphabet has 26 letters
- 26 divided by 2 equals 13
- Applying ROT13 twice restores the original text
- Non-alphabetic characters are not affected


2&#41; `tr` command concept

The `tr` command performs character-by-character translation on input data.

Basic form: `tr 'set1' 'set2'`

- Characters in `set1` are replaced by characters in `set2`
- Mapping is positional (first-to-first, second-to-second)
- Translation operates on individual characters, not words


3&#41; Alphabet range notation

| Expression | Meaning                    |
|-----------|----------------------------|
| A-Z       | All uppercase letters      |
| a-z       | All lowercase letters      |
| A-Za-z    | All alphabetic characters  |

Using `A-z` is discouraged because it includes non-letter ASCII characters.


4&#41; ROT13 mapping with `tr`

| Left range | Right range | Purpose                    |
|-----------|-------------|----------------------------|
| A-Z       | N-ZA-M      | Uppercase ROT13 mapping    |
| a-z       | n-za-m      | Lowercase ROT13 mapping    |

Each range expands to 26 characters.
Characters are translated based on their position in the expanded sets.

Examples:
- A → N
- B → O
- M → Z
- N → A
- Z → M


5&#41; Pipe usage

- The pipe operator (`|`) passes the output of `cat` as input to `tr`
- This allows processing file contents without modifying the original file


6&#41; Common `tr` options

| Option | Name        | Description                                      |
|-------|-------------|--------------------------------------------------|
| -d    | delete      | Deletes characters specified in the set          |
| -s    | squeeze     | Replaces repeated characters with a single one   |
| -c    | complement  | Uses the complement of the specified character set |

Notes:
- Options can be combined (e.g., `-dc`)
- `tr` options modify how character sets are interpreted


## Mastery Check
- [x] Understands the ROT13 substitution principle
- [x] Understands that `tr` operates on individual characters
- [x] Can use alphabet ranges correctly in `tr`
- [x] Understands positional character mapping
- [x] Knows common `tr` options and their purposes
- [x] Can decode ROT13-encoded text using a Unix pipeline
