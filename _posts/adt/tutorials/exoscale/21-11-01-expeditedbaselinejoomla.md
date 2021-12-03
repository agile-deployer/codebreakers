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

1. Choose a unique identifier for my baseline repositories, in this case I am going to call them, "communitybuilder" yours will be a different name.
2. Go to you git provider account console with your browser, in this case it is my "adt-demos" account with Github and create two private repositories:

>     communitybuilder-webroot-sourcecode-baseline
>     communitybuilder-db-baseline

Once these two repositories have been created you are ready to make a baseline of the joomla install that you have modified. 

3. To generate your baseline, you have to run two commands on your build machine. At the command prompt of your build machine cd into the **helperscripts** directory of your agile deployment toolkit installation. In my case it is like this:

>     cd /home/agile-deployer/agile-infrastructure-build-client-scripts/helperscripts

Once you are in that directory, you need to issue the command:

>     /bin/sh PerformWebsiteBaseline.sh

Once that starts running, you need to answer the questions you are prompted for entering, "communitybuilder" if you are prompted for an identifier. 

In a minute or two your webiste baseline will have been generated and you should check in its repository that sourceode has been generated to it. 

Now you need to generate a baseline of the database. To do that you need to issue the command:

>     /bin/sh PerformDatabaseBaseline.sh

If there is a prompt for an identifier, I enter "communitybuilder" and make very sure that the repository communitybuilder-db-baseline exists

In short order, my database is backed up to the Github repository and again, I should check that the repository I have chosen has been updated using the github console.

-----------------------------------------------

My application baselines are now complete. The process for generating baselines is the same whichever application type you have built, Joomla, Wordpress, Drupal or Moodle. 

The next step is to make a deployment of these baselines. So, if I have any webservers or databases running with my cloudhost, I need to take them off line (shut them down) and destroy them. 

I am then interested in template 2 because that is the template that is used for deploying baselined application. If its not clear, template 1 is used for virgin CMS deployments, template 2 is used for baselined application deployments and template 3 is used for temporal deployments. 

So, template 2 is located here on my build machine:

>     /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale2.tmpl

I can copy the credentials that I need from the values that I set them to previously in template1. So, looking in template1,

>     /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale1.tmpl

I can extract the values for the following variables:

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

What I then do is adjust /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale2.tmpl to contain these values instead of its defaults. 

With that done, because I used "Postgres" which from the file dbe.dat in the webroot of my baseline when I deployed Joomla originally, I need to make sure that I set the database to use as follows:

>     export DATABASE_INSTALLATION_TYPE="Postgres"

There are some other values that I need to change in /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale2.tmpl, as follows:

>     export APPLICATION="joomla" #MANDATORY (joomla or wordpress or drupal or moodle)
>     export APPLICATION_IDENTIFIER="1" #MANDATORY (1 for joomla, 2 for wordpress, 3 for drupal, 4 for moodle)
>     export BASELINE_DB_REPOSITORY="communitybuilder-db-baseline" #MANDATORY
>     export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="communitybuilder-webroot-sourcecode-baseline" #MANDATORY
>     export PERSIST_ASSETS_TO_CLOUD="0" #MANDATORY This should only be 0 if your application has a very small number of assets
>     export DIRECTORIES_TO_MOUNT="" #MANDATORY - this will define which directories in your webroot will be mounted from S3, if PERSIST_ASSETS_TO_CLOUD=1

You can make any other adjustments you want like if you want to choose APACHE instead of NGINX or change the size of the machines (you can find out about such things in the specification).

With your baseline template fully configured, you are now ready to perform a baseline build (in other words, directly install a live application starting from zilch).
That will look something like the following:



