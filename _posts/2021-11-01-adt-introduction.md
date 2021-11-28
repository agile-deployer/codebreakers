---
layout: post
description: The Agile Deployment Toolkit Introduction
title: Introduction
permalink: /introduction/
hide: true
---

### [Agile Deployment Toolkit](https://github.com/agile-deployer)

* Is shared hosting not the ideal solution for your web hosting?

* Do you want to have your own set of configured VPS servers but do not want to spend the time configuring and deploying software on them?

* Do you want to have consistent security processes baked in to your server deployments? 

* Would you like to be able to redeploy to a different (supported) VPS host easily - within 20 minutes or so, if you needed to?

* Does automated server configuration with the latest releases of software included for each deployment sound attractive?

* Would you like a low barrier to entry solution using nothing but basic scripting techniques?

Then you might be interested in the Agile Deployment Toolkit which currently supports Joomla, Wordpress, Moodle and Drupal CMS applications. 

--------------

**MOTIVATION:** You can find lots of tutorials online which show how to install and configure server machines using products such as Apache, Nginx, Mysql, Postgres and so on. Following these tutorials to build your own server system is time consuming and possibly error prone if, for example, you don't remember to do everything with regard to security when you build your server, you could have problems. What I decided to do was write some scripts which would automate the building of my servers in a consistent and predictable cross platform way. In this way, popular CMS systems can be deployed starting from scratch with brand new VPS machines in minutes rather than possibly hours or even days providing nothing to the scripts but configuration parameters. For some people, this solution might be a good fit for their server deployments rather than having to follow tutorials and so on. With this method, you still have full access to your VPS systems to tinker with the configuration or you could modify the scripts directly to attain an "other than default" configuration for your server systems. This approach has application backups and so on built in and the scripts are written to be extensible by anyone. 

Deploy to any one of several major cloud providers according to your needs. This toolkit uses the term agile to indicate that it's easy to redeploy to another one of the supported cloud hosts should your current cloudhost not support your needs - in an agile way.  This toolkit is ideal for anyone who wants to investigate how to run their own server systems. It gives a unique, consistent way of server deployment which can be reviewed, tweaked and understood in the same way that car enthusiasts might review, tweak and understand the inner workings of their cars.

Many VPS providers out there, don't necessarily have clear processes for deploying scalable CMS systems, so, maybe, if that's the case, this might help. This toolkit is built from the ground up to be extensible so, if you have a use case or requirement that it doesn't fulfil, you are welcome to fork the repositories and extend as your needs demand. There's many many PHP applications out there and almost certainly with appropriate extensions to these scripts they can be deployed and operated at scale.  The design pattern here is essentially akin to a CMS system's design in that I write and maintain a core set of scripts and other developers, if they choose to, can extend the scripts to meet additional needs or requirements. 

**OBJECTIVE:** To provide a well written and designed toolkit which facilitates repeated bespoke CMS application deployments to various VPS providers with customised branding using nothing but command line configuration options.

**NOTE:**  I am open to all improvement suggestions and the toolkit has been written to be easily extensible in all regards, so you are free to extend this toolkit to meet your own needs should your requirements fall outside that which is already supported. 

--------------------

Below is  a list of VPS cloud hosts that this toolkit currently supports.

![]({{ site.baseurl }}/images/do.jpg "Digital Ocean Cloud Hosting") 
<img src="/images/do.jpg" alt="Digital Ocean Cloud Hosting" width="250" height="250">



![]({{ site.baseurl }}/images/exo.png "Exoscale Cloud Hosting")  

![]({{ site.baseurl }}/images/lin.png "Linode Cloud Hosting")  

![]({{ site.baseurl }}/images/vult.jpg "Vultr Cloud Hosting")  

![]({{ site.baseurl }}/images/aws.png "Amazon Web Services")  


