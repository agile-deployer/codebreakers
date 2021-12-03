---
layout: post
description: The Agile Deployment Toolkit Exoscale Tutorials Expedited Virgin
title: Exoscale ADT Tutorials Expedited Text
permalink: /adtexoscaletutorialsexpeditedvirgin/
hide: true
category: agiledeploymenttoolkit
---

1. Begin by following this: [Build Machine Setup](https://www.codebreakers.uk/adtexoscaletutorialsbuildmachine/)  

2. At this point, your build machine should be up and running. Please review [Tightening Build Machine Firewall](https://github.com/agile-deployer/agile-infrastructure-build-client-scripts/blob/master/doco/AgileToolkitDeployment/TightenBuildMachineAccess.md). At this point, your build machine will only accept connections from your laptop. If you need access from other ip addresses you need to use the technique described in "Tightening Build Machine Firewall" to grant access to additional IP addresses. This will be the case every time your laptop changes its IP address as you travel about, so, you might want to setup and configure an S3 client on your laptop to enable you to grant access to new IP addresses easily.  

3. [Here](https://www.codebreakers.uk/adtexoscaletutorialsexpeditedvirgin/) is an example of how you run through a build of the latest version of Joomla using the expedited method.

4. The next step is to use your new virgin CMS installation to build you use case specific application customisations which may take weeks depending on how complex your application needs to be. You most likely will want to take baselines of your application along the way until you have your final baseline of your application in place. A baseline is basically a copy of your webroot and your dstabase stored in your application git repository that can be redeployed as many times as needed. In order to create your baseline follow what I write here: 