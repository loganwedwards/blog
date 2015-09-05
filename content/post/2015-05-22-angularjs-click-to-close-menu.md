---
title: AngularJS Click to Close Menu
author: logan
layout: post
date: 2015-05-22
url: /2015/05/angularjs-click-to-close-menu/
categories:
  - Code
tags:
  - AngularJS
  - HTML
  - Javascript
---
Recently, at <a href="http://www.zubie.com" target="_blank">work</a>, I came across (or was told to fix) a need to give a more natural feel to the UX on our web app. We have various menus throughout the app that can be toggled by clicking/touching an element, but the only way to close them is to click/touch the same element again. With mobile UX paradigms making their way into every aspect of our lives, I had to rethink the original approach on how to show or hide content when the user&#8217;s interactions are required. I&#8217;m used to swipes and clicking **off** of elements to close them, so let&#8217;s bring them to our web experience.

AngularJS has a great set of directives, including `ng-show`, which I use extensively to display or hide content based on user interaction or the <a href="http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller" target="_blank">model</a>.

The app is becoming more complex and allows for more interaction that originally designed, so it was time to sit down and fix the wonky interaction!

Here&#8217;s how I solved the problem.

  1. Create a directive to throw on an element that will be interacted with
  2. (Optional) Add a class to child elements where you want to prevent the default close behavior. For this, you&#8217;ll need to modify the directive to check for the existence of the child class.

## Directive

<pre class="lang:js decode:true ">'use strict';
angular.module('app')
    .directive('closeOnClick', function () {
        return {
            scope: {
                watchValue: '='
            },
            restrict: 'EA',
            link: function (scope, element) {
                element.bind('click', function (e) {
                    scope.watchValue = !scope.watchValue;
                    // prevents a double click behavior                    
                    e.stopPropagation();
                    // let Angular know we're doing our thing
                    scope.$apply()
                });
            },
            controller: function ($scope, $document) {
                $document.on('click', function (e) {
                    if ($scope.watchValue) {
                        $scope.watchValue = false;
                        $scope.$apply();
                    }
                });
            }
        }
});</pre>

What is happening is an event handler is bound to the element on creation (during the linking phase). This is what listens to our click and inverts the the watchValue that we defined. The controller function takes care of listening for clicks on the document as a whole and if the menu or object is open (or truthy), then, let&#8217;s go ahead and close/hide the element.

Usage in the view

<pre class="lang:xhtml decode:true" title="Usage in the view">&lt;div close-on-click watch-value="showStuff"&gt;
    &lt;div ng-show="showStuff"&gt;
        &lt;h1&gt;Cool hidden stuff&lt;/h1&gt;
    &lt;/div&gt;
&lt;/div&gt;</pre>

That&#8217;s it! Now, we have an improved user experience with Angular&#8217;s most powerful component, directives!