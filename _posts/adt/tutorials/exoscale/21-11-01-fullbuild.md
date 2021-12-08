---
layout: post
description: The Agile Deployment Toolkit Exoscale Tutorials Full Build
title: Exoscale ADT Tutorials Full Build
permalink: /adtexoscaletutorialsfullbuild/
hide: true
category: agiledeploymenttoolkit
---

**PREBUILD NECESSITIES**

If you don't already have a build machine running in the Exoscale cloud, follow these steps to get ready for the main build)

1. Begin by following this: [Build Machine Setup](https://www.codebreakers.uk/adtexoscaletutorialsbuildmachineexpedited/)  

2. At this point, your build machine should be up and running. Please review [Tightening Build Machine Firewall](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/TightenBuildMachineAccess.md). At this point, your build machine will only accept connections from your laptop. If you need access from other ip addresses you need to use the technique described in "Tightening Build Machine Firewall" to grant access to additional IP addresses. This will be the case every time your laptop changes its IP address as you travel about, so, you might want to setup and configure an S3 client on your laptop to enable you to grant access to new IP addresses easily. 

-----------------------------

**FULL BUILD PROCESS**

The full build process is interactive and guided so you need to answer the questions it posits when it posits them to perform a full build:

>     ssh onto the build machine you started in 1. from your laptop.

>     cd /home/<username>/agile-infrastructure-build-client-scripts/
  
>     /bin/sh AgileDeploymentToolkit.sh
  
Once you run this script you will prompted to enter various credentials as required. 


