## Silent Boot to an application

I have been looking for differnt options to create a linux system that, when turned on, boots directly to an application without showing any additional texts or something. Similar to what we see in game consoles (Atart, PS, Nintendo, ...). 

It took me awhile though to find out Arch Linux is one of the best options as it provides the barebone and you build upon it as you need. (So you can either build a 1-story building or 110-story Sears Tower). The following steps are the basics that gives you a starting point to have something handy.

1- grub document should be replaced by the file in /etc/default/grub   (Includes some information to hide the texts while booting up the system)

2- logind.conf should be replaced by the similar file in /etc/systemd/logind.conf (Includes the information to enable AutoVTs=6) 

3- then we should edit the getty@tty1 file by running the following command:

	sudo systemctl edit getty@tty1
	
and using the codes below:

	[Service]
	ExecStart=
	ExecStart=-/usr/bin/agetty --skip-login --login-option "-f username“ %I 38400 linux

4- Need to edit the ~/.bash_profile to enable Xsession for possible application that have graphical requirements (can not be run solely through Terminal)

5- modify the terminal command to open application in ~/.xinitrc file 


### I am also trying to build a makefile for this project to automate the process. Please let me know if you are familiar with Unix platforms and interested in collaborating on building this makefile. You might know how to contact me, but in case :) [jahanpour.ehsan@gmail.com](jahanpour.ehsan@gmail.com)
