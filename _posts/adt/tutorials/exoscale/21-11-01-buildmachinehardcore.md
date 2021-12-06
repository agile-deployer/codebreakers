---
layout: post
description: The Agile Deployment Toolkit Exoscale Build Machine Method
title: Exoscale ADT Tutorials Build Machine Method
permalink: /adtexoscaletutorialsbuildmachinehardcore/
hide: true
category: agiledeploymenttoolkit
---

### PRE BUILD PREPARATIONS FOR HARDCORE BUILDS:


1) If you don't have an SSH key pair or if you want a specific SSH key pair for your builds, issue the following command:

&nbsp;  
&nbsp; 
>     /usr/bin/ssh-keygen -t rsa 

&nbsp;  
&nbsp; 

Your key will be saved to the indicated file, for example, **/root/.ssh/id_rsa** your path might be different such as **/home/bob/.ssh/id_rsa**
	 
Issue the command (for example)

&nbsp;  
&nbsp; 	 
>     /bin/cat /root/.ssh/id_rsa.pub - this will be your <ssh-public-key-substance>

&nbsp;  
&nbsp; 	 
This will give you your **public** key which you need later so, take a copy of the output that is printed to the screen.

&nbsp;  
&nbsp;  
&nbsp;  

--------------------
	
2) Take on your laptop, take a copy of the script: [Initial Script](./agile-infrastructure-build-client-scripts/userdata/${userdatascript}) - where ${userdatascript} is the name you have given to your userdata script. 
	
&nbsp;  
&nbsp;  
&nbsp; 

------------------
	
3) If you look into the script that you made a copy of in 2, you need to populate the following variables in your copy:

&nbsp;  
&nbsp;
	
>     export BUILDMACHINE_USER=""
>     export BUILDMACHINE_PASSWORD="" 
>     export BUILDMACHINE_SSH_PORT=""
>     export LAPTOP_IP=""
	
>     export SSH=\"\" 
	
&nbsp;  
&nbsp; 	
Now you need to decide on a username for your build machine, a password for your build machine, a port for your build machine's ssh system and the IP address of your desktop or laptop.
	
If I decide on a username of "agile-deployer" then in the copy that I made in 2, I need to change it as follows:  
	
&nbsp;  
&nbsp; 
	
>     export BUILDMACHINE_USER="agile-deployer"

&nbsp;  
&nbsp;
	
If I decide on a password of "QQQPPPZZZMMM123098" then in the copy that I made in 2, I need to change it as follows:

&nbsp;  
&nbsp;
	
>     export BUILDMACHINE_PASSWORD="QQQPPPZZZMMM123098"

&nbsp;  
&nbsp;
	
If you decide on an SSH_PORT of "1035" then in the copy that I made in 2, I need to change it as follows:

&nbsp;  
&nbsp;
	
>     export BUILDMACHINE_SSH_PORT="1035"

&nbsp;  
&nbsp; 

You need to give the script your laptop IP address. You can do this by going to https://www.whatsmyip.com and so, if your ip address is: "111.111.111.111" and pasting your ip address into your copy as follows:

&nbsp;  
&nbsp;
	
>     export LAPTOP_IP="111.111.111.111"

&nbsp;  
&nbsp;
	
The **public** ssh key that you took a copy of in 1 needs to be pasted as follows:

&nbsp;  
&nbsp;
	
>     export SSH=\"<ssh-public-key-substance>\"

&nbsp;  
&nbsp; 

The top part of the copy that you made in 2 will now look like this:

&nbsp;  
&nbsp; 

>     #!/bin/bash
>    
>     /bin/mkdir /root/logs
>    
>     OUT_FILE="webserver-build-out-`/bin/date | /bin/sed 's/ //g'`"
>     exec 1>>/root/logs/${OUT_FILE}
>     ERR_FILE="webserver-build-err-`/bin/date | /bin/sed 's/ //g'`"
>     exec 2>>/root/logs/${ERR_FILE}
>     
>     ###############################################################################################
>     # SET THESE FOR YOUR BUILD CLIENT MACHINE
>     # THIS WILL NOT START A BUILD IT WILL JUST SETUP THE TOOLKIT
>     # USE THIS IF YOU WANT TO PERFORM AN EXPEDITED OR A FULL BUILD FROM THE COMMAND LINE
>     # ssh -i <ssh-private-key> -p ${BUILDCLIENT_SSH_PORT} $BUILDCLIENT_USER@<buildclientip>
>     # $BUILDCLIENT_USER>sudo su
>     # password:${BUILDCLIENT_PASSWORD}
>     # cd agile-infrastructure-build-client-scripts/logs
>     #################################################################################################
>     export BUILDMACHINE_USER="agile-deployer"
>     export BUILDMACHINE_PASSWORD="QQQPPPZZZMMM123098" #Make sure any password you choose is strong enough to pass any strength enforcement rules of your OS
>     export BUILDMACHINE_SSH_PORT="1035"
>     export LAPTOP_IP="111.111.111.111"
>      
>     /bin/echo "
>     #BASE OVERRIDES
>     export SSH=\"ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDEgqlNPY9uh6SpihNXm/7XGqOKvAcH8Z0Y6pZG9lTIm/PHI5VijIFqs0OzM3DPLFARtut7lojBoKq9ljBmKeVBGX5EkJ5O3CJfEZs9E13e2Qk+7F9wTmoMBG8XY4l/SmD9HddLTS/7Oadg+C4RDxHlSMrl1PSCdzlM14spHCI8rwUntNCUY+fObolqel0829zYDX0oEWzYyoIEUs1847X3cRp9+yZsjqSD5Nw9jacLcWjtdfClEvx5F8ZVm0+s5OLtz9cCf6NkOgYf3KFz+e8qAO/w83Umh5B2Gem1uOxSDtUmzVlRiMTfP6CTSKRnYRnkb97F9RZsmAsG6+g+eKvp root@penguin\" #paste your public key here
>     
>     The rest of the script will appear below here

&nbsp;  
&nbsp;  
&nbsp; 

-----------------

4) Take a copy of this entire updated script and keep it safe because you will likely want to use this script multiple times in future deployments remember that anyone who has a copy of this script you have made has enough information to access the build machine you are going to deploy in a minute. 

&nbsp;  
&nbsp;  
&nbsp; 

---------------
	
5) What you need to do now is to use this script to spin up your build machine and you will do this by pasting it into the user data area of your build machine.

You will need to create a security group for your build machine. You can do this as follows:
&nbsp;  
&nbsp; 
	
Click on the security groups option of your exoscale GUI
![](https://www.codebreakers.uk/images/exoscaletutorial/image3.png "Exoscale Tutorial Image 3")
&nbsp;  
&nbsp; 
Click "Add Security Group" and call it **PRECISELY** "adt-build-machine" or something to your liking and then click "Create Group"

![](https://www.codebreakers.uk/images/exoscaletutorial/image5.png "Exoscale Tutorial Image 5") 
&nbsp;  
&nbsp;
You can then see your new security Group "adt-build-machine" listed

![](https://www.codebreakers.uk/images/exoscaletutorial/image6.png "Exoscale Tutorial Image 6")  
&nbsp;  
&nbsp;
Click on the "adt-build-machine" security group

Add rules to the "adt-build-machine" security group to allow pinging and your build client to connect. 
	
![](https://www.codebreakers.uk/images/exoscaletutorial/image8.png "Exoscale Tutorial Image 8")  
	
So you will need to add 2 rules  
	
1) Ping  
2) A rule to allow acccess to your build machines defined SSH_PORT from your laptop.  
   If you SSH_PORT is 1035 and your build client IP is 111.111.111.111 then you will need a TCP rule with "CIDR 111.111.111.111/32 1035"

You can see in this image that port 1035 is about to be opened up to the ip address of my laptop 111.111.111.111/32  
	
![](https://www.codebreakers.uk/images/exoscaletutorial/image17.png "Exoscale Tutorial Image 17") 
&nbsp;  
&nbsp;

---------------

6) You need to spin up a small machine to be your build machine by clicking "Add" on the top right of the GUI. And then follow these steps:

>     1. Select which template you want debian 10 (or later) or ubuntu 20.04 (or later)
>     2. Select which zone you want to deploy to, for example, CH-GVA-2
>     3. Select instance type "Tiny" for example
>     4. Select disk size (50GB)
>     5. Ignore SSH KEY
>     6. Make sure your "adt-build-machine" security group is set
>     7. In the "User Data" area of your VPC machine, paste the entire script that you were left with from 4.
>     8. Click Create and wait for your machine to build

Graphically you can see what I have described in these 8 steps here:

&nbsp;  
&nbsp;  
&nbsp;
	
![](https://www.codebreakers.uk/images/exoscaletutorial/image12.png "Exoscale Tutorial Image 12")  
![](https://www.codebreakers.uk/images/exoscaletutorial/image13.png "Exoscale Tutorial Image 13")  

&nbsp;  
&nbsp;  
&nbsp;
	
---------------

7) Once the machine has built you can access it as follows:
	
&nbsp;  
&nbsp; 
	
>     Discover what the machine's IP address is by looking at the Exoscale GUI system for the IP address of the build machine - In this case: 185.19.29.134

&nbsp;  
&nbsp;
	
Now on your laptop issue the command:

&nbsp;  
&nbsp;

>     ssh -i /root/.ssh/id_rsa -p ${BUILDCLIENT_SSH_PORT} $BUILDCLIENT_USER@<buildclientip>

&nbsp;  
&nbsp;
	
or yours might be:

&nbsp;  
&nbsp;
	
>     ssh -i /home/${username}/.ssh/id_rsa -p ${BUILDCLIENT_SSH_PORT} $BUILDCLIENT_USER@<buildclientip>	

&nbsp;  
&nbsp;

Once logged in to your build machine

&nbsp;  
&nbsp;

>     sudo su 
>     [sudo] password for agile-deployer:

&nbsp;  
&nbsp;

And then enter your build machine password

&nbsp;  
&nbsp; 	

>     ${BUILDMACHINE_PASSWORD}

&nbsp;  
&nbsp;		
	
In Graphical form, it looks like this:

&nbsp;  
&nbsp;
	
Grab your build machine's IP address (third column)
![](https://www.codebreakers.uk/images/exoscaletutorial/image15.png "Exoscale Tutorial Image 15")
	
&nbsp;  
&nbsp;
	
Run through the commands as shown on your laptop to access your build machine

&nbsp;  
&nbsp;
	
![](https://www.codebreakers.uk/images/exoscaletutorial/image16.png "Exoscale Tutorial Image 16")
		
--------------------------------------
