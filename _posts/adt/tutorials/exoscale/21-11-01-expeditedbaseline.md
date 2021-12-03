---
layout: post
description: The Agile Deployment Toolkit Exoscale Tutorials Expedited Baseline Joomla
title: Exoscale ADT Tutorials Expedited Baseline Joomla
permalink: /adtexoscaletutorialsexpeditedbaseline/
hide: true
category: agiledeploymenttoolkit
---

If you have followed the tutorial here, then you will have an active Joomla, or possibly Wordpress, Drupal or Moodle installation active through your web browser.
What you need to do now is to customise your version of (Joomla) so that it is a specialised application for example a blog or a social network and so on. 

What I have done for this tutorial is install a very simple application using a tool called "Community Builder" which you can find here: [Community Builder](www.joomlapolis.com). Literally all I have done is install the latest version (at the time) into my Joomla installation that I installed earlier. 

The next thing I have to do is to generate a baseline of my application so that the baseline can be redeployed. A baseline is stored with whatever git provider you have set in your template when you made your deployment. In my case my git account is my "adt-demos" account with Github. 

In order to create the baseline I am going to deploy, I need to do the following:

1. Choose a unique identifier for my baseline repositories, in this case I am going to call them, "communitybuilder"
2. Go to you git provider account console with your browser, in this case it is my "adt-demos" account with Github and create two private repositories:

>     communitybuilder-webroot-sourcecode-baseline
>     communitybuilder-db-baseline

Once these two repositories have been created you are ready to make a baseline of the joomla install that you have modified. 

3. To generate your baseline, you have to run two commands on your build machine. At the command prompt of your build machine cd into the **helperscripts** directory of your agile deployment toolkit installation. In my case it is like this:

>    cd /home/agile-deployer/agile-infrastructure-build-client-scripts/helperscripts

Once you are in that directory, you need to issue the command:

>    /bin/sh PerformWebsiteBaseline.sh

Once that starts running, you need to answer the questions you are prompted for entering, "communitybuilder" if you are prompted for an identifier. 
