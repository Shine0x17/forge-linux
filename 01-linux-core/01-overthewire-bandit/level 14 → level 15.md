# Bandit Level 14 → Level 15

## Goal
Read the password for the next level by submitting the current level password
to port 30000 on localhost.


## What I did
- Confirmed that a service was listening on port 30000
- Used `nc` to connect to localhost on port 30000
- Sent the bandit14 password through the connection
- Received the bandit15 password from the server


## Command
- `ss -ltn`
- `nc localhost 30000`


## Reading Notes
- `localhost` means the current machine (Bandit server itself, not my home PC)
- Port numbers represent network service entry points on a computer
- `ss -ltn` shows TCP ports that are currently listening
- `nc` (netcat) connects to an IP address and port
- `nc` first establishes a connection, then sends input
- No prompt usually means `nc` is waiting for input
- Text typed in `nc` is sent directly to the connected service
- `Ctrl + C` terminates an active `nc` session

| `ss` option | Meaning | Description                              |
|-------------|---------|------------------------------------------|
| -l          | Listen  | Shows only listening ports               |
| -t          | TCP     | Displays only TCP connections            |
| -n          | Numeric | Displays addresses and ports as numbers  |

| `nc` option | Meaning  | Description                              |
|-------------|----------|------------------------------------------|
| (none)      | Default  | Connects to the target IP and port        |
| -v          | Verbose  | Shows connection status                  |
| -l          | Listen   | Listens for incoming connections         |

| `nc` Command Structure        | Meaning                                |
|------------------------------|----------------------------------------|
| `nc [option] [address] [port]` | Connect to a target address and port   |


## Mastery Check
- [x] Understands that `localhost` refers to the current server
- [x] Understands that ports represent running services
- [x] Can use `ss -ltn` to check listening ports
- [x] Can connect to a port using `nc`
- [x] Understands that `nc` uses connection → send → receive workflow
