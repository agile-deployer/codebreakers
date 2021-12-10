---
layout: post
description: The Agile Deployment Toolkit Linode Tutorials Expedited Virgin  
title: Linode ADT Tutorials Linode Virgin
permalink: /adtlinodetutorialsexpeditedvirgin/
hide: true
category: agiledeploymenttoolkit
---

**PREBUILD NECESSITIES**

If you don't already have a build machine running in the Linode cloud, follow these steps to get ready for the main build)

1. Begin by following this: [Build Machine Setup](https://www.codebreakers.uk/adtlinodetutorialsbuildmachineexpedited/)  

2. At this point, your build machine should be up and running. Please review [Tightening Build Machine Firewall](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/TightenBuildMachineAccess.md). At this point, your build machine will only accept connections from your laptop. If you need access from other ip addresses you need to use the technique described in "Tightening Build Machine Firewall" to grant access to additional IP addresses. This will be the case every time your laptop changes its IP address as you travel about, so, you might want to setup and configure an S3 client on your laptop to enable you to grant access to new IP addresses easily. 

-----------------------------

**EXPEDITED BUILD PROCESS**

This will deploy the latest version of Joomla using template 1 which you can read about here: [template 1](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/templatedconfigurations/templates/linode/linode1.description) and the expedited method.

If you have followed these steps your build machine is online and secured and you have an SSH session open to it from your laptop through which to initiate your build processes.

We need several pieces of information from our cloud host and 3rd party services for a successful build to be possible:

I am going to use the example of joomla to build from and so this example will build a virgin installation of the latest version of joomla

---------------------------------------

To find the latest version of Joomla, I go to this URL in my browser:

[Joomla Latest](https://downloads.joomla.org/)

And I note the latest version in a separate text file:

>     joomla_version="4.0.4"  

You can of course use a legacy version of joomla also by choosing a different version numnber. 

-------------------------------------

I then need a set of compute access keys so, I go to the top right and select "API Keys" and generate a personal access token with "Domains, Images, IPs, Linodes, Object Storage, Stackscripts and Volumes" enabled. This personal access token I shall call "AAAAA"

>     linode_personal_access_token="AAAAA"  where AAAAA is the actual values generated when I click "Create Token"

-------------------------

You now need to set up Object Storage and obtain Object Storage Keys. You can do this by Selecting Object Storage on the left hand side of your Linode console. 

You then click "Access Key" and then, "Create Access Key" and this will display an "Access Key" and a "Secret Key" which you need to make a note of and keep safe:

>     linode_S3_access_key="BBBBB"
>     linode_S3_secret_key="CCCCC"


-----------------------------------

You now need to make a note of the email address that you have registered with your Linode account:

>     linode_email="testemail@testemail.com"

-----------------------------------

You then need the url that you want to use for your website. If you don't have a DNS URL for your website, you need to purchase one and set the nameservers to Linode as described [here](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/Nameservers.md)

>     linode_dns_name="www.testsocialnetwork.org.uk"

-------------------------------

You then need the username and owner of you git provider application repositories.
To do this, if you don't have a git account sign up with one (in this case using github, but, you have the choice of bitbucket and gitlab as well) and record the username that you sign up with:

>     gitusername="mytestgituser"

Then create a "personal access token" by following: 

[Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) making sure you give it all "repo" permissions

>     gitpersonalaccesstoken="KKKKK" where KKKKK represents your actual personal access token

--------------------------------

To keep this as simple as possible, I have missed out the SMTP credentials, but, you can find out more about them [here](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/DeployingSMTPService.md). If you wish to include SMTP credentials you will need to have a service offering set up with either sendpulse, mailjet or AWS SES.

So, that should be all the core credentials that I need to make a deployment. I can save my text file now (and keep it secure) because I might want to use these credentials again for other deployments or redeployments. 

--------------------------------------------
--------------------------------------------

So, at the command line of my build machine that we spun up earlier:

My chosen username is "agile-deployer"

So, to begin an expedited build process, I need to:

>     cd /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/linode

Then we can open up the 

>     vi linode1.tmpl

This file looks like this (I have put a dashes before each line I wish to modify for this deployment which is for illustrative purposes only):

>     ###############################################################################################
>     # Refer to: ${BUILD_HOME}/templatedconfigurations/specification.md
>     ###############################################################################################
>     ----- export APPLICATION=""
>     ----- export JOOMLA_VERSION="" #MANDATORY - change this to the version you want to deploy, for example 4.0.3 set it to "" if you are deploying anything but joomla
>     export DRUPAL_VERSION="9.2.1"  #MANDATORY - change this to the version you want to deploy, for example, 9.2.6 set it to "" if you are deploying anything but drupal
>     ----- export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="" #MANDATORY 
>     #^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
>     # change this to, for example, JOOMLA:4.0.3 if you are deploying drupal (APPLICATION=joomla)
>     # change this to, WORDPRESS if you are deploying wordpress
>     # change this to, for example, DRUPAL:9.2.6 if you are deploying drupal (APPLICATION=drupal)
>     # change this to, MOODLE if you are deploying moodle
>     #############################################################################################
>     ----- export S3_ACCESS_KEY=""  #MANDATORY
>     ----- export S3_SECRET_KEY=""  #MANDATORY
>     export S3_HOST_BASE="eu-central-1.linodeobjects.com" #MANDATORY
>     export S3_LOCATION="US" #For linode, this always needs to be set to "US"
>     ----- export TOKEN="" #MANDATORY this is your linode personal access token
>     export ACCESS_KEY=""   #NOT REQUIRED
>     export SECRET_KEY=""   #NOT REQUIRED
>     ----- export DNS_USERNAME=""  #MANDATORY
>     ----- export DNS_SECURITY_KEY=""   #MANDATORY
>     export DNS_CHOICE="linode" #MANDATORY - you will need to set your DNS nameservers according to this choice
>     ----- export CLOUDHOST_EMAIL_ADDRESS="" #MANDATORY
>     export BUILDOS="debian" #MANDATORY one of ubuntu|debian
>     export BUILDOS_VERSION="11" #MANDATORY one of 20.04|10
>     export DEFAULT_USER="root" #MANDATORY - This should always be 'root' on linode
>     ----- export BUILD_IDENTIFIER="" #MANDATORY
>     ----- export WEBSITE_DISPLAY_NAME="" #MANDATORY
>     ----- export WEBSITE_NAME="" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial
>     ----- export WEBSITE_URL=""  #MANDATORY
>     export APPLICATION_REPOSITORY_PROVIDER="github" #MANDATORY
>     ----- export APPLICATION_REPOSITORY_OWNER="" #MANDATORY
>     ----- export APPLICATION_REPOSITORY_USERNAME="" #MANDATORY
>     export APPLICATION_REPOSITORY_PASSWORD="" #MANDATORY
>     ----- export APPLICATION_REPOSITORY_TOKEN="" #MANDATORY
>     export SYSTEM_EMAIL_PROVIDER="" #MANDATORY
>     export SYSTEM_TOEMAIL_ADDRESS="" #MANDATORY
>     export SYSTEM_FROMEMAIL_ADDRESS="" #MANDATORY
>     export SYSTEM_EMAIL_USERNAME="" #MANDATORY
>     export SYSTEM_EMAIL_PASSWORD="" #MANDATORY
>     export DIRECTORIES_TO_MOUNT="" #This should always be unset for a virgin deployments
>     export DB_PORT="2035"
>     export SSH_PORT="1035"
>     export GATEWAY_GUARDIAN="0"
>     export PRODUCTION="0"
>     export DEVELOPMENT="1"
>     export BUILD_CHOICE="0"
>     ----- export WEBSERVER_CHOICE="APACHE"
>     export NO_AUTOSCALERS="1"
>     export NUMBER_WS="1"
>     export SUPERSAFE_WEBROOT="1"
>     export SUPERSAFE_DB="1"
>     ----- export DATABASE_INSTALLATION_TYPE="MySQL"
>     export PERSIST_ASSETS_TO_CLOUD="0" #This should always be set to 0 for a virgin deployment
>     export DISABLE_HOURLY="0"
>     export SERVER_TIMEZONE_CONTINENT="Europe"
>     export SERVER_TIMEZONE_CITY="London"
>     export BASELINE_DB_REPOSITORY="VIRGIN"
>     export BUILD_ARCHIVE_CHOICE="virgin"
>     export APPLICATION_LANGUAGE="PHP"
>     ----- export APPLICATION_IDENTIFIER="0"
>     export PHP_VERSION="8.0"
>     export REGION=""
>     export REGION_ID="eu-central"
>     export DB_SIZE="g6-nanode-1"
>     export DB_SERVER_TYPE="g6-nanode-1"
>     export WS_SIZE="g6-nanode-1"
>     export WS_SERVER_TYPE="g6-nanode-1"
>     export AS_SIZE="g6-nanode-1"
>     export AS_SERVER_TYPE="g6-nanode-1"
>     export CLOUDHOST="linode"
>     export MACHINE_TYPE="LINODE"
>     export ALGORITHM="rsa"
>     export USER="root"
>     export CLOUDHOST_USERNAME="root"
>     export CLOUDHOST_PASSWORD=""
>     export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"
>     export PREVIOUS_BUILD_CONFIG="0"
>     export GIT_USER="Templated User"
>     export GIT_EMAIL_ADDRESS="templateduser@dummyemailZ123.com"
>     export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"
>     export INFRASTRUCTURE_REPOSITORY_OWNER="agile-deployer"
>     export INFRASTRUCTURE_REPOSITORY_USERNAME="agile-deployer"
>     export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"
>     export DATASTORE_CHOICE="linode"
>     export SSL_GENERATION_METHOD="AUTOMATIC"
>     export SSL_GENERATION_SERVICE="LETSENCRYPT"
>     export BYPASS_DB_LAYER="0"
>     export DBaaS_HOSTNAME=""
>     export DBaaS_USERNAME=""
>     export DBaaS_PASSWORD=""
>     export DBaaS_DBNAME=""
>     export DATABASE_DBaaS_INSTALLATION_TYPE=""
>     export DBaaSDBSECURITYGROUP=""
>     export DBIP=""
>     export DBIP_PRIVATE=""
>     export WSIP=""
>     export WSIP_PRIVATE=""
>     export ASIP=""
>     export ASIP_PRIVATE=""
>     export APPLICATION_NAME=""
>     export MAPS_API_KEY=""
>     export PHP_MODE=""
>     export PHP_MAX_CHILDREN=""
>     export PHP_START_SERVERS=""
>     export PHP_MIN_SPARE_SERVERS=""
>     export PHP_MAX_SPARE_SERVERS=""
>     export PHP_PROCESS_IDLE_TIMEOUT=""
>     export IN_MEMORY_CACHING=""
>     export IN_MEMORY_CACHING_PORT=""
>     export IN_MEMORY_CACHING_HOST=""
>     export IN_MEMORY_CACHING_SECURITY_GROUP=""
>     export ENABLE_EFS=""
>     export SUBNET_ID=""
>     export AUTOSCALE_FROM_SNAPSHOTS=""
>     export GENERATE_SNAPSHOTS=""
>     export SNAPSHOT_ID=""
>     export WEBSERVER_IMAGE_ID=""
>     export AUTOSCALER_IMAGE_ID=""
>     export DATABASE_IMAGE_ID=""
>     export BUILD_HOME=""
>     export BUILD_CLIENT_IP=""
>     export PUBLIC_KEY_ID=""


So, I have referred to the specification and I have freely chosen to modify the  

**WEBSERVER_CHOICE to "NGINX"**   
**APPLICATION_IDENTIFIER to "1"**  
**DATABASE_INSTALLATION_TYPE to "Postgres"**  

So, editing /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/linode/linode1.tmpl and using the values I recorded in my text file earlier, I modify the file as follows, the lines beginning with dashes have been modified


>     ###############################################################################################
>     # Refer to: ${BUILD_HOME}/templatedconfigurations/specification.md
>     ###############################################################################################
>     ----- export APPLICATION="joomla"
>     ----- export JOOMLA_VERSION="4.0.4" #MANDATORY - change this to the version you want to deploy, for example 4.0.3 set it to "" if you are deploying anything but joomla
>     export DRUPAL_VERSION="9.2.1"  #MANDATORY - change this to the version you want to deploy, for example, 9.2.6 set it to "" if you are deploying anything but drupal
>     ----- export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="JOOMLA:4.0.4" #MANDATORY 
>     #^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
>     # change this to, for example, JOOMLA:4.0.3 if you are deploying drupal (APPLICATION=joomla)
>     # change this to, WORDPRESS if you are deploying wordpress
>     # change this to, for example, DRUPAL:9.2.6 if you are deploying drupal (APPLICATION=drupal)
>     # change this to, MOODLE if you are deploying moodle
>     #############################################################################################
>     ----- export S3_ACCESS_KEY="BBBBB"  #MANDATORY
>     ----- export S3_SECRET_KEY="CCCCC"  #MANDATORY
>     export S3_HOST_BASE="eu-central-1.linodeobjects.com" #MANDATORY
>     export S3_LOCATION="US" #For linode, this always needs to be set to "US"
>     ----- export TOKEN="AAAAA" #MANDATORY this is your linode personal access token
>     export ACCESS_KEY=""   #NOT REQUIRED
>     export SECRET_KEY=""   #NOT REQUIRED
>     ----- export DNS_USERNAME="testemail@testemail.com"  #MANDATORY (the email address of your linode account)
>     ----- export DNS_SECURITY_KEY="AAAAA"   #MANDATORY
>     export DNS_CHOICE="linode" #MANDATORY - you will need to set your DNS nameservers according to this choice
>     ----- export CLOUDHOST_EMAIL_ADDRESS="testemail@testemail.com" #MANDATORY
>     export BUILDOS="debian" #MANDATORY one of ubuntu|debian
>     export BUILDOS_VERSION="11" #MANDATORY one of 20.04|10
>     export DEFAULT_USER="root" #MANDATORY - This should always be 'root' on linode
>     ----- export BUILD_IDENTIFIER="nuocial" #MANDATORY
>     ----- export WEBSITE_DISPLAY_NAME="Test Social Network" #MANDATORY
>     ----- export WEBSITE_NAME="testsocialnetwork" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial
>     ----- export WEBSITE_URL="www.testsocialnetwork.org.uk"  #MANDATORY
>     export APPLICATION_REPOSITORY_PROVIDER="github" #MANDATORY
>     ----- export APPLICATION_REPOSITORY_OWNER="githusername" #MANDATORY
>     ----- export APPLICATION_REPOSITORY_USERNAME="gutusername" #MANDATORY
>     export APPLICATION_REPOSITORY_PASSWORD="" #MANDATORY
>     ----- export APPLICATION_REPOSITORY_TOKEN="gitpersonalaccesstoken" #MANDATORY
>     export SYSTEM_EMAIL_PROVIDER="" #MANDATORY
>     export SYSTEM_TOEMAIL_ADDRESS="" #MANDATORY
>     export SYSTEM_FROMEMAIL_ADDRESS="" #MANDATORY
>     export SYSTEM_EMAIL_USERNAME="" #MANDATORY
>     export SYSTEM_EMAIL_PASSWORD="" #MANDATORY
>     export DIRECTORIES_TO_MOUNT="" #This should always be unset for a virgin deployments
>     export DB_PORT="2035"
>     export SSH_PORT="1035"
>     export GATEWAY_GUARDIAN="0"
>     export PRODUCTION="0"
>     export DEVELOPMENT="1"
>     export BUILD_CHOICE="0"
>     ----- export WEBSERVER_CHOICE="NGINX"
>     export NO_AUTOSCALERS="1"
>     export NUMBER_WS="1"
>     export SUPERSAFE_WEBROOT="1"
>     export SUPERSAFE_DB="1"
>     ----- export DATABASE_INSTALLATION_TYPE="Postgres"
>     export PERSIST_ASSETS_TO_CLOUD="0" #This should always be set to 0 for a virgin deployment
>     export DISABLE_HOURLY="0"
>     export SERVER_TIMEZONE_CONTINENT="Europe"
>     export SERVER_TIMEZONE_CITY="London"
>     export BASELINE_DB_REPOSITORY="VIRGIN"
>     export BUILD_ARCHIVE_CHOICE="virgin"
>     export APPLICATION_LANGUAGE="PHP"
>     ----- export APPLICATION_IDENTIFIER="1"
>     export PHP_VERSION="8.0"
>     export REGION=""
>     export REGION_ID="eu-central"
>     export DB_SIZE="g6-nanode-1"
>     export DB_SERVER_TYPE="g6-nanode-1"
>     export WS_SIZE="g6-nanode-1"
>     export WS_SERVER_TYPE="g6-nanode-1"
>     export AS_SIZE="g6-nanode-1"
>     export AS_SERVER_TYPE="g6-nanode-1"
>     export CLOUDHOST="linode"
>     export MACHINE_TYPE="LINODE"
>     export ALGORITHM="rsa"
>     export USER="root"
>     export CLOUDHOST_USERNAME="root"
>     export CLOUDHOST_PASSWORD=""
>     export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"
>     export PREVIOUS_BUILD_CONFIG="0"
>     export GIT_USER="Templated User"
>     export GIT_EMAIL_ADDRESS="templateduser@dummyemailZ123.com"
>     export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"
>     export INFRASTRUCTURE_REPOSITORY_OWNER="agile-deployer"
>     export INFRASTRUCTURE_REPOSITORY_USERNAME="agile-deployer"
>     export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"
>     export DATASTORE_CHOICE="linode"
>     export SSL_GENERATION_METHOD="AUTOMATIC"
>     export SSL_GENERATION_SERVICE="LETSENCRYPT"
>     export BYPASS_DB_LAYER="0"
>     export DBaaS_HOSTNAME=""
>     export DBaaS_USERNAME=""
>     export DBaaS_PASSWORD=""
>     export DBaaS_DBNAME=""
>     export DATABASE_DBaaS_INSTALLATION_TYPE=""
>     export DBaaSDBSECURITYGROUP=""
>     export DBIP=""
>     export DBIP_PRIVATE=""
>     export WSIP=""
>     export WSIP_PRIVATE=""
>     export ASIP=""
>     export ASIP_PRIVATE=""
>     export APPLICATION_NAME=""
>     export MAPS_API_KEY=""
>     export PHP_MODE=""
>     export PHP_MAX_CHILDREN=""
>     export PHP_START_SERVERS=""
>     export PHP_MIN_SPARE_SERVERS=""
>     export PHP_MAX_SPARE_SERVERS=""
>     export PHP_PROCESS_IDLE_TIMEOUT=""
>     export IN_MEMORY_CACHING=""
>     export IN_MEMORY_CACHING_PORT=""
>     export IN_MEMORY_CACHING_HOST=""
>     export IN_MEMORY_CACHING_SECURITY_GROUP=""
>     export ENABLE_EFS=""
>     export SUBNET_ID=""
>     export AUTOSCALE_FROM_SNAPSHOTS=""
>     export GENERATE_SNAPSHOTS=""
>     export SNAPSHOT_ID=""
>     export WEBSERVER_IMAGE_ID=""
>     export AUTOSCALER_IMAGE_ID=""
>     export DATABASE_IMAGE_ID=""
>     export BUILD_HOME=""
>     export BUILD_CLIENT_IP=""
>     export PUBLIC_KEY_ID=""

If all the dashes I have added are removed, then this file (with live values and not symbolic ones) would be ready for deployment.

-----------------------------

You should now be at a point where your build machine is running and configured ready to deploy Joomla in a virgin (or uncustomised) configuration. I will show you what this will likely look like in a video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/XI3z8cScN48" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---------------------------

Assuming that you have your Joomla application online now after following that video, what I would do if I wanted to build a Wordpress, Moodle or Drupal installation would be to follow the same procedure with the same template, but, minimally change the template as follows:

#### For Wordpress:

>     export APPLICATION="wordpress"
>     export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="WORDPRESS" #MANDATORY 
>     export APPLICATION_IDENTIFIER="2"
>     export DATABASE_INSTALLATION_TYPE="MySQL" #I don't support Wordpress using Postgres

#### For Drupal:

>     export APPLICATION="drupal"
>     export DRUPAL_VERSION="9.2.6" 
>     export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="DRUPAL:9.2.6" #MANDATORY 
>     export APPLICATION_IDENTIFIER="3"

#### For Moodle:

>     export APPLICATION="moodle"
>     export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="MOODLE" #MANDATORY 
>     export APPLICATION_IDENTIFIER="4"

So, you have a template now that you can use over and over again for deploying different installations of these CMS systems. You can study the spec and learn how to modify the template in order to change machine sizes, regions, PHP settings and so on. 
