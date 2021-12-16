---
layout: post
description: The Agile Deployment Toolkit Exoscale Tutorials Hardcore Temporal Joomla
title: Exoscale ADT Tutorials Hardcore Temporal Joomla
permalink: /adtexoscaletutorialshardcoretemporal/
hide: true
category: agiledeploymenttoolkit
---

**YOU MUST HAVE THE MACHINES STILL RUNNING FROM THE PREVIOUS TUTORIAL TO COMPLETE THIS TUTORIAL SUCCESSFULLY**

On your build machine, you need to now make temporal backups of your application sourcecode and your application database.
You do this as follows:

>     cd /home/<your username>/agile-infrastructure-build-client-scripts/helperscripts

Then perform a temporal database backup
  
>     /bin/sh PerformDatabaseBackup.sh
 
Answering all of the questions and picking a periodicity, for example, HOURLY (make sure DISABLE_HOURLY=0) in your template
  
Then perform a temporal website sourcecode backup
  
>     /bin/sh PerformWebsiteBackup.sh
  
Making sure you pick the same periodicity as for the temporal database backup, for example, "HOURLY"
  
What we are then interested in is template 3 which is at:
  
>     /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale3.tmpl
  
I can extract the values for the following variables from template 1 or template 2 which I used in the previous tutorial and set them in template 3, replace these with your own live values:

>     export S3_ACCESS_KEY="AAAAA"  #MANDATORY
>     export S3_SECRET_KEY="BBBBB"  #MANDATORY
>     export ACCESS_KEY="XXXXX"   #MANDATORY
>     export SECRET_KEY="YYYYY"   #MANDATORY
>     export DNS_USERNAME="testemail@testemail.com"  #MANDATORY
>     export DNS_SECURITY_KEY="CCCCC:DDDDD"   #MANDATORY - This is your access key and your secret key, written: DNS_SECURITY_KEY="${ACCESS_KEY}:${SECRET_KEY}"
>     export CLOUDHOST_EMAIL_ADDRESS="testemail@testemail.com" #MANDATORY
>     export WEBSITE_DISPLAY_NAME="Test Social Network" #MANDATORY
>     export WEBSITE_NAME="testsocialnetwork" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial
>     export WEBSITE_URL="www.testsocialnetwork.org.uk"  #MANDATORY
>     export APPLICATION_REPOSITORY_OWNER="mytestgituser" #MANDATORY
>     export APPLICATION_REPOSITORY_USERNAME="mytestgituser" #MANDATORY
>     export APPLICATION_REPOSITORY_TOKEN="KKKKK" #MANDATORY
  
What I then do is adjust  

>     /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale3.tmpl  
  
to contain these values instead of its defaults.
  
I then need to set the template to use the temporal backups that I have generated and I do that by setting these values in template3:
  
>     export APPLICATION="joomla" #MANDATORY (joomla or wordpress or drupal or moodle)
>     export BUILD_CHOICE="2" #MANDATORY 2=hourly, 3=daily, 4=weekly, 5=monthly, 6=bimonthly
>     export BUILD_ARCHIVE_CHOICE="hourly" #MANDATORY hourly, daily, weekly, monthly, bimonthly
>     export PERSIST_ASSETS_TO_CLOUD="1" #MANDATORY This should only be 0 if your application has a very small number of assets
>     export DIRECTORIES_TO_MOUNT="images" #MANDATORY - this will define which directories in your webroot will be mounted from S3, if PERSIST_ASSETS_TO_CLOUD=1
  
Shutdown any webservers that you have running from tutorial 2 and you are then ready to perform a temporal build, as shown below:
  
You can make any other adjustments you want like if you want to choose APACHE instead of NGINX or change the size of the machines (you can find out about such things in the specification).

**FOLLOW THESE STEPS ON YOUR LAPTOP IF YOU DON'T HAVE A BUILD SERVER RUNNING**

You now need to copy your template as follows on your laptop:  

>     /bin/cp ./agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale2.tmpl ./agile-infrastructure-build-client-scripts/overridescripts/exoscale2override.tmpl  

Then you need to run the script:

>     cd helperscripts

>     ./GenerateHardcoreUserDataScript.sh

This will leave you with a script:

>    ../userdatascripts/${userdatascript}   

where ${userdatascript} is the descriptive name you gave when prompted.  

>     Now you have your userdata script take a copy of it using copy and paste and then follow [these](https://www.codebreakers.uk/adtexoscaletutorialsbuildmachinehardcore)   
>     instructions PASTING THE SCRIPT YOU HAVE JUST COPIED INTO THE USERDATA AREA OF YOUR EXOSCALE MACHINE INSTEAD OF THE MODIFIED TEMPLATE. 
>     The build machine will then install **AND**  run the agile deployment toolkit. This is just an alternative method to the expedited build process which you may or
>     may not perfer.


>     At this point, your build machine should be up and running. Please review  
>  
>     ./agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/TightenBuildMachineAccess.md.  
> 
>      At this point, your build machine will only accept connections from your laptop. If you need access from other ip addresses you need to use the technique described in "Tightening Build Machine Access" to grant access to additional IP addresses. This will be the case every time your laptop changes its IP address as you travel about, so, you might want to setup and configure an S3 client on your laptop to enable you to grant access to new IP addresses easily. 

**IF YOU DO HAVE A BUILD SERVER RUNNING FROM A PREVIOUS BUILD, THEN JUST DO THE FOLLOWING**
  
  <iframe width="560" height="315" src="https://www.youtube.com/embed/WiuacLCV_XU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
  If all has gone according to plan, you will have seen a full deployment of your temporal backup. 
  
  ------------------------
  **DEPLOYMENT USING MANAGED DATABASES**
  
  There's something else to be aware of, if you want to deploy a managed DBaaS system instead of just using the one that is built in to the build process you can do that as detailed in [this](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/DeployingDBaaS-Shortcut.md) and [this](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/DeployingDBaaS.md) document
  
  ------------------------
  **DEPLOYMENT USING SNAPSHOTS**
  
  You can also build your webservers using snapshots that you generate and then use. You can read about how to perform snapshot builds [here](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/SnapshotsWorkflow.md).
  
  ------------------------
  **OTHER APPLICATION TYPES**
  
In order to do a temporaly build from backups you have made for a different application type (wordpress, drupal or moodle) you will need to alter the following variables in your template compared to what you have used above:
  
  For Wordpress:
  
>     export APPLICATION="wordpress"
>     export DIRECTORIES_TO_MOUNT="wp-content.uploads"
  
  For Drupal:
  
>     export APPLICATION="drupal"
>     export DIRECTORIES_TO_MOUNT="sites.default.files"
  
  For Moodle:
  
>     export APPLICATION="moodle"
>     export DIRECTORIES_TO_MOUNT="moodledata.filedir"
