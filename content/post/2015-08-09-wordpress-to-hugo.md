+++
date = "2015-08-09T16:27:05-04:00"
title = "Wordpress to Hugo"
+++

Wordpress is arguably the most prolific blogging platform. It's actually more than
that really. It's a full-featured CMS and while it has its uses, I've fallen out of
love with all the overhead of just keeping a simple blog going. This is the first
post written on Hugo, a static site generator written in Go.

I've decided to leave a dynamic CMS in favor of a simpler solution that fits my workflow
of a software engineer better.

### I don't need:

* Expensive hosting
* To deal with PHP
* To deal with security around MYSQL
* To manage a software stack for a simple blog

___

### I do like:

* Markdown
* Fast websites
* Low cost
* Open source (Wordpress falls into here too)
* Using the same tools as my normal dev workflow
* Learning something new (in this case Go and Go templating)

Using Hugo requires a bit upfront work to get things deploying automatically, but once
that is setup, my blog is deployed with a simple `git push`. I used [Wercker](http://app.wercker.com) as suggested on Hugo's official site. It even supports
Docker out of the box! So this project alone has let me touch a bunch of new areas and
now I can focus on writing content.

My wife has a food blog, chocolateandcarrots.com, where she needs to deal with users,
comments, nested taxonomies and a simple UI for managing her content, so she'll stick
with Wordpress for now.
