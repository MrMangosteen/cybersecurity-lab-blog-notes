# 11/17/2026

Objective: Gain control of Metasploitable Virtual Machine (VM) though Kali Linux

- Booted up Kali Linux (attack machine) and Metasploitable (victim machine) on Oracle VirtualBox (VBox).

Commands ran:
- In Metasploitable:
	- 'ifconfig'
		This outputs various information about the machine, most crucially, the IP address.

- In Kali Linux (in Terminal):
	- 'ping 192.168.x.x'
		ping makes sure that the attack machine can connect to the victim machine.
		pinged victim's IP
	
	- 'nmap -sC 192.168.x.x'
		nmap scans for ports on target IP
	This command scans for open ports on the victim machine
	
	Ran into an error as retransmission hit its cap of 10.
	
	Decided to shutdown Kali and reconfigure network from NAT to Bridged Adapter.
	- Unfortunately, this led to pinging failure so cannot connect to Metasploitable.
	
	Changing network back to NAT
	
	Reran command:
	- 'nmap -Pn 192.168.x.x'
		-Pn should skip host discovery to make nmap more successful
   
	Did not work, retransmission cap hit once again

- Changing tool from terminal to Metasploit Framework

	Pinged victim IP using same command as before
	
	Attempting to preform nmap:
	- 'nmap -Pn 192.168.x.x'
	
	failure due to retransmission cap being hit


Results: Due to repeated failures and it getting late, today's entry will end here, will attempt another day soon.

# 11/20/2026

Objective: Gain remote control of Metasploitable2 through Kali Linux

- Booted up Kali Linux as the attack machine and Metasploitable2 as the victim machine.
- Main changes from previous entry:
	- Increased base memory of Metasploitable2 from 512 mb to 1 gb (1000 mb)

- Commands ran:
	- On Metasploitable2
		- 'ifconfig'
			To double check IP address
	
	- On Kali Linux:
		- 'ping 192.168.56.102'
			- ![[Pasted image 20261122142937.png]]
			- Connection successful: 0% packet loss
		- 'nmap -Pn -sV 192.168.56.102'
			- ![[Pasted image 20261122142948.png]]
			- This time, it was successful and multiple open ports can be seen below, '-sV' also lets us see the versions. We will be targeting Port 23 "telnet" in this case.
		- 'telnet --help'
			- ![[Pasted image 20261122143008.png]]
			- This just allows to see possible commands that can be ran with telnet
		- 'telnet 192.168.56.102'
			- ![[Pasted image 20261122143030.png]]
			- Allows us to remotely access the victim machine through the login
				- A lot of this is just me messing around or misspelling commands
				- The few successful commands:
				- 'pwd' 
					Lets us view a list of directories
				- 'cd /home'
					Changes directory to /home
				- 'ls'
					Gives a list of files

Results: It seems allocating more memory to Metasploitable was able to make nmap work more effectively and gaining remote access to the victim machine was successful. Next steps should be figuring out how to get remote access without logging in.


# 11/21/2026

Minor addendum: Switched the operating system on my laptop from Windows to Linux Mint. May take time to reinstall and reconfigure Oracle VBox and VMs. Also, I know images don't show up in GitHub, I don't know how to fix.