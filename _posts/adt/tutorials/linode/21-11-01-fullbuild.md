---
layout: post
description: The Agile Deployment Toolkit Linode Tutorials Full Build
title: Linode ADT Tutorials Full Build
permalink: /adtlinodetutorialsfullbuild/
hide: true
category: agiledeploymenttoolkit
---

**PREBUILD NECESSITIES**

If you don't already have a build machine running in the Linode cloud, follow these steps to get ready for the main build)

1. Begin by following this: [Build Machine Setup](https://www.codebreakers.uk/adtlinodetutorialsbuildmachineexpedited/)  

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

> I then need a personal access token so I go to the top right and select "API Keys" and generate a personal access token with 

> Account,Domains, Images, IPs, Linodes, Object Storage, Stackscripts and Volumes

> scope enabled. This personal access token I shall give a value of "AAAAA"

**IMPORTANT EDIT: To use the native firewalling system the linode-cli tool seems to only accept personal access tokens with full access rights, so, whilst that is the case, you will need to ignore the above scoping and just chose "Select All" with "Read and Write" access when you create your personal access token.** 

>     linode_personal_access_token="AAAAA"  where AAAAA is the actual values generated when I click "Create Token"

-------------------------

You now need to set up Object Storage and obtain Object Storage Keys. You can do this by Selecting Object Storage on the left hand side of your Linode console. 

You then click "Access Key" and then, "Create Access Key" and this will display an "Access Key" and a "Secret Key" which you need to make a note of and keep safe:

>     linode_S3_access_key="BBBBB"
>     linode_S3_secret_key="CCCCC"


-----------------------------------

You now need to make a note of the email address that you have registered with your linode account:

>     linode_email="testemail@testemail.com"

-----------------------------------

You then need the url that you want to use for your website. If you don't have a DNS URL for your website, you need to purchase one and set the nameservers to linode as described in ./agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/Nameservers.md

>     linode_dns_name="www.testsocialnetwork.org.uk"

-------------------------------

You then need the username and owner of you git provider application repositories.
To do this, if you don't have a git account sign up with one (in this case using github, but, you have the choice of bitbucket and gitlab as well) and record the username that you sign up with:

>     gitusername="mytestgituser"

Then create a "personal access token" by following: 

[Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) making sure you give it all "repo" permissions as well as the "delete repository" permission

>     gitpersonalaccesstoken="KKKKK" where KKKKK represents your actual personal access token

--------------------------------

**THE ACTUAL BUILD**

The full build process is interactive and guided so you need to answer the questions it posits when it posits them to perform a full build:

>     ssh onto the build machine you started in 1. from your laptop.

>     cd /home/<username>/agile-infrastructure-build-client-scripts/
  
>     /bin/sh AgileDeploymentToolkit.sh
  
Once you run this script you will prompted to enter various credentials as required. 
