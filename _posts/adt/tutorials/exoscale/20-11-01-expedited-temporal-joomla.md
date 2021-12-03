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
  
>     
