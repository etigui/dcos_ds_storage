[<< Back](README.md)
## DC/OS master
- Config Centos/Vbox (hostname, ip, DNS, gateway, proxy, netmask)
- Install nano, wget
- Disabled firewall
- Install docker
- Add public key to authorized_keys
- Add private key
- Modify proxy
- Install DC/OS

## DC/OS Agents
- Config Centos/Vbox (hostname, ip, DNS, gateway, proxy, netmask)
- Install nano, wget
- Disabled firewall
- Install docker
- Add public key to authorized_keys
- Add private key
- Modify proxy

### To Install before
	$> sudo yum install wget
	$> sudo yum install nano

### Add proxy

[Configure Proxy Clients to connect to the Proxy server](https://www.server-world.info/en/note?os=CentOS_7&p=squid&f=2)

Add follows to the end (set proxy settings to the environment variables)  
	
	$> sudo nano /etc/profile  

		MY_PROXY="http://129.194.185.57:3128/"
		HTTP_PROXY=$MY_PROXY
		HTTPS_PROXY=$MY_PROXY
		FTP_PROXY=$MY_PROXY
		http_proxy=$MY_PROXY
		https_proxy=$MY_PROXY
		ftp_proxy=$MY_PROXY
		export HTTP_PROXY HTTPS_PROXY FTP_PROXY http_proxy https_proxy ftp_proxy


For yum (add to the end)

	$> sudo nano /etc/yum.conf

		proxy=http://129.194.185.57:3128/

For wget (add to the end "modify existing")

	$> sudo nano /etc/wgetrc
	
		http_proxy = http://129.194.185.57:3128/
		https_proxy = http://129.194.185.57:3128/
		ftp_proxy = http://129.194.185.57:3128/
		use_prox = on


### Disabled firewall

	$> sudo systemctl stop firewalld
	$> sudo systemctl disable firewalld

## SSH keys
> private key: no passphrase

	$> ssh-keygen -t rsa -b 4096 -C "mesos@example.com" -f $HOME/.ssh id_rsa_mesos

		-----BEGIN RSA PRIVATE KEY-----
		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
		-----END RSA PRIVATE KEY-----


		ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCk2S/AdWm4k1KkPwJCXCVY2JJeOptU9MOYECZiKV37xu12K9ltELrkZ3E3qiIswyWLmOtZV7Cr4NcqCxU5LOaazieKXuB5UbxnmJJ1+fHrkrsIeX8m0JAB7PXaY8BISbu3ctUJAAcn7C62pHJoc+xibH0IKop4ptKqsjZAPzLowph1EgJAOFteTqZieKJC1114TMupA4+0ay4aDp0jDgyXFUm7KDs82MRIb09rpRz4nnu3FZqA4NSzva8AOwFDGHVi32CLv3cBJsGumBFD8NRi13rW6qhYLXKUmlNeM7UGnNE/+6Y5uTp4I7nR4OKThS1B+PgnP0wiIqlODgJ9r9JFhj/qDgJuEu1b4Nk2s4mDz4VG+xW+QEG/0ztLQJCTizDKxoh2zaUCy0/SlrkIS8ztq+dLSsyS+iyN0uzlA/lnAn6hz95VFCSg3IKCXm54w8H1qfoNjHLeelQ8i4MAo43kVa6R93RQhi9WCLj3FLezS93xhvovlyOoRfmEcY3o6UuH+eiqnnb2GDcWJc99fOKzJAbZziiRWtP5IYHHY7quVqOPNKCv1DGZmEGw0STINNPFjL3bhnjWGTGQnyPj5NqvvZZyLpa151YQzbkEWjRGEoz0x79I6p2jDApgJKzbVO1dgWD1wsI8bgeA5L4N3vRup34SGzJlEXQyQb8OW1Gb3Q== mesos@example.com


### Add public key in authorized_keys
[How do I add an SSH key to my remote server](https://serverfault.com/questions/472207/how-do-i-add-an-ssh-key-to-my-remote-server)  
[Example syntax for Secure Copy](http://www.hypexr.org/linux_scp_help.php)  

	$> mkdir -p ~/.ssh
	$> scp -P 22 id_rsa_mesos.pub root@<ip>:/root/.ssh
	$> cat /root/.ssh/id_rsa_mesos.pub >> /root/.ssh/authorized_keys

## Enable remote port forwarding SSH
[SSH Tunnel - Local and Remote Port Forwarding Explained With Examples](http://blog.trackets.com/2014/05/17/ssh-tunnel-local-and-remote-port-forwarding-explained-with-examples.html)

Host (Centos)

	$> sudo nano /etc/ssh/sshd_config

		GatewayPorts yes

	$> sudo service sshd restart

Client

	$> ssh -L 9000:localhost:9000 -p 8822 root@129.194.184.114

		GOTO => http://localhost:9000/#/
## Install Docker

[Install Docker on CentOS](https://dcos.io/docs/1.10/installing/custom/system-requirements/install-docker-centos/)  
[Install Docker on CentOS](https://docs.mesosphere.com/1.10/installing/custom/system-requirements/install-docker-centos/)  

## Install DC/OS
[GUI DC/OS Installation Guide](https://dcos.io/docs/1.10/installing/custom/gui/)

	$> sudo curl -O https://downloads.dcos.io/dcos/stable/dcos_generate_config.sh
	
	# If proxy
	$> sudo curl -x http://129.194.185.57:3128 -O https://downloads.dcos.io/dcos/stable/dcos_generate_config.sh

	$> ./dcos_generate_config.sh --web -v

		#GOTO
		http://<ip or localhost>:9000/#/
