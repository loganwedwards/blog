---
title: Helpful Plugins for Migrating WordPress from localhost to Production
author: logan
layout: post
date: 2014-03-09
url: /2014/03/helpful-plugins-for-migrating-wordpress-from-localhost-to-production/
categories:
  - Web
tags:
  - development
  - php
  - Wordpress
---
There are some tutorials available for migrating a local instance of WordPress to a live instance for the world to see. In my case, I was ready to deploy some local development to the host, but in my case, I was adding a new custom child theme based on twenty-thirteen (it&#8217;s live at [chocolateandcarrots.com][1]). I was pursuing the path of creating a brand new instance of WordPress using a new, clean database, but problems arose when trying to import the content, specifically the post&#8217;s featured image. For some reason, the links would not update, even though everything was on the same server. I&#8217;d like to share some of the plugins I used for a smooth transition from local development to production:

  * <a title="Search and Replace" href="http://bueltge.de/wp-suchen-und-ersetzen-de-plugin/114/" target="_blank">Search and Replace</a> by Frank Bultge: This plugin allows to replace strings in the database. I mostly used this when downloading the production database and content (for offline development). I would essentially replace the host url with &#8216;localhost:8888&#8242; (port 8888 since that&#8217;s the default set by MAMP), so all of the content would properly render.
  * <a title="Regenerate Thumbnails" href="http://www.viper007bond.com/wordpress-plugins/regenerate-thumbnails/" target="_blank">Regenerate Thumbnails</a> by Viper007Bond: I&#8217;m sure I would have pulled my hair out if I didn&#8217;t find this plugin. Since the website I was working on is image heavy, having a featured post for the blog page was essential. After setting the custom thumbnail size in the WordPress admin area and adding the hook in functions.php, I fired up the plugin and it automagically reproduced thumbnails for my posts. Ahhh!

If you need to do some WordPress administration for batch jobs, I highly recommend these plugins.

 [1]: http://chocolateandcarrots.com "chocolateandcarrots.com"