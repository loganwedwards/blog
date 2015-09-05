---
title: Transferring Domains with Google Apps and GoDaddy
author: logan
layout: post
date: 2012-05-05
url: /2012/05/transferring-domains-with-google-apps-and-godaddy/
categories:
  - Stuff
tags:
  - bluehost
  - godaddy
  - google apps
  - host
  - registrar
  - transfer
  - web
---
A lengthy title, I know, but being that I just went through this process, I felt it was good to let others know of the steps before I purge them from my memory.

For a personal reason, I decided to transfer my domain from GoDaddy to my current host. The process of transferring domain names is not truly simple (as it can differ from registrar to registrar), but these are the general steps that I took to transfer the domain from GoDaddy to Bluehost, my current host (and new registrar):

1. Sign in to Google Apps and click on the &#8220;Domain Settings&#8221; tab. From there, go to &#8220;Domain Names&#8221; and follow the link for &#8220;Advanced DNS settings.&#8221;
![Google Apps Console](/img/2012/05/Screen-shot-2012-01-26-at-7.06.34-PM.png)
2. Login to the GoDaddy domain manager and unlock your domain (you may see a lock icon).
![GoDaddy Domain Change](/img/2012/05/Screen-shot-2012-01-26-at-7.05.48-PM.png)
3. While still logged into the GoDaddy domain manager, click on your domain. Under domain details, there is a link to send and _Authorization Code_ via email. You will also notice that under &#8220;Domain Enhancements&#8221; that _Privacy_ is set to on; it will need to be disabled, but will be performed later.
4. To disable privacy, login to domainsbyproxy.com. I don&#8217;t recall ever receiving credentials for this site, so I just requested the password (which actually sends you the required username). Using the recovered username and the password from your Google Apps account found in step 1, select the domain and click the button to &#8220;Cancel private registration.&#8221;
![domainsbyproxy pre login](/img/2012/05/Screen-shot-2012-01-26-at-6.52.40-PM.png)
![domainsbyproxy first step](/img/2012/05/Screen-shot-2012-01-26-at-6.55.06-PM.png)
![Domainsbyproxy](/img/2012/05/Screen-shot-2012-01-26-at-6.55.56-PM.png)
5. Login to your Bluehost cPanel to transfer the domain to your new registrar. Follow the steps (providing the authorization codes, as needed). It may take some time, but this should be what is needed to successfully transfer your domain from GoDaddy to Bluehost.

This is a fairly specific circumstance, but I figured since I&#8217;ve been there, someone else has/or will too. To setup using my new host with Gmail, I just used their built in wizard to handled all of the details.
