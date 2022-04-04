---
layout: post
description: The Agile Deployment Toolkit Tutorials
title: Tutorials
permalink: /awstemplate2/
hide: true
category: agiledeploymenttoolkit
---

**This file is at: /home/agile-deployer/agile-infrastructure-build-client-scripts/templatedconfigurations/templates/aws/aws2.tmpl on my build machine**  
**This is how your template should look (obviously with your own values if you are making a virgin deployment of a CMS, in this case Joomla, on the AWS provider)**   

-----------------------

export APPLICATION="wordpress" #MANDATORY (joomla or wordpress or drupal or moodle)  
export APPLICATION_IDENTIFIER="2" #MANDATORY (1 for joomla, 2 for wordpress, 3 for drupal, 4 for moodle)  
export BASELINE_DB_REPOSITORY="wordydemo-db-baseline" #MANDATORY  
export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="wordydemo-webroot-sourcecode-baseline" #MANDATORY  
export PERSIST_ASSETS_TO_CLOUD="2" #MANDATORY   
export DIRECTORIES_TO_MOUNT="wp-content.uploads" #MANDATORY - this will define which directories in your webroot will be mounted from S3, if PERSIST_ASSETS_TO_CLOUD=1  
export APPLICATION_REPOSITORY_PROVIDER="github" #MANDATORY  MAKE SURE THESE 5 APPLICATION_* settings are correct for where your application repositories are.  
export APPLICATION_REPOSITORY_OWNER="adt-demos" #MANDATORY  
export APPLICATION_REPOSITORY_USERNAME="adt-demos" #MANDATORY  
export APPLICATION_REPOSITORY_PASSWORD="none" #MANDATORY  
export APPLICATION_REPOSITORY_TOKEN="ghp_ijwnefijnweifjnweifjnwefijnweon" #MANDATORY  
export S3_ACCESS_KEY="WWJijnwcdonwdcojnerojn"  #MANDATORY  
export S3_SECRET_KEY="kwndcojnwefonwefonwefonwefoknweofkm2eofkmokme"  #MANDATORY  
export S3_HOST_BASE="s3.eu-west-1.amazonaws.com" #MANDATORY  
export S3_LOCATION="EU" #MANDATORY  
export TOKEN="" #NOT REQUIRED  
export ACCESS_KEY="WWJijnwcdonwdcojnerojn"   #MANDATORY  
export SECRET_KEY="kwndcojnwefonwefonwefonwefoknweofkm2eofkmokme"   #MANDATORY  
export DNS_USERNAME="you@cloudflaremail.tld"  #MANDATORY - the email address you registered for cloudflare with  
export DNS_SECURITY_KEY="kmnwefonerfiwefoiunwefojnqeijnefjnwpkdm"   #MANDATORY  
export DNS_CHOICE="cloudflare" #MANDATORY - you will need to set your DNS nameservers according to this choice  
export CLOUDHOST_EMAIL_ADDRESS="you@cloudhostemail.tld" #MANDATORY  
export BUILDOS="debian" #MANDATORY one of ubuntu|debian  
export BUILDOS_VERSION="11" #MANDATORY one of 20.04 22.04|10 11  
export DEFAULT_USER="admin" #MANDATORY - This must be "ubuntu" if you are deploying ubuntu and "admin" if you are deploying debian 
export BUILD_IDENTIFIER="nuocial" #MANDATORY  
export WEBSITE_DISPLAY_NAME="Nuocial" #MANDATORY  
export WEBSITE_NAME="nuocial" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial  
export WEBSITE_URL="demo.nuocial.org.uk"  #MANDATORY  
export SYSTEM_EMAIL_PROVIDER="3" #MANDATORY  
export SYSTEM_TOEMAIL_ADDRESS="webmaster@nuocial.org.uk" #MANDATORY  
export SYSTEM_FROMEMAIL_ADDRESS="webmaster@nuocial.org.uk" #MANDATORY  
export SYSTEM_EMAIL_USERNAME="dwijnweijnweoi2oi23oinjwefojnwe" #MANDATORY  
export SYSTEM_EMAIL_PASSWORD="ownefoinwefinefoi2km2m23fon2efin3efiin3foi2wdokmo32" #MANDATORY  
export SERVER_TIMEZONE_CONTINENT="Europe"  
export SERVER_TIMEZONE_CITY="London"  
export PRODUCTION="0"  
export DEVELOPMENT="1"  
export SUPERSAFE_WEBROOT="1"  
export WEBSERVER_CHOICE="NGINX"   
export NUMBER_WS="1"   
export NO_AUTOSCALERS="1"  
export SUPERSAFE_DB="1"  
export DISABLE_HOURLY="0"  
export DATABASE_INSTALLATION_TYPE="MySQL"  
export DB_PORT="2035"  
export SSH_PORT="1035"  
export GATEWAY_GUARDIAN="0"  
export BUILD_CHOICE="1" #MANDATORY  
export BUILD_ARCHIVE_CHOICE="baseline"  
export APPLICATION_LANGUAGE="PHP"  
export PHP_VERSION="8.0"  
export REGION=""  
export REGION_ID="eu-west-1"  
export DB_SIZE="t2.micro"  
export DB_SERVER_TYPE="t2.micro"  
export WS_SIZE="t2.micro"  
export WS_SERVER_TYPE="t2.micro"  
export AS_SIZE="t2.micro"  
export AS_SERVER_TYPE="t2.micro"  
export CLOUDHOST="aws"  
export MACHINE_TYPE="AWS"  
export ALGORITHM="rsa"  
export USER="root"  
export CLOUDHOST_USERNAME=""  
export CLOUDHOST_PASSWORD=""  
export PREVIOUS_BUILD_CONFIG="0"  
export GIT_USER="Templated User"  
export GIT_EMAIL_ADDRESS="templateduser@dummyemailX123.com"  
export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"  
export INFRASTRUCTURE_REPOSITORY_OWNER="agile-deployer"  
export INFRASTRUCTURE_REPOSITORY_USERNAME="agile-deployer"  
export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"  
export DATASTORE_CHOICE="amazonS3"  
export SSL_GENERATION_METHOD="AUTOMATIC"  
export SSL_GENERATION_SERVICE="LETSENCRYPT"  
export BYPASS_DB_LAYER="0"  
export APPLICATION_NAME="WORDY DEMO APPLICATION"  
export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"  
export DBaaS_HOSTNAME=""  
export DBaaS_USERNAME=""  
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
