# Bandit Level 0

## Goal
Log in to the Bandit server using SSH.


## What I did
- SSH login tested
- Environment check complete


## Command
`ssh -p 2220 bandit0@bandit.labs.overthewire.org`


## Reading Notes (From It’s FOSS)
```
One of the SSH hardening practice is to change the default SSH port.  
It reduces the number of bot attacks on the server.  
The default SSH port number is 22. So when you use SSH, it tries to connect to the default port 22.  
But if the remote server uses some other port for SSH, you should provide the port number.  

[Change the default SSH port on Linux server]
- Step 1: Choose a port number  
	You can choose any port number between 0 and 65535 except the common networking ports like 21, 80, 443 etc.  
	Login to the server where you want to make these changes.  
 
- Step 2: Allow the new port through the firewall  
	Check the firewall status.  
	Allow the new port through the firewall.  

- Step 3: Edit the ssh config file
	Use Vim or Nano to edit the config file in the terminal.  
	`nano /etc/ssh/sshd_config` > `Include /etc/ssh/sshd_config.d/*.conf`  
	Change the line to [Port xxxx] format where xxxx is the port number you chose.  
	Save the change and exit the nano editor.  

- Step 4: Restart SSH service  
	Now that you have made changes to config file, restart the service SSH daemon.  
	Most distros these days use systemd and hence use this command to restart it.  
	`systemctl restart sshd`  
	Now when you have to connect to the server via SSH, specify the port number.  
	`ssh -p xxxx user@ip`  

- Conclusion  
	Not that it will stop SSH attacks but changing the default port does reduce the number of attacks automated bot target on the port 22.
```

## Mastery Check
- [x] Can SSH into the server without help
- [x] Can explain the goal of Level 0

