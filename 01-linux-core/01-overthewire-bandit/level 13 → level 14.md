# Bandit Level 13 → Level 14

## Goal
Log into `bandit14` using the provided private SSH key  
and read the password from `/etc/bandit_pass/bandit14`.


## What I did
- Checked the ownership and permissions of `sshkey.private` using `ls -l`
- Discovered that SSH connections via `localhost` are blocked on the server
- Used `scp` to copy the private key file to the local machine
- Verified that the key file was downloaded correctly
- Logged in to `bandit14` using key-based authentication with `ssh -i`
- Retrieved the password from `/etc/bandit_pass/bandit14`


## Command
- `ls -l sshkey.private`
- `scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private .`
- `ssh -i .\sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org`
- `cat /etc/bandit_pass/bandit14`


## Reading Notes

1&#41; SSH authentication methods

SSH supports two main authentication methods.

- Password authentication  
  → Login using account password

- Key-based authentication  
  → Login using private/public key pair

In this level, key-based authentication was required.

2&#41; SSH options used

| Option | Meaning       | Description                    |
|--------|---------------|--------------------------------|
| -i     | Identity file | Specifies the private key file |
| -p     | Port (ssh)    | Specifies SSH port number      |

3&#41; SCP options used

| Option | Meaning       | Description                  |
|--------|---------------|------------------------------|
| -P     | Port (scp)    | Specifies remote port number |
| -r     | Recursive     | Copy directories recursively|
| -i     | Identity file | Specify key file (optional)  |

4&#41; File permission overview (`ls -l`)

Example output: `-rw-r----- 1 bandit14 bandit13 1679 sshkey.private`

Meaning:
- Owner: bandit14
- Group: bandit13
- Others: no permission

Only the file owner can change permissions using `chmod`.

5&#41; PowerShell directory commands

In PowerShell, `ls` is an alias of `dir`.

- `ls`  → List directory contents
- `dir` → List directory contents


## Mastery Check
- [x] Understands SSH password vs key authentication
- [x] Can use `ssh -i` for key-based login
- [x] Knows the difference between `-p` (ssh) and `-P` (scp)
- [x] Can copy files using `scp`
- [x] Can interpret `ls -l` permission output
