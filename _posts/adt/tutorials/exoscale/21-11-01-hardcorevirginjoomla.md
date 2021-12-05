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





