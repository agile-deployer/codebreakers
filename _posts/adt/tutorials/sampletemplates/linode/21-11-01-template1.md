---
layout: post
description: The Agile Deployment Toolkit Tutorials
title: Template 1
permalink: /linodetemplate1/
hide: true
category: agiledeploymenttoolkit
---

**This file is at: /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/linode/linode1.tmpl on my build machine**  
**This is how your template should look (obviously with your own values if you are making a virgin deployment of a CMS, in this case Joomla, on the Linode provider)** 

export APPLICATION="joomla"  #MANDATORY  
export LINODEACCOUNT_USERNAME="user123" #MANDATORY  
export JOOMLA_VERSION="4.1.2" #MANDATORY - change this to the version you want to deploy, for example 4.0.3 set it to "" if you are deploying anything but joomla  
export DRUPAL_VERSION=""  #MANDATORY - change this to the version you want to deploy, for example, 9.2.6 set it to "" if you are deploying anything but drupal  
export APPLICATION_IDENTIFIER="1" #MANDATORY - 1 for joomla, 2 for wordpress, 3 for drupal, 4 for moodle  
export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="JOOMLA:4.1.2" #MANDATORY  
export CLOUDHOST_USERNAME="root"  
export CLOUDHOST_PASSWORD="denrn3refjecner" #MANDATORY  
export S3_ACCESS_KEY="SHhfbSHSYHybfybDHhbSJjJD"  #MANDATORY  
export S3_SECRET_KEY="dnwjndjchedu3d3unecjwsjSJbdebdeuejndeubn"  #MANDATORY  
export S3_HOST_BASE="eu-central-1.linodeobjects.com" #MANDATORY  
export S3_LOCATION="US" #For linode, this always needs to be set to "US"  
export TOKEN="jbdcjdjcbdecuecu3edi2kwdnswmnueuefujbnecnbwcb3uewdjubnewc" #MANDATORY this is your linode personal access token  
export ACCESS_KEY=""   #NOT REQUIRED  
export SECRET_KEY=""   #NOT REQUIRED  
export DNS_USERNAME="you@cloudflareemail.tld"  #MANDATORY - the email address you registered for cloudflare with  
export DNS_SECURITY_KEY="iwdnij3f9un34fijnwdjvkneijvn"   #MANDATORY  
export DNS_CHOICE="cloudflare" #MANDATORY - you will need to set your DNS nameservers according to this choice  
export CLOUDHOST_EMAIL_ADDRESS="you@cloudhost.tld" #MANDATORY - the email address you registered for linode with  
export BUILDOS="ubuntu" #MANDATORY one of ubuntu|debian  
export BUILDOS_VERSION="22.04" #MANDATORY one of 20.04 22.04|10 11  
export DEFAULT_USER="root" #MANDATORY - This should always be 'root' on linode  
export BUILD_IDENTIFIER="nuocial" #MANDATORY  
export WEBSITE_DISPLAY_NAME="Nuocial" #MANDATORY  
export WEBSITE_NAME="nuocial" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial  
export WEBSITE_URL="demo.nuocial.org.uk"  #MANDATORY  
export APPLICATION_REPOSITORY_PROVIDER="github" #MANDATORY  
export APPLICATION_REPOSITORY_OWNER="adt-demos" #MANDATORY  
export APPLICATION_REPOSITORY_USERNAME="adt-demos" #MANDATORY  
export APPLICATION_REPOSITORY_PASSWORD="" #MANDATORY  
export APPLICATION_REPOSITORY_TOKEN="ghp_nedvuerf913rfiunwervijnwviunerv" #MANDATORY  
export SYSTEM_EMAIL_PROVIDER="3" #MANDATORY 3=AWS-SES  
export SYSTEM_TOEMAIL_ADDRESS="webmaster@nuocial.org.uk" #MANDATORY  
export SYSTEM_FROMEMAIL_ADDRESS="webmaster@nuocial.org.uk" #MANDATORY  
export SYSTEM_EMAIL_USERNAME="SJDJJNJNSJFUJ93eriefdiniDJND" #MANDATORY - AWS SES USERNAME  
export SYSTEM_EMAIL_PASSWORD="jnwdcionwdfoinwe9finweofin2irj2oriwekfjuhfp2ef2kmf" #MANDATORY AWS SES PASSWORD  
export DIRECTORIES_TO_MOUNT="" #This should always be unset for a virgin deployments  
export DB_PORT="2035"  
export SSH_PORT="1035"  
export GATEWAY_GUARDIAN="0"  
export PRODUCTION="0"  
export DEVELOPMENT="1"  
export BUILD_CHOICE="0"  
export WEBSERVER_CHOICE="APACHE"  
export NO_AUTOSCALERS="1"  
export NUMBER_WS="1"  
export SUPERSAFE_WEBROOT="1"  
export SUPERSAFE_DB="1"  
export DATABASE_INSTALLATION_TYPE="MySQL"   
export PERSIST_ASSETS_TO_CLOUD="0" #This should always be set to 0 for a virgin deployment  
export DISABLE_HOURLY="0"  
export SERVER_TIMEZONE_CONTINENT="Europe"  
export SERVER_TIMEZONE_CITY="London"  
export BASELINE_DB_REPOSITORY="VIRGIN"  
export BUILD_ARCHIVE_CHOICE="virgin"  
export APPLICATION_LANGUAGE="PHP"  
export PHP_VERSION="8.0"  
export REGION=""   
export REGION_ID="eu-central"  
export DB_SIZE="g6-nanode-1"  
export DB_SERVER_TYPE="g6-nanode-1"  
export WS_SIZE="g6-nanode-1"  
export WS_SERVER_TYPE="g6-nanode-1"  
export AS_SIZE="g6-nanode-1"  
export AS_SERVER_TYPE="g6-nanode-1"  
export CLOUDHOST="linode"  
export MACHINE_TYPE="LINODE"  
export ALGORITHM="rsa"  
export USER="root"  
export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"  
export PREVIOUS_BUILD_CONFIG="0"  
export GIT_USER="Templated User"  
export GIT_EMAIL_ADDRESS="templateduser@dummyemailZ123.com"  
export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"  
export INFRASTRUCTURE_REPOSITORY_OWNER="agile-deployer"  
export INFRASTRUCTURE_REPOSITORY_USERNAME="agile-deployer"  
export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"  
export DATASTORE_CHOICE="linode"  
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
export BUILD_HOME=""  
export BUILD_CLIENT_IP=""  
export PUBLIC_KEY_ID=""  
