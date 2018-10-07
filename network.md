[<< Back](README.md)
# Network

	Gateway: 10.194.184.1  
	Netmask: 255.255.252.0 (/22)  
	DNS1: 129.194.8.7   
	DNS2: 129.194.4.6  
	Proxy http: 129.194.185.57:3128

### School SSH computer
[sitehepia.hesge.ch](https://sitehepia.hesge.ch/iti/All.html)

## Config DC/OS
### Master
	PC: ITI-A406-14
	Session: etienne.guignard
	SSH: ssh etienne.guignard@129.194.184.11 
	Public IP: 129.194.184.114 /22
	Private IP: 10.194.184.210 /22  

### Agent 13
	PC: ITI-A406-13
	Session: hassine.rmiza
	SSH: ssh hassine.rmiza@129.194.184.113
	Public IP: 129.194.184.113 /22
	Private IP: 10.194.184.212 /22

### Agent 16
	PC:ITI-A406-16
	Session: thomasch.crockfor
	SSH: ssh thomasch.crockfor@129.194.184.116
	Public IP: 129.194.184.116 /22
	Private IP: 10.194.184.211 /22


## Config vagrant DC/OS
### Port forwarding
	Host A1: 		129.194.184.112:8088		Guest: 192.168.65.90  
	Host P1: 		129.194.184.112				Guest: 192.168.65.60  
	Host SSH: 		127.0.0.1 	   :2222		Guest: <ip> 		 :22  
	Host m1.DCOS:	129.194.184.112:8080		Guest: 192.168.65.90:80  
	Host m1.MESOS:	129.194.184.112:8081		Guest: 192.168.65.90:8080  
	Host p1.docker.Nginx: 129.194.184.112:8000	Guest:   

### Install dcos client
	$> curl -O https://downloads.dcos.io/binaries/cli/linux/x86-64/dcos-1.9/dcos

### Connection ssh pc_school and M1
	$> ssh quentin-zeller@129.194.184.112
	$> cd /usr/local/scratch/quentin.zeller/vagrant/dcos-vagrant/
	$> vagrant global-status
	$> vagrant ssh m1