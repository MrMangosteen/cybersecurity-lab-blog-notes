# 11/17/2026

Objective: Gain control of Metasploitable Virtual Machine though Kali Linux

- Booted up Kali Linux (attack machine) and Metasploitable (victim machine)

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
