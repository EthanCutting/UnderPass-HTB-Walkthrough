# UnderPass-HTB-Walkthrough
# Port Scanning
for my HTB machine I was using the IP Address 10.10.11.48 , before doing a nmap scan you will need to add the IP and host in /etc/hosts/ directory and save it like this 10.10.11.48.underpass.htb

command to acccess /etc/hosts:

- sudo nano /etc/hosts/
- sudo cat /etc/hosts/ (This is good to always double check your work before moving on)

Now, moving on to the nmap scaning to find open ports:
- nmap -sV -Pn 10.10.11.48

damn this didn't give me anything good, so i run a TCP and UPD scan to see all the other open ports:
- sudo nmap -sU underpass.htb -Pn


# Harvesting using snmpbulkwalk
"snmpbulkwalk" is a command used to retrieve a large amount of data from a network device using the SNMP protocol, by sending a single "GETBULK" request to efficiently retrieve a whole tree of information (like a subtree within the MIB) from the device, making it faster than the standard "snmpwalk" command which queries one variable at a time; essentially, it allows you to efficiently gather a large set of data from a network device with a single SNMP request. 

Command: 

- snmpbulkwalk -c public -v2c underpass.htb

Output

- steve@underpass.htb
- UnDerPass.htb is the only daloradius server in the basin!
this information give me some information about the machine and after some looking into about daloradius severs, I found out a website with default login credentials.

Website: http://underpass.htb/daloradius/app/operators/login.php





# Root Flag
using the command sudo -l this help me list the current user privileges level , I find that the mosh-server doesnot need root privilege and I am able to go inside this directory.

using these command one by one will give you access to mosh-server:

- sudo /usr/bin/mosh-server new -p 61113
- MOSH_KEY=<Key> mosh-client 127.0.0.1 61113
