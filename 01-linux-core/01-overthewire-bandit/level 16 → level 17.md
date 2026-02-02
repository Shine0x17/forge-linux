# Bandit Level 16 → Level 17

## Goal
Find the correct SSL/TLS service between ports 31000 and 32000 and retrieve the private key for the next level.


## What I did
- Scanned localhost ports 31000–32000 to find which ports were open
- Found open ports: 31046, 31518, 31691, 31790, 31960
- Tested each open port to check whether it supports SSL/TLS using openssl s_client
- Confirmed 31046 and 31691 were not SSL/TLS (handshake error: unexpected message)
- Confirmed 31518 was SSL/TLS but acted as an echo server (returned the password unchanged)
- Connected to 31790 over SSL/TLS and submitted the bandit16 password
- Received "Correct!" and an RSA private key for bandit17


## Command
- nmap -p 31000-32000 localhost
- openssl s_client -connect localhost:PORT -quiet


## Reading Notes
- nmap is used to scan a port range and list which ports are open
- openssl s_client is used to test SSL/TLS connections to a host and port
- If a port does not speak SSL/TLS, the handshake fails with an error
- Some SSL/TLS services are decoys and simply echo the input
- The correct service returns the next credential after successful authentication


## Mastery Check
- [x] Can scan port ranges with nmap
- [x] Can identify SSL/TLS services with openssl
- [x] Can distinguish echo servers from real services

