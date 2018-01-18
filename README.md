1- grub document should be replaced by the file in /etc/default/grub   (Includes some information to hide the texts while booting up the system)

2- logind.conf should be replaced by the similar file in /etc/systemd/logind.conf (Includes the information to enable AutoVTs=6) 

3- then we should edit the getty@tty1 file by running the following command:

	$ ### sudo systemctl edit getty@tty1
and using the codes below:

[Service]
ExecStart=
ExecStart=-/usr/bin/agetty --skip-login --login-option "-f username“ %I 38400 linux

4- Need to edit the ~/.bash_profile to enable Xsession for possible application that have graphical requirements (can not be run solely through Terminal)

5- modify the terminal command to open application in ~/.xinitrc file 
