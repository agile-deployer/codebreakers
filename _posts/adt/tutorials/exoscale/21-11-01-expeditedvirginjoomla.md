---
layout: post
description: The Agile Deployment Toolkit Exoscale Tutorials Expedited Virgin Joomla 
title: Exoscale ADT Tutorials Expedited Virgin Joomla
permalink: /adtexoscaletutorialsexpeditedvirginjoomla/
hide: true
category: agiledeploymenttoolkit
---

If you have followed these steps your build machine is online and secured and you have an SSH session open to it from your laptop through which to initiate your build processes.

We need several pieces of information from our cloud host and 3rd party services for a successful build to be possible:

I am going to use the example of joomla to build from and so this example will build a virgin installation of the latest version of joomla

To find the latest version of Joomla, I go to this URL in my browser:

https://downloads.joomla.org/

And I note the latest version in a separate text file:

joomla_version="4.0.4"

I then need a set of compute access keys so, I go to the IAM option on my exoscale dashboard and generate an IAM key with compute access. In my separate text file, I record:

exoscale_access_key_compute="XXXXX"  where XXXXX and YYYYY are the actual values generated when I click "Add Key"
exoscale_secret_key_compute="YYYYY"

I then need a set of Object Storage (S3) access keys so, I go to the IAM option on my exoscale dashboard and generate an IAM key with S3 access. In my separate text file, I record:

exoscale_access_key_s3="AAAAA"  where AAAAA and BBBBB are the actual values generated when I click "Add Key"
exoscale_secret_key_s3="BBBBB"


I then need a set of DNS access keys so, I go to the IAM option on my exoscale dashboard and generate an IAM key with DNS access. In my separate text file, I record:

exoscale_access_key_dns="CCCCC"  where CCCCC and DDDDD are the actual values generated when I click "Add Key"
exoscale_secret_key_dns="DDDDD"

You now need to make a note of the email address that you have registered with your exoscale account:

exoscale_email="testemail@testemail.com"

You then need the url that you want to use for your website. If you don't have a DNS URL for your website, you need to purchase one and set the nameservers to exoscale as described [here](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/Nameservers.md)

exoscale_dns_name="www.testsocialnetwork.org.uk"

You then need the username and owner of you gitprovider application repositories.
To do this, if you don't have a git account sign up with one (in this case using github, but, you have the choice of bitbucket and gitlab as well) and record the username that you sign up with:

gitusername="mytestgituser"

Then create a "personal access token" by following: 

[Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) making sure you give it all "repo" permissions

gitpersonalaccesstoken="KKKKK" where KKKKK represents your actual personal access token

To keep this as simple as possible, I have missed out the SMTP credentials, but, you can find out more about them [here](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/DeployingSMTPService.md)

So, that should be all the core credentials that I need to make a deployment. I can save my text file now (and keep it secure) because I might want to use these credentials again for other deployments or redeployments. 

--------------------------------------------

So, at the command line of my build machine that we spun up earlier:

My chosen username is "agile-deployer"

So, to begin an expedited build process, I need to:

cd /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale

Then we can open up the 

vi exoscale1.tmpl

This file looks like this (I have put a dashes before each line I wish to modify for this deployment which is for illustrative purposes only):

###############################################################################################
# Refer to: ${BUILD_HOME}/templatedconfigurations/specification.md
###############################################################################################
------export APPLICATION=""
export JOOMLA_VERSION="" #MANDATORY - change this to the version you want to deploy, for example 4.0.3 set it to "" if you are deploying anything but joomla
export DRUPAL_VERSION=""  #MANDATORY - change this to the version you want to deploy, for example, 9.2.6 set it to "" if you are deploying anything but drupal
------export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="" #MANDATORY 
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
# change this to, for example, JOOMLA:4.0.3 if you are deploying drupal (APPLICATION=joomla)
# change this to, WORDPRESS if you are deploying wordpress
# change this to, for example, DRUPAL:9.2.6 if you are deploying drupal (APPLICATION=drupal)
# change this to, MOODLE if you are deploying moodle
#############################################################################################
------export S3_ACCESS_KEY=""  #MANDATORY
------export S3_SECRET_KEY=""  #MANDATORY
export S3_HOST_BASE="sos-ch-gva-2.exo.io" #MANDATORY
export S3_LOCATION="US" #For exoscale, this always needs to be set to "US"
export TOKEN="" #NOT REQUIRED
------export ACCESS_KEY=""   #MANDATORY
------export SECRET_KEY=""   #MANDATORY
------export DNS_USERNAME=""  #MANDATORY
------export DNS_SECURITY_KEY=""   #MANDATORY - This is your access key and your secret key, written: DNS_SECURITY_KEY="${ACCESS_KEY}:${SECRET_KEY}"
export DNS_CHOICE="exoscale" #MANDATORY - you will need to set your DNS nameservers according to this choice
------export CLOUDHOST_EMAIL_ADDRESS="" #MANDATORY
export BUILDOS="debian" #MANDATORY one of ubuntu|debian
export BUILDOS_VERSION="11" #MANDATORY one of 20.04|10 11
export DEFAULT_USER="debian" #MANDATORY - - This must be "ubuntu" if you are deploying ubuntu and "debian" if you are deploying debian
------export WEBSITE_DISPLAY_NAME="" #MANDATORY
------export WEBSITE_NAME="" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial
------export WEBSITE_URL=""  #MANDATORY
export APPLICATION_REPOSITORY_PROVIDER="github" #MANDATORY
------export APPLICATION_REPOSITORY_OWNER="" #MANDATORY
------export APPLICATION_REPOSITORY_USERNAME="" #MANDATORY
export APPLICATION_REPOSITORY_PASSWORD="" #MANDATORY
------export APPLICATION_REPOSITORY_TOKEN="" #MANDATORY
export SYSTEM_EMAIL_PROVIDER="" #MANDATORY
export SYSTEM_TOEMAIL_ADDRESS="" #MANDATORY
export SYSTEM_FROMEMAIL_ADDRESS="" #MANDATORY
export SYSTEM_EMAIL_USERNAME="" #MANDATORY
export SYSTEM_EMAIL_PASSWORD="" #MANDATORY
export DIRECTORIES_TO_MOUNT="" #This should always be unset for a virgin deployments
export DB_PORT="2035"
export SSH_PORT="1035"
export GATEWAY_GUARDIAN="0"
export PRODUCTION="0"
export DEVELOPMENT="1"
export BUILD_CHOICE="0"
------export WEBSERVER_CHOICE="APACHE"
export NO_AUTOSCALERS="1"
export NUMBER_WS="1"
export SUPERSAFE_WEBROOT="1"
export SUPERSAFE_DB="1"
------export DATABASE_INSTALLATION_TYPE="MySQL"
export PERSIST_ASSETS_TO_CLOUD="0" #This should always be set to 0 for a virgin deployment
export DISABLE_HOURLY="0"
export SERVER_TIMEZONE_CONTINENT="Europe"
export SERVER_TIMEZONE_CITY="London"
export BASELINE_DB_REPOSITORY="VIRGIN"
export BUILD_ARCHIVE_CHOICE="virgin"
export APPLICATION_LANGUAGE="PHP"
------export APPLICATION_IDENTIFIER="3"
------export PHP_VERSION="7.4"
export REGION=""
export REGION_ID="1128bd56-b4d9-4ac6-a7b9-c715b187ce11"
export DB_SIZE="10G"
export DB_SERVER_TYPE="b6cd1ff5-3a2f-4e9d-a4d1-8988c1191fe8"
export WS_SIZE="10G"
export WS_SERVER_TYPE="b6cd1ff5-3a2f-4e9d-a4d1-8988c1191fe8"
export AS_SIZE="10G"
export AS_SERVER_TYPE="b6cd1ff5-3a2f-4e9d-a4d1-8988c1191fe8"
export CLOUDHOST="exoscale"
export MACHINE_TYPE="EXOSCALE"
export ALGORITHM="rsa"
export USER="root"
export CLOUDHOST_USERNAME="root"
export CLOUDHOST_PASSWORD=""
export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"
export PREVIOUS_BUILD_CONFIG="0"
export GIT_USER="Templated User"
export GIT_EMAIL_ADDRESS="templateduser@dummyemailZ123.com"
export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"
export INFRASTRUCTURE_REPOSITORY_OWNER="agile-deployer"
export INFRASTRUCTURE_REPOSITORY_USERNAME="agile-deployer"
export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"
export DATASTORE_CHOICE="exoscale"
export SSL_GENERATION_METHOD="AUTOMATIC"
export SSL_GENERATION_SERVICE="LETSENCRYPT"
export BYPASS_DB_LAYER="0"
export DBaaS_HOSTNAME=""
export DBaaS_USERNAME=""
export DBaaS_PASSWORD=""
export DBaaS_DBNAME=""
export DATABASE_DBaaS_INSTALLATION_TYPE=""
export DBaaSDBSECURITYGROUP=""
export DBIP=""
export DBIP_PRIVATE=""
export WSIP=""
export WSIP_PRIVATE=""
export ASIP=""
export ASIP_PRIVATE=""
export APPLICATION_NAME=""
export MAPS_API_KEY=""
export PHP_MODE=""
export PHP_MAX_CHILDREN=""
export PHP_START_SERVERS=""
export PHP_MIN_SPARE_SERVERS=""
export PHP_MAX_SPARE_SERVERS=""
export PHP_PROCESS_IDLE_TIMEOUT=""
export IN_MEMORY_CACHING=""
export IN_MEMORY_CACHING_PORT=""
export IN_MEMORY_CACHING_HOST=""
export IN_MEMORY_CACHING_SECURITY_GROUP=""
export ENABLE_EFS=""
export SUBNET_ID=""
export AUTOSCALE_FROM_SNAPSHOTS=""
export GENERATE_SNAPSHOTS=""
export SNAPSHOT_ID=""
export WEBSERVER_IMAGE_ID=""
export AUTOSCALER_IMAGE_ID=""
export DATABASE_IMAGE_ID=""
export BUILD_HOME="/home/agile-deployer/agile-infrastructure-build-client-scripts"
export BUILD_CLIENT_IP="185.19.29.134"
export BUILD_IDENTIFIER="nuocial"
export PUBLIC_KEY_ID="AGILE_TOOLKIT_PUBLIC_KEY-nuocial"


So, I have referred to the specification and I have freely chosen to modify the WEBSERVER_CHOICE to "NGINX" PHP_VERSION to "8.0" APPLICATION_IDENTIFIER to "1" and DATABASE_INSTALLATION_TYPE to "Postgres"

So, editing /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/exoscale/exoscale1.tmpl and using the values I recorded in my text file earlier, I modify the file as follows, the lines beginning with dashes have been modified


###############################################################################################
# Refer to: ${BUILD_HOME}/templatedconfigurations/specification.md
###############################################################################################
------export APPLICATION="joomla"
export JOOMLA_VERSION="" #MANDATORY - change this to the version you want to deploy, for example 4.0.3 set it to "" if you are deploying anything but joomla
export DRUPAL_VERSION=""  #MANDATORY - change this to the version you want to deploy, for example, 9.2.6 set it to "" if you are deploying anything but drupal
------export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="JOOMLA:4.0.4" #MANDATORY 
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
# change this to, for example, JOOMLA:4.0.3 if you are deploying drupal (APPLICATION=joomla)
# change this to, WORDPRESS if you are deploying wordpress
# change this to, for example, DRUPAL:9.2.6 if you are deploying drupal (APPLICATION=drupal)
# change this to, MOODLE if you are deploying moodle
#############################################################################################
------export S3_ACCESS_KEY="AAAAA"  #MANDATORY
------export S3_SECRET_KEY="BBBBB"  #MANDATORY
export S3_HOST_BASE="sos-ch-gva-2.exo.io" #MANDATORY
export S3_LOCATION="US" #For exoscale, this always needs to be set to "US"
export TOKEN="" #NOT REQUIRED
------export ACCESS_KEY="XXXXX"   #MANDATORY
------export SECRET_KEY="YYYYY"   #MANDATORY
------export DNS_USERNAME="testemail@testemail.com"  #MANDATORY
------export DNS_SECURITY_KEY="CCCCC:DDDDD"   #MANDATORY - This is your access key and your secret key, written: DNS_SECURITY_KEY="${ACCESS_KEY}:${SECRET_KEY}"
export DNS_CHOICE="exoscale" #MANDATORY - you will need to set your DNS nameservers according to this choice
------export CLOUDHOST_EMAIL_ADDRESS="testemail@testemail.com" #MANDATORY
export BUILDOS="debian" #MANDATORY one of ubuntu|debian
export BUILDOS_VERSION="11" #MANDATORY one of 20.04|10 11
export DEFAULT_USER="debian" #MANDATORY - - This must be "ubuntu" if you are deploying ubuntu and "debian" if you are deploying debian
------export WEBSITE_DISPLAY_NAME="Test Social Network" #MANDATORY
------export WEBSITE_NAME="testsocialnetwork" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial
------export WEBSITE_URL="www.testsocialnetwork.org.uk"  #MANDATORY
export APPLICATION_REPOSITORY_PROVIDER="github" #MANDATORY
------export APPLICATION_REPOSITORY_OWNER="mytestgituser" #MANDATORY
------export APPLICATION_REPOSITORY_USERNAME="mytestgituser" #MANDATORY
export APPLICATION_REPOSITORY_PASSWORD="" #MANDATORY
------export APPLICATION_REPOSITORY_TOKEN="KKKKK" #MANDATORY
export SYSTEM_EMAIL_PROVIDER="" #MANDATORY
export SYSTEM_TOEMAIL_ADDRESS="" #MANDATORY
export SYSTEM_FROMEMAIL_ADDRESS="" #MANDATORY
export SYSTEM_EMAIL_USERNAME="" #MANDATORY
export SYSTEM_EMAIL_PASSWORD="" #MANDATORY
export DIRECTORIES_TO_MOUNT="" #This should always be unset for a virgin deployments
export DB_PORT="2035"
export SSH_PORT="1035"
export GATEWAY_GUARDIAN="0"
export PRODUCTION="0"
export DEVELOPMENT="1"
export BUILD_CHOICE="0"
------export WEBSERVER_CHOICE="NGINX"
export NO_AUTOSCALERS="1"
export NUMBER_WS="1"
export SUPERSAFE_WEBROOT="1"
export SUPERSAFE_DB="1"
------export DATABASE_INSTALLATION_TYPE="Postgres"
export PERSIST_ASSETS_TO_CLOUD="0" #This should always be set to 0 for a virgin deployment
export DISABLE_HOURLY="0"
export SERVER_TIMEZONE_CONTINENT="Europe"
export SERVER_TIMEZONE_CITY="London"
export BASELINE_DB_REPOSITORY="VIRGIN"
export BUILD_ARCHIVE_CHOICE="virgin"
export APPLICATION_LANGUAGE="PHP"
------export APPLICATION_IDENTIFIER="1"
------export PHP_VERSION="8.0"
export REGION=""
export REGION_ID="1128bd56-b4d9-4ac6-a7b9-c715b187ce11"
export DB_SIZE="10G"
export DB_SERVER_TYPE="b6cd1ff5-3a2f-4e9d-a4d1-8988c1191fe8"
export WS_SIZE="10G"
export WS_SERVER_TYPE="b6cd1ff5-3a2f-4e9d-a4d1-8988c1191fe8"
export AS_SIZE="10G"
export AS_SERVER_TYPE="b6cd1ff5-3a2f-4e9d-a4d1-8988c1191fe8"
export CLOUDHOST="exoscale"
export MACHINE_TYPE="EXOSCALE"
export ALGORITHM="rsa"
export USER="root"
export CLOUDHOST_USERNAME="root"
export CLOUDHOST_PASSWORD=""
export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"
export PREVIOUS_BUILD_CONFIG="0"
export GIT_USER="Templated User"
export GIT_EMAIL_ADDRESS="templateduser@dummyemailZ123.com"
export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"
export INFRASTRUCTURE_REPOSITORY_OWNER="agile-deployer"
export INFRASTRUCTURE_REPOSITORY_USERNAME="agile-deployer"
export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"
export DATASTORE_CHOICE="exoscale"
export SSL_GENERATION_METHOD="AUTOMATIC"
export SSL_GENERATION_SERVICE="LETSENCRYPT"
export BYPASS_DB_LAYER="0"
export DBaaS_HOSTNAME=""
export DBaaS_USERNAME=""
export DBaaS_PASSWORD=""
export DBaaS_DBNAME=""
export DATABASE_DBaaS_INSTALLATION_TYPE=""
export DBaaSDBSECURITYGROUP=""
export DBIP=""
export DBIP_PRIVATE=""
export WSIP=""
export WSIP_PRIVATE=""
export ASIP=""
export ASIP_PRIVATE=""
export APPLICATION_NAME=""
export MAPS_API_KEY=""
export PHP_MODE=""
export PHP_MAX_CHILDREN=""
export PHP_START_SERVERS=""
export PHP_MIN_SPARE_SERVERS=""
export PHP_MAX_SPARE_SERVERS=""
export PHP_PROCESS_IDLE_TIMEOUT=""
export IN_MEMORY_CACHING=""
export IN_MEMORY_CACHING_PORT=""
export IN_MEMORY_CACHING_HOST=""
export IN_MEMORY_CACHING_SECURITY_GROUP=""
export ENABLE_EFS=""
export SUBNET_ID=""
export AUTOSCALE_FROM_SNAPSHOTS=""
export GENERATE_SNAPSHOTS=""
export SNAPSHOT_ID=""
export WEBSERVER_IMAGE_ID=""
export AUTOSCALER_IMAGE_ID=""
export DATABASE_IMAGE_ID=""
export BUILD_HOME="/home/agile-deployer/agile-infrastructure-build-client-scripts"
export BUILD_CLIENT_IP="185.19.29.134"
export BUILD_IDENTIFIER="nuocial"
export PUBLIC_KEY_ID="AGILE_TOOLKIT_PUBLIC_KEY-nuocial"

If all the dashes I have added are removed, then this file (with live values and not symbolic ones) would be ready for deployment.

I will record a short video to show how the deployment is made:
