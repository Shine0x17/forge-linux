# Bandit Level 15 → Level 16

## Goal
Read the password for the next level by submitting the current level password  
to port 30001 on localhost using an SSL/TLS encrypted connection.


## What I did
- Checked that a service was listening on port 30001  
- Tried connecting with `nc` and confirmed it did not work  
- Recognized that the service required SSL/TLS  
- Connected using `openssl s_client`  
- Sent the bandit15 password  
- Received the bandit16 password  


## Command
- `ss -ltn`  
- `nc localhost 30001`  
- `openssl s_client -connect localhost:30001`  
- `openssl s_client -connect localhost:30001 -quiet`  


## Reading Notes
- Port 30001 uses SSL/TLS encryption
- `nc` cannot communicate with encrypted services
- `openssl s_client` is used for SSL/TLS connections
- `openssl` uses subcommands such as `s_client`
- `s_client` works similarly to `nc` but supports encryption

| `openssl` Command Structure                | Meaning |
|-------------------------------------------|---------|
| `openssl s_client [options]`              | Run s_client with options |
| `openssl s_client -connect <host>:<port>` | Connect to a TLS server |

| `s_client` Option | Meaning | Description |
|-------------------|---------|-------------|
| (none)            | Default | Shows certificate and handshake info |
| `-connect`        | Connect | Specifies target host and port |
| `-quiet`          | Quiet   | Suppresses most diagnostic output |


## Mastery Check
- [x] Understands why `nc` fails on SSL/TLS ports
- [x] Understands that `openssl` uses subcommands like `s_client`
- [x] Can use `openssl s_client` to connect to encrypted services
- [x] Can specify a target using `-connect`
- [x] Can use `-quiet` to simplify interaction
