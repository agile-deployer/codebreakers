---
layout: post
description: The Agile Deployment Toolkit Tutorials
title: Template 3
permalink: /vultrtemplate3/
hide: true
category: agiledeploymenttoolkit
---

**This file is at: /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/vultr/vultr3.tmpl on my build machine**  
**This is how your template should look (obviously with your own values if you are making a temporal deployment of a CMS, in this case Joomla, on the Vultr provider)**

export APPLICATION="wordpress" #MANDATORY joomla, wordpress, drupal or moodle  
export BUILD_CHOICE="2" #MANDATORY 2=hourly, 3=daily, 4=weekly, 5=monthly, 6=bimonthly  
export BUILD_ARCHIVE_CHOICE="hourly" #MANDATORY hourly, daily, weekly, monthly, bimonthly  
export PERSIST_ASSETS_TO_CLOUD="2" #MANDATORY    
export APPLICATION_IDENTIFIER="2" #MANDATORY - 1 for joomla, 2 for wordpress, 3 for drupal, 4 for moodle  
export DIRECTORIES_TO_MOUNT="wp-content.uploads" #MANDATORY The directories of dynamic assets in your webroot that will be stored in S3  
export S3_ACCESS_KEY="jnsdjnefjnwefijnwefojnweflnwef"  #MANDATORY  
export S3_SECRET_KEY="23eo2eonwefoinewrfoin2eoin23roi23rpim23oknwefon"  #MANDATORY  
export S3_HOST_BASE="ewr1.vultrobjects.com" #MANDATORY  
export S3_LOCATION="US" #For vultr, this always needs to be set to "US"  
export TOKEN="ojnwefijn23roin243foin23ofn2eofin2eofn2eofinoin2fon" #MANDATORY this is your vultr personal access token  
export ACCESS_KEY=""   #NOT REQUIRED  
export SECRET_KEY=""   #NOT REQUIRED  
export DNS_USERNAME="you@cloudflaremail.tld"  #MANDATORY - the email address you registered for cloudflare with  
export DNS_SECURITY_KEY="ownmefoin3foin32efoip2efoin243rgonron2epi"   #MANDATORY  
export DNS_CHOICE="cloudflare" #MANDATORY - you will need to set your DNS nameservers according to this choice  
export CLOUDHOST_EMAIL_ADDRESS="you@cloudhost.tld" #MANDATORY - the email address you registered for your cloudhost with  
export BUILDOS="debian" #MANDATORY one of ubuntu|debian  
export BUILDOS_VERSION="11" #MANDATORY one of 20.04 22.04|10 11  
export DEFAULT_USER="root" #MANDATORY - This should always be 'root' on vultr  
export BUILD_IDENTIFIER="nuocial" #MANDATORY  
export WEBSITE_DISPLAY_NAME="Nuocial" #MANDATORY  
export WEBSITE_NAME="nuocial" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial  
export WEBSITE_URL="demo.nuocial.org.uk"  #MANDATORY  
export APPLICATION_REPOSITORY_PROVIDER="github" #MANDATORY Make sure these 5 settings match where your backups is stored with your git provider  
export APPLICATION_REPOSITORY_OWNER="adt-demos" #MANDATORY  
export APPLICATION_REPOSITORY_USERNAME="adt-demos" #MANDATORY  
export APPLICATION_REPOSITORY_PASSWORD="none" #MANDATORY   
export APPLICATION_REPOSITORY_TOKEN="ghp_wiejnfwiefnwiuenfijnwefkn" #MANDATORY  
export SYSTEM_EMAIL_PROVIDER="3" #MANDATORY AWS SES  
export SYSTEM_TOEMAIL_ADDRESS="webmaster@nuocial.org.uk" #MANDATORY  
export SYSTEM_FROMEMAIL_ADDRESS="webmaster@nuocial.org.uk" #MANDATORY  
export SYSTEM_EMAIL_USERNAME="oinwjefonef9unwefijnqdijnqwd" #MANDATORY  
export SYSTEM_EMAIL_PASSWORD="iwnefijnwefiun2efiun2qdfoiqwwofinwoefnonwefinefin" #MANDATORY  
export SERVER_TIMEZONE_CONTINENT="Europe"  
export SERVER_TIMEZONE_CITY="London"  
export PRODUCTION="1"  
export DEVELOPMENT="0"  
export SUPERSAFE_WEBROOT="1"  
export WEBSERVER_CHOICE="NGINX"  
export NO_AUTOSCALERS="1"  
export NUMBER_WS="2"  
export SUPERSAFE_DB="1"  
export DISABLE_HOURLY="0"  
export DATABASE_INSTALLATION_TYPE="MySQL"  
export DB_PORT="2035"  
export SSH_PORT="1035"  
export GATEWAY_GUARDIAN="0"  
export BASELINE_DB_REPOSITORY=""  
export APPLICATION_BASELINE_SOURCECODE_REPOSITORY=""  
export APPLICATION_LANGUAGE="PHP"  
export PHP_VERSION="8.0"  
export REGION=""  
export REGION_ID="lhr"  
export DB_SIZE="vc2-1c-1gb"  
export DB_SERVER_TYPE="vc2-1c-1gb"  
export WS_SIZE="vc2-1c-1gb"  
export WS_SERVER_TYPE="vc2-1c-1gb"  
export AS_SIZE="vc2-1c-1gb"  
export AS_SERVER_TYPE="vc2-1c-1gb"  
export CLOUDHOST="vultr"  
export MACHINE_TYPE="VULTR"  
export ALGORITHM="rsa"  
export USER="root"  
export CLOUDHOST_USERNAME="root"  
export CLOUDHOST_PASSWORD=""  
export PREVIOUS_BUILD_CONFIG="0"  
export GIT_USER="Templated User"  
export GIT_EMAIL_ADDRESS="templateduser@dummyemailX123.com"  
export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"  
export INFRASTRUCTURE_REPOSITORY_OWNER="agile-deployer"  
export INFRASTRUCTURE_REPOSITORY_USERNAME="agile-deployer"  
export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"  
export DATASTORE_CHOICE="vultr"  
export SSL_GENERATION_METHOD="AUTOMATIC"  
export SSL_GENERATION_SERVICE="LETSENCRYPT"  
export BYPASS_DB_LAYER="0"  
export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"  
export DBaaS_HOSTNAME=""  
export DBaaS_USERNAME=""  
export DBaaS_PASSWORD=""  
export DBaaS_DBNAME=""  
export DATABASE_DBaaS_INSTALLATION_TYPE=""  
export DBaaSDBSECURITYGROUP=""  
export WSIP=""  
export WSIP_PRIVATE=""  
export DBIP=""  
export DBIP_PRIVATE=""  
export ASIP=""  
export ASIP_PRIVATE=""  
export APPLICATION_NAME="WORDY DEMO APPLICATION"  
export DNS_REGION=""  
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
export ASSETS_BUCKET=""  
export JOOMLA_VERSION=""   
export DRUPAL_VERSION=""  
export BUILD_HOME=""  
export BUILD_CLIENT_IP=""  
export PUBLIC_KEY_ID=""   
