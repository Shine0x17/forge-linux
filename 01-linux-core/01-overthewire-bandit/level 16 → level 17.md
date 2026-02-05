# Bandit Level 16 → Level 17

## Goal
Retrieve the credentials for the next level by submitting the current password
to the correct SSL/TLS-enabled port between 31000 and 32000 on localhost.


## What I Did
- Scanned ports in the range 31000–32000 to find open services
- Checked which open ports supported SSL/TLS
- Tested TLS-enabled ports using openssl
- Found the correct server that returned an RSA private key
- Saved the private key to a file using redirection
- Copied the key file to the local machine
- Logged in to bandit17 using SSH key authentication


## Command
- `nmap -p 31000-32000 localhost`
- `openssl s_client -connect localhost:PORT -quiet`
- `cat > bandit17.key`
- `chmod 600 bandit17.key`
- `scp -P 2220 bandit16@bandit.labs.overthewire.org:/tmp/bandit17.key .`
- `ssh -i bandit17.key bandit17@bandit.labs.overthewire.org -p 2220`


## Reading Notes
- Port Scanning and Service Discovery
  - This level required scanning a specific port range to locate active services.
  - Only ports marked as `open` were relevant for further testing.

- TLS Identification
  - TLS-enabled ports were identified by successful SSL handshakes.
  - Non-TLS ports returned protocol or handshake errors.
  - The correct port returned an RSA private key after password submission.

- Private Key Handling
  - The private key had to be saved without extra characters.
  - Copy-paste mistakes could insert unwanted prompt text.
  - `cat > file` writes input directly to the file.

- Input Control
  - `Ctrl+D` sends EOF and ends input normally.
  - `Ctrl+C` interrupts input but usually keeps written data.

- Security and Authentication
  - SSH requires strict permission settings for private keys.
  - `chmod 600` allows only the owner to access the key.

- File Transfer
  - `scp` was used to securely transfer the key file.

| `nmap` Command Structure | Meaning |
|--------------------------|---------|
| `nmap [option] [target]` | Scan target host |

| `nmap` option | Meaning | Description |
|---------------|---------|-------------|
| -p            | Port    | Specify port range |
| -sV           | Service | Detect service version |
| -v            | Verbose | Show detailed output |

| `openssl` Command Structure | Meaning |
|-----------------------------|---------|
| `openssl s_client -connect host:port` | TLS connection |

| `openssl` option | Meaning | Description |
|------------------|---------|-------------|
| -connect         | Target  | Specify address and port |
| -quiet           | Quiet   | Hide handshake logs |

| `cat` Command Structure | Meaning |
|-------------------------|---------|
| `cat > file`            | Write input to file |

| `cat` redirection | Meaning | Description |
|-------------------|---------|-------------|
| >                 | Output  | Redirect output to file |
| >>                | Append  | Append output to file |

| `ssh` Command Structure | Meaning |
|-------------------------|---------|
| `ssh -i key user@host -p port` | Login using private key |

| `ssh` option | Meaning | Description |
|--------------|---------|-------------|
| -i           | Identity | Specify private key |
| -p           | Port     | Specify SSH port |

| `scp` Command Structure | Meaning |
|-------------------------|---------|
| `scp -P port user@host:file local` | Copy remote file |

| `scp` option | Meaning | Description |
|--------------|---------|-------------|
| -P           | Port    | Specify SSH port |


## Mastery Check
- [x] Can scan port ranges using nmap
- [x] Can identify TLS-enabled services
- [x] Can test encrypted services with openssl
- [x] Can safely store sensitive data using redirection
- [x] Can manage file permissions for private keys
- [x] Can transfer files using scp
- [x] Can authenticate using SSH private keys