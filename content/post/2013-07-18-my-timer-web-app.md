---
title: My Timer Web App
author: logan
layout: post
date: 2013-07-18
url: /2013/07/my-timer-web-app/
categories:
  - Projects
tags:
  - Brackets
  - CSS3
  - HTML5
  - Javascript
  - JQuery
  - webkit
---

![Hero Image](/img/2013/07/Clock-Promo-Med.jpg)

I spent the weekend cooking up a [web app](https://chrome.google.com/webstore/detail/timer/keajpdeigjicancnhaknebefgekooiof?hl=en-US). It&#8217;s fairly simple. Three files serves up everything I need for a simple timer (a few more added so it could be published as a packaged app in the Chrome Web Store). I feel that I have followed the MVC design intent fairly well with a HTML file (for content organization), a CSS file (for beautification and some animation) and a Javascript file to handle the timer functionality. I learned quite a bit and the saying that I&#8217;m used to at my day job still applies: nothing is rarely ever as simple as it seems. Let me explain. I had to figure out and overcome some default behaviors for styling as well as how to implement my own timing function. I&#8217;m sure there is a library somewhere, but no better way to learn than to implement it yourself. I did find some great resources, which will be posted at the bottom.

## HTML

The markup is short and sweet. Keep in mind that all of the imagery is pure HTML and CSS; no images were uploaded. I basically set a bunch of `div` elements up to arrange the second hand, the clock face and the control labels.

## CSS

This was fun. I&#8217;ve used the `transition` and `transform` properties before, but combining this with `keyframes` opens up interesting animation possibilities.

To animate the hand, a JQuery selector adds this class:

    .animation {
      animation: orbit 60s steps(360) infinite;
      -webkit-animation: orbit 60s steps(360) infinite;
      animation-duration: 60s;
      -webkit-animation-duration: 60s;
    }



I created an animation property called orbit. I directly prescribed the animation conditions at 0, 50 and 100% of the animation:


    @-webkit-keyframes orbit {
      0% {
        -webkit-transform: rotate(180deg);
        -webkit-transform-origin:top;
        transform: rotate(180deg);
        transform-origin:top;
      }
      50% {
        -webkit-transform: rotate(360deg);
        -webkit-transform-origin:top;
        transform: rotate(360deg);
        transform-origin:top;
      }
      100% {
        -webkit-transform: rotate(540deg);
        -webkit-transform-origin:top;
        transform: rotate(540deg);
        transform-origin:top;
      }
    }


## Javascript (JQuery)

I used JQuery to speed up development time and let me focus on the fun stuff: the timing! Since calculating times can be a bit tricky since I want the screen to continually update the elapsed time, since you know, I&#8217;m making a timer application! I accomplished this with the built-in `setInterval()` function. I feel that it is called often enough for a simple timer app (10 times / second). The interesting part on how the timing works is below. Note: Some variables were defined outside of the scope shown below. The main takeaway was how to deal with pausing and resuming the timer: a global variable `$prevTime` was used to store the total elapsed time, which was added to the current timer. Note: On the output, there should be a `p` wrapped around the `formatTime($totalTime)` call&#8230; something strange with WordPress&#8217; text editor removing these.


    $("#start").click(function () {

    if(!$running){
    $running = true; // Ensure that we can't start a 2nd concurrent timer

    $start = new Date().getTime();

    $doTime = window.setInterval(function() {clock($prevTime);},100);


    // Run this function on setInterval to continuously update
    // the time shown on the page.


    function clock($p) {
    $prevTime = $p; // pass in the previous time
    $time = (new Date().getTime() - $start); // start calculating

    $time = ($time / 100) / 10;
    $time += parseFloat($prevTime); // add previously elapsed time

    $totalTime = ($time).toFixed(2); // set to 2 decimals
    $("#time").html("<span>" + formatTime($totalTime) + "</span>");
    }


I implemented a simple version of a `printf`-like function for the time format.


    function formatTime($tIn) {
    var $hr, $min, $sec;
    var $t = $tIn;
    var $out = "";
    $hr = Math.floor($t / 3600); // hold the hours
    $t -= $hr * 3600; // update the time var
    $min = Math.floor($t / 60); // hold the minutes
    $t -= $min * 60; // update the time var
    $sec = $t.toFixed(2); // assign the seconds


    // Some basic formatting for the output.
    // Note this is a string and is not the
    // number used for any time calculations.
    
    $out = $hr + ":" + $min + ":" + $sec;
    return $out;
    };


The code is hosted on my <a title="Github" href="https://github.com/loganwedwards/HTML-Timer" target="_blank">Github account</a>.

 [1]: http://www.le-create.com/blog/wp-content/uploads/2013/07/Clock-Promo-Med.jpg
