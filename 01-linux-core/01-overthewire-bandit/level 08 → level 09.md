# Bandit Level 8 → Level 9

## Goal
Read the password for the next level from the file `data.txt`,
where the password is the only line of text that occurs exactly once.


## What I did
- Identified that most lines in `data.txt` are duplicated
- Used `sort` to group identical lines together
- Used `uniq -u` to extract the line that appears only once
- Retrieved the unique line as the password for the next level


## Command
- `sort data.txt | uniq -u`


## Reading Notes
- `sort` rearranges lines so that identical lines become adjacent.
- `uniq` operates only on **consecutive** duplicate lines.
- Because of this behavior, `sort` must be used before `uniq`.
- `uniq -u` outputs only lines that occur **exactly once**.
- The pipe (`|`) passes the output of `sort` directly into `uniq`.

| `sort` option | Meaning        | Description                                  |
|---------------|----------------|----------------------------------------------|
| (none)        | Default sort   | Sorts lines alphabetically (A → Z)           |
| -r            | Reverse        | Sorts lines in reverse order (Z → A)         |
| -n            | Numeric        | Sorts lines based on numeric value           |
| -u            | Unique         | Sorts and removes duplicate lines            |
| -k N          | Key            | Sorts using the Nth field as the key         |
| -t X          | Delimiter      | Uses X as the field separator                |

| `uniq` option | Meaning        | Description                                  |
|---------------|----------------|----------------------------------------------|
| (none)        | Default uniq   | Collapses consecutive duplicate lines        |
| -u            | Unique only    | Outputs only lines that occur exactly once   |
| -c            | Count          | Prefixes lines with the number of occurrences|
| -d            | Duplicates     | Outputs only duplicated lines                |


## Mastery Check
- [x] Understands why `sort` is required before `uniq`
- [x] Can identify unique lines using `uniq -u`
- [x] Can solve problems using pipes to combine commands
- [x] Understands that `uniq` works on consecutive lines only
