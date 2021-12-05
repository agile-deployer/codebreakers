---
layout: post
description: The Agile Deployment Toolkit Exoscale Tutorials Hardcore Virgin Joomla
title: Exoscale ADT Tutorials Hardcore Virgin Joomla
permalink: /adtexoscaletutorialshardcorevirginjoomla/
hide: true
category: agiledeploymenttoolkit
---



**HARDCORE BUILD PROCESS**

1. On your laptop perform the following command:

>     git clone https://github.com/agile-deployer/agile-infrastructure-build-client-scripts.git

We need several pieces of information from our cloud host and 3rd party services for a successful build to be possible:

I am going to use the example of joomla to build from and so this example will build a virgin installation of the latest version of joomla

---------------------------------------

To find the latest version of Joomla, I go to this URL in my browser:

[Joomla Latest](https://downloads.joomla.org/)

And I note the latest version in a **separate text file**:

>     joomla_version="4.0.4"  

You can of course use a legacy version of joomla also by choosing a different version numnber. 

-------------------------------------

I then need a set of compute access keys so, I go to the IAM option on my exoscale dashboard and generate an IAM key with compute access. In my separate text file, I record:

>     exoscale_access_key_compute="XXXXX"  where XXXXX and YYYYY are the actual values generated when I click "Add Key"
>     exoscale_secret_key_compute="YYYYY"

I then need a set of Object Storage (S3) access keys so, I go to the IAM option on my exoscale dashboard and generate an IAM key with S3 access. In my separate text file, I record:

>     exoscale_access_key_s3="AAAAA"  where AAAAA and BBBBB are the actual values generated when I click "Add Key"
>     exoscale_secret_key_s3="BBBBB"


I then need a set of DNS access keys so, I go to the IAM option on my exoscale dashboard and generate an IAM key with DNS access. In my separate text file, I record:

>     exoscale_access_key_dns="CCCCC"  where CCCCC and DDDDD are the actual values generated when I click "Add Key"
>     exoscale_secret_key_dns="DDDDD"

**NOTE:** Alternatively you could generate one set of IAM keys and give that one set all three permissions, Compute, DNS and S3. You wouldn't have to juggle three set of keys then and could use the same key pair in all three cases.

-----------------------------------

You now need to make a note of the email address that you have registered with your exoscale account:

>     exoscale_email="testemail@testemail.com"

-----------------------------------

You then need the url that you want to use for your website. If you don't have a DNS URL for your website, you need to purchase one and set the nameservers to exoscale as described [here](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/Nameservers.md)

>     exoscale_dns_name="www.testsocialnetwork.org.uk"

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

2. Now do the following:

>     cd agile-infrastructure-build-client-scripts/helperscripts

>     /bin/sh GenerateHardcoreUserDataScript.sh

What I have done is run a sample execution of GenerateHardcoreUserData.sh so you can get an idea of how I set the values. This is just a dump of an example run through and it only sets the mandatory values to set other values such as machine size or database type you need to answer "Y" to the last question and review all non-mandatory settings as well. 

>    root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# /bin/sh GenerateOverrideTemplate.sh

############################################################################################################
WARNING: THERE IS NO SANITY CHECKING IF YOU USE THIS SCRIPT WHICH MEANS THAT IF YOU ENTER ANYTHING INCORRECT
YOU WON'T FIND OUT ABOUT IT UNTIL YOU CONFIGURE A BUILD USING THE OUTPUT FROM THIS SCRIPT AND THE BUILD FAILS
AT THE END, THIS SCRIPT WILL OUTPUT ITS CONFIGURATION AND YOU CAN TAKE A COPY OF THE OUTPUT AND STORE IT ON YOUR LAPTOP OR DESKTOP
FOR USE IN CURRENT AND FUTURE DEPLOYMENTS
BE AWARE THAT THE OUTPUT GENERATED WILL CONTAIN SENSITIVE INFORMATION WHICH YOU NEED TO KEEP SECURE
############################################################################################################
Press <enter> to continue

Which Cloudhost are you using? 1) Digital Ocean 2) Exoscale 3) Linode 4) Vultr 5)AWS. Please Enter the number for your cloudhost
2
Please tell us which template you wish to override
1.                   VIRGIN DEVELOPMENT MODE INSTALLATION OF JOOMLA, WORDPRESS, DRUPAL or MOODLE
2.                   BASELINED DEVELOPMENT MODE DEPLOY OF A BASELINED JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
3.                   TEMPORAL PRODUCTION MODE DEPLOY OF A BACKED UP JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
Please input a number between 1 and 3 to select a template to override
1
###############################################################################
YOU NEED TO SET ALL OF THESE VARIABLES TO SANE VALUES FOR THE BUILD TO FUNCTION
###############################################################################
Press <enter to begin>

############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### JOOMLA_VERSION

If you are deploying a virgin joomla installation, you must give the version number of joomla that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.

---- 
Found a variable JOOMLA_VERSION what do you want to set it to?
Its current value is "3.9.22" press <enter> to retain, anything else to override
4.0.4
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DRUPAL_VERSION

If you are deploying a virgin drupal installation, you must give the version number of drupal that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.

---- 
Found a variable DRUPAL_VERSION what do you want to set it to?
Its current value is "9.2.1" press <enter> to retain, anything else to override
N/A
OK, thanks...




/bin/sed: -e expression #1, char 54: unknown option to `s'
/bin/sed: -e expression #1, char 90: unknown option to `s'
############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_BASELINE_SOURCECODE_REPOSITORY

If you are deploying a virgin application, you can set this to "JOOMLA:{latest_version}", "WORDPRESS", "DRUPAL:{latest_version}" or "MOODLE"

-----
Found a variable APPLICATION_BASELINE_SOURCECODE_REPOSITORY what do you want to set it to?
Its current value is "JOOMLA:3.9.22" press <enter> to retain, anything else to override
JOOMLA:4.0.4
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### S3_ACCESS_KEY 
### S3_SECRET_KEY

These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 

You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:

##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY

##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.

##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.

##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 

##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY

-----
Found a variable S3_ACCESS_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
AAAA
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### S3_SECRET_KEY

These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 

You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:

##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY

##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.

##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.

##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 

##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY

-----
Found a variable S3_SECRET_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
BBBB
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### S3_HOST_BASE 

This parameter is the S3 endpoint for your deployment. It should be located as near as possible to where (in the world) you plan to run your VPS systems.

##### digital ocean - Available endpoints to choose from (2020) - nyc3.digitaloceanspaces.com, ams3.digitaloceanspaces.com, sfo2.digitaloceanspaces.com, sgp1.digitaloceanspaces.com, fra1.digitaloceanspaces.com

##### exoscale - Available endpoints to choose from (2020) - sos-ch-gva-2.exo.io, sos-ch-dk-2.exo.io, sos-de-fra-1.exo.io, sos-de-muc-1.exo.io, sos-at-vie-1.exo.io, sos-bg-sof-1

##### linode - Available endpoints to choose from (2020) - us-east-1.linodeobjects.com, eu-central-1.linodeobjects.com, ap-south-1.linodeobjects.com

##### vultr - Available endpints to choose from (2020) - ewr1.vultrobjects.com, 

##### Amazon - There are lots of S3 endpoints to choose from for Amazon. Your S3 endpoint should be region specific. For example if you are in eu-west-1 in would be, s3.eu-west-1.amazonaws.com

You can set your ${S3_HOST_BASE} parameter in your template to one of these listed endpoints depending on who your object storage is hosted with (which will likely be the ssame provider as your VPS systems). 

-----
Found a variable S3_HOST_BASE what do you want to set it to?
Its current value is "sos-ch-gva-2.exo.io" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### ACCESS_KEY
### SECRET_KEY

Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively

##### digital ocean - Does not use access keys and secret keys, see TOKEN

##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

##### linode - Does not use access keys and secret keys, see TOKEN

##### Vultr - Does not use access keys and secret keys, see TOKEN

##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

-----
Found a variable ACCESS_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
XXXX
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SECRET_KEY

Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively

##### digital ocean - Does not use access keys and secret keys, see TOKEN

##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

##### linode - Does not use access keys and secret keys, see TOKEN

##### Vultr - Does not use access keys and secret keys, see TOKEN

##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

-----
Found a variable SECRET_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
YYYY
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DNS_USERNAME

This will be the username for your DNS service provider

##### cloudflare - the emal address of username of your cloudflare account

##### digitalocean - your digital ocean account email address

##### exoscale - your exoscale account email address

##### linode - your linode account email address

##### vultr - your vultr account email address

-----
Found a variable DNS_USERNAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
testemail@testemail.com
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DNS_SECURITY_KEY 

This is the security key which will enable us to manipulate records as needed with your DNS provider. You can find this key as follows for each provider:

##### cloudflare - Ths is the Global API key for your cloudflare account which you can find by clicking on your profile at the top right of the screen

##### digital ocean - The access token for your digital ocean account, (can be the same as TOKEN)

##### exoscale  - The access key and secret key for your exoscale account. You need to enter this as ${ACCESS_KEY}:${SECRET_KEY}. You can use the same access key and secret key as your main account or you can create separate ones with only DNS manipulation rights. 

##### linode - A personal access token with DNS manipulation rights (can be the same value as TOKEN)

##### Vultr - A personal access token with DNS manipulation rights (can be the same as TOKEN)

------
Found a variable DNS_SECURITY_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
CCCC:DDDD
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DNS_CHOICE  

This can be set to one of these values 

##### "cloudflare" 
##### "digitalocean" 
##### "exoscale"
##### "linode"
##### "vultr"

It defines which of the (supported) DNS service you would like to use with your deployment.

---------------
Found a variable DNS_CHOICE what do you want to set it to?
Its current value is "exoscale" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
Found a variable CLOUDHOST_EMAIL_ADDRESS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
testemail@testemail.com
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### BUILDOS

This is the BUILDOS you wish to use for your servers, it can be one of "ubutnu" or "debian"

-----
Found a variable BUILDOS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
debian
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### BUILDOS_VERSION

This is the BUILDOS_VERSION you are deploying for this can be "20.04" or "22.04" if BUILDOS is "ubuntu" and "10" or "11" if BUILDOS is "debian"

-----
Found a variable BUILDOS_VERSION what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
11
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DEFAULT_USER

When you deploy to exoscale, the default user should be set to "ubuntu" if you are deploying Ubuntu and "debian" if you are deploying to Debian.
When you deploy to AWS, the default user should be set to "ubuntu" if you are deploying Ubuntu and "admin" if you are deploying to Debian.
For all other cases, the DEFAULT_USER should be set to "root"

-----
Found a variable DEFAULT_USER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
debian
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### BUILD_IDENTIFIER

This is a unique string to describe your build. If you have multiple builds that you want to give similar names you should call them, for example, "1-testbuild" or "2-testbuild" or "3-testbuild$

-----
Found a variable BUILD_IDENTIFIER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
nuocial
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### WEBSITE_DISPLAY_NAME

This is simply the display name of your application, for example, "My Social Network", or "My Blog" and so on. It should be descriptive of your website and likely will be similar to the core part of the WEBSITE_URL described below

-----
Found a variable WEBSITE_DISPLAY_NAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
Test Social Network
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### WEBSITE_NAME

This HAS to be exactly the same of the core part of the URL name of your website. So, if your website is called www.nuocial.org.uk, then, this value MUST be "nuocial"

-----
Found a variable WEBSITE_NAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
testsocialnetwork
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### WEBSITE_URL

This is the URL of your website. It can be any valid URL

-----
Found a variable WEBSITE_URL what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
www.testsocialnetwork.org.uk
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_PROVIDER

This is the git service provider where your application repositories are hosted. It has to be one of "github", "bitbucket" or "gitlab". If you fill this variable with one of those three exact strings, then, that will tell us who your application code is hosted with. It may or may not be hosted with the same provider as the infrastructure code for the agile deployment toolkit

-----
Found a variable APPLICATION_REPOSITORY_PROVIDER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
github
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_OWNER

This is the username of the user who owns (or created) your application repositories with your chosen git service provider

-----
Found a variable APPLICATION_REPOSITORY_OWNER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
adt-demos
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_USERNAME

This is the username of the user that you are currently using to access the application repositories. For example, the repositories might be owned by userA and are kept private but, userB is granted access. In this case the APPLICATION_REPOSITORY_OWNER would be userA and the APPLICATION_REPOSITORY_USERNAME would be userB. If you are the application repository owner, then this username and the owner name above will be the same.

-----
Found a variable APPLICATION_REPOSITORY_USERNAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
adt-demos
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_PASSWORD  

This is the password for the APPLICATION_REPOSITORY_USERNAME or the application repository user. This is the password for your user account with your git provider. If the application repositories are public (be careful not to expose sensitive credentials if you make your application repos public), then a password is not needed in which case this value must be precisely written or set to **"none"**

-----
Found a variable APPLICATION_REPOSITORY_PASSWORD what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_TOKEN

Github and Gitlab prefer personal access tokens to passwords, so, if you wish to, you can generate personal access tokens at:

Github: www.github.com/settings/tokens
Gitlab: www.gitlab.com/profile/personal_access_tokens

Make sure these tokens have the rights to create and destroy repositories as well as to read and write from them. Most likely, you want to have a separate git provider account for your associated deployments. This will override APPLICATION_REPOSITORY_PASSWORD

------
Found a variable APPLICATION_REPOSITORY_TOKEN what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
KKKKK
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_EMAIL_PROVIDER

At the moment, there are three SMTP email service providers. Enter the number value, "1", "2" or "3" to select which provider you want to use for your SMTP service. If you leave these variables blank, you simply won't receive any system emails to give status updated on build progression, server intialisations and so on. You are free to leave these variables blank, as you choose.

Enter "1" - Sendpulse (www.sendpulse.com)
Enter "2" - Google (gmail)
Enter "3" - AWS SES 

-----
Found a variable SYSTEM_EMAIL_PROVIDER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_TOEMAIL_ADDRESS 

The email address that system emails will be sent to this can be any email address that you have access to. MAYBE, the emails get marked as spam depending on your provider. If you take them out of the spam folder, then, the system should learn they are not spam. Most likely you will want to have a dedicated email address for your system emails for your deployed application as they will likely fill up your inbox otherwise.

-----
Found a variable SYSTEM_TOEMAIL_ADDRESS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_FROMEMAIL_ADDRESS

The email address that system emails will be sent from. This should be an email address that the system emails are sent from. In your SYSTEM_TOEMAIL_ADDRESS inbox, this will be the email address that the system messages are seen to be sent from or to have originated from.

-----
Found a variable SYSTEM_FROMEMAIL_ADDRESS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_EMAIL_USERNAME

This is the username of your SMTP user. For Amazon SES, for example, this will be the username generated when you enable the SES service. This is the SMTP username. 

-----
Found a variable SYSTEM_EMAIL_USERNAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_EMAIL_PASSWORD

This is the password of your SMTP user. For Amazon SES, for example, this will be the password generated when you enable the SES service. This is the SMTP password. 

----
Found a variable SYSTEM_EMAIL_PASSWORD what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




###################################################################################################################################
Do you want to review the rest of the variables that are being used or do you want to accept the default template values
If you want to change machine sizes or regions for example, you need to change them here so that they override the templated values
###################################################################################################################################
Enter 'y' or 'Y' if you wish to review/override the rest of the variables used by this template, 'N' or 'n' will use the default settings
N
######################################################################################################################
Cheers. Your configuration has been written to: /home/agile-deployer/new/agile-infrastructure-build-client-scripts/overridescripts/exoscale1override.tmpl
You should meticulously review this configuration file before deploying.
You can edit and make changes to this configuration file as you desire but keep it with the same filename to deploy it
######################################################################################################################
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# 
exit
Script done.
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# cat typescript
Script started on 2021-12-05 23:21:38+00:00 [TERM="xterm-256color" TTY="/dev/pts/0" COLUMNS="243" LINES="60"]
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# sh GenerateOverrideTemplate.sh
############################################################################################################
WARNING: THERE IS NO SANITY CHECKING IF YOU USE THIS SCRIPT WHICH MEANS THAT IF YOU ENTER ANYTHING INCORRECT
YOU WON'T FIND OUT ABOUT IT UNTIL YOU CONFIGURE A BUILD USING THE OUTPUT FROM THIS SCRIPT AND THE BUILD FAILS
AT THE END, THIS SCRIPT WILL OUTPUT ITS CONFIGURATION AND YOU CAN TAKE A COPY OF THE OUTPUT AND STORE IT ON YOUR LAPTOP OR DESKTOP
FOR USE IN CURRENT AND FUTURE DEPLOYMENTS
BE AWARE THAT THE OUTPUT GENERATED WILL CONTAIN SENSITIVE INFORMATION WHICH YOU NEED TO KEEP SECURE
############################################################################################################
Press <enter> to continue

Which Cloudhost are you using? 1) Digital Ocean 2) Exoscale 3) Linode 4) Vultr 5)AWS. Please Enter the number for your cloudhost
2
Please tell us which template you wish to override
1.                   VIRGIN DEVELOPMENT MODE INSTALLATION OF JOOMLA, WORDPRESS, DRUPAL or MOODLE
2.                   BASELINED DEVELOPMENT MODE DEPLOY OF A BASELINED JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
3.                   TEMPORAL PRODUCTION MODE DEPLOY OF A BACKED UP JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
Please input a number between 1 and 3 to select a template to override
1
###############################################################################
YOU NEED TO SET ALL OF THESE VARIABLES TO SANE VALUES FOR THE BUILD TO FUNCTION
###############################################################################
Press <enter to begin>

############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### JOOMLA_VERSION

If you are deploying a virgin joomla installation, you must give the version number of joomla that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.

---- 
Found a variable JOOMLA_VERSION what do you want to set it to?
Its current value is "3.9.22" press <enter> to retain, anything else to override
4.0.4
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DRUPAL_VERSION

If you are deploying a virgin drupal installation, you must give the version number of drupal that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.

---- 
Found a variable DRUPAL_VERSION what do you want to set it to?
Its current value is "9.2.1" press <enter> to retain, anything else to override
N/A
OK, thanks...




/bin/sed: -e expression #1, char 54: unknown option to `s'
/bin/sed: -e expression #1, char 90: unknown option to `s'
############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_BASELINE_SOURCECODE_REPOSITORY

If you are deploying a virgin application, you can set this to "JOOMLA:{latest_version}", "WORDPRESS", "DRUPAL:{latest_version}" or "MOODLE"

-----
Found a variable APPLICATION_BASELINE_SOURCECODE_REPOSITORY what do you want to set it to?
Its current value is "JOOMLA:3.9.22" press <enter> to retain, anything else to override
JOOMLA:4.0.4
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### S3_ACCESS_KEY 
### S3_SECRET_KEY

These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 

You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:

##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY

##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.

##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.

##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 

##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY

-----
Found a variable S3_ACCESS_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
AAAA
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### S3_SECRET_KEY

These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 

You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:

##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY

##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.

##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.

##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 

##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY

-----
Found a variable S3_SECRET_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
BBBB
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### S3_HOST_BASE 

This parameter is the S3 endpoint for your deployment. It should be located as near as possible to where (in the world) you plan to run your VPS systems.

##### digital ocean - Available endpoints to choose from (2020) - nyc3.digitaloceanspaces.com, ams3.digitaloceanspaces.com, sfo2.digitaloceanspaces.com, sgp1.digitaloceanspaces.com, fra1.digitaloceanspaces.com

##### exoscale - Available endpoints to choose from (2020) - sos-ch-gva-2.exo.io, sos-ch-dk-2.exo.io, sos-de-fra-1.exo.io, sos-de-muc-1.exo.io, sos-at-vie-1.exo.io, sos-bg-sof-1

##### linode - Available endpoints to choose from (2020) - us-east-1.linodeobjects.com, eu-central-1.linodeobjects.com, ap-south-1.linodeobjects.com

##### vultr - Available endpints to choose from (2020) - ewr1.vultrobjects.com, 

##### Amazon - There are lots of S3 endpoints to choose from for Amazon. Your S3 endpoint should be region specific. For example if you are in eu-west-1 in would be, s3.eu-west-1.amazonaws.com

You can set your ${S3_HOST_BASE} parameter in your template to one of these listed endpoints depending on who your object storage is hosted with (which will likely be the ssame provider as your VPS systems). 

-----
Found a variable S3_HOST_BASE what do you want to set it to?
Its current value is "sos-ch-gva-2.exo.io" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### ACCESS_KEY
### SECRET_KEY

Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively

##### digital ocean - Does not use access keys and secret keys, see TOKEN

##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

##### linode - Does not use access keys and secret keys, see TOKEN

##### Vultr - Does not use access keys and secret keys, see TOKEN

##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

-----
Found a variable ACCESS_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
XXXX
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SECRET_KEY

Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively

##### digital ocean - Does not use access keys and secret keys, see TOKEN

##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

##### linode - Does not use access keys and secret keys, see TOKEN

##### Vultr - Does not use access keys and secret keys, see TOKEN

##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys

-----
Found a variable SECRET_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
YYYY
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DNS_USERNAME

This will be the username for your DNS service provider

##### cloudflare - the emal address of username of your cloudflare account

##### digitalocean - your digital ocean account email address

##### exoscale - your exoscale account email address

##### linode - your linode account email address

##### vultr - your vultr account email address

-----
Found a variable DNS_USERNAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
testemail@testemail.com
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DNS_SECURITY_KEY 

This is the security key which will enable us to manipulate records as needed with your DNS provider. You can find this key as follows for each provider:

##### cloudflare - Ths is the Global API key for your cloudflare account which you can find by clicking on your profile at the top right of the screen

##### digital ocean - The access token for your digital ocean account, (can be the same as TOKEN)

##### exoscale  - The access key and secret key for your exoscale account. You need to enter this as ${ACCESS_KEY}:${SECRET_KEY}. You can use the same access key and secret key as your main account or you can create separate ones with only DNS manipulation rights. 

##### linode - A personal access token with DNS manipulation rights (can be the same value as TOKEN)

##### Vultr - A personal access token with DNS manipulation rights (can be the same as TOKEN)

------
Found a variable DNS_SECURITY_KEY what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
CCCC:DDDD
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DNS_CHOICE  

This can be set to one of these values 

##### "cloudflare" 
##### "digitalocean" 
##### "exoscale"
##### "linode"
##### "vultr"

It defines which of the (supported) DNS service you would like to use with your deployment.

---------------
Found a variable DNS_CHOICE what do you want to set it to?
Its current value is "exoscale" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
Found a variable CLOUDHOST_EMAIL_ADDRESS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
testemail@testemail.com
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### BUILDOS

This is the BUILDOS you wish to use for your servers, it can be one of "ubutnu" or "debian"

-----
Found a variable BUILDOS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
debian
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### BUILDOS_VERSION

This is the BUILDOS_VERSION you are deploying for this can be "20.04" or "22.04" if BUILDOS is "ubuntu" and "10" or "11" if BUILDOS is "debian"

-----
Found a variable BUILDOS_VERSION what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
11
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### DEFAULT_USER

When you deploy to exoscale, the default user should be set to "ubuntu" if you are deploying Ubuntu and "debian" if you are deploying to Debian.
When you deploy to AWS, the default user should be set to "ubuntu" if you are deploying Ubuntu and "admin" if you are deploying to Debian.
For all other cases, the DEFAULT_USER should be set to "root"

-----
Found a variable DEFAULT_USER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
debian
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### BUILD_IDENTIFIER

This is a unique string to describe your build. If you have multiple builds that you want to give similar names you should call them, for example, "1-testbuild" or "2-testbuild" or "3-testbuild$

-----
Found a variable BUILD_IDENTIFIER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
nuocial
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### WEBSITE_DISPLAY_NAME

This is simply the display name of your application, for example, "My Social Network", or "My Blog" and so on. It should be descriptive of your website and likely will be similar to the core part of the WEBSITE_URL described below

-----
Found a variable WEBSITE_DISPLAY_NAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
Test Social Network
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### WEBSITE_NAME

This HAS to be exactly the same of the core part of the URL name of your website. So, if your website is called www.nuocial.org.uk, then, this value MUST be "nuocial"

-----
Found a variable WEBSITE_NAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
testsocialnetwork
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### WEBSITE_URL

This is the URL of your website. It can be any valid URL

-----
Found a variable WEBSITE_URL what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
www.testsocialnetwork.org.uk
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_PROVIDER

This is the git service provider where your application repositories are hosted. It has to be one of "github", "bitbucket" or "gitlab". If you fill this variable with one of those three exact strings, then, that will tell us who your application code is hosted with. It may or may not be hosted with the same provider as the infrastructure code for the agile deployment toolkit

-----
Found a variable APPLICATION_REPOSITORY_PROVIDER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
github
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_OWNER

This is the username of the user who owns (or created) your application repositories with your chosen git service provider

-----
Found a variable APPLICATION_REPOSITORY_OWNER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
adt-demos
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_USERNAME

This is the username of the user that you are currently using to access the application repositories. For example, the repositories might be owned by userA and are kept private but, userB is granted access. In this case the APPLICATION_REPOSITORY_OWNER would be userA and the APPLICATION_REPOSITORY_USERNAME would be userB. If you are the application repository owner, then this username and the owner name above will be the same.

-----
Found a variable APPLICATION_REPOSITORY_USERNAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
adt-demos
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_PASSWORD  

This is the password for the APPLICATION_REPOSITORY_USERNAME or the application repository user. This is the password for your user account with your git provider. If the application repositories are public (be careful not to expose sensitive credentials if you make your application repos public), then a password is not needed in which case this value must be precisely written or set to **"none"**

-----
Found a variable APPLICATION_REPOSITORY_PASSWORD what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### APPLICATION_REPOSITORY_TOKEN

Github and Gitlab prefer personal access tokens to passwords, so, if you wish to, you can generate personal access tokens at:

Github: www.github.com/settings/tokens
Gitlab: www.gitlab.com/profile/personal_access_tokens

Make sure these tokens have the rights to create and destroy repositories as well as to read and write from them. Most likely, you want to have a separate git provider account for your associated deployments. This will override APPLICATION_REPOSITORY_PASSWORD

------
Found a variable APPLICATION_REPOSITORY_TOKEN what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override
KKKKK
OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_EMAIL_PROVIDER

At the moment, there are three SMTP email service providers. Enter the number value, "1", "2" or "3" to select which provider you want to use for your SMTP service. If you leave these variables blank, you simply won't receive any system emails to give status updated on build progression, server intialisations and so on. You are free to leave these variables blank, as you choose.

Enter "1" - Sendpulse (www.sendpulse.com)
Enter "2" - Google (gmail)
Enter "3" - AWS SES 

-----
Found a variable SYSTEM_EMAIL_PROVIDER what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_TOEMAIL_ADDRESS 

The email address that system emails will be sent to this can be any email address that you have access to. MAYBE, the emails get marked as spam depending on your provider. If you take them out of the spam folder, then, the system should learn they are not spam. Most likely you will want to have a dedicated email address for your system emails for your deployed application as they will likely fill up your inbox otherwise.

-----
Found a variable SYSTEM_TOEMAIL_ADDRESS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_FROMEMAIL_ADDRESS

The email address that system emails will be sent from. This should be an email address that the system emails are sent from. In your SYSTEM_TOEMAIL_ADDRESS inbox, this will be the email address that the system messages are seen to be sent from or to have originated from.

-----
Found a variable SYSTEM_FROMEMAIL_ADDRESS what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_EMAIL_USERNAME

This is the username of your SMTP user. For Amazon SES, for example, this will be the username generated when you enable the SES service. This is the SMTP username. 

-----
Found a variable SYSTEM_EMAIL_USERNAME what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




############################################################################################
Explanation from the specification regarding this variable:
############################################################################################
### SYSTEM_EMAIL_PASSWORD

This is the password of your SMTP user. For Amazon SES, for example, this will be the password generated when you enable the SES service. This is the SMTP password. 

----
Found a variable SYSTEM_EMAIL_PASSWORD what do you want to set it to?
Its current value is "" press <enter> to retain, anything else to override

OK, thanks...




###################################################################################################################################
Do you want to review the rest of the variables that are being used or do you want to accept the default template values
If you want to change machine sizes or regions for example, you need to change them here so that they override the templated values
###################################################################################################################################
Enter 'y' or 'Y' if you wish to review/override the rest of the variables used by this template, 'N' or 'n' will use the default settings
N
######################################################################################################################
Cheers. Your configuration has been written to: /home/agile-deployer/new/agile-infrastructure-build-client-scripts/overridescripts/exoscale1override.tmpl
You should meticulously review this configuration file before deploying.
You can edit and make changes to this configuration file as you desire but keep it with the same filename to deploy it
######################################################################################################################
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# 
exit

Script done on 2021-12-05 23:26:37+00:00 [COMMAND_EXIT_CODE="0"]
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# ls -l
total 220
-rwx------ 1 root root  5394 Dec  5 21:39 AdjustScaling.sh
-rwx------ 1 root root  2977 Dec  5 20:54 CleanBuildMachineBackups.sh
-rwx------ 1 root root  5217 Dec  5 20:54 ConnectToAutoscaler.sh
-rwx------ 1 root root  5030 Dec  5 20:54 ConnectToDB.sh
-rwx------ 1 root root  5161 Dec  5 20:54 ConnectToWebserver.sh
-rwx------ 1 root root  5018 Dec  5 20:54 CopyToAutoscaler.sh
-rwx------ 1 root root  5632 Dec  5 20:54 CopyToDatabase.sh
-rwx------ 1 root root  5701 Dec  5 20:54 CopyToWebserver.sh
-rwx------ 1 root root  5396 Dec  5 20:54 ExecuteOnAutoscaler.sh
-rwx------ 1 root root  5292 Dec  5 20:54 ExecuteOnDatabase.sh
-rwx------ 1 root root  5354 Dec  5 20:54 ExecuteOnWebserver.sh
-rwx------ 1 root root  3925 Dec  5 20:54 GenerateHardcoreUserDataScript.sh
-rwx------ 1 root root 10794 Dec  5 20:54 GenerateOverrideTemplate.sh
-rwx------ 1 root root  3746 Dec  5 20:54 ManuallyUpdateSSLCertificate.sh
-rwx------ 1 root root  2598 Dec  5 20:54 MonitorWebserver.sh
-rwx------ 1 root root  1730 Dec  5 20:54 ObtainGatewayGuardianPasswords.sh
-rwx------ 1 root root 11968 Dec  5 20:54 PerformDatabaseBackup.sh
-rwx------ 1 root root  9073 Dec  5 20:54 PerformDatabaseBaseline.sh
-rwx------ 1 root root 12346 Dec  5 20:54 PerformWebsiteBackup.sh
-rwx------ 1 root root  9472 Dec  5 20:54 PerformWebsiteBaseline.sh
-rwx------ 1 root root  1869 Dec  5 20:54 README
-rwx------ 1 root root  5449 Dec  5 20:54 RebootInfrastructure.sh
-rwx------ 1 root root  2637 Dec  5 20:54 ResetBuildKit.sh
-rwx------ 1 root root  7859 Dec  5 20:54 ShutdownInfrastructure.sh
-rw-r--r-- 1 root root 29583 Dec  5 23:26 typescript
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# cp type* 1
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# vi 1
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# sed 's/^/\>     /g' 1
>     Script started on 2021-12-05 23:21:38+00:00 [TERM="xterm-256color" TTY="/dev/pts/0" COLUMNS="243" LINES="60"]
>     root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# sh GenerateOverrideTemplate.sh
############################################################################################################
>     WARNING: THERE IS NO SANITY CHECKING IF YOU USE THIS SCRIPT WHICH MEANS THAT IF YOU ENTER ANYTHING INCORRECT
>     YOU WON'T FIND OUT ABOUT IT UNTIL YOU CONFIGURE A BUILD USING THE OUTPUT FROM THIS SCRIPT AND THE BUILD FAILS
>     AT THE END, THIS SCRIPT WILL OUTPUT ITS CONFIGURATION AND YOU CAN TAKE A COPY OF THE OUTPUT AND STORE IT ON YOUR LAPTOP OR DESKTOP
>     FOR USE IN CURRENT AND FUTURE DEPLOYMENTS
>     BE AWARE THAT THE OUTPUT GENERATED WILL CONTAIN SENSITIVE INFORMATION WHICH YOU NEED TO KEEP SECURE
>     ############################################################################################################
>     Press <enter> to continue
>     
>     Which Cloudhost are you using? 1) Digital Ocean 2) Exoscale 3) Linode 4) Vultr 5)AWS. Please Enter the number for your cloudhost
>     2
>     Please tell us which template you wish to override
>     1.                   VIRGIN DEVELOPMENT MODE INSTALLATION OF JOOMLA, WORDPRESS, DRUPAL or MOODLE
>     2.                   BASELINED DEVELOPMENT MODE DEPLOY OF A BASELINED JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
>     3.                   TEMPORAL PRODUCTION MODE DEPLOY OF A BACKED UP JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
>     Please input a number between 1 and 3 to select a template to override
>     1
>     ###############################################################################
>     YOU NEED TO SET ALL OF THESE VARIABLES TO SANE VALUES FOR THE BUILD TO FUNCTION
>     ###############################################################################
>     Press <enter to begin>
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### JOOMLA_VERSION
>     
>     If you are deploying a virgin joomla installation, you must give the version number of joomla that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.
>     
>     ---- 
>     Found a variable JOOMLA_VERSION what do you want to set it to?
>     Its current value is "3.9.22" press <enter> to retain, anything else to override
>     4.0.4
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DRUPAL_VERSION
>     
>     If you are deploying a virgin drupal installation, you must give the version number of drupal that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.
>     
>     ---- 
>     Found a variable DRUPAL_VERSION what do you want to set it to?
>     Its current value is "9.2.1" press <enter> to retain, anything else to override
>     N/A
>     OK, thanks...
>     
>     
>     
>     
>     /bin/sed: -e expression #1, char 54: unknown option to `s'
>     /bin/sed: -e expression #1, char 90: unknown option to `s'
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_BASELINE_SOURCECODE_REPOSITORY
>     
>     If you are deploying a virgin application, you can set this to "JOOMLA:{latest_version}", "WORDPRESS", "DRUPAL:{latest_version}" or "MOODLE"
>     
>     -----
>     Found a variable APPLICATION_BASELINE_SOURCECODE_REPOSITORY what do you want to set it to?
>     Its current value is "JOOMLA:3.9.22" press <enter> to retain, anything else to override
>     JOOMLA:4.0.4
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### S3_ACCESS_KEY 
>     ### S3_SECRET_KEY
>     
>     These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 
>     
>     You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:
>     
>     ##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY
>     
>     ##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.
>     
>     ##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.
>     
>     ##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 
>     
>     ##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY
>     
>     -----
>     Found a variable S3_ACCESS_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     AAAA
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### S3_SECRET_KEY
>     
>     These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 
>     
>     You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:
>     
>     ##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY
>     
>     ##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.
>     
>     ##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.
>     
>     ##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 
>     
>     ##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY
>     
>     -----
>     Found a variable S3_SECRET_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     BBBB
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### S3_HOST_BASE 
>     
>     This parameter is the S3 endpoint for your deployment. It should be located as near as possible to where (in the world) you plan to run your VPS systems.
>     
>     ##### digital ocean - Available endpoints to choose from (2020) - nyc3.digitaloceanspaces.com, ams3.digitaloceanspaces.com, sfo2.digitaloceanspaces.com, sgp1.digitaloceanspaces.com, fra1.digitaloceanspaces.com
>     
>     ##### exoscale - Available endpoints to choose from (2020) - sos-ch-gva-2.exo.io, sos-ch-dk-2.exo.io, sos-de-fra-1.exo.io, sos-de-muc-1.exo.io, sos-at-vie-1.exo.io, sos-bg-sof-1
>     
>     ##### linode - Available endpoints to choose from (2020) - us-east-1.linodeobjects.com, eu-central-1.linodeobjects.com, ap-south-1.linodeobjects.com
>     
>     ##### vultr - Available endpints to choose from (2020) - ewr1.vultrobjects.com, 
>     
>     ##### Amazon - There are lots of S3 endpoints to choose from for Amazon. Your S3 endpoint should be region specific. For example if you are in eu-west-1 in would be, s3.eu-west-1.amazonaws.com
>     
>     You can set your ${S3_HOST_BASE} parameter in your template to one of these listed endpoints depending on who your object storage is hosted with (which will likely be the ssame provider as your VPS systems). 
>     
>     -----
>     Found a variable S3_HOST_BASE what do you want to set it to?
>     Its current value is "sos-ch-gva-2.exo.io" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### ACCESS_KEY
>     ### SECRET_KEY
>     
>     Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively
>     
>     ##### digital ocean - Does not use access keys and secret keys, see TOKEN
>     
>     ##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     ##### linode - Does not use access keys and secret keys, see TOKEN
>     
>     ##### Vultr - Does not use access keys and secret keys, see TOKEN
>     
>     ##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     -----
>     Found a variable ACCESS_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     XXXX
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SECRET_KEY
>     
>     Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively
>     
>     ##### digital ocean - Does not use access keys and secret keys, see TOKEN
>     
>     ##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     ##### linode - Does not use access keys and secret keys, see TOKEN
>     
>     ##### Vultr - Does not use access keys and secret keys, see TOKEN
>     
>     ##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     -----
>     Found a variable SECRET_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     YYYY
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DNS_USERNAME
>     
>     This will be the username for your DNS service provider
>     
>     ##### cloudflare - the emal address of username of your cloudflare account
>     
>     ##### digitalocean - your digital ocean account email address
>     
>     ##### exoscale - your exoscale account email address
>     
>     ##### linode - your linode account email address
>     
>     ##### vultr - your vultr account email address
>     
>     -----
>     Found a variable DNS_USERNAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     testemail@testemail.com
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DNS_SECURITY_KEY 
>     
>     This is the security key which will enable us to manipulate records as needed with your DNS provider. You can find this key as follows for each provider:
>     
>     ##### cloudflare - Ths is the Global API key for your cloudflare account which you can find by clicking on your profile at the top right of the screen
>     
>     ##### digital ocean - The access token for your digital ocean account, (can be the same as TOKEN)
>     
>     ##### exoscale  - The access key and secret key for your exoscale account. You need to enter this as ${ACCESS_KEY}:${SECRET_KEY}. You can use the same access key and secret key as your main account or you can create separate ones with only DNS manipulation rights. 
>     
>     ##### linode - A personal access token with DNS manipulation rights (can be the same value as TOKEN)
>     
>     ##### Vultr - A personal access token with DNS manipulation rights (can be the same as TOKEN)
>     
>     ------
>     Found a variable DNS_SECURITY_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     CCCC:DDDD
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DNS_CHOICE  
>     
>     This can be set to one of these values 
>     
>     ##### "cloudflare" 
>     ##### "digitalocean" 
>     ##### "exoscale"
>     ##### "linode"
>     ##### "vultr"
>     
>     It defines which of the (supported) DNS service you would like to use with your deployment.
>     
>     ---------------
>     Found a variable DNS_CHOICE what do you want to set it to?
>     Its current value is "exoscale" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     Found a variable CLOUDHOST_EMAIL_ADDRESS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     testemail@testemail.com
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### BUILDOS
>     
>     This is the BUILDOS you wish to use for your servers, it can be one of "ubutnu" or "debian"
>     
>     -----
>     Found a variable BUILDOS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     debian
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### BUILDOS_VERSION
>     
>     This is the BUILDOS_VERSION you are deploying for this can be "20.04" or "22.04" if BUILDOS is "ubuntu" and "10" or "11" if BUILDOS is "debian"
>     
>     -----
>     Found a variable BUILDOS_VERSION what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     11
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DEFAULT_USER
>     
>     When you deploy to exoscale, the default user should be set to "ubuntu" if you are deploying Ubuntu and "debian" if you are deploying to Debian.
>     When you deploy to AWS, the default user should be set to "ubuntu" if you are deploying Ubuntu and "admin" if you are deploying to Debian.
>     For all other cases, the DEFAULT_USER should be set to "root"
>     
>     -----
>     Found a variable DEFAULT_USER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     debian
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### BUILD_IDENTIFIER
>     
>     This is a unique string to describe your build. If you have multiple builds that you want to give similar names you should call them, for example, "1-testbuild" or "2-testbuild" or "3-testbuild$
>     
>     -----
>     Found a variable BUILD_IDENTIFIER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     nuocial
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### WEBSITE_DISPLAY_NAME
>     
>     This is simply the display name of your application, for example, "My Social Network", or "My Blog" and so on. It should be descriptive of your website and likely will be similar to the core part of the WEBSITE_URL described below
>     
>     -----
>     Found a variable WEBSITE_DISPLAY_NAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     Test Social Network
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### WEBSITE_NAME
>     
>     This HAS to be exactly the same of the core part of the URL name of your website. So, if your website is called www.nuocial.org.uk, then, this value MUST be "nuocial"
>     
>     -----
>     Found a variable WEBSITE_NAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     testsocialnetwork
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### WEBSITE_URL
>     
>     This is the URL of your website. It can be any valid URL
>     
>     -----
>     Found a variable WEBSITE_URL what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     www.testsocialnetwork.org.uk
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_PROVIDER
>     
>     This is the git service provider where your application repositories are hosted. It has to be one of "github", "bitbucket" or "gitlab". If you fill this variable with one of those three exact strings, then, that will tell us who your application code is hosted with. It may or may not be hosted with the same provider as the infrastructure code for the agile deployment toolkit
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_PROVIDER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     github
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_OWNER
>     
>     This is the username of the user who owns (or created) your application repositories with your chosen git service provider
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_OWNER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     adt-demos
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_USERNAME
>     
>     This is the username of the user that you are currently using to access the application repositories. For example, the repositories might be owned by userA and are kept private but, userB is granted access. In this case the APPLICATION_REPOSITORY_OWNER would be userA and the APPLICATION_REPOSITORY_USERNAME would be userB. If you are the application repository owner, then this username and the owner name above will be the same.
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_USERNAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     adt-demos
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_PASSWORD  
>     
>     This is the password for the APPLICATION_REPOSITORY_USERNAME or the application repository user. This is the password for your user account with your git provider. If the application repositories are public (be careful not to expose sensitive credentials if you make your application repos public), then a password is not needed in which case this value must be precisely written or set to **"none"**
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_PASSWORD what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_TOKEN
>     
>     Github and Gitlab prefer personal access tokens to passwords, so, if you wish to, you can generate personal access tokens at:
>     
>     Github: www.github.com/settings/tokens
>     Gitlab: www.gitlab.com/profile/personal_access_tokens
>     
>     Make sure these tokens have the rights to create and destroy repositories as well as to read and write from them. Most likely, you want to have a separate git provider account for your associated deployments. This will override APPLICATION_REPOSITORY_PASSWORD
>     
>     ------
>     Found a variable APPLICATION_REPOSITORY_TOKEN what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     KKKKK
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_EMAIL_PROVIDER
>     
>     At the moment, there are three SMTP email service providers. Enter the number value, "1", "2" or "3" to select which provider you want to use for your SMTP service. If you leave these variables blank, you simply won't receive any system emails to give status updated on build progression, server intialisations and so on. You are free to leave these variables blank, as you choose.
>     
>     Enter "1" - Sendpulse (www.sendpulse.com)
>     Enter "2" - Google (gmail)
>     Enter "3" - AWS SES 
>     
>     -----
>     Found a variable SYSTEM_EMAIL_PROVIDER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_TOEMAIL_ADDRESS 
>     
>     The email address that system emails will be sent to this can be any email address that you have access to. MAYBE, the emails get marked as spam depending on your provider. If you take them out of the spam folder, then, the system should learn they are not spam. Most likely you will want to have a dedicated email address for your system emails for your deployed application as they will likely fill up your inbox otherwise.
>     
>     -----
>     Found a variable SYSTEM_TOEMAIL_ADDRESS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_FROMEMAIL_ADDRESS
>     
>     The email address that system emails will be sent from. This should be an email address that the system emails are sent from. In your SYSTEM_TOEMAIL_ADDRESS inbox, this will be the email address that the system messages are seen to be sent from or to have originated from.
>     
>     -----
>     Found a variable SYSTEM_FROMEMAIL_ADDRESS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_EMAIL_USERNAME
>     
>     This is the username of your SMTP user. For Amazon SES, for example, this will be the username generated when you enable the SES service. This is the SMTP username. 
>     
>     -----
>     Found a variable SYSTEM_EMAIL_USERNAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_EMAIL_PASSWORD
>     
>     This is the password of your SMTP user. For Amazon SES, for example, this will be the password generated when you enable the SES service. This is the SMTP password. 
>     
>     ----
>     Found a variable SYSTEM_EMAIL_PASSWORD what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ###################################################################################################################################
>     Do you want to review the rest of the variables that are being used or do you want to accept the default template values
>     If you want to change machine sizes or regions for example, you need to change them here so that they override the templated values
>     ###################################################################################################################################
>     Enter 'y' or 'Y' if you wish to review/override the rest of the variables used by this template, 'N' or 'n' will use the default settings
>     N
>     ######################################################################################################################
>     Cheers. Your configuration has been written to: /home/agile-deployer/new/agile-infrastructure-build-client-scripts/overridescripts/exoscale1override.tmpl
>     You should meticulously review this configuration file before deploying.
>     You can edit and make changes to this configuration file as you desire but keep it with the same filename to deploy it
>     ######################################################################################################################
>     root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# 
>     exit
>     
>     Script done on 2021-12-05 23:26:37+00:00 [COMMAND_EXIT_CODE="0"]
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# sed 's/^/\>     /g' 1 > 2
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# vi 2
root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# cat 2
>     Script started on 2021-12-05 23:21:38+00:00 [TERM="xterm-256color" TTY="/dev/pts/0" COLUMNS="243" LINES="60"]
>     root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# sh GenerateOverrideTemplate.sh
############################################################################################################
>     WARNING: THERE IS NO SANITY CHECKING IF YOU USE THIS SCRIPT WHICH MEANS THAT IF YOU ENTER ANYTHING INCORRECT
>     YOU WON'T FIND OUT ABOUT IT UNTIL YOU CONFIGURE A BUILD USING THE OUTPUT FROM THIS SCRIPT AND THE BUILD FAILS
>     AT THE END, THIS SCRIPT WILL OUTPUT ITS CONFIGURATION AND YOU CAN TAKE A COPY OF THE OUTPUT AND STORE IT ON YOUR LAPTOP OR DESKTOP
>     FOR USE IN CURRENT AND FUTURE DEPLOYMENTS
>     BE AWARE THAT THE OUTPUT GENERATED WILL CONTAIN SENSITIVE INFORMATION WHICH YOU NEED TO KEEP SECURE
>     ############################################################################################################
>     Press <enter> to continue
>     
>     Which Cloudhost are you using? 1) Digital Ocean 2) Exoscale 3) Linode 4) Vultr 5)AWS. Please Enter the number for your cloudhost
>     2
>     Please tell us which template you wish to override
>     1.                   VIRGIN DEVELOPMENT MODE INSTALLATION OF JOOMLA, WORDPRESS, DRUPAL or MOODLE
>     2.                   BASELINED DEVELOPMENT MODE DEPLOY OF A BASELINED JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
>     3.                   TEMPORAL PRODUCTION MODE DEPLOY OF A BACKED UP JOOMLA WORDPRESS DRUPAL OR MOODLE APPLICATION
>     Please input a number between 1 and 3 to select a template to override
>     1
>     ###############################################################################
>     YOU NEED TO SET ALL OF THESE VARIABLES TO SANE VALUES FOR THE BUILD TO FUNCTION
>     ###############################################################################
>     Press <enter to begin>
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### JOOMLA_VERSION
>     
>     If you are deploying a virgin joomla installation, you must give the version number of joomla that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.
>     
>     ---- 
>     Found a variable JOOMLA_VERSION what do you want to set it to?
>     Its current value is "3.9.22" press <enter> to retain, anything else to override
>     4.0.4
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DRUPAL_VERSION
>     
>     If you are deploying a virgin drupal installation, you must give the version number of drupal that you are deploying here. In such a template, you will likely want to update this version number to be the latest available.
>     
>     ---- 
>     Found a variable DRUPAL_VERSION what do you want to set it to?
>     Its current value is "9.2.1" press <enter> to retain, anything else to override
>     N/A
>     OK, thanks...
>     
>     
>     
>     
>     /bin/sed: -e expression #1, char 54: unknown option to `s'
>     /bin/sed: -e expression #1, char 90: unknown option to `s'
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_BASELINE_SOURCECODE_REPOSITORY
>     
>     If you are deploying a virgin application, you can set this to "JOOMLA:{latest_version}", "WORDPRESS", "DRUPAL:{latest_version}" or "MOODLE"
>     
>     -----
>     Found a variable APPLICATION_BASELINE_SOURCECODE_REPOSITORY what do you want to set it to?
>     Its current value is "JOOMLA:3.9.22" press <enter> to retain, anything else to override
>     JOOMLA:4.0.4
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### S3_ACCESS_KEY 
>     ### S3_SECRET_KEY
>     
>     These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 
>     
>     You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:
>     
>     ##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY
>     
>     ##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.
>     
>     ##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.
>     
>     ##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 
>     
>     ##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY
>     
>     -----
>     Found a variable S3_ACCESS_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     AAAA
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### S3_SECRET_KEY
>     
>     These grant you access to manipulate an object store. Under the principle of least privileges, you should grant as few privileges to these keys wen you create them as possible. The DATASTORE_CHOICE setting (see below) will determine which Object Storage you are using and you will need to generate access keys appropriate to that setting. 
>     
>     You can get your S3_ACCESS_KEY and S3_SECRET KEY as follows:
>     
>     ##### digital ocean - Login to your digital ocean account and go to the API submenu (on the left bottom) and generate "Digital Ocean Spaces Keys". This will give you an access key which you can paste into your template. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY
>     
>     ##### exoscale - Login to your exoscale account and go to the IAM menu (on the right) and generate a pair of API keys which have access to object storage capabilities. The first key is the S3_ACCESS_KEY and the second key is the S3_SECRET_KEY which you can post into your template.
>     
>     ##### linode - Login to your Linode account and go to the Object Storage menu on the right then select the Access Key menu and select "Create an Access Key" and that will generate an access key and a secret key which you can copy into your template as S3_ACCESS_KEY and S3_SECRET_KEY.
>     
>     ##### vultr - You need to subscribe to S3 Object Storage and this will grant you a pair of S3 access keys which you can copy and paste into your template. 
>     
>     ##### AWS - Under your IAM user, create a pair of keys which have S3 manipulation capabilities and paste them into your template as S3_ACCESS_KEY and S3_SECRET_KEY
>     
>     -----
>     Found a variable S3_SECRET_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     BBBB
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### S3_HOST_BASE 
>     
>     This parameter is the S3 endpoint for your deployment. It should be located as near as possible to where (in the world) you plan to run your VPS systems.
>     
>     ##### digital ocean - Available endpoints to choose from (2020) - nyc3.digitaloceanspaces.com, ams3.digitaloceanspaces.com, sfo2.digitaloceanspaces.com, sgp1.digitaloceanspaces.com, fra1.digitaloceanspaces.com
>     
>     ##### exoscale - Available endpoints to choose from (2020) - sos-ch-gva-2.exo.io, sos-ch-dk-2.exo.io, sos-de-fra-1.exo.io, sos-de-muc-1.exo.io, sos-at-vie-1.exo.io, sos-bg-sof-1
>     
>     ##### linode - Available endpoints to choose from (2020) - us-east-1.linodeobjects.com, eu-central-1.linodeobjects.com, ap-south-1.linodeobjects.com
>     
>     ##### vultr - Available endpints to choose from (2020) - ewr1.vultrobjects.com, 
>     
>     ##### Amazon - There are lots of S3 endpoints to choose from for Amazon. Your S3 endpoint should be region specific. For example if you are in eu-west-1 in would be, s3.eu-west-1.amazonaws.com
>     
>     You can set your ${S3_HOST_BASE} parameter in your template to one of these listed endpoints depending on who your object storage is hosted with (which will likely be the ssame provider as your VPS systems). 
>     
>     -----
>     Found a variable S3_HOST_BASE what do you want to set it to?
>     Its current value is "sos-ch-gva-2.exo.io" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### ACCESS_KEY
>     ### SECRET_KEY
>     
>     Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively
>     
>     ##### digital ocean - Does not use access keys and secret keys, see TOKEN
>     
>     ##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     ##### linode - Does not use access keys and secret keys, see TOKEN
>     
>     ##### Vultr - Does not use access keys and secret keys, see TOKEN
>     
>     ##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     -----
>     Found a variable ACCESS_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     XXXX
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SECRET_KEY
>     
>     Some providers use an access key and a secret key to control access to their compute resources. You need to generate an access and secret key for your provider and use them here as ACCESS_KEY and SECRET_KEY respectively
>     
>     ##### digital ocean - Does not use access keys and secret keys, see TOKEN
>     
>     ##### exoscale - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     ##### linode - Does not use access keys and secret keys, see TOKEN
>     
>     ##### Vultr - Does not use access keys and secret keys, see TOKEN
>     
>     ##### AWS - You can generate access keys and secret keys to control access to your compute resources. Note, this is distinct from the object storage access keys
>     
>     -----
>     Found a variable SECRET_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     YYYY
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DNS_USERNAME
>     
>     This will be the username for your DNS service provider
>     
>     ##### cloudflare - the emal address of username of your cloudflare account
>     
>     ##### digitalocean - your digital ocean account email address
>     
>     ##### exoscale - your exoscale account email address
>     
>     ##### linode - your linode account email address
>     
>     ##### vultr - your vultr account email address
>     
>     -----
>     Found a variable DNS_USERNAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     testemail@testemail.com
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DNS_SECURITY_KEY 
>     
>     This is the security key which will enable us to manipulate records as needed with your DNS provider. You can find this key as follows for each provider:
>     
>     ##### cloudflare - Ths is the Global API key for your cloudflare account which you can find by clicking on your profile at the top right of the screen
>     
>     ##### digital ocean - The access token for your digital ocean account, (can be the same as TOKEN)
>     
>     ##### exoscale  - The access key and secret key for your exoscale account. You need to enter this as ${ACCESS_KEY}:${SECRET_KEY}. You can use the same access key and secret key as your main account or you can create separate ones with only DNS manipulation rights. 
>     
>     ##### linode - A personal access token with DNS manipulation rights (can be the same value as TOKEN)
>     
>     ##### Vultr - A personal access token with DNS manipulation rights (can be the same as TOKEN)
>     
>     ------
>     Found a variable DNS_SECURITY_KEY what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     CCCC:DDDD
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DNS_CHOICE  
>     
>     This can be set to one of these values 
>     
>     ##### "cloudflare" 
>     ##### "digitalocean" 
>     ##### "exoscale"
>     ##### "linode"
>     ##### "vultr"
>     
>     It defines which of the (supported) DNS service you would like to use with your deployment.
>     
>     ---------------
>     Found a variable DNS_CHOICE what do you want to set it to?
>     Its current value is "exoscale" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     Found a variable CLOUDHOST_EMAIL_ADDRESS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     testemail@testemail.com
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### BUILDOS
>     
>     This is the BUILDOS you wish to use for your servers, it can be one of "ubutnu" or "debian"
>     
>     -----
>     Found a variable BUILDOS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     debian
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### BUILDOS_VERSION
>     
>     This is the BUILDOS_VERSION you are deploying for this can be "20.04" or "22.04" if BUILDOS is "ubuntu" and "10" or "11" if BUILDOS is "debian"
>     
>     -----
>     Found a variable BUILDOS_VERSION what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     11
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### DEFAULT_USER
>     
>     When you deploy to exoscale, the default user should be set to "ubuntu" if you are deploying Ubuntu and "debian" if you are deploying to Debian.
>     When you deploy to AWS, the default user should be set to "ubuntu" if you are deploying Ubuntu and "admin" if you are deploying to Debian.
>     For all other cases, the DEFAULT_USER should be set to "root"
>     
>     -----
>     Found a variable DEFAULT_USER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     debian
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### BUILD_IDENTIFIER
>     
>     This is a unique string to describe your build. If you have multiple builds that you want to give similar names you should call them, for example, "1-testbuild" or "2-testbuild" or "3-testbuild$
>     
>     -----
>     Found a variable BUILD_IDENTIFIER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     nuocial
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### WEBSITE_DISPLAY_NAME
>     
>     This is simply the display name of your application, for example, "My Social Network", or "My Blog" and so on. It should be descriptive of your website and likely will be similar to the core part of the WEBSITE_URL described below
>     
>     -----
>     Found a variable WEBSITE_DISPLAY_NAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     Test Social Network
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### WEBSITE_NAME
>     
>     This HAS to be exactly the same of the core part of the URL name of your website. So, if your website is called www.nuocial.org.uk, then, this value MUST be "nuocial"
>     
>     -----
>     Found a variable WEBSITE_NAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     testsocialnetwork
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### WEBSITE_URL
>     
>     This is the URL of your website. It can be any valid URL
>     
>     -----
>     Found a variable WEBSITE_URL what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     www.testsocialnetwork.org.uk
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_PROVIDER
>     
>     This is the git service provider where your application repositories are hosted. It has to be one of "github", "bitbucket" or "gitlab". If you fill this variable with one of those three exact strings, then, that will tell us who your application code is hosted with. It may or may not be hosted with the same provider as the infrastructure code for the agile deployment toolkit
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_PROVIDER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     github
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_OWNER
>     
>     This is the username of the user who owns (or created) your application repositories with your chosen git service provider
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_OWNER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     adt-demos
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_USERNAME
>     
>     This is the username of the user that you are currently using to access the application repositories. For example, the repositories might be owned by userA and are kept private but, userB is granted access. In this case the APPLICATION_REPOSITORY_OWNER would be userA and the APPLICATION_REPOSITORY_USERNAME would be userB. If you are the application repository owner, then this username and the owner name above will be the same.
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_USERNAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     adt-demos
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_PASSWORD  
>     
>     This is the password for the APPLICATION_REPOSITORY_USERNAME or the application repository user. This is the password for your user account with your git provider. If the application repositories are public (be careful not to expose sensitive credentials if you make your application repos public), then a password is not needed in which case this value must be precisely written or set to **"none"**
>     
>     -----
>     Found a variable APPLICATION_REPOSITORY_PASSWORD what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### APPLICATION_REPOSITORY_TOKEN
>     
>     Github and Gitlab prefer personal access tokens to passwords, so, if you wish to, you can generate personal access tokens at:
>     
>     Github: www.github.com/settings/tokens
>     Gitlab: www.gitlab.com/profile/personal_access_tokens
>     
>     Make sure these tokens have the rights to create and destroy repositories as well as to read and write from them. Most likely, you want to have a separate git provider account for your associated deployments. This will override APPLICATION_REPOSITORY_PASSWORD
>     
>     ------
>     Found a variable APPLICATION_REPOSITORY_TOKEN what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     KKKKK
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_EMAIL_PROVIDER
>     
>     At the moment, there are three SMTP email service providers. Enter the number value, "1", "2" or "3" to select which provider you want to use for your SMTP service. If you leave these variables blank, you simply won't receive any system emails to give status updated on build progression, server intialisations and so on. You are free to leave these variables blank, as you choose.
>     
>     Enter "1" - Sendpulse (www.sendpulse.com)
>     Enter "2" - Google (gmail)
>     Enter "3" - AWS SES 
>     
>     -----
>     Found a variable SYSTEM_EMAIL_PROVIDER what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_TOEMAIL_ADDRESS 
>     
>     The email address that system emails will be sent to this can be any email address that you have access to. MAYBE, the emails get marked as spam depending on your provider. If you take them out of the spam folder, then, the system should learn they are not spam. Most likely you will want to have a dedicated email address for your system emails for your deployed application as they will likely fill up your inbox otherwise.
>     
>     -----
>     Found a variable SYSTEM_TOEMAIL_ADDRESS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_FROMEMAIL_ADDRESS
>     
>     The email address that system emails will be sent from. This should be an email address that the system emails are sent from. In your SYSTEM_TOEMAIL_ADDRESS inbox, this will be the email address that the system messages are seen to be sent from or to have originated from.
>     
>     -----
>     Found a variable SYSTEM_FROMEMAIL_ADDRESS what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_EMAIL_USERNAME
>     
>     This is the username of your SMTP user. For Amazon SES, for example, this will be the username generated when you enable the SES service. This is the SMTP username. 
>     
>     -----
>     Found a variable SYSTEM_EMAIL_USERNAME what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ############################################################################################
>     Explanation from the specification regarding this variable:
>     ############################################################################################
>     ### SYSTEM_EMAIL_PASSWORD
>     
>     This is the password of your SMTP user. For Amazon SES, for example, this will be the password generated when you enable the SES service. This is the SMTP password. 
>     
>     ----
>     Found a variable SYSTEM_EMAIL_PASSWORD what do you want to set it to?
>     Its current value is "" press <enter> to retain, anything else to override
>     
>     OK, thanks...
>     
>     
>     
>     
>     ###################################################################################################################################
>     Do you want to review the rest of the variables that are being used or do you want to accept the default template values
>     If you want to change machine sizes or regions for example, you need to change them here so that they override the templated values
>     ###################################################################################################################################
>     Enter 'y' or 'Y' if you wish to review/override the rest of the variables used by this template, 'N' or 'n' will use the default settings
>     N
>     ######################################################################################################################
>     Cheers. Your configuration has been written to: /home/agile-deployer/new/agile-infrastructure-build-client-scripts/overridescripts/exoscale1override.tmpl
>     You should meticulously review this configuration file before deploying.
>     You can edit and make changes to this configuration file as you desire but keep it with the same filename to deploy it
>     ######################################################################################################################
>     root@VM-cec31855-4825-4c91-aff7-ee0656518555:/home/agile-deployer/new/agile-infrastructure-build-client-scripts/helperscripts# 
>     exit
>     
>     Script done on 2021-12-05 23:26:37+00:00 [COMMAND_EXIT_CODE="0"]



