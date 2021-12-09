---
layout: post
description: The Agile Deployment Toolkit Linode Build Machine Method
title: Linode ADT Tutorials Build Machine Method
permalink: /adtlinodetutorialsbuildmachineexpedited/
hide: true
category: agiledeploymenttoolkit
---

### PRE BUILD PREPARATIONS FOR EXPEDITED AND FULL BUILDS:

Before performing an expedited or full build, you need to set up a build machine. The way you do this for Exoscale is as follows:

----------------

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
	
2) Take a copy of the script: [Initial Script](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/templatedconfigurations/templateoverrides/OverrideScriptLinode.sh) and make a stack sript out of it which will look like:
  
  ![](https://www.codebreakers.uk/images/linodetutorial/image11.png "Linode Tutorial Image 17") 

	
&nbsp;  
&nbsp;  
&nbsp; 

------------------
	
3) If you deploy a machine (debian of ubuntu) using the stack script that you made in 2, you need to populate the following variables in your copy:

&nbsp;  
&nbsp;
	
>     BUILDMACHINE_USER=""  (for example agile-deployer)
>     BUILDMACHINE_PASSWORD=""  (Make sure the password is complex enough to satisfy any strength checks that the OS performs)
>     BUILDMACHINE_SSH_PORT="" (for example 1056)
>     LAPTOP_IP=""   (www.whatsmyip.com)
	
>     SSH=\"\"  (the public key that you installed on your laptop as a key pair in 1)

	
	################REVIEW FIREWALL
	################# SPIN UP LINODE
	
	**********************************

3)  If you are sure that all your variables are set correctly in the stack script you have created, you can now deploy a machine using it and it will install the agile deployment toolkit on it.  

&nbsp;  
&nbsp;  
&nbsp; 

--------------- 
	
6) Add rules to the "adt-build-machine" security group to allow pinging and your build client to connect.  
	
So you will need to add 2 rules  
	
1) Ping  
2) A rule to allow acccess to your build machines defined SSH_PORT from your laptop.  
   If you SSH_PORT is 1035 and your build client IP is 111.111.111.111 then you will need a TCP rule with "CIDR 111.111.111.111/32 1035"

You can see in this image that port 1035 is about to be opened up to the ip address of my laptop 111.111.111.111/32  
	
![](https://www.codebreakers.uk/images/exoscaletutorial/image17.png "Exoscale Tutorial Image 17") 
&nbsp;  
&nbsp;
	
	
---------------

7) You need to spin up a small machine to be your build machine by clicking "Add" on the top right of the GUI. And then follow these steps:

>     1. Select which template you want debian 10 (or later) or ubuntu 20.04 (or later)
>     2. Select which zone you want to deploy to, for example, CH-GVA-2
>     3. Select instance type "Tiny" for example
>     4. Select disk size (50GB)
>     5. Ignore SSH KEY
>     6. Make sure your security group "adt-build-machine" is set for this machine and deselect the "default" security group if it is selected. 
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

8) Once the machine has built you can access it as follows:
	
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
	
 
