\# Bandit Level 18 → Level 19



\## Goal

Read the password from the `readme` file despite automatic logout on login.





\## What I Did

\- Tried normal SSH login and got logged out immediately

\- Realized that `.bashrc` was forcing logout

\- Used SSH with direct command execution

\- Read the `readme` file using `cat`

\- Retrieved the next password





\## Command

\- `ssh bandit18@bandit.labs.overthewire.org -p 2220`

\- `ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"`





\## Reading Notes

\- `.bashrc` runs automatically when bash starts.

\- Interactive SSH sessions were terminated by `.bashrc`.

\- Executing commands directly with SSH avoids loading bash.

\- `ssh "command"` can be used to bypass shell startup scripts.





\## Mastery Check

\- \[x] Can bypass automatic logout using SSH

\- \[x] Can execute remote commands remotely

\- \[x] Understands the difference between interactive login and command execution



