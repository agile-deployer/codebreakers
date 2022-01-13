---
layout: post
description: The Agile Deployment Toolkit Vultr Tutorials Full Build
title: Vultr ADT Tutorials Full Build
permalink: /adtvultrtutorialsfullbuild/
hide: true
category: agiledeploymenttoolkit
---

**PREBUILD NECESSITIES**

If you don't already have a build machine running in the Vultr cloud, follow these steps to get ready for the main build)

1. Begin by following this: [Build Machine Setup](https://www.codebreakers.uk/adtvultrtutorialsbuildmachineexpedited/)  

2. At this point, your build machine should be up and running. Please review [Tightening Build Machine Firewall](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/TightenBuildMachineAccess.md). At this point, your build machine will only accept connections from your laptop. If you need access from other ip addresses you need to use the technique described in "Tightening Build Machine Firewall" to grant access to additional IP addresses. This will be the case every time your laptop changes its IP address as you travel about, so, you might want to setup and configure an S3 client on your laptop to enable you to grant access to new IP addresses easily. 

-----------------------------

**FULL BUILD PROCESS**

To begin with you will need to have prepared, as a mimimum, for a Joomla interactive build the following information:

To find the latest version of Joomla, I go to this URL in my browser:

[Joomla Latest](https://downloads.joomla.org/)

And I note the latest version in a separate text file:

>     joomla_version="4.0.4"  

You can of course use a legacy version of joomla also by choosing a different version numnber. 

-------------------------------------

I then need a set of compute access keys so, I go to the IAM option on my vultr dashboard and generate an IAM key with compute access. In my separate text file, I record:

>     vultr_access_key_compute="XXXXX"  where XXXXX and YYYYY are the actual values generated when I click "Add Key"
>     vultr_secret_key_compute="YYYYY"

I then need a set of Object Storage (S3) access keys so, I go to the IAM option on my vultr dashboard and generate an IAM key with S3 access. In my separate text file, I record:

>     vultr_access_key_s3="AAAAA"  where AAAAA and BBBBB are the actual values generated when I click "Add Key"
>     vultr_secret_key_s3="BBBBB"


I then need a set of DNS access keys so, I go to the IAM option on my vultr dashboard and generate an IAM key with DNS access. In my separate text file, I record:

>     vultr_access_key_dns="CCCCC"  where CCCCC and DDDDD are the actual values generated when I click "Add Key"
>     vultr_secret_key_dns="DDDDD"

**NOTE:** Alternatively you could generate one set of IAM keys and give that one set all three permissions, Compute, DNS and S3. You wouldn't have to juggle three set of keys then and could use the same key pair in all three cases.

-----------------------------------

You now need to make a note of the email address that you have registered with your vultr account:

>     vultr_email="testemail@testemail.com"

-----------------------------------

You then need the url that you want to use for your website. If you don't have a DNS URL for your website, you need to purchase one and set the nameservers to vultr as described in ./agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/Nameservers.md

>     vultr_dns_name="www.testsocialnetwork.org.uk"

-------------------------------

You then need the username and owner of you git provider application repositories.
To do this, if you don't have a git account sign up with one (in this case using github, but, you have the choice of bitbucket and gitlab as well) and record the username that you sign up with:

>     gitusername="mytestgituser"

Then create a "personal access token" by following: 

[Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) making sure you give it all "repo" permissions

>     gitpersonalaccesstoken="KKKKK" where KKKKK represents your actual personal access token

--------------------------------

**THE ACTUAL BUILD**

The full build process is interactive and guided so you need to answer the questions it posits when it posits them to perform a full build:

>     ssh onto the build machine you started in 1. from your laptop.

>     cd /home/<username>/agile-infrastructure-build-client-scripts/
  
>     /bin/sh AgileDeploymentToolkit.sh
  
Once you run this script you will prompted to enter various credentials as required. 
