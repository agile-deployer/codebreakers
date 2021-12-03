---
layout: post
description: The Agile Deployment Toolkit Exoscale Tutorials Expedited Temporal Joomla
title: Exoscale ADT Tutorials Expedited Temporal Joomla
permalink: /adtexoscaletutorialsexpeditedtemporal/
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
  
I can extract the values for the following variables from template 1 or template 2 which I used in the previous tutorial and set them in template 3:

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
  
What I then do is adjust /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale3.tmpl to contain these values instead of its defaults.
  
I then need to set the template to use the temporal backups that I have generated and I do that by setting these values in template3:
  
  
  

