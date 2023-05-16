Installing Fail2Ban on your (home)server

At some point you have the idea of installing a server at home becuase you want to store backups or want to share fotos eg. 
Great idea! Why would you order a vps if you have a space computer and have a internet connection. But as soon as you put the portforwarding rule in your 
router and you take a look at your log files, it looks like the whole evil world is trying to login at your server at the same time!

So lets install **Fail2Ban** in order to try to keep those evil persons out.

## Fail2ban

In the example below i assume you have a ubuntu / debian based linux server installed. Of course Fail2Ban can be installed
on other distros too, but then you will have to use your own package manager in order to install the pakkages.

First make sure that your server is uptodate.

	$ sudo apt update && sudo apt upgrade

Then install fail2ban with apt (or other package manager)

	$ sudo apt install fail2ban

Enable the service

	$ sudo systemctl enable fail2ban.service

Let's create a configuration file 

	sudo nano /etc/fail2ban/jail.local

	[sshd]
	enabled = true
	port = ssh
	filter = sshd
	logpath = /var/log/auth.log
	maxretry = 3
	findtime = 300
	bantime = 3600
	ignoreip = 127.0.0.1 ::1
	ban.multipliers = 1 2 4 8 16 32 64

Restart the service

	sudo systemctl restart fail2ban.service

Now if everything wen the way it should be you can u the client to see the status

## Fail2ban-client

In order to see which jails are defined you can use following command:

	sudo fail2ban-client status

And to see the status of the particular jail:

	sudo faul2ban-client status sshd

You wil see the number of ips that are blocked.

Now your data on your server will be on a little bit safer place.

Tags: keep-this-tag-format, tags-are-optional, beware-with-underscores-in-markdown, example
