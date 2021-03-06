---
layout: post
description: The Agile Deployment Toolkit Introduction
title: Introduction
permalink: /introduction/
hide: true
category: agiledeploymenttoolkit
---

### [Agile Deployment Toolkit](https://github.com/agile-deployer)

* Is shared hosting not the ideal solution for your web hosting?

* Do you want to have your own set of configured VPS servers but do not want to spend the time configuring and deploying software on them?

* Do you want to have consistent security processes baked in to your server deployments? 

* Would you like to be able to redeploy to a different (supported) VPS host easily - within 20 minutes or so if needed?

* Does automated server configuration with the latest releases of software included for each deployment sound attractive?

* Would you like a low barrier to entry solution using nothing but basic scripting techniques?

Then you might be interested in the Agile Deployment Toolkit which currently supports Joomla, Wordpress, Moodle and Drupal CMS applications. 

--------------

**MOTIVATION:** You can find lots of tutorials online which show how to install and configure server machines using products such as Apache, Nginx, Mysql, Postgres and so on. Following these tutorials to build your own server system is time consuming and possibly error prone if, for example, you don't remember to do everything with regard to security when you build your server, you could have problems. Because for most of the systems that I want to deploy a common architecture is possible, what I decided to do was write some scripts for my own use and which I share here which would automate the building of my servers in a consistent and predictable way. Using my software, popular CMS systems can be deployed starting from scratch with brand new VPS machines in minutes rather than possibly hours or even days providing nothing to the scripts but configuration parameters. For some people, this solution might be a good fit for their server deployments rather than having to follow tutorials and so on. There are alternative "infrastructure as code" methods but my approach is a bit more traditional. With this method, you still have full access to your VPS systems to tinker with the configuration, or, you could modify the scripts directly to attain an "other than default" configuration for your server systems. This approach has application backups and so on built in and the scripts are written to be extensible by anyone. 

You can deploy to any one of several major cloud providers according to your needs. This toolkit uses the term "agile" to indicate that it's easy to redeploy to another one of the supported cloudhosts should your current cloudhost not support your needs at any point in time- in an agile way.  This toolkit is ideal for anyone who wants to investigate how to, or is a student of how to run their own server systems. It gives a unique, consistent way of server deployment which can be reviewed, tweaked and understood in the same way that car enthusiasts might review, tweak and understand the inner workings of their cars. The intention is to use this for serious systems, but, learners or students might find it of benefit if they want to experiment with server configurations and so on. 

Many VPS providers out there, don't necessarily have clear processes for deploying scalable CMS systems in a manner in which you as a developer retain full control, so, maybe, if that's the case, this might help. This toolkit is built from the ground up to be extensible so, if you have a use case or requirement that it doesn't fulfil, you are welcome to fork the repositories and extend as your needs demand, if, for example, you wanted to support "Cake PHP" or some other framework its quite possible to "fork and extend". There's many many PHP applications out there and almost certainly with appropriate extensions to support these applications it should be possible that they can be deployed and operated at scale.  The design pattern of this toolkit essentially akin to a CMS system's design in that I write and maintain a core set of scripts and other developers, if they choose to, can extend the scripts to meet additional needs or requirements. The ultimate aim is to be able to treat whole applications as "out of the box" solutions.  

**OBJECTIVE:** To provide a well written and designed toolkit which facilitates repeated bespoke CMS application deployments to various VPS providers with customised branding using nothing but command line configuration options.

--------------------

#### Below is  a list of VPS cloud hosts that this toolkit currently supports.

--------------------

[![Digital Ocean](https://www.codebreakers.uk/images/do.png "Digital Ocean Cloud Hosting")](http://www.digitalocean.com)

Digital Ocean is a cloudhost that is simple to use and global. They also provide managed databases and so on, so their service offering is growing. 

&nbsp;  
&nbsp;  
&nbsp;  
&nbsp;  

-------------------

[![Exoscale](https://www.codebreakers.uk/images/exoscale.svg "Exoscale Cloud Hosting")](http://www.exoscale.com)


Exoscale is a Swiss cloudhost, so, if you like the idea of being with a Europe centric cloudhost because their datacentres are either in Switzerland or elsewhere in Europe.  

&nbsp;  
&nbsp;  
&nbsp;  
&nbsp;  

---------------------

[![Linode](https://www.codebreakers.uk/images/lin.svg "Linode Cloud Hosting")](http://www.linode.com)


Linode is a cloudhost from the US with global reach. Again, their interfaces are simple and their service offerings are expanding.   

&nbsp;  
&nbsp;  
&nbsp;  
&nbsp;   

----------------------

[![Vultr](https://www.codebreakers.uk/images/vult.png "Vultr Cloud Hosting")](http://www.vultr.com)


Vultr are a smart cloudhosting company. They seem particularly strong on security to me with processes and so on in place to make sure that things are tied down in terms of security.  

&nbsp;  
&nbsp;  
&nbsp;  
&nbsp;  

----------------------

[![AWS](https://www.codebreakers.uk/images/aws.png "Amazon Web Services")](http://www.aws.com)

AWS is the world's largest cloudhost. It also provides a plethora of services such as managed databases and so on which means that your application will be well served if you deploy here. 
&nbsp;  
&nbsp;  
&nbsp;  
&nbsp;  

------------------------


